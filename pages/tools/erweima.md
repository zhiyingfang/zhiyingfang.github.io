---
permalink: /2016/04/13/utility-tools/erweima
---
<html class="no-js no-browser" lang="en">
<head>
	<meta charset="utf-8">
	<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
	<title>��ά��������</title>
	<meta name="keywords" content="��ά�����ɹ���,JS��ά������,��ά��������,jQuery��ά��������,jQuery��ά������" />
	<meta name="description" content="��ά�����ɲ������ʾ��������">	
	<meta name="viewport" content="width=device-width">			
	<link href='/assets/tools/erweima/styles.css' rel='stylesheet'>
	<script src="/assets/tools/erweima/jquery-1.10.2.js"></script>
	<script src="/assets/tools/erweima/jqueryqr.js"></script>
	<script src="/assets/tools/erweima/ff-range.js"></script>
	<script src="/assets/tools/erweima/scripts.js"></script>
</head>
<body>
	<div id="container"><canvas width="400" height="400"></canvas></div>

	<div class="control left">
		<a id="banner" href="http://zhiyingfang.github.io">All for PPTer</a>
		<hr/>
		<label for="render">��Ⱦģʽ</label>
		<select id="render">
			<option value="canvas" selected="selected">Canvas</option>
			<option value="image">Image</option>
			<option value="div">DIV</option>
		</select>
		<hr/>
		<label for="size">��ά��ߴ�:</label>
		<input id="size" type="range" value="400" min="100" max="1000" step="50" />
		<label for="fill">��ά����ɫ</label>
		<input id="fill" type="color" value="#333333" />
		<label for="background">��ά�뱳����ɫ</label>
		<input id="background" type="color" value="#ffffff" />
		<label for="text">��ά������</label>
		<textarea id="text">All for PPTer</textarea>
		<hr/>
		<label for="minversion">MIN VERSION:</label>
		<input id="minversion" type="range" value="6" min="1" max="10" step="1" />
		<label for="eclevel">���У��ˮƽ</label>
		<select id="eclevel">
			<option value="L">L - Low (7%)</option>
			<option value="M">M - Medium (15%)</option>
			<option value="Q">Q - Quartile (25%)</option>
			<option value="H" selected="selected">H - High (30%)</option>
		</select>
		<label for="quiet">�汾:</label>
		<input id="quiet" type="range" value="1" min="0" max="4" step="1" />
		<label for="radius">Բ����:</label>
		<input id="radius" type="range" value="50" min="0" max="50" step="10" />
		<a id="download" download="qrcode.png">���ض�ά��</a>
	</div>

	<div class="control right">
		<label for="mode">��ά��LOGO����</label>
		<select id="mode">
			<option value="0">0 - Normal</option>
			<option value="1">1 - Label-Strip</option>
			<option value="2" selected="selected">2 - Label-Box</option>
			<option value="3">3 - Image-Strip</option>
			<option value="4">4 - Image-Box</option>
		</select>
		<hr/>
		<label for="msize">��ά��LOGO�ߴ�:</label>
		<input id="msize" type="range" value="11" min="0" max="40" step="1" />
		<label for="mposx">��ά��LOGOX����:</label>
		<input id="mposx" type="range" value="50" min="0" max="100" step="1" />
		<label for="mposy">��ά��LOGOY����:</label>
		<input id="mposy" type="range" value="50" min="0" max="100" step="1" />
		<hr/>
		<label for="label">��ǩ</label>
		<input id="label" type="text" value="3464.com" />
		<label for="font">��������</label>
		<input id="font" type="text" value="Ubuntu" />
		<label for="fontcolor">������ɫ:</label>
		<input id="fontcolor" type="color" value="#ff9818" />
		<hr/>
		<label for="image">�ϴ���ά��LOGO</label>
		<input id="image" type="file" />
	</div>

	<img id="img-buffer" src="images/dummy.png" />	
</body>
</html>

