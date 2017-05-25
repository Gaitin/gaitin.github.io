---
layout: post
title:  "checkBoxDemo"
date:   2017-05-25 17:07:35 +0800
categories: demo
tags: [demo]
---
### checkBoxDemo ###


绑定合适的事件处理函数，实现以下逻辑：

当用户勾上“全选”时，自动选中所有语言，并把“全选”变成“全不选”；

当用户去掉“全不选”时，自动不选中所有语言；

当用户点击“反选”时，自动把所有语言状态反转（选中的变为未选，未选的变为选中）；

当用户把所有语言都手动勾上时，“全选”被自动勾上，并变为“全不选”；

当用户手动去掉选中至少一种语言时，“全不选”自动被去掉选中，并变为“全选”。




<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<!-- HTML结构 -->
<form id="test-form" action="test" style="width: 300px;height: 300px;background-color: #eee">
    <legend>请选择想要学习的编程语言：</legend>
    <fieldset>
        <p><label class="selectAll"><input type="checkbox"> <span class="selectAll">全选</span><span class="deselectAll">全不选</span></label> <a href="javascript:;" class="invertSelect">反选</a></p>
        <p><label><input type="checkbox" name="lang" value="javascript"> JavaScript</label></p>
        <p><label><input type="checkbox" name="lang" value="python"> Python</label></p>
        <p><label><input type="checkbox" name="lang" value="ruby"> Ruby</label></p>
        <p><label><input type="checkbox" name="lang" value="haskell"> Haskell</label></p>
        <p><label><input type="checkbox" name="lang" value="scheme"> Scheme</label></p>
        <p><button type="submit">Submit</button></p>
    </fieldset>
</form>
<script src="https://cdn.bootcss.com/jquery/1.12.4/jquery.js"></script>
<script>
    'use strict';

    var
        form = $('#test-form'),
        langs = form.find('[name=lang]'),
        selectAll = form.find('label.selectAll :checkbox'),
        selectAllLabel = form.find('label.selectAll span.selectAll'),
        deselectAllLabel = form.find('label.selectAll span.deselectAll'),
        invertSelect = form.find('a.invertSelect');

    // 重置初始化状态:
    form.find('*').show().off();
    form.find(':checkbox').prop('checked', false).off();
    deselectAllLabel.hide();
    // 拦截form提交事件:
    form.off().submit(function (e) {
        e.preventDefault();
        alert(form.serialize());
    });



    $('.selectAll input:first-child').on('click',function () {
        if(this.checked){
            $('input[name=lang]').prop('checked',true);
            selectAllLabel.hide();
            deselectAllLabel.show();
        }else{
            $('input[name=lang]').prop('checked',false);
            selectAllLabel.show();
            deselectAllLabel.hide();
        }
    });
    
    $('.invertSelect').on('click',function () {
        let list=$('input[name=lang]');
        let checkList=$('input[name=lang]:checked');
        let notChecked=$('input[name=lang]').not('input:checked');
        //选中的变为未选中，未选中变为选中
        checkList.prop('checked',false);
        notChecked.prop('checked',true);
        
        let checkList1=$('input[name=lang]:checked');
        if(checkList1.length==list.length){
            $('.selectAll input:first-child').prop('checked',true);
            selectAllLabel.hide();
            deselectAllLabel.show();
        }else{
            $('.selectAll input:first-child').prop('checked',false);
            selectAllLabel.show();
            deselectAllLabel.hide();
        }

    });

    $('input[name=lang]').on('click',function () {
        let list=$('input[name=lang]');
        let checkList=$('input[name=lang]:checked');

        if(checkList.length==list.length){
            $('.selectAll input:first-child').prop('checked',true);
            selectAllLabel.hide();
            deselectAllLabel.show();
        }else{
            $('.selectAll input:first-child').prop('checked',false);
            selectAllLabel.show();
            deselectAllLabel.hide();
        }

    })

</script>
</body>
</html>

### 代码 ###
	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <title>Title</title>
	</head>
	<body>
	<!-- HTML结构 -->
	<form id="test-form" action="test" style="width: 300px;height: 300px;background-color: #eee">
	    <legend>请选择想要学习的编程语言：</legend>
	    <fieldset>
	        <p><label class="selectAll"><input type="checkbox"> <span class="selectAll">全选</span><span class="deselectAll">全不选</span></label> <a href="javascript:;" class="invertSelect">反选</a></p>
	        <p><label><input type="checkbox" name="lang" value="javascript"> JavaScript</label></p>
	        <p><label><input type="checkbox" name="lang" value="python"> Python</label></p>
	        <p><label><input type="checkbox" name="lang" value="ruby"> Ruby</label></p>
	        <p><label><input type="checkbox" name="lang" value="haskell"> Haskell</label></p>
	        <p><label><input type="checkbox" name="lang" value="scheme"> Scheme</label></p>
	        <p><button type="submit">Submit</button></p>
	    </fieldset>
	</form>
	<script src="https://cdn.bootcss.com/jquery/1.12.4/jquery.js"></script>
	<script>
	    'use strict';
	
	    var
	        form = $('#test-form'),
	        langs = form.find('[name=lang]'),
	        selectAll = form.find('label.selectAll :checkbox'),
	        selectAllLabel = form.find('label.selectAll span.selectAll'),
	        deselectAllLabel = form.find('label.selectAll span.deselectAll'),
	        invertSelect = form.find('a.invertSelect');
	
	    // 重置初始化状态:
	    form.find('*').show().off();
	    form.find(':checkbox').prop('checked', false).off();
	    deselectAllLabel.hide();
	    // 拦截form提交事件:
	    form.off().submit(function (e) {
	        e.preventDefault();
	        alert(form.serialize());
	    });
	
	
	
	    $('.selectAll input:first-child').on('click',function () {
	        if(this.checked){
	            $('input[name=lang]').prop('checked',true);
	            selectAllLabel.hide();
	            deselectAllLabel.show();
	        }else{
	            $('input[name=lang]').prop('checked',false);
	            selectAllLabel.show();
	            deselectAllLabel.hide();
	        }
	    });
	    
	    $('.invertSelect').on('click',function () {
	        let list=$('input[name=lang]');
	        let checkList=$('input[name=lang]:checked');
	        let notChecked=$('input[name=lang]').not('input:checked');
	        //选中的变为未选中，未选中变为选中
	        checkList.prop('checked',false);
	        notChecked.prop('checked',true);
	        
	        let checkList1=$('input[name=lang]:checked');
	        if(checkList1.length==list.length){
	            $('.selectAll input:first-child').prop('checked',true);
	            selectAllLabel.hide();
	            deselectAllLabel.show();
	        }else{
	            $('.selectAll input:first-child').prop('checked',false);
	            selectAllLabel.show();
	            deselectAllLabel.hide();
	        }
	
	    });
	
	    $('input[name=lang]').on('click',function () {
	        let list=$('input[name=lang]');
	        let checkList=$('input[name=lang]:checked');
	
	        if(checkList.length==list.length){
	            $('.selectAll input:first-child').prop('checked',true);
	            selectAllLabel.hide();
	            deselectAllLabel.show();
	        }else{
	            $('.selectAll input:first-child').prop('checked',false);
	            selectAllLabel.show();
	            deselectAllLabel.hide();
	        }
	
	    })
	
	</script>
	</body>
	</html>