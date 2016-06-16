# 关于布局

## 布局
- 两列布局（左右定宽）
	- 都float:left
	- 左边left 右边right

- 两列布局（左边定宽，右边自适应）
	- 左边浮动，右边加上一个margin-left值（等于左宽）
	- 浮动和负边距实现
	
	
			<div id="left">
				Left Sidebar
			</div>
			<div id="content">
				<div id="contentInner">
					Main Content
				</div>
			</div>
	
			*{
				margin: 0;
				padding: 0;
			}
			#left {
				background-color: green;
				float: left;
				width: 220px;
				margin-right: -100%;
			}
			
			#content {
				float: left;
				width: 100%;
			}
			
			#contentInner {
				margin-left: 220px;/*==等于左边栏宽度值==*/
				background-color: orange;
			}
 
- css实现三栏布局，中间自适应

方法一：自身浮动法。左栏左浮动，右栏右浮动。
  
	  .left , .right{
                height: 300px;
                width: 200px;
            }
           .right{
                float: right;
                background-color: red;
            }
            .left{
                float: left;
                background-color: #080808;
            }
            .middle{
               height: 300px;
                margin: 0 200px;//没有这行，当宽度缩小到一定程度的时候，中间的内容可能换行
                background-color: blue;
            }
方法二：margin负值法
  
	  <style>
            body{
                margin: 0;
                padding: 0;
            }
            .left , .right{
                height: 300px;
                width: 200px;
                float: left;
            }
            .right{
                margin-left: -200px;
                background-color: red;
            }

            .left{
                margin-left: -100%;
                background-color: #080808;
            }

            .middle{
                height: 300px;
                width: 100%;
                float: left;
               background-color: blue;
            }
        </style>

    <!--放第一行-->

    <div class="middle">middle</div>
    <div class="left">left</div>
    <div class="right">right</div>
方法三：绝对定位法。左右两栏采用绝对定位，分别固定于页面的左右两侧，中间的主体栏用左右margin值撑开距离。
	
	<style>
	    body{
	        margin: 0;
	       padding: 0;
	    }	
	    .left , .right{
	      top: 0;
	        height: 300px;
	       width: 200px;
	        position: absolute;
	    }	
	    .right{
	        right: 0;
	        background-color: red;
	    }
	    .left{
	        left: 0;
	       background-color: #080808;
	    }
	    .middle{
	        margin: 0 200px;
	       height: 300px;
	        background-color: blue;
	    }
		</style>
			
		<div class="left">left</div>	
		<!--这种方法没有严格限定中间这栏放置何处-->	
		<div class="middle">middle</div>		
		<div class="right">right</div>

-  一个满屏 品 字布局 如何设计?

简单的方式：
    上面的div宽100%，
    下面的两个div分别宽50%，
    然后用float或者inline使其不换行即可

- 用纯CSS创建一个三角形的原理是什么？

把上、左、右三条边隐藏掉（颜色设为 `transparent`）
			
	#demo {
		width: 0;
		height: 0;
		border-width: 20px;
		border-style: solid;
		border-color: transparent transparent red transparent;
	}