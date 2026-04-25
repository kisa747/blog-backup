---
layout: post
title: Wordpress 一键填写评论者信息
date: 2010-09-20
tags: ["wordpress","技巧","评论"]
---

评论可以说是博客生命的源泉，但是每次评论时都要手动输入昵称、邮箱、网址，是不是太麻烦了？有了下面的 JS 代码，就可以轻松实现一键填写评论者信息。代码参考自：[http://cheon.info/1161](http://cheon.info/1161)。

**使用方法**：在下面的信息输入框中输入对应的信息，点击生成代码，拖拽下面的链接"**快速填写 WP 评论信息**"到您的书签工具栏或者右键单击链接把它添加到您的收藏夹中即可，以后在要评论的页面，点击该书签，所有的信息就自动填上去了，是不是很酷呢？

<!-- more -->

```js
<script type="text/javascript">
(function($){
	$(document).ready(function() {
		$('.code_result').hide();
		$('#generate_code').click(function(){
			var re = /^[0-9a-zA-Z]+([\.\-\_][0-9a-zA-Z]+)*@[0-9a-zA-Z]+([\.\-][0-9a-zA-Z]+)*.[a-zA-Z]+$/;
			if($('#commenter_author').val() == '') {
				$('#commenter_author').css('border', 'solid 1px #ff0000');
				$('#commenter_author').focus();
			} else if(!re.test($('#commenter_email').val())) {
				$('#commenter_email').css('border', 'solid 1px #ff0000');
				$('#commenter_email').focus();
			} else {
				var commenter_code = 'javascript:document.getElementById(\'author\').value = \''+$('#commenter_author').val()+'\'; document.getElementById(\'email\').value = \''+$('#commenter_email').val()+'\'; document.getElementById(\'url\').value = \''+$('#commenter_url').val()+'\'; void(0)';
				$('#wp_commenter_code').html(commenter_code);
				$('.code_result>a').attr('href', commenter_code);
				$('.code_result').show();
			}
		});
		$('#cheon_code_generator input').keyup(function() {
			$(this).css('border', 'solid 1px #000000');
		});
	});
})(jQuery);
</script>
<div id="cheon_code_generator" style="padding:10px;">

昵称(必须)：  

<input type="text" value="" name="commenter_author" id="commenter_author" style="border:solid 1px #000;">

邮箱地址(必须)：  

<input type="text" value="" name="commenter_email" id="commenter_email" style="border:solid 1px #000;">

站点：  

<input type="text" value="" name="commenter_url" id="commenter_url" style="border:solid 1px #000;">

<textarea cols="40" rows="10" name="wp_commenter_code" id="wp_commenter_code" style="border:solid 1px #000;"></textarea>

<input type="button" value="生成代码" id="generate_code" style="border:solid 1px #000;">
```

右键单击链接把它添加到您的收藏夹中可创建一个快速填写 WP 评论者信息的快捷方式。

