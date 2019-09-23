# react-typescript

### 项目概况
***
使用蚂蚁金服的Antd开发的一套后台管理系统，主要用到了react、typescript、antd、mobx等技术，使用webpack4打包构建，包含React16的code splitting等新特性。

### 项目主要技术结构

***
* react
* typescript
* antd
* mobx
* webpack4
* react-router4

### 安装
***
在终端下操作

项目地址: (`git clone`)

```
git clone git@github.com:xpioneer/react-typescript.git
```

安装node_modules依赖 `yarn`

```
yarn #in your command terminal
```
***


### 运行
启动开发服务: (http://localhost:8022)

```
yarn start
```

生产环境打包

```
yarn build
```
//自定义滚动条

<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>演示：jQuery.nicescroll美化滚动条</title>
<meta name="keywords" content="美化滚动条,jquery.nicescroll" />
<meta name="description" content="jQuery滚动条插件兼容ie6+、手机、ipad。" />
<style type="text/css">
	        *{
				margin: 0;
				padding: 0;
				font-size: 0;
				outline: none;
				border: none;
	        }
			.scrollContain{
				width: 100%;
				height: 200px;
				overflow-y: scroll;
				position: relative;
				left: 0;
				top: 0;
			}
            .scroll{
				background: #9cb945;
			}
			.scrollDt{
				border-radius: 4px;
				background: red;
				width: 4px;
				height: 10px;
				position: absolute;
				left: 2px;
				top: 0;
				display: none;
			}
	        p{
				font-size: 13px;
			}
			.scrollHide{
				overflow: hidden;
				width: 200px;
				background: red;
			}
        </style>
</head>
<body>
<div class="scrollHide" id="scrollHide">
	<div class="scrollContain" id="scrollContain">
		<div class="scrollDt" id="scrollDt">
		</div>
		<div class="scroll" id="scrollContent">
			<p>fsdfsdfdsfdsf</p>
			<p>fsdfsdfdsfdsf</p>
			<p>fsdfsdfdsfdsf</p>
			<p>fsdfsdfdsfdsf</p>
			<p>fsdfsdfdsfdsf</p>
			<p>fsdfsdfdsfdsf</p>
			<p>fsdfsdfdsfdsf</p>
			<p>fsdfsdfdsfdsf</p>
			<p>fsdfsdfdsfdsf</p>
			<p>fsdfsdfdsfdsf</p>
			<p>fsdfsdfdsfdsf</p>
			<p>fsdfsdfdsfdsf</p>
			<p>fsdfsdfdsfdsf</p>
			<p>fsdfsdfdsfdsf</p>
			<p>fsdfsdfdsfdsf</p>
			<p>fsdfsdfdsfdsf</p>
		</div>
	</div>
</div>

<!--<script src="http://www.jq22.com/jquery/1.9.1/jquery.min.js"></script>-->
<!--<script type="text/javascript" src="http://www.jq22.com/demo/jQueryNicescroll20160214/js/jquery.nicescroll.js"></script>-->
<script type="text/javascript">
	function defineScroll(data) {
		var contain = getDom(data.contain);
		var contentContain = getDom(data.contentContain);
		var scrollDom = getDom(data.scrollDom);
		var content = getDom(data.content);

		var contentWidth = content.offsetWidth
		contentContain.style.width = (getScrollBarWidth(contentContain)*2+contentWidth*1)+"px"
		function getScrollTop(DOM,leftScroll,content,scrollHide) {
			var scroll_top = 0;
			if (DOM && DOM.scrollTop) {
				scroll_top = DOM.scrollTop;
			}else if (document.body) {
				scroll_top = document.body.scrollTop;
			}
			//获取视口高度
			var viewHeiht = DOM.offsetHeight
			//获取内容高度
			var contentHeight = content.offsetHeight
			var contentWidth = content.offsetWidth
			DOM.style.width = (getScrollBarWidth(DOM)*2+contentWidth*1)+"px"
			//设置滚动条高度
			leftScroll.style.height = (viewHeiht - (contentHeight - viewHeiht))+"px"
			leftScroll.style.display = 'block'
			// return scroll_top;
			leftScroll.style.top = scroll_top*2+"px"
			return false
		}
		function getScrollBarWidth(Dom) {
			var scrollBarWidth = Dom.offsetWidth - Dom.clientWidth;
			//将添加的元素删除
			return scrollBarWidth;
		}
		function getDom(id) {
			return document.getElementById(id)
		}

		function addEvent(id,type,fn,isBubble){

			var dom = document.getElementById(id);
			if(!isBubble) isBubble=false;
			if(dom.addEventListenner){
				dom.addEventListenner(type,fn,isBubble);
			}else if(dom.attachEvent){
				Transit = function(){
					fn.call(dom);
				}
				dom.attachEvent('on'+type,Transit);
			}else{
				dom['on'+type] = fn;
			}
		}
		function removeEvent(id,type,fn,isBubble){
			var dom = document.getElementById(id);
			if(!isBubble) isBubble=false;
			if(dom.removeEventListenner){
				dom.removeEventListenner(type,fn,isBubble)
			}else if(dom.detachEvent){
				dom.detachEvent('on'+type,Transit)
			}else{
				dom['on'+type]=null;
			}

		}


		addEvent(data.contentContain,"scroll",function () {
			getScrollTop(contentContain,scrollDom,content,contain);
		},false)
		addEvent(data.contain,"mouseover",function () {
			getScrollTop(contentContain,scrollDom,content,contain);
		},true)
		addEvent(data.contain,"mouseout",function () {
			scrollDom.style.display = "none"
		},true)
	}



	defineScroll({
		contain:"scrollHide",
		contentContain:"scrollContain",
		scrollDom:"scrollDt",
		content:"scrollContent",
	})







</script>
</body>
</html>



