# 关于CSS3

## CSS3新增特性
- 边框：border-radius,box-shadow,border-image
- 背景：background-size,backgound-origin,background-clip
- @font-face 加载字体样式
- 文本效果：word-wrap 单词换行方式;text-overflow 当前行超过指定容器边界如何显示，clip表示直接切割，ellipsis表示省略号;word-break,text-outline等等
- 文字渲染：text-fill-color,text-stroke-color,text-stroke-width,分别表示文字内部填充颜色、边界填充颜色、边界宽度
- 多列布局：column-count,column-rule,column-gap,分别表示布局列数、列间间隔条样式、列与列之间的间隔
- 2D转换 transform,方法有translate(),rotate(),scale(),skew(),matrix(),分别表示旋转、尺寸变化、翻转、组合所有2D方法
- 3D转换 transform，方法有在2D的基础上加 3d或X,Y,Z,比如rotateZ(angle),rotate3d(x,y,z,angle),以及perspective(n)规定透视效果
- 过渡 transition : property duration timing-function delay 
- 动画 @keyframes规则用于创建动画，animation:name duration timing-function delay iteration-count direction play-state fill-mode
- 盒子模型：box-sizing，resize，outline-offset
- 透明度：rgba(255,255,255,0.8)
- 渐变效果：gradient，，linear–线性渐变
-  媒体查询：@media


## flex 布局相关属性
###创建flex容器 
display:flex;

### 一些概念
direction:rtl; 也会让flex item从右向左布局

主轴和侧轴
![主轴和侧轴](https://static.bocoup.com/blog/flexbox%20diagram%202.jpg)

### flex container 的属性
- flex-direction：row | row-reverse | column | column-reverse 表示flex item的排列方式，默认为row。表示和writing-mode一样方式排列，而column则是在侧轴上布局
- justify-content：flex-start | flex-end | center | space-between | space-around 调整flex items 在主轴的位置，分别就是从开始位置、结束位置、居中、两端顶格有间隔、两端不顶格有间隔
- align-items:flex-start | flex-end | center | baseline | stretch 调整flex items在侧轴的位置
- flex-wrap: nowrap | wrap | wrap-reverse 伸缩行是否换行，wrap-reverse让flex items在侧轴方向相反
- align-content: stretch | flex-start | flex-end | center | space-between | space-around 改变flex-wrap的行为，和align-items相似，但是它调整的是flex lines
- flex-flow:[flex-direction][flex-wrap]

### flex items 的属性
- order 设置顺序
- margin auto加方向可以把flex items推向不同方向，都auto实现垂直居中
- align-self: stretch | flex-start | flex-end | center | baseline 设置item自己的主轴位置
- flex: [number] 设置子元素是否可伸缩，number表示在可伸缩位置中占的比例
- flex:initial 有空位的时候不伸缩，没有的时候会变得稍微小点
- flex：none 都会伸缩
