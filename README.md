# binbin06
<!DOCTYPE html>
<html>
<head>
	<title>binbin07</title>
	<style type="text/css">
		#tree{
			width: 600px;
		}
		.foot{
			background-color: white;
			border: 2px solid #999;
			padding:20px 10px;
			width: 45%;
			box-sizing: border-box;
			float: left;
			margin: 0 2.5%;
		}
		.active{
			background-color: #F08080;
			padding:20px 10px;
			border: 2px solid #999;
			width: 45%;
			box-sizing: border-box;
			float: left;
			margin: 0 2.5%;
		}
		.first{
			z-index: 10;
		}
		.second{
			z-index: 20;
		}
		.third{
			z-index: 30;
		}
		.fourth{
			z-index: 40;
		}
		#ppp{
			float: left;
		}
	</style>
</head>
<body>
<div id="ppp">
<button id="DLR">前序遍历</button>
<button id="LDR">中序遍历</button>
<button id="LRD">后序遍历</button>
</div>
<div id="tree" class="foot" class="first">
	<div class="foot" class="second">
		<div class="foot" class="third">
			<div class="foot" class="fourth"></div>
			<div class="foot"></div>
		</div>
		<div class="foot" class="third">
			<div class="foot" class="fourth"></div>
			<div class="foot" class="fourth"></div>
		</div>
	</div>
	<div class="foot" class="second">
		<div class="foot" class="third">
			<div class="foot" class="fourth"></div>
			<div class="foot" class="fourth"></div>
		</div>
		<div class="foot" class="third">
			<div class="foot" class="fourth"></div>
			<div class="foot" class="fourth"></div>
		</div>
	</div>
</div>
<script type="text/javascript">
	var a = document.getElementById("DLR");
	var tree = document.getElementById("tree");
	var Nodearray = new Array();
	function active(Nodearray){
		var i=0;
		var int = setInterval(function(){
			if (i<Nodearray.length) {
				if (i>0) {
				Nodearray[i-1].className= "foot";}
				Nodearray[i].className = "active";
				i++;
			} else {
				Nodearray[i-1].className = "foot";
				clearInterval(int);
			}
		},500);
	}
	function DLR(root){
		if (!root) {
			return;
		} else {
			Nodearray.push(root);
			DLR(root.children[0]);
			DLR(root.children[1]);
		}
	}
	function LDR(root){
		if (!root) {
			return;
		} else {
			LDR(root.children[0]);
			Nodearray.push(root);
			LDR(root.children[1]);
		}
	}
	function LRD(root){
		if (!root) {
			return;
		} else {
			LRD(root.children[0]);
			LRD(root.children[1]);
			Nodearray.push(root);
		}
	}
	a.onclick = function(){
		Nodearray = [];
		DLR(tree);
		active(Nodearray);
	};
	document.getElementById("LDR").onclick = function(){
		Nodearray = [];
		LDR(tree);
		active(Nodearray);
	};
	document.getElementById("LRD").onclick = function(){
		Nodearray = [];
		LRD(tree);
		active(Nodearray);
	};
</script>
</body>
</html>
