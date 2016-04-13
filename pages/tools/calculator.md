---
permalink: /2016/04/13/utility-tools/calculator
---

<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
<title>计算器</title>
<style type="text/css"><!--
* {margin:10 0px;padding:0px;font-size:12px;color:#333;border:0px;font-family:"microsoft yahei",Helvetica,sans-serif;}
body {line-height:300%}
label {color:#FFF;}
#calculator_base,#calculator_complete {position:relative;margin:0 auto;padding-top:10px;width:540px;}
#calculator_base_cup,#calculator_complete_cup {padding-bottom:10px;}
#calculator_base_container,#calculator_complete_container {width:437px;height:448px;margin:0px 10px;background:url(/assets/tools/images/siverbg.png) no-repeat 0 0;}
#calculator_complete_container {height:578px;background-image:url(/assets/tools/images/siverbg2.png);}
/* table */
#base_table_main td {height:53px;}
#complete_table_main td {height:40px;*height:38px;}
#complete_table_more td {height:40px;}
.calculator_table {width:100%;}
.calculator_table td {text-align:center;padding:0px;margin:0px;}
.topRowCss td {height:30px;*height:32px;color:#FFF;padding-top:3px;}
#baseEprsPanel,#completeEprsPanel {text-align:right;}
/* button */
.baseBtnCommonCss {width:94px;height:44px;background:url(/assets/tools/images/d1btn.gif) no-repeat 0 -44px;font-size:14px;color:#FFF;}
.baseBtnCss1 {background-image:url(/assets/tools/images/d0btn.gif);}
.baseBtnCss2 {background-image:url(/assets/tools/images/d2btn.gif);font-size:20px;}
.baseBtnCss3 {background-image:url(/assets/tools/images/d3btn.gif);font-size:16px;}
.baseBtnCss4 {background-image:url(/assets/tools/images/d4btn.gif);font-size:20px;}
.completeBtnCommonCss {width:64px;height:34px;border:0px;background:url(/assets/tools/images/e0btn.gif) no-repeat 0 -34px;font-size:14px;color:#FFF;}
.completeBtnCss1 {background-image:url(/assets/tools/images/e1btn.gif);}
.completeBtnCss2 {background-image:url(/assets/tools/images/e3btn.gif);}
.completeBtnCss3 {background-image:url(/assets/tools/images/e2btn.gif);font-size:18px;}
.completeBtnCss4 {background-image:url(/assets/tools/images/e4btn.gif);font-size:18px;}
.completeBtnCss5 {width:74px;height:34px;background:url(/assets/tools/images/e5btn.jpg) no-repeat 0 -34px;}
/* common */
.displayCss {width:390px;height:56px;text-align:right;font-size:40px;padding:0 5px;
	*line-height:100%; /* for ie */}
.helperBox {width:42px;height:27px;color:#FFF;text-align:center;background-color:#CCC;background:url(/assets/tools/images/num.gif) no-repeat;margin:0px;padding:0px;
	*line-height:100%; /* for ie */}
.calculator_tab {position:absolute;left:457px;top:10px;height:62px;width:62px;background:url(/assets/tools/images/cal_tab.gif) no-repeat;}
.calculator_tab ul {list-style:none;width:100%;height:100%;margin:0px;padding:0px;}
.calculator_tab ul li {height:31px;width:100%;color:#FFF;text-align:center;cursor:pointer;line-height:100%;}
.selTabTop {background:url(/assets/tools/images/cal_tab_top.gif) no-repeat;}
.selTabBottom {background:url(/assets/tools/images/cal_tab_bottom.gif) no-repeat;}
--></style>
<script language="javascript">
<!--//
function FloatAdd(arg1,arg2){   
	var r1,r2,m;   
	try{r1=arg1.toString().split(".")[1].length}catch(e){r1=0}   
	try{r2=arg2.toString().split(".")[1].length}catch(e){r2=0}   
	m=Math.pow(10,Math.max(r1,r2))   
	return (arg1*m+arg2*m)/m   
}
function FloatSub(arg1,arg2){   
	var r1,r2,m,n;   
	try{r1=arg1.toString().split(".")[1].length}catch(e){r1=0}   
	try{r2=arg2.toString().split(".")[1].length}catch(e){r2=0}   
	m=Math.pow(10,Math.max(r1,r2));   
	//动态控制精度长度   
	n=(r1>=r2)?r1:r2;   
	return ((arg1*m-arg2*m)/m).toFixed(n);   
}
 //浮点数乘法运算   
function FloatMul(arg1,arg2)    
{    
	var m=0,s1=arg1.toString(),s2=arg2.toString();    
	try{m+=s1.split(".")[1].length}catch(e){}    
	try{m+=s2.split(".")[1].length}catch(e){}    
	return Number(s1.replace(".",""))*Number(s2.replace(".",""))/Math.pow(10,m)    
}    
//浮点数除法运算   
function FloatDiv(arg1,arg2){    
	var t1=0,t2=0,r1,r2;    
	try{t1=arg1.toString().split(".")[1].length}catch(e){}    
	try{t2=arg2.toString().split(".")[1].length}catch(e){}    
	with(Math){    
		r1=Number(arg1.toString().replace(".",""))    
		r2=Number(arg2.toString().replace(".",""))    
		return (r1/r2)*pow(10,t2-t1);    
	}    
}

	// global variables
	var g_type = 0;
	var endNumber = true;
	var mem = 0,carry = 10,layer = 0;
	var hexnum = "0123456789abcdef";
	var angle = "d",stack = "",level = "0";
	var $c_get = function(tagId){return document.getElementById(tagId);}
	var lastOperator = "";
	var isMaxLen = false;
	//数字键
	function inputkey(key,ent){
		if(isMaxLen == false){//alert(isMaxLen);

		// input express by key
		if(lastOperator == "="){
			$c_get("completeEprsPanel").innerHTML = key;
		}else{
			if(lastOperator == "m"){
				$c_get("completeEprsPanel").innerHTML = "";
			}
			$c_get("completeEprsPanel").innerHTML += key;
		}
		//$c_get("completeEprsPanel").scrollLeft = $c_get("completeEprsPanel").scrollWidth;
		//document.calc.display.scrollLeft = document.calc.display.scrollWidth;/* for ie */

		var index=key.charCodeAt(0);
		if ((carry == 2 && (index == 48 || index == 49)) || (carry == 8 && index >= 48 && index <= 55) || (carry == 10 && (index >= 48 && index <= 57 || index == 46)) || (carry == 16 && ((index >= 48 && index <= 57) || (index >= 97 && index <= 102))))
		if(endNumber){
			endNumber = false;
			if(index == 46){
				if(document.calc.display.value.indexOf(".") != -1){
					//
				}else{
					document.calc.display.value += key;
				}
			}else{
				document.calc.display.value = key;
			}
		}
		else if(document.calc.display.value == null || document.calc.display.value == "0")
			if(index == 46){
				if(document.calc.display.value.indexOf(".") != -1){
					//
				}else{
					document.calc.display.value += key;
				}
			}else{
				document.calc.display.value = key;
			}
		else{
			if(index == 46){
				if(document.calc.display.value.indexOf(".") != -1){
					//
				}else{
					document.calc.display.value += key;
				}
			}else{
			document.calc.display.value += key;
			}
			}
			//document.calc.display.value += key;
		
		//
		lastOperator = "";
		try{
			var evnt = ent || window.event;
			var target = evnt.srcElement || evnt.target;
			target.blur();
		}catch(e){}
		
		if(document.calc.display.value.length > 16){
			isMaxLen = true;
		}
		
		}// isMaxLen
		else{
			alert("只能输入不大于17位的字符");
		}
	}
	function changeSign(ent){
		if (document.calc.display.value != "0")
			if(document.calc.display.value.substr(0,1) == "-")
			document.calc.display.value = document.calc.display.value.substr(1);
			else
			document.calc.display.value = "-" + document.calc.display.value;
			
		try{
			var evnt = ent || window.event;
			var target = evnt.srcElement || evnt.target;
			target.blur();
		}catch(e){}
	}
	//函数键
	function inputfunction(fun,shiftfun,ent){
		endNumber = true;
		if (document.calc.shiftf.checked)
			document.calc.display.value = decto(funcalc(shiftfun,(todec(document.calc.display.value,carry))),carry);
		else
			document.calc.display.value = decto(funcalc(fun,(todec(document.calc.display.value,carry))),carry);
		document.calc.shiftf.checked = false
		document.calc.hypf.checked = false	
		inputshift();
		
		try{
			var evnt = ent || window.event;
			var target = evnt.srcElement || evnt.target;
			target.blur();
		}catch(e){}
	}
	function inputtrig(trig,arctrig,hyp,archyp,ent){
		if (document.calc.hypf.checked)
			inputfunction(hyp,archyp);
		else
			inputfunction(trig,arctrig);
			
		try{
			var evnt = ent || window.event;
			var target = evnt.srcElement || evnt.target;
			target.blur();
		}catch(e){}
	}
	//运算符
	function operation(join,newlevel,ent){
		endNumber = true
		var temp = stack.substr(stack.lastIndexOf("(") + 1) + document.calc.display.value;
/*		var s = stack.substr(stack.length-1);
		if((s == "+" || s == "-" || s == "*" || s == "/") && carry == 10){
			//var s = stack.substr(stack.length-1);//stack.substr(stack.lastIndexOf("(") + 1);
			var args1 = temp.split(s)[0];
			var args2 = temp.split(s)[1];
			//alert(args1 + " @@ " + args2);
			switch(s){
				case "+":
					temp = FloatAdd(args1,args2);
					break;
				case "-":
					temp = FloatSub(args1,args2);
					break;
				case "*":
					temp = FloatMul(args1,args2);
					break;
				case "/":
					temp = FloatDiv(args1,args2);
					break;
			}
			document.calc.display.value = temp;
		}*/
		
		while (newlevel != 0 && (newlevel <= (level.charAt(level.length - 1)))){
/*			if(carry == 10){
				if((s != "+" && s != "-" && s != "*" && s != "/")){
					temp=parse(temp);
				}
			}else{
				temp=parse(temp);
			}
			level=level.slice(0,-1);*/
			temp=parse(temp);
			level=level.slice(0,-1);
		}
/*		if(carry == 10){
			if((s != "+" && s != "-" && s != "*" && s != "/")){
				if (temp.match(/^(.*\d[\+\-\*\/\%\^\&\|x])?([+-]?[0-9a-f\.]+)$/));
					document.calc.display.value = RegExp.$2;
			}else{*/
				if (temp.match(/^(.*\d[\+\-\*\/\%\^\&\|x])?([+-]?[0-9a-f\.]+)$/));
					document.calc.display.value = RegExp.$2;
//			}
//		}
		stack = stack.substr(0,stack.lastIndexOf("(") + 1) + temp + join;
		document.calc.operator.value = " "+ join +" ";
		level = level + newlevel;

		// add express by operator
		$c_get("completeEprsPanel").innerHTML += document.calc.operator.value;
		lastOperator = join;
		
		try{
			var evnt = ent || window.event;
			var target = evnt.srcElement || evnt.target;
			target.blur();
		}catch(e){}
		
		isMaxLen = false;
	}
	//括号
	function addbracket(obj,ent){
		endNumber = true;
		document.calc.display.value = 0;
		stack = stack + "(";
		document.calc.operator.value = "   ";
		level = level + 0
	
		layer += 1
		document.calc.bracket.value = "(=" + layer
		
		if(lastOperator == "="){
			$c_get("completeEprsPanel").innerHTML = obj.value;
		}else{
			if(lastOperator == "m"){
				$c_get("completeEprsPanel").innerHTML = "";
			}
			$c_get("completeEprsPanel").innerHTML += obj.value;
		}
		lastOperator = obj.value;
		
		try{
			var evnt = ent || window.event;
			var target = evnt.srcElement || evnt.target;
			target.blur();
		}catch(e){}
	}
	function disbracket(obj,ent){
		endNumber = true;
		var temp = stack.substr(stack.lastIndexOf("(") + 1) + document.calc.display.value;
/*		var s = stack.substr(stack.length-1);
		if((s == "+" || s == "-" || s == "*" || s == "/") && carry == 10){
			//var s = stack.substr(stack.length-1);//stack.substr(stack.lastIndexOf("(") + 1);
			var args1 = temp.split(s)[0];
			var args2 = temp.split(s)[1];
			//alert(args1 + " @@ " + args2);
			switch(s){
				case "+":
					temp = FloatAdd(args1,args2);
					break;
				case "-":
					temp = FloatSub(args1,args2);
					break;
				case "*":
					temp = FloatMul(args1,args2);
					break;
				case "/":
					temp = FloatDiv(args1,args2);
					break;
			}
			document.calc.display.value = temp;
		}*/
		while ((level.charAt(level.length - 1)) > 0)
		{
/*			if(carry == 10){
				if((s != "+" && s != "-" && s != "*" && s != "/")){
					temp=parse(temp);
				}
			}else{
				temp=parse(temp);
			}
			level = level.slice(0,-1);*/
			temp=parse(temp);
			level=level.slice(0,-1);
		}	
		document.calc.display.value = temp;
		
		stack = stack.substr(0,stack.lastIndexOf("("));
		document.calc.operator.value = "   ";
		level = level.slice(0,-1);
		layer -= 1;
		if (layer > 0)
			document.calc.bracket.value = "(=" + layer;
		else
			document.calc.bracket.value = "";
			
		if(lastOperator == "="){
			$c_get("completeEprsPanel").innerHTML = obj.value;
		}else{
			if(lastOperator == "m"){
				$c_get("completeEprsPanel").innerHTML = "";
			}
			$c_get("completeEprsPanel").innerHTML += obj.value;
		}
		lastOperator = obj.value;
		
		try{
			var evnt = ent || window.event;
			var target = evnt.srcElement || evnt.target;
			target.blur();
		}catch(e){}
	}
	//等号
	function result(ent){
		endNumber = true;
		while (layer > 0)
			disbracket();
		var temp = stack + document.calc.display.value;
/*		var s = stack.substr(stack.length-1);
		if((s == "+" || s == "-" || s == "*" || s == "/") && carry == 10){
			//var s = stack.substr(stack.length-1);//stack.substr(stack.lastIndexOf("(") + 1);
			var args1 = temp.split(s)[0];
			var args2 = temp.split(s)[1];
			//alert(args1 + " @@ " + args2);
			switch(s){
				case "+":
					temp = FloatAdd(args1,args2);
					break;
				case "-":
					temp = FloatSub(args1,args2);
					break;
				case "*":
					temp = FloatMul(args1,args2);
					break;
				case "/":
					temp = FloatDiv(args1,args2);
					break;
			}
			document.calc.display.value = temp;
		}*/
		//
		while((level.charAt(level.length - 1)) > 0){
/*			if(carry == 10){
				if((s != "+" && s != "-" && s != "*" && s != "/")){
					temp=parse(temp);
				}
			}else{
				temp=parse(temp);
			}
			level = level.slice(0,-1);*/
			temp=parse(temp);
			level=level.slice(0,-1);
		}
		document.calc.display.value = temp;//parseFloat(temp).toLocaleString();//temp
		document.calc.bracket.value = "";
		document.calc.operator.value = "";
		stack = "";
		level = "0";
		
		// clear express
		lastOperator = "=";
		
		try{
			var evnt = ent || window.event;
			var target = evnt.srcElement || evnt.target;
			target.blur();
		}catch(e){}
		
		isMaxLen = false;
	}
	//修改键
	function backspace(ent){
		try{
			document.getElementById("completeEprsPanel").innerHTML = document.getElementById("completeEprsPanel").innerHTML.substring(0,document.getElementById("completeEprsPanel").innerHTML.length-1);
		}catch(e){}
		if (!endNumber){
			if(document.calc.display.value.length > 1){
				document.calc.display.value = document.calc.display.value.substring(0,document.calc.display.value.length - 1);
			}else{
				document.calc.display.value = 0;
			}
		}
		
		try{
			var evnt = ent || window.event;
			var target = evnt.srcElement || evnt.target;
			target.blur();
		}catch(e){}
		
		if(document.calc.display.value.length <= 16){
			isMaxLen = false;
		}
	}
	function clearall(ent){
		document.calc.display.value = 0;
		endNumber = true;
		stack = "";
		level = "0";
		layer = "";
		document.calc.operator.value = "";
		document.calc.bracket.value = "";
		
		document.getElementById("completeEprsPanel").innerHTML = "";
		
		try{
			var evnt = ent || window.event;
			var target = evnt.srcElement || evnt.target;
			target.blur();
		}catch(e){}
		
		isMaxLen = false;
	}
	//转换键
	function inputChangCarry(newcarry,ent){
		endNumber = true;
		document.calc.display.value=(decto(todec(document.calc.display.value,carry),newcarry));
		carry = newcarry;
		document.calc.sin.disabled = (carry != 10);
		document.calc.cos.disabled = (carry != 10)
		document.calc.tan.disabled = (carry != 10)
		document.calc.bt.disabled = (carry != 10)
		document.calc.pi.disabled = (carry != 10)
		document.calc.e.disabled = (carry != 10)
		document.calc.kp.disabled = (carry != 10)
		document.calc.k2.disabled = (carry <= 2)
		document.calc.k3.disabled = (carry <= 2)
		document.calc.k4.disabled = (carry <= 2)
		document.calc.k5.disabled = (carry <= 2)
		document.calc.k6.disabled = (carry <= 2)
		document.calc.k7.disabled = (carry <= 2)
		document.calc.k8.disabled = (carry <= 8)
		document.calc.k9.disabled = (carry <= 8)
		document.calc.ka.disabled = (carry <= 10)
		document.calc.kb.disabled = (carry <= 10)
		document.calc.kc.disabled = (carry <= 10)
		document.calc.kd.disabled = (carry <= 10)
		document.calc.ke.disabled = (carry <= 10)
		document.calc.kf.disabled = (carry <= 10)
		document.calc.sin.style.color = (carry != 10)?"#999":"#fff";
			document.calc.sin.style.background = (carry != 10) ? "url(/assets/tools/images/e5btn-dis.png) no-repeat 0 0px" : "url(/assets/tools/images/e5btn.jpg) no-repeat 0 -34px";
		document.calc.cos.style.color = (carry != 10)?"#aca899":"#fff";
			document.calc.cos.style.background = (carry != 10) ? "url(/assets/tools/images/e5btn-dis.png) no-repeat 0 0px" : "url(/assets/tools/images/e5btn.jpg) no-repeat 0 -34px";
		document.calc.tan.style.color = (carry != 10)?"#aca899":"#fff";
			document.calc.tan.style.background = (carry != 10) ? "url(/assets/tools/images/e5btn-dis.png) no-repeat 0 0px" : "url(/assets/tools/images/e5btn.jpg) no-repeat 0 -34px";
		document.calc.bt.style.color = (carry != 10)?"#aca899":"#fff";
			document.calc.bt.style.background = (carry != 10) ? "url(/assets/tools/images/e5btn-dis.png) no-repeat 0 0px" : "url(/assets/tools/images/e5btn.jpg) no-repeat 0 -34px";
		document.calc.pi.style.color = (carry != 10)?"#aca899":"#fff";
			document.calc.pi.style.background = (carry != 10) ? "url(/assets/tools/images/e5btn-dis.png) no-repeat 0 0px" : "url(/assets/tools/images/e5btn.jpg) no-repeat 0 -34px";
		document.calc.e.style.color = (carry != 10)?"#aca899":"#fff";
			document.calc.e.style.background = (carry != 10) ? "url(/assets/tools/images/e5btn-dis.png) no-repeat 0 0px" : "url(/assets/tools/images/e5btn.jpg) no-repeat 0 -34px";
		document.calc.kp.style.color = (carry != 10)?"#aca899":"#fff";
			document.calc.kp.style.background = (carry != 10) ? "url(/assets/tools/images/e3btn-dis.png) no-repeat 0 0px" : "url(/assets/tools/images/e3btn.gif) no-repeat 0 -34px";
		document.calc.k2.style.color = (carry <= 2)?"#aca899":"#fff";
			document.calc.k2.style.background = (carry <= 2) ? "url(/assets/tools/images/e3btn-dis.png) no-repeat 0 0px" : "url(/assets/tools/images/e3btn.gif) no-repeat 0 -34px";
		document.calc.k3.style.color = (carry <= 2)?"#aca899":"#fff";
			document.calc.k3.style.background = (carry <= 2) ? "url(/assets/tools/images/e3btn-dis.png) no-repeat 0 0px" : "url(/assets/tools/images/e3btn.gif) no-repeat 0 -34px";
		document.calc.k4.style.color = (carry <= 2)?"#aca899":"#fff";
			document.calc.k4.style.background = (carry <= 2) ? "url(/assets/tools/images/e3btn-dis.png) no-repeat 0 0px" : "url(/assets/tools/images/e3btn.gif) no-repeat 0 -34px";
		document.calc.k5.style.color = (carry <= 2)?"#aca899":"#fff";
			document.calc.k5.style.background = (carry <= 2) ? "url(/assets/tools/images/e3btn-dis.png) no-repeat 0 0px" : "url(/assets/tools/images/e3btn.gif) no-repeat 0 -34px";
		document.calc.k6.style.color = (carry <= 2)?"#aca899":"#fff";
			document.calc.k6.style.background = (carry <= 2) ? "url(/assets/tools/images/e3btn-dis.png) no-repeat 0 0px" : "url(/assets/tools/images/e3btn.gif) no-repeat 0 -34px";
		document.calc.k7.style.color = (carry <= 2)?"#aca899":"#fff";
			document.calc.k7.style.background = (carry <= 2) ? "url(/assets/tools/images/e3btn-dis.png) no-repeat 0 0px" : "url(/assets/tools/images/e3btn.gif) no-repeat 0 -34px";
		document.calc.k8.style.color = (carry <= 8)?"#aca899":"#fff";
			document.calc.k8.style.background = (carry <= 8) ? "url(/assets/tools/images/e3btn-dis.png) no-repeat 0 0px" : "url(/assets/tools/images/e3btn.gif) no-repeat 0 -34px";
		document.calc.k9.style.color = (carry <= 8)?"#aca899":"#fff";
			document.calc.k9.style.background = (carry <= 8) ? "url(/assets/tools/images/e3btn-dis.gif) no-repeat 0 0px" : "url(/assets/tools/images/e3btn.gif) no-repeat 0 -34px";
		document.calc.ka.style.color = (carry <= 10)?"#aca899":"#fff";
			document.calc.ka.style.background = (carry <= 10) ? "url(/assets/tools/images/e3btn-dis.gif) no-repeat 0 0px" : "url(/assets/tools/images/e0btn.gif) no-repeat 0 -34px";
		document.calc.kb.style.color = (carry <= 10)?"#aca899":"#fff";
			document.calc.kb.style.background = (carry <= 10) ? "url(/assets/tools/images/e3btn-dis.gif) no-repeat 0 0px" : "url(/assets/tools/images/e0btn.gif) no-repeat 0 -34px";
		document.calc.kc.style.color = (carry <= 10)?"#aca899":"#fff";
			document.calc.kc.style.background = (carry <= 10) ? "url(/assets/tools/images/e3btn-dis.gif) no-repeat 0 0px" : "url(/assets/tools/images/e0btn.gif) no-repeat 0 -34px";
		document.calc.kd.style.color = (carry <= 10)?"#aca899":"#fff";
			document.calc.kd.style.background = (carry <= 10) ? "url(/assets/tools/images/e3btn-dis.gif) no-repeat 0 0px" : "url(/assets/tools/images/e0btn.gif) no-repeat 0 -34px";
		document.calc.ke.style.color = (carry <= 10)?"#aca899":"#fff";
			document.calc.ke.style.background = (carry <= 10) ? "url(/assets/tools/images/e3btn-dis.gif) no-repeat 0 0px" : "url(/assets/tools/images/e0btn.gif) no-repeat 0 -34px";
		document.calc.kf.style.color = (carry <= 10)?"#aca899":"#fff";
			document.calc.kf.style.background = (carry <= 10) ? "url(/assets/tools/images/e3btn-dis.gif) no-repeat 0 0px" : "url(/assets/tools/images/e0btn.gif) no-repeat 0 -34px";
		document.calc.sin.style.cursor = (carry != 10)?"default":"pointer";
		document.calc.cos.style.cursor = (carry != 10)?"default":"pointer";
		document.calc.tan.style.cursor = (carry != 10)?"default":"pointer";
		document.calc.bt.style.cursor = (carry != 10)?"default":"pointer";
		document.calc.pi.style.cursor = (carry != 10)?"default":"pointer";
		document.calc.e.style.cursor = (carry != 10)?"default":"pointer";
		document.calc.kp.style.cursor = (carry != 10)?"default":"pointer";
		document.calc.k2.style.cursor = (carry <= 2)?"default":"pointer";
		document.calc.k3.style.cursor = (carry <= 2)?"default":"pointer";
		document.calc.k4.style.cursor = (carry <= 2)?"default":"pointer";
		document.calc.k5.style.cursor = (carry <= 2)?"default":"pointer";
		document.calc.k6.style.cursor = (carry <= 2)?"default":"pointer";
		document.calc.k7.style.cursor = (carry <= 2)?"default":"pointer";
		document.calc.k8.style.cursor = (carry <= 8)?"default":"pointer";
		document.calc.k9.style.cursor = (carry <= 8)?"default":"pointer";
		document.calc.ka.style.cursor = (carry <= 10)?"default":"pointer";
		document.calc.kb.style.cursor = (carry <= 10)?"default":"pointer";
		document.calc.kc.style.cursor = (carry <= 10)?"default":"pointer";
		document.calc.kd.style.cursor = (carry <= 10)?"default":"pointer";
		document.calc.ke.style.cursor = (carry <= 10)?"default":"pointer";
		document.calc.kf.style.cursor = (carry <= 10)?"default":"pointer";
		
		try{
			var evnt = ent || window.event;
			var target = evnt.srcElement || evnt.target;
			target.blur();
		}catch(e){}
	}
	function inputChangAngle(angletype,ent){
		endNumber = true
		angle = angletype
		if (angle=="d")
			document.calc.display.value = radiansToDegress(document.calc.display.value)
		else
			document.calc.display.value = degressToRadians(document.calc.display.value)
		endNumber = true
		
		try{
			var evnt = ent || window.event;
			var target = evnt.srcElement || evnt.target;
			target.blur();
		}catch(e){}
	}
	function inputshift(ent){
		if (document.calc.shiftf.checked){
			document.calc.bt.value = "deg"
			document.calc.ln.value = "exp"
			document.calc.log.value = "expd"
	
			if (document.calc.hypf.checked){
				document.calc.sin.value = "ahs"
				document.calc.cos.value = "ahc"
				document.calc.tan.value = "aht"
			}
			else{
				document.calc.sin.value = "asin"
				document.calc.cos.value = "acos"
				document.calc.tan.value = "atan"
			}
	
			document.calc.sqr.value = "x^.5"
			document.calc.cube.value = "x^.3"
	
			document.calc.floor.value = "小数"
		}
		else{
			document.calc.bt.value = "d.ms"
			document.calc.ln.value = "ln"
			document.calc.log.value = "log"
	
			if (document.calc.hypf.checked){
				document.calc.sin.value = "hsin"
				document.calc.cos.value = "hcos"
				document.calc.tan.value = "htan"
			}
			else{
				document.calc.sin.value = "sin"
				document.calc.cos.value = "cos"
				document.calc.tan.value = "tan"
			}
	
			document.calc.sqr.value = "x^2"
			document.calc.cube.value = "x^3"
	
			document.calc.floor.value = "取整"
		}
	
		try{
			var evnt = ent || window.event;
			var target = evnt.srcElement || evnt.target;
			target.blur();
		}catch(e){}
	}
	//存储器部分
	function clearmemory(ent){
		mem = 0
		document.calc.memory.value = "   "

		var evnt = ent || window.event;
		var target = evnt.srcElement || evnt.target;
		target.blur();
	}
	function getmemory(ent){
		endNumber = true
		document.calc.display.value = decto(mem,carry)
		
		try{
			var evnt = ent || window.event;
			var target = evnt.srcElement || evnt.target;
			target.blur();
		}catch(e){}
	}
	function putmemory(ent){
		endNumber = true
		if (document.calc.display.value != 0)
		{
			mem = todec(document.calc.display.value,carry)
			document.calc.memory.value = " M "
		}
		else
			document.calc.memory.value = "   "
		
		lastOperator = "m";
		
		try{
			var evnt = ent || window.event;
			var target = evnt.srcElement || evnt.target;
			target.blur();
		}catch(e){}
	}
	function addmemory(ent){
		endNumber = true
		mem = parseFloat(mem)+parseFloat(todec(document.calc.display.value,carry))
		if (mem==0)
			document.calc.memory.value = "   "
		else
			document.calc.memory.value = " M "
		
		lastOperator = "m";
		
		try{
			var evnt = ent || window.event;
			var target = evnt.srcElement || evnt.target;
			target.blur();
		}catch(e){}
	}
	function multimemory(ent){
		endNumber = true
		mem = parseFloat(mem)*parseFloat(todec(document.calc.display.value,carry))
		if (mem==0)
			document.calc.memory.value = "   "
		else
			document.calc.memory.value = " M "
		
		lastOperator = "m";
		
		try{
			var evnt = ent || window.event;
			var target = evnt.srcElement || evnt.target;
			target.blur();
		}catch(e){}
	}
	//十进制转换
	function todec(num,oldcarry){
		if (oldcarry==10 || num==0) return(num)
		var neg = (num.charAt(0)=="-")
		if (neg) num = num.substr(1)
		var newnum = 0
		for (var index = 1;index <= num.length;index++)
			newnum = newnum*oldcarry+hexnum.indexOf(num.charAt(index-1))
		if (neg)
			newnum=-newnum
		return(newnum)
	}
	function decto(num,newcarry){
		var neg = (num<0)
		if (newcarry==10 || num==0) return(num)
		num = ""+Math.abs(num)
		var newnum = ""
		while (num != 0)
		{
			newnum = hexnum.charAt(num%newcarry)+newnum
			num = Math.floor(num/newcarry)
		}
		if (neg)
			newnum="-"+newnum
		return(newnum)
	}
	//表达式解析
	function parse(string){
		//try{
		if (string.match(/^(.*\d[\+\-\*\/\%\^\&\|x\<])?([+-]?[0-9a-f\.]+)([\+\-\*\/\%\^\&\|x\<])([+-]?[0-9a-f\.]+)$/))
			return(RegExp.$1+cypher(RegExp.$2,RegExp.$3,RegExp.$4))
		else
			return(string)
		//}catch(e){}
	}
	//数学运算和位运算
	function cypher(left,join,right){
		left = todec(left,carry)
		right = todec(right,carry)
		if (join=="+")
			return(decto(parseFloat(left)+parseFloat(right),carry))
		if (join=="-")
			return(decto(left-right,carry))
		if (join=="*")
			return(decto(left*right,carry))
		if (join=="/" && right != 0)
			return(decto(left/right,carry))
		if (join=="%")
			return(decto(left%right,carry))
		if (join=="&")
			return(decto(left&right,carry))
		if (join=="|")
			return(decto(left|right,carry))
		if (join=="^")
			return(decto(Math.pow(left,right),carry))
	
		if (join=="x")
			return(decto(left^right,carry))
		if (join=="<")
			return(decto(left<<right,carry))
		alert("除数不能为零")
		return(left)
	}
	//函数计算
	function funcalc(fun,num){
		with(Math){
			if (fun=="pi")
				return(PI)
			if (fun=="e")
				return(E)
	
			if (fun=="abs")
				return(abs(num))
			if (fun=="ceil")
				return(ceil(num))
			if (fun=="round")
				return(round(num))
	
			if (fun=="floor")
				return(floor(num))
			if (fun=="deci")
				return(num-floor(num))
	
	
			if (fun=="ln" && num>0)
				return(log(num))
			if (fun=="exp")
				return(exp(num))
			if (fun=="log" && num>0)
				return(log(num)*LOG10E)
			if (fun=="expdec")
				return(pow(10,num))
	
	
			if (fun=="cube")
				return(num*num*num)
			if (fun=="cubt")
				return(pow(num,1/3))
			if (fun=="sqr")
				return(num*num)
			if (fun=="sqrt" && num>=0)
				return(sqrt(num))
	
			if (fun=="!")
				return(factorial(num))
	
			if (fun=="recip" && num != 0)
				return(1/num)
	
			if (fun=="dms")
				return(dms(num))
			if (fun=="deg")
				return(deg(num))
	
			if (fun=="~")
				return(~num)
	
			if (angle=="d"){
				if (fun=="sin")
					return(sin(degressToRadians(num)))
				if (fun=="cos")
					return(cos(degressToRadians(num)))
				if (fun=="tan")
					return(tan(degressToRadians(num)))
	
				if (fun=="arcsin" && abs(num) <= 1)
					return(radiansToDegress(asin(num)))
				if (fun=="arccos" && abs(num) <= 1)
					return(radiansToDegress(acos(num)))
				if (fun=="arctan")
					return(radiansToDegress(atan(num)))
			}
			else{
				if (fun=="sin")
					return(sin(num))
				if (fun=="cos")
					return(cos(num))
				if (fun=="tan")
					return(tan(num))
	
				if (fun=="arcsin" && abs(num) <= 1)
					return(asin(num))
				if (fun=="arccos" && abs(num) <= 1)
					return(acos(num))
				if (fun=="arctan")
					return(atan(num))
			}
	
			if (fun=="hypsin")
				return((exp(num)-exp(0-num))*0.5)
			if (fun=="hypcos")
				return((exp(num)+exp(-num))*0.5)
			if (fun=="hyptan")
				return((exp(num)-exp(-num))/(exp(num)+exp(-num)))
	
			if (fun=="ahypsin" | fun=="hypcos" | fun=="hyptan"){
				alert("对不起,公式还没有查到!")
				return(num)
			}
	
			alert("超出函数定义范围")
			return(num)
		}
	}
	function factorial(n){
		n = Math.abs(parseInt(n))
		var fac = 1
		for (;n>0;n-=1)
			fac*=n
		return(fac)
	}
	function dms(n){
		var neg = (n<0)
		with(Math)
		{	
			n = abs(n)
			var d = floor(n)
			var m = floor(60*(n-d))
			var s = (n-d)*60-m
		}
		var dms = d+m/100+s*0.006
		if (neg) 
			dms=-dms
		return(dms)
	}
	function deg(n){
		var neg = (n<0)
		with(Math)
		{
			n = abs(n)
			var d = floor(n)
			var m = floor((n-d)*100)
			var s = (n-d)*100-m
		}
		var deg = d+m/60+s/36
		if (neg) 
			deg=-deg
		return(deg)
	}
	function degressToRadians(degress){
		return(degress*Math.PI/180)
	}
	function radiansToDegress(radians){
		return(radians*180/Math.PI)
	}
//界面
//-->
</script>
<script type="text/javascript">
<!--//
var data = {left:"",sign:"",right:"",result:""}
var current = false; // write to data.left
var m = "";
var lastIsMemory = false; // last operator is memory
var isMaxLength = false; // maxlength
var c_get = function(tagId){return document.getElementById(tagId);}
var c_getByName = function(tagParent,tagName,tagType){
	var eles = "";
	if(!tagParent){
		eles = document.getElementsByTagName(tagName);
	}else{
		eles = c_get(tagParent).getElementsByTagName(tagName);
	}
	if(tagType){
		var tags = [];
		for(var i=0;i<eles.length;i++){
			if(eles[i].type == tagType){
				tags.push(eles[i]);
			}
		}
		return tags;
	}
	return eles;
}

var calculator = {
	arith : function(sn){
		if(parseFloat(data.sign) != -2){
			switch(parseFloat(data.sign)){
				case 0:
					data.result = FloatAdd(parseFloat(data.left) , parseFloat(data.right));
					break;
				case 1:
					data.result = FloatSub(parseFloat(data.left) , parseFloat(data.right));
					break;
				case 2:
					data.result = parseFloat(data.left) * parseFloat(data.right);//FloatMul(parseFloat(data.left) , parseFloat(data.right));
					break;
				case 3:
					data.result = parseFloat(data.left) / parseFloat(data.right);//FloatDiv(parseFloat(data.left) , parseFloat(data.right));
					break;
			}
			data.left = "";
			data.sign = sn;
			data.right = "";
			current = false;
//			if(data.result.toString().length >= 3){
//				c_get("resultIpt").value = Number(data.result).toLocaleString();
//			}else{
//				c_get("resultIpt").value = data.result;
//			}
			c_get("resultIpt").value = data.result;//Number(data.result).toLocaleString();
		}
	},
	foo : function(sn){
		if(!lastIsMemory){ // 不是M
			if(data.left == ""){
				if(data.result != ""){
					data.left = data.result;
					current = true;
				}else{
					return false;
				}
			}else{
				if(data.right == ""){
					current = true;
				}else{
					calculator.arith(sn);
					data.left = data.result;
					data.sign = sn;
					data.right = "";
					current = true;
				}
			}
		}else{ // 是M
			if(data.left != "" && data.right != ""){
				calculator.arith(sn);
				data.left = data.result;
				data.sign = sn;
				data.right = "";
				current = true;
			}else{
				data.left = m;
				current = true;
			}
			lastIsMemory = false;
		}
		data.sign = sn;
	},
	input : function(key,type){
		if(type != -2){
			if(data.sign.toString() == "-2"){
				c_get("baseEprsPanel").innerHTML = key.value;
			}else{
				if(!lastIsMemory){
					c_get("baseEprsPanel").innerHTML += key.value;
				}else{
					c_get("baseEprsPanel").innerHTML = key.value;
				}
			}
			//c_get("baseEprsPanel").scrollLeft = c_get("baseEprsPanel").scrollWidth;
			//c_get("resultIpt").scrollLeft = c_get("resultIpt").scrollWidth;/* for ie */
		}
		switch(type){
			case -1: // number
				if(isMaxLength == false){
					if(c_get("resultIpt").value.substring(0,1) == "0" && key.value == "0" && c_get("resultIpt").value.length <= 1){
					}else{
						if(!lastIsMemory){ // 不是M
							if(current){
								if((data.right.toString().indexOf(".") != -1 && key.value == ".")){
									return false;
								}else{
									if(key.value == "." && (data.right == "" || data.right == "0")){
										data.right = "0" + key.value;
									}else{
										if(data.right.toString().length <= 1 && data.right == "0"){
											data.right = key.value
										}else{
											data.right += key.value;
										}
									}
									c_get("resultIpt").value = data.right;
								}
							}else{
								if((data.left.toString().indexOf(".") != -1 && key.value == ".")){
									return false;
								}else{
									if(key.value == "." && (data.left == "" || data.left == "0")){
										data.left = "0" + key.value;
									}else{
										if(data.left.toString().length <= 1 && data.left == "0"){
											data.left = key.value
										}else{
											data.left += key.value;
										}
									}
									c_get("resultIpt").value = data.left;
								}
							}
						}else{
							current = false;
							data.left = key.value;
							c_get("resultIpt").value = data.left;
							lastIsMemory = false;
							//c_get("baseEprsPanel").innerHTML = "";
						}
						if(data.sign.toString() == "-2"){
							data.sign = "";
						}
						if(c_get("resultIpt").value.length > 16){
							isMaxLength = true;
						}
					}
				}// isMaxLength
				else{
					alert("只能输入不大于17位的字符");
				}
				break;
			case -2:
				if(data.left != "" && data.right != ""){
					calculator.arith(-2);
				}else{
					if(data.result != "" && data.sign != "" && parseFloat(data.sign) != -2){
						data.right = data.left;
						data.left = data.result;
						calculator.arith(-2);
					}
				}
				isMaxLength = false;
				break;
			case -3:
				if(c_get("resultIpt").value.substring(0,1) == "-"){
					c_get("resultIpt").value = c_get("resultIpt").value.substr(1);
				}else{
					c_get("resultIpt").value = "-" + c_get("resultIpt").value;
				}

				//if(data.result == ""){
					if(current == false){
						if(data.left == ""){
							if(data.result != ""){
								data.left = data.result;
								data.left = -Number(data.left);
							}
						}else{
							//data.left = -data.left;
							data.left = c_get("resultIpt").value;
						}
					}else{
						data.right = c_get("resultIpt").value;
					}
				//}else{
					//data.result = -data.result;
					//c_get("resultIpt").value = data.result;
				//}
				//alert(data.left + " @@ " + data.sign + " @@ " + data.right);
				break;
			case 0:
				calculator.foo(0);isMaxLength = false;
				break;
			case 1:
				calculator.foo(1);isMaxLength = false;
				break;
			case 2:
				calculator.foo(2);isMaxLength = false;
				break;
			case 3:
				calculator.foo(3);isMaxLength = false;
				break;
		}
		key.blur();
	},
	output : function(pnl,str,isLink){
		if(isLink){
			pnl.innerHTML += str;
		}else{
			pnl.innerHTML = str;
		}
	},
	remove : function(){
		if(current == false){
			if(data.left.length > 0){
				data.left = data.left.substring(0,data.left.length-1);
				c_get("resultIpt").value = data.left;
			}
		}else{
			if(data.right.length > 0){
				data.right = data.right.substring(0,data.right.length-1);
				c_get("resultIpt").value = data.right;
			}
		}
		try{
			c_get("baseEprsPanel").innerHTML = c_get("baseEprsPanel").innerHTML.substring(0,c_get("baseEprsPanel").innerHTML.length-1);
		}catch(e){}
		c_get("simpleDel").blur();
		
		if(c_get("resultIpt").value.length <= 16){
			isMaxLength = false;
		}
	},
	clearAll : function(){
		c_get("resultIpt").value = 0;
		current = false;
		data.left = data.right = data.result = "";
		//m = "";
		c_get("baseEprsPanel").innerHTML = "";
		c_get("simpleClearAllBtn").blur();
		
		isMaxLength = false;
	},
	memory : function(obj,type){
		switch(type){
			// m
			case 0:
				if(c_get("resultIpt").value != ""){
					m = parseFloat(c_get("resultIpt").value);
				}
				lastIsMemory = true;
				break;
			// output m
			case 1:
				if(m != ""){
					if(parseFloat(data.sign) != -2 && data.sign.toString() != ""){
						if(current){
							data.right = m;
						}else{
							data.left = m;
						}
						c_get("baseEprsPanel").innerHTML += m;
					}
					c_get("resultIpt").value = m;
				}
				lastIsMemory = true;
				break;
			// clear m
			case 2:
				m = "";
				break;
			// m+
			case -1:
				if(m == ""){
					if(c_get("resultIpt").value != ""){
						m = parseFloat(c_get("resultIpt").value);
					}
				}else{
					if(c_get("resultIpt").value != ""){
						m = parseFloat(m) + parseFloat(c_get("resultIpt").value);
					}
				}
				lastIsMemory = true;
				break;
			// m*
			case -2:
				if(m == ""){
					if(c_get("resultIpt").value != ""){
						m = parseFloat(c_get("resultIpt").value);
					}
				}else{
					if(c_get("resultIpt").value != ""){
						m = parseFloat(m) * parseFloat(c_get("resultIpt").value);
					}
				}
				lastIsMemory = true;
				break;
		}
		obj.blur();
	}
}

//-->
</script>
</head>
<body topmargin="0" leftmargin="0" style="BACKGROUND-COLOR: transparent">
 
<div id="calculator_base">
<div id="calculator_base_cup">
<div id="calculator_base_container">
<table id="base_table_top" class="calculator_table" cellpadding="0" cellspacing="0" border="0" style="table-layout:fixed;height:120px;">
<tr><td colspan="3" style="height:17px;*height:15px;"></td></tr>
<tr>
<td colspan="3" style="height:60px;">
<input type="text" id="resultIpt" readonly="readonly" class="displayCss" width="390" value="0" size="17" maxlength="17" style="height:53px;*height:56px;"/>
</td>
</tr>
<tr class="topRowCss" style="display:none;">
<td width="117" valign="middle"></td>
<td id="baseEprsPanel" valign="middle" width="290" style="text-align:right"></td>
<td width="30"></td>
</tr>
<tr><td colspan="3" style="height:40px;*height:30px;">&nbsp;</td>
</tr>
</table>
<table id="base_table_main" class="calculator_table" align="center" cellpadding="0" cellspacing="0" border="0" style="width:96%;">
<tr>
<td><input type="button" value="存储" onclick="calculator.memory(this,0);" class="baseBtnCommonCss"/></td>
<td><input type="button" value="取存" onclick="calculator.memory(this,1);" class="baseBtnCommonCss"/></td>
<td><input type="button" id="simpleDel" value="退格" onclick="calculator.remove();" class="baseBtnCommonCss baseBtnCss1"/></td>
<td><input type="button" id="simpleClearAllBtn" value="清屏" onclick="calculator.clearAll();" class="baseBtnCommonCss baseBtnCss1"/></td>
</tr>
<tr>
<td><input type="button" value="累存" onclick="calculator.memory(this,-1);" class="baseBtnCommonCss"/></td>
<td><input type="button" value="积存" onclick="calculator.memory(this,-2);" class="baseBtnCommonCss"/></td>
<td><input type="button" value="清存" onclick="calculator.memory(this,2);" class="baseBtnCommonCss"/></td>
<td><input type="button" id="simpleDivi" value="÷" onclick="calculator.input(this,3);" class="baseBtnCommonCss baseBtnCss2"/></td>
</tr>
<tr>
<td><input type="button" id="simple7" value="7" onclick="calculator.input(this,-1);" class="baseBtnCommonCss baseBtnCss3"/></td>
<td><input type="button" id="simple8" value="8" onclick="calculator.input(this,-1);" class="baseBtnCommonCss baseBtnCss3"/></td>
<td><input type="button" id="simple9" value="9" onclick="calculator.input(this,-1);" class="baseBtnCommonCss baseBtnCss3"/></td>
<td><input type="button" id="simpleMulti" value="×" onclick="calculator.input(this,2);" class="baseBtnCommonCss baseBtnCss2"/></td>
</tr>
<tr>
<td><input type="button" id="simple4" value="4" onclick="calculator.input(this,-1);" class="baseBtnCommonCss baseBtnCss3"/></td>
<td><input type="button" id="simple5" value="5" onclick="calculator.input(this,-1);" class="baseBtnCommonCss baseBtnCss3"/></td>
<td><input type="button" id="simple6" value="6" onclick="calculator.input(this,-1);" class="baseBtnCommonCss baseBtnCss3"/></td>
<td><input type="button" id="simpleSubtr" value="-" onclick="calculator.input(this,1);" class="baseBtnCommonCss baseBtnCss2"/></td>
</tr>
<tr>
<td><input type="button" id="simple1" value="1" onclick="calculator.input(this,-1);" class="baseBtnCommonCss baseBtnCss3"/></td>
<td><input type="button" id="simple2" value="2" onclick="calculator.input(this,-1);" class="baseBtnCommonCss baseBtnCss3"/></td>
<td><input type="button" id="simple3" value="3" onclick="calculator.input(this,-1);" class="baseBtnCommonCss baseBtnCss3"/></td>
<td><input type="button" id="simpleAdd" value="+" onclick="calculator.input(this,0);" class="baseBtnCommonCss baseBtnCss2"/></td>
</tr>
<tr>
<td><input type="button" id="simple0" value="0" onclick="calculator.input(this,-1);" class="baseBtnCommonCss baseBtnCss3"/></td>
<td><input type="button" id="simpleDot" value="." onclick="calculator.input(this,-1);" class="baseBtnCommonCss baseBtnCss3"/></td>
<td><input type="button" value="+/-" onclick="calculator.input(this,-3);" class="baseBtnCommonCss baseBtnCss3"/></td>
<td><input type="button" id="simpleEqual" value="=" onclick="calculator.input(this,-2);" class="baseBtnCommonCss baseBtnCss4"/></td>
</tr>
</table>
</div>
<div class="calculator_tab" id="calculator_tabs">
<ul>
<li>基础</li>
<li class="selTabBottom" onclick="showCalculator(1);">高级</li>
</ul>
</div>
</div>
</div>
 
 
<div id="calculator_complete">
<div id="calculator_complete_cup">
<div id="calculator_complete_container">
<form id="completeFrm" name="calc" style="margin:0px;padding:0px;">
<div id="complete_button_panel">
<table id="complete_table_top" class="calculator_table" cellpadding="0" cellspacing="0" border="0" style="table-layout:fixed;">
<tr><td colspan="3" style="height:17px;*height:17px;"></td></tr>
<tr>
<td colspan="3" style="height:60px;">
<input type="text" name="display" readonly="readonly" value="0" class="displayCss" size="17" maxlength="17"/>
</td>
</tr>
<tr class="topRowCss" style="display:none;">
<td width="117" valign="middle">&nbsp;</td>
<td id="completeEprsPanel" valign="middle" width="290" style="text-align:right"></td>
<td width="30"></td>
</tr>
<tr><td style="height:40px;*height:47px;" colspan="3">&nbsp;</td></tr>
</table>
<table id="complete_table_rdo" align="center" class="calculator_table" cellpadding="0" cellspacing="0" border="0" style="width:96%;height:30px;">
<tr>
<td><input type="radio" name="carry" id="carry16" onclick="inputChangCarry(16);"/><label for="carry16">十六进制</label></td>
<td><input type="radio" name="carry" id="carry10" onclick="inputChangCarry(10);" checked="checked"/><label for="carry10">十进制</label></td>
<td><input type="radio" name="carry" id="carry8" onclick="inputChangCarry(8);"/><label for="carry8">八进制</label></td>
<td><input type="radio" name="carry" id="carry2" onclick="inputChangCarry(2);"/><label for="carry2">二进制</label></td>
<td width="10%"></td>
<td><input type="radio" name="angle" id="angleid" checked="checked" value="d" onclick="inputChangAngle('d')"/><label for="angleid">角度制</label></td>
<td><input type="radio" name="angle" id="angleid2" value="r" onclick="inputChangAngle('r');"/><label for="angleid2">弧度制</label></td>
</tr>
</table>
<table id="complete_table_chk" align="center" class="calculator_table" cellpadding="0" cellspacing="0" border="0" style="width:96%;height:30px;">
<tr>
<td><input type="checkbox" name="shiftf" id="shiftid" onclick="inputshift();"/><label for="shiftid" style="color:#FFF;">上档功能</label></td>
<td><input type="checkbox" name="hypf" id="hypfid" onclick="inputshift();"/><label for="hypfid" style="color:#FFF;">双曲函数</label></td>
<td>
<div style="float:left;"><input type="text" name="bracket" readonly="readonly" size="3" class="helperBox" value=""/></div>
<div style="float:left;"><input type="text" name="memory" readonly="readonly" size="3" class="helperBox"/></div>
<div style="float:left;"><input type="text" name="operator" readonly="readonly" size="3" class="helperBox" style="width:45px;" id="operatorIpt"/></div>
</td>
<td><input type="button" id="completeDel" value="退格" onclick="backspace();" class="completeBtnCommonCss"/></td>
<td><input type="button" value="清屏" onclick="document.calc.display.value=0;document.getElementById('completeEprsPanel').innerHTML = '';this.blur();" class="completeBtnCommonCss"/></td>
</tr>
</table>
<table id="complete_table_main" class="calculator_table" align="center" cellpadding="0" cellspacing="0" border="0" style="width:97%;*margin-top:2px;">
<tr>
<td><input type="button" value="存储" onclick="putmemory();" class="completeBtnCommonCss completeBtnCss1"/></td>
<td><input type="button" value="取存" onclick="getmemory();" class="completeBtnCommonCss completeBtnCss1"/></td>
<td><input type="button" value="累存" onclick="addmemory();" class="completeBtnCommonCss completeBtnCss1"/></td>
<td><input type="button" value="积存" onclick="multimemory();" class="completeBtnCommonCss completeBtnCss1"/></td>
<td><input type="button" value="清存" onclick="clearmemory();" class="completeBtnCommonCss completeBtnCss1"/></td>
<td><input type="button" value="全清" onclick="clearall();" class="completeBtnCommonCss"/></td>
</tr>
<tr>
<td><input type="button" id="complete7" name="k7" value="7" onclick="inputkey('7');" class="completeBtnCommonCss completeBtnCss2"/></td>
<td><input type="button" id="complete8" name="k8" value="8" onclick="inputkey('8');" class="completeBtnCommonCss completeBtnCss2"/></td>
<td><input type="button" id="complete9" name="k9" value="9" onclick="inputkey('9');" class="completeBtnCommonCss completeBtnCss2"/></td>
<td><input type="button" id="completeDivi" value="÷" onclick="operation('/',6);" class="completeBtnCommonCss completeBtnCss3"/></td>
<td><input type="button" value="取余" onclick="operation('%',6);" class="completeBtnCommonCss"/></td>
<td><input type="button" value="与" onclick="operation('&amp;',3);" class="completeBtnCommonCss"/></td>
</tr>
<tr>
<td><input type="button" id="complete4" name="k4" value="4" onclick="inputkey('4');" class="completeBtnCommonCss completeBtnCss2"/></td>
<td><input type="button" id="complete5" name="k5" value="5" onclick="inputkey('5');" class="completeBtnCommonCss completeBtnCss2"/></td>
<td><input type="button" id="complete6" name="k6" value="6" onclick="inputkey('6');" class="completeBtnCommonCss completeBtnCss2"/></td>
<td><input type="button" id="completeMulti" value="×" onclick="operation('*',6);" class="completeBtnCommonCss completeBtnCss3"/></td>
<td><input type="button" value="取整" name="floor" onclick="inputfunction('floor','deci');" class="completeBtnCommonCss"/></td>
<td><input type="button" value="或" onclick="operation('|',1);" class="completeBtnCommonCss"/></td>
</tr>
<tr>
<td><input type="button" id="complete1" name="k1" value="1" onclick="inputkey('1');" class="completeBtnCommonCss completeBtnCss2"/></td>
<td><input type="button" id="complete2" name="k2" value="2" onclick="inputkey('2');" class="completeBtnCommonCss completeBtnCss2"/></td>
<td><input type="button" id="complete3" name="k3" value="3" onclick="inputkey('3');" class="completeBtnCommonCss completeBtnCss2"/></td>
<td><input type="button" id="completeSubtr" value="-" onclick="operation('-',5);" class="completeBtnCommonCss completeBtnCss3"/></td>
<td><input type="button" value="左移" onclick="operation('<',4);" class="completeBtnCommonCss"/></td>
<td><input type="button" value="非" onclick="inputfunction('~','~');" class="completeBtnCommonCss"/></td>
</tr>
<tr>
<td><input type="button" id="complete0" name="k0" value="0" onclick="inputkey('0');" class="completeBtnCommonCss completeBtnCss2"/></td>
<td><input type="button" value="+/-" onclick="changeSign();" class="completeBtnCommonCss completeBtnCss2"/></td>
<td><input type="button" id="completeDot" name="kp" value="." onclick="inputkey('.');" class="completeBtnCommonCss completeBtnCss2"/></td>
<td><input type="button" id="completeAdd" value="+" onclick="operation('+',5);" class="completeBtnCommonCss completeBtnCss3"/></td>
<td><input type="button" id="completeEqual" value="=" onclick="result();" class="completeBtnCommonCss completeBtnCss4"/></td>
<td><input type="button" value="异或" onclick="operation('x',2);" class="completeBtnCommonCss"/></td>
</tr>
<tr>
<td><input type="button" name="ka" value="A" onclick="inputkey('a');" class="completeBtnCommonCss"/></td>
<td><input type="button" name="kb" value="B" onclick="inputkey('b');" class="completeBtnCommonCss"/></td>
<td><input type="button" name="kc" value="C" onclick="inputkey('c');" class="completeBtnCommonCss"/></td>
<td><input type="button" name="kd" value="D" onclick="inputkey('d');" class="completeBtnCommonCss"/></td>
<td><input type="button" name="ke" value="E" onclick="inputkey('e');" class="completeBtnCommonCss"/></td>
<td><input type="button" name="kf" value="F" onclick="inputkey('f');" class="completeBtnCommonCss"/></td>
</tr>
<tr><td style="height:11px;*height:18px;" colspan="6"></td></tr>
</table>
</div>
<table id="complete_table_more" class="calculator_table" align="center" cellpadding="0" cellspacing="0" border="0" style="width:90%;*margin-top:2px;">
<tbody id="moreFn">
<tr>
<td><input type="button" name="pi" value="PI" onclick="inputfunction('pi','pi');" class="completeBtnCommonCss completeBtnCss5"/></td>
<td><input type="button" name="e" value="E" onclick="inputfunction('e','e');" class="completeBtnCommonCss completeBtnCss5"/></td>
<td><input type="button" name="bt" value="d.ms" onclick="inputfunction('dms','deg');" class="completeBtnCommonCss completeBtnCss5"/></td>
<td><input type="button" value="(" onclick="addbracket(this);" class="completeBtnCommonCss completeBtnCss5"/></td>
<td><input type="button" value=")" onclick="disbracket(this);" class="completeBtnCommonCss completeBtnCss5"/></td>
</tr>
<tr>
<td><input type="button" name="ln" value="ln" onclick="inputfunction('ln','exp');" class="completeBtnCommonCss completeBtnCss5"/></td>
<td><input type="button" name="log" value="log" onclick="inputfunction('log','expdec');" class="completeBtnCommonCss completeBtnCss5"/></td>
<td><input type="button" name="sin" value="sin" onclick="inputtrig('sin','arcsin','hypsin','ahypsin');" class="completeBtnCommonCss completeBtnCss5"/></td>
<td><input type="button" name="cos" value="cos" onclick="inputtrig('cos','arccos','hypcos','ahypcos');" class="completeBtnCommonCss completeBtnCss5"/></td>
<td><input type="button" name="tan" value="tan" onclick="inputtrig('tan','arctan','hyptan','ahyptan');" class="completeBtnCommonCss completeBtnCss5"/></td>
</tr>
<tr>
<td><input type="button" value="n!" onclick="inputfunction('!','!');" class="completeBtnCommonCss completeBtnCss5"/></td>
<td><input type="button" value="1/x" onclick="inputfunction('recip','recip');" class="completeBtnCommonCss completeBtnCss5"/></td>
<td><input type="button" name="sqr" value="x^2" onclick="inputfunction('sqr','sqrt');" class="completeBtnCommonCss completeBtnCss5"/></td>
<td><input type="button" name="cube" value="x^3" onclick="inputfunction('cube','cubt');" class="completeBtnCommonCss completeBtnCss5"/></td>
<td><input type="button" value="x^y" onclick="operation('^',7);" class="completeBtnCommonCss completeBtnCss5"/></td>
</tr>
</tbody>
</table>
</form>
</div>
<div class="calculator_tab" id="calculator_tabs2">
<ul>
<li class="selTabTop" onclick="showCalculator(0);">基础</li>
<li>高级</li>
</ul>
</div>
</div>
</div>
<script type="text/javascript">
	c_get("calculator_complete").style.display = "none";
</script>
 
<script type="text/javascript">
<!--//
	var byKeyBoard = function(kyCd,evnt){
		var $g = function(tagId){return document.getElementById(tagId);}
		var cd = Number(kyCd);
		var chars = "simple";
		if(c_get("calculator_base").style.display == "none"){
			chars = "complete";
		}
		if(cd == 48 || cd == 96){
			$g(chars + "0").click();
			return false;
		}
		if(cd == 49 || cd == 97){
			$g(chars + "1").click();
			return false;
		}
		if(cd == 50 || cd == 98){
			$g(chars + "2").click();
			return false;
		}
		if(cd == 51 || cd == 99){
			$g(chars + "3").click();
			return false;
		}
		if(cd == 52 || cd == 100){
			$g(chars + "4").click();
			return false;
		}
		if(cd == 53 || cd == 101){
			$g(chars + "5").click();
			return false;
		}
		if(cd == 54 || cd == 102){
			$g(chars + "6").click();
			return false;
		}
		if(cd == 55 || cd == 103){
			$g(chars + "7").click();
			return false;
		}
		if(cd == 56 || cd == 104){
			$g(chars + "8").click();
			return false;
		}
		if(cd == 57 || cd == 105){
			$g(chars + "9").click();
			return false;
		}
		if(cd == 13 || cd == 187){
			$g(chars + "Equal").click();
			return false;
		}
		if(cd == 190 || cd == 110){
			$g(chars + "Dot").click();
			return false;
		}
		if(cd == 109 || cd == 189){
			$g(chars + "Subtr").click();
			return false;
		}
		switch(kyCd){
			case 107:
				$g(chars + "Add").click();
				break;
			case 109:
				$g(chars + "Subtr").click();
				break;
			case 189:
				$g(chars + "Subtr").click();
				break;
			case 106:
				$g(chars + "Multi").click();
				break;
			case 111:
				$g(chars + "Divi").click();
				break;
			case 46:
				//calculator.global.$("simpleDel").click();
				$g(chars + "Del").click();
				break;
		}
	}
	var showCalculator = function(idx,obj){
		bdjs.clearAutoHeight();
		if(idx){
			c_get("calculator_base").style.display = "none";
			c_get("calculator_complete").style.display = "block";
			c_get("calculator_complete").style.position = "relative";
			c_get("calculator_complete_container").style.height = "578px";
			//sc_get("calculator_complete_container").style.backgroundImage = "url(/assets/tools/images/siverbg2.png)";
			bdjs.setHeight(585);
		}else{
			c_get("calculator_base").style.display = "block";
			c_get("calculator_complete").style.display = "none";
			bdjs.setHeight(465);
		}
		calculator.clearAll();
		clearall();
	}
	window.onload = function(){
		document.onkeydown = function(evn){
			var evnt = evn || window.event;
			var keyCode = evnt.keyCode;
			byKeyBoard(keyCode,evnt);
		}
		var buttons = c_getByName("calculator_base_container","input","button");
		var complete_buttons = c_getByName("complete_button_panel","input","button");
		var fn_buttons = c_getByName("moreFn","input","button");
		for(var i=0;i<buttons.length;i++){
			buttons[i].onmousedown = function(){
				this.style.backgroundPosition = "0 0";
				this.style.color = "#f0f0f0";
				this.onmouseup = function(){
					this.style.backgroundPosition = "0 -44px";
					this.style.color = "#fff";
				}
			}
		}
		for(var i=0;i<complete_buttons.length;i++){
			complete_buttons[i].onmousedown = function(){
				this.style.backgroundPosition = "0 0";
				this.onmouseup = function(){
					this.style.backgroundPosition = "0 -34px";
				}
			}
		}
		for(var i=0;i<fn_buttons.length;i++){
			fn_buttons[i].onmousedown = function(){
				this.style.backgroundPosition = "0 0px";
				this.onmouseup = function(){
					this.style.backgroundPosition = "0 -34px";
				}
			}
		}
		inputChangCarry(10);
		
		
		//* background *//
		var linkArgs = location.search;
		if(linkArgs.indexOf("canvas_pos=search") != -1){ // yulan
			document.getElementById("calculator_base").style.width = "540px";
			//document.getElementById("calculator_base").style.background = "#dba869 url(/assets/tools/images/woodbg.gif) repeat-y 0 0";
			document.getElementById("calculator_tabs").style.left = "457px";
			document.getElementById("calculator_base_container").style.margin = "0px 10px";
			
			document.getElementById("calculator_complete").style.width = "540px";
			//document.getElementById("calculator_complete").style.background = "#dba869 url(/assets/tools/images/woodbg.gif) repeat-y 0 0";
			document.getElementById("calculator_tabs2").style.left = "457px";
			document.getElementById("calculator_complete_container").style.margin = "0px 10px";
		}else{
			document.getElementById("calculator_base").style.width = "800px";
			//document.getElementById("calculator_base").style.background = "#dba869 url(/assets/tools/images/woodbgb.jpg) repeat-y 0 0";
			document.getElementById("calculator_tabs").style.left = "450px";
			document.getElementById("calculator_base_container").style.margin = "0";
			
			document.getElementById("calculator_complete").style.width = "800px";
			//document.getElementById("calculator_complete").style.background = "#dba869 url(/assets/tools/images/woodbgb.jpg) repeat-y 0 0";
			document.getElementById("calculator_tabs2").style.left = "450px";
			document.getElementById("calculator_complete_container").style.margin = "0";
		}
	}
//-->
</script>
<script type="text/javascript" src="/assets/tools/
js/unitpngfix.js"></script>
<script type="text/javascript" src="/assets/tools/
js/bdjs_client-1.0.js"></script>
</body>
</html>
