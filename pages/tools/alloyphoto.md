---
permalink: /2016/04/13/utility-tools/alloyphoto
---
<html lang="en">
<head>
	<meta charset="UTF-8">
  <meta name="author" content="Tencent.AlloyTeam.Dorsywang" />
  <meta name="copyright" content="Tencent.AlloyTeam" />
  <meta name="keywords" content="alloyPhoto 简约版,alloyImage,alloyPhoto,html5 canvas,alloyTeam" />
  <meta name="description" content="alloyPhoto简约版，一款基于alloyImage库的图像处理应用,alloyImage是基于html5的图像处理js代码库。" />
  
	<title>AlloyPhoto 简约版</title>
  <link media="all" rel="stylesheet" href="/assets/tools/alloyphoto/main.css" type="text/css" />
  <link media="all" rel="stylesheet" href="/assets/tools/alloyphoto/bar.css" type="text/css" />
  <script type="text/javascript" src="/assets/tools/alloyphoto/alloyimage.js"></script>
  <script type="text/javascript" src="/assets/tools/alloyphoto/main2.js"></script>
</head>
<body>
<div class="header">AlloyPhoto 简约版</div>
<div class="wrapper">
  <div class="left">
    <h3>效果</h3>
    <ul id="effects" class="effects">
      <li class="e_item">
        <div class="imgWrapper">
        </div>
      </li>
    </ul>
  </div>
  <div class="right">
    <div id="picWrapper" class="picWrapper">
        <img src="img/bulding.jpg" class="pic" id="pic" alt="" draggable="false"/>

        <div id="infoMsg">
          处理中
        </div>
    </div>
    
  </div>	
</div>
<div class="command">
  <ul class="demoImg">
    <li>示例图片 <br />demos</li>
    <li class="d_item"><img src="/assets/tools/alloyphoto/bulding.jpg" /><div class='lab'>建筑</div></li>
    <li class="d_item"><img src="/assets/tools/alloyphoto/big.jpg" /><div class='lab'>特写</div></li>
    <li class="d_item"><img src="/assets/tools/alloyphoto/small.jpg" /><div class='lab'>微距</div></li>
    <li class="d_item"><img src="/assets/tools/alloyphoto/girl.jpg" /><div class='lab'>人物</div></li>
    <li class="d_item"><img src="/assets/tools/alloyphoto/inner.jpg" /><div class='lab'>室内</div></li>
    <li class="d_item"><img src="/assets/tools/alloyphoto/pet.jpg" /><div class='lab'>宠物</div></li>
    <li class="d_item"><img src="/assets/tools/alloyphoto/scen.jpg" /><div class='lab'>风景</div></li>
    <li class="d_item"><img src="/assets/tools/alloyphoto/stop.jpg" /><div class='lab'>静物</div></li>
  </ul>
  <ul class="command_items">
    <li>
        <a class="button" href="#" class="mask">打开图片</a>
    </li>
  </ul>
  <div class="footer">
    <div class="links">
      <a href="http://zhiyingfang.github.io/2016/04/13/utility-tools/alloyphotopro">专业版</a> &nbsp;&nbsp;<a href="http://zhiyingfang.github.io/" target="_blank">ALL for PPTer</a>
    </div>
    <div class="copyright">Copyright &copy; <script>document.write(new Date().getFullYear());</script> <a href="http://www.AlloyTeam.com/" target="_blank">Tencent AlloyTeam</a>. All Rights Reserved.</div>
  </div>
</div>
<input type="file" name="open" id="open" class="open" />
<script type="text/javascript">

	  var _gaq = _gaq || [];
	  _gaq.push(['_setAccount', 'UA-23019343-9']);
	  _gaq.push(['_trackPageview']);

	  (function() {
		var ga = document.createElement('script'); ga.type = 'text/javascript'; ga.async = true;
		ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 'http://www') + '.google-analytics.com/ga.js';
		var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(ga, s);
	  })();

</script>

</body>
</html>
