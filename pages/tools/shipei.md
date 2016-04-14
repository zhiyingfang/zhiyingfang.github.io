---
permalink: /2016/04/13/utility-tools/shipei
---
<html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <title>移动跨屏模拟</title>
    
    <link href="/assets/tools/shipei/shipei.css" rel="stylesheet"/>

</head>
<body>
    <div class="Tool-MainWrap ww100">
        <p class="ClassHead-wrap clearfix">
            <a href="http://zhiyingfang.github.io/2016/04/13/utility-tools/shipei" class="CHeadcur ml15">移动跨屏模拟</a>
            <a href="http://zhiyingfang.github.io/2016/04/13/utility-tools/">其他实用工具</a>
            <a href="http://zhiyingfang.github.io" class="spreturn fr" target="_blank">All for PPTer</a>
        </p>
        <div class="DelHeadWrap bor-b1s03 bg-white pb10">
            <!--PingSearch-begin-->
            <div class="publicSearch clearfix">
                <form autocomplete="off" action="/2016/04/13/utility-tools/shipei" method="get" id="_form">
                    <div class="search-write-wrap pt15 fl clearfix">
                        <div class="search-write-left w480 pr" id="inputInfo">
                            <input class="search-write-cont w460 WrapHid" id="inputURL" name="url" url="true" value="" />
                            <a href="javascript:" title="清空" class="quickdelete _CentHid"></a>
                            <b class="search-hint CentHid" id="inputInfo2">输入网址请去掉“https://”</b>
                        </div>
                        <div class="search-write-right">
                            <input class="search-write-btn" type="submit" value="分析" id="btnCMF" onclick="return checkForm()" />
                        </div>
                    </div>
                    <div class="spPhoneType fl clearfix">
                        <div class="fl spFanz mr10"><a href="javascript:" id="reverse"><span>翻转</span></a></div>
                        <dl class="mr10 pr spImgWrap">
                            <dt class="dtImgPh"><span>手机</span></dt>
                            <dd class="dtType w350">
                                <div class="Sp-arrow icon corner"></div>
                                <div class="fl w160">
                                    <a href="#target_middle" class="change" data-px="320*480" rel="nofollow">iPhone 4 <i>(320 x 480)</i></a>
                                    <a href="#target_middle" class="change" data-px="320*568" rel="nofollow">iPhone 5 <i>(320 x 568)</i></a>
                                    <a href="#target_middle" class="change" data-px="375*667" rel="nofollow">iPhone 6 <i>(375 x 667)</i></a>
                                    <a href="#target_middle" class="change" data-px="384*567" rel="nofollow">Nexus 4<i>(384 x 567)</i></a>
                                    <a href="#target_middle" class="change" data-px="360*567" rel="nofollow">Nexus 5<i>(360 x 567)</i></a>
                                    <a href="#target_middle" class="change" data-px="412*659" rel="nofollow">Nexus 6<i>(412 x 659)</i></a>
                                </div>
                                <div class="fl w180">
                                    <a href="#target_middle" class="change spCurt" data-px="414*736" rel="nofollow">iPhone 6 Plus<i>(414 x 736)</i></a>
                                    <a href="#target_middle" class="change" data-px="360*640" rel="nofollow">Galaxy S III <i>(360 x 640)</i></a>
                                    <a href="#target_middle" class="change" data-px="320*533" rel="nofollow">Lumia 520 <i>(320 x 533)</i></a>
                                    <a href="#target_middle" class="change" data-px="384*640" rel="nofollow">Optimus L70 <i>(384 x 640)</i></a>
                                    <a href="#target_middle" class="change" data-px="480*800" rel="nofollow">Optimus 3D <i>(480 x 800)</i></a>
                                </div>
                            </dd>
                        </dl>
                        <dl class="mr20 pr spImgWrap">
                            <dt class="dtImgPb"><span>平板</span></dt>
                            <dd class="dtType w412">
                                <div class="Sp-arrow icon corner"></div>
                                <div class="fl w170">
                                    <a href="#target_middle" class="change" data-px="1024*768" rel="nofollow">iPad Mini <i>(768 x 1024)</i></a>
                                    <a href="#target_middle" class="change" data-px="1024*768" rel="nofollow">iPad 2 <i>(768 x 1024)</i></a>
                                    <a href="#target_middle" class="change" data-px="2048*1536" rel="nofollow">iPad 3 <i>(1536 x 2048)</i></a>
                                    <a href="#target_middle" class="change" data-px="1280*800" rel="nofollow">Fire HD <i>(800 x 1280)</i></a>
                                    <a href="#target_middle" class="change" data-px="2560*1600" rel="nofollow">Fire HDX<i>(1600 x 2560)</i></a>
                                </div>
                                <div class="fl w220">
                                    <a href="#target_middle" class="change" data-px="1024*600" rel="nofollow">Asus Eee 1000 <i>(600 x 1024)</i></a>
                                    <a href="#target_middle" class="change" data-px="1920*1280" rel="nofollow">Nook HD+(B&amp;N) <i>(1280 x 1920)</i></a>
                                    <a href="#target_middle" class="change" data-px="1440*900" rel="nofollow">Nook HD(B&amp;N) <i>(900 x 1440)</i></a>
                                    <a href="#target_middle" class="change" data-px="1280*720" rel="nofollow">Galaxy Note <i>(720 x 1280))</i></a>
                                    <a href="#target_middle" class="change" data-px="1280*800" rel="nofollow">Galaxy Tab 10.1 <i>(800 x 1280)</i></a>
                                </div>
                            </dd>
                        </dl>
                        <dl class="pr spImgWrap">
                            <dt class="dtImgPc"><span>PC</span></dt>
                            <dd class="dtType w510">
                                <div class="Sp-arrow icon corner"></div>
                                <div class="fl w220">
                                    <a href="#target_middle" class="change" data-px="1920*1080" rel="nofollow">iMac 21.5"<i>(1080 x 1920)</i></a>
                                    <a href="#target_middle" class="change" data-px="2560*1440" rel="nofollow">iMac 27.5"<i>(1440 x 2560)</i></a>
                                    <a href="#target_middle" class="change" data-px="1366*768" rel="nofollow">11" MacBook Air <i>(768 x 1366)</i></a>
                                    <a href="#target_middle" class="change" data-px="1440*900" rel="nofollow">13" MacBook Air <i>(900 x 1440)</i></a>
                                    <a href="#target_middle" class="change" data-px="1366*768" rel="nofollow">Alienware M14x <i>(768 x 1366)</i></a>
                                </div>
                                <div class="fl w280">
                                    <a href="#target_middle" class="change" data-px="1920*1080" rel="nofollow">Ideapad Y580 <i>(1080 x 1920)</i></a>
                                    <a href="#target_middle" class="change" data-px="1600*900" rel="nofollow">ThinkPad X1 Carbon <i>(900 x 1600)</i></a>
                                    <a href="#target_middle" class="change" data-px="1920*1080" rel="nofollow">Alienware M17x/M18x <i>(1080 x 1920)</i></a>
                                    <a href="#target_middle" class="change" data-px="2880*1800" rel="nofollow">15" MacBook Pro Retina <i>(1800 x 2880)</i></a>
                                </div>
                            </dd>
                        </dl>
                        
                    </div>
                </form>
            </div>
        </div>
        <div class="spMain pr">
            <div id="ruller"></div>
            <div id="ruller02"></div>
            <div class="fz24 YaHei col-blue02 fb" id="curDevice">iPhone 6 Plus<i>(414 x 736)</i></div>
            <iframe src="" security="restricted" id="ck_iframe" class="spTypeCent" style="width:414px;height:736px;" frameborder="0" frameSpacing="0" marginHeight="0" scrolling="yes"></iframe>
            
        </div>
    </div>
   
    <div id="ToolBox">
        <div id="xhead"></div>
        <ul id="xlist"></ul>
        <div id="xfoot"></div>
    </div>
    <div id="loadingDiv" class="loading"></div>
    <div id="loadingDivMessage" class="loading">
        正在分析中...
    </div>
    <script src="/assets/tools/shipei/shipei.js"></script>

    <script>
        var g_inverse = false;
        function checkForm() {
            var $url = $("#inputURL");
            if (checkRequired($url)) {
                loadingState(true);
                $("#ck_iframe").attr("src", "http://" + $url.val());
                setTimeout(function () { loadingState(false); }, 120000);
            } else {
                $("#inputInfo").css({ "border-color": "red" });
                $("#inputInfo2").css({ "color": "#ff8a8a" });
                $("#inputInfo2").text("请输入正确的URL地址(如:zhiyingfang.github.io)");
            }
            return false;
        }
        function Sp() {
            var winWidth = window.innerWidth || document.documentElement && document.documentElement.clientWidth || 0;
            if (winWidth < 1050) {
                $(".spImgWrap .dtType").css({ left: "auto", right: "0" });
                $(".dtType .Sp-arrow").css({ left: "auto", right: "20px" });
            } else {
                $(".spImgWrap .dtType").css({ left: "0px", right: "auto" });
                $(".dtType .Sp-arrow").css({ left: "20px", right: "auto" });
            }
        }
        $(function () {
            Sp();
            $(window).on('resize', function () { Sp() });
            menuHover($(".spImgWrap dt"), $(".spImgWrap dd"));
            $(".change").each(function (i, n) {
                $(this).bind("click", function () {
                    g_inverse = false;
                    $("#curDevice").text($(this).text());
                    removeClass();
                    $(this).addClass("spCurt");
                    setWH($(this));
                });
            });
            $("#reverse").bind("click", function () {
                $(".spCurt").each(function (i, n) {
                    setWH($(this), !g_inverse);
                });
            });
            $("#ck_iframe").bind("load", function () {
                loadingState(false);
            });
        });
        function removeClass() {
            $(".spCurt").each(function (i, n) {
                $(this).removeClass("spCurt");
            });
        }
        function setWH($obj, $reverse) {
            var size = $obj.attr("data-px");
            var sizeArr = size.split("*");
            if (sizeArr.length == 2) {
                var $iframe = $("#ck_iframe");
                var width = (parseInt(($reverse ? sizeArr[1] : sizeArr[0]), 10));//默认是 宽*高 ，反转则反
                var height = parseInt(($reverse ? sizeArr[0] : sizeArr[1]), 10);//默认是 宽*高 ，反转则反
                $iframe.animate({ width: width + 14, height: height }, 700);
                g_inverse = !g_inverse;
            }
        }
        function loadingState(flag) {
            var $url = $("#inputURL");
            var $btn = $("#btnCMF");
            if (flag) {
                $url.attr("readonly", "readonly");
                $btn.val("分析中..");
                $btn.attr("disabled", "disabled");
                //$(".loading").show();
            } else {
                $url.removeAttr("readonly");
                $btn.val("分析");
                $btn.removeAttr("disabled");
                //$(".loading").hide();
            }
        }
    </script>
</body>
</html>
