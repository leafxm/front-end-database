# 关于布局

## 左边定宽，右边自适应的两列布局
- float + margin

左定宽，设置float：left,右设置margin-left为左边的宽度。

- absolute + margin

父元素设置相对定位，左定宽设置绝对定位，右设置margin-left为左边的宽度。

- float + overflow

左定宽，设置float：left,右设置overflow 不为 visible 生成BFC。

- flex 

父元素设置 display:flex,左定宽，右设置 flex:1


## 左右定宽，中间自适应的三栏布局

- float + margin

左定宽、设置float：left,右定宽、设置float：right,中间设置margin为左、右边的宽度。

- absolute + margin

父元素设置相对定位，左、右定宽设置绝对定位，左设置left:0,右设置right:0,中间设置margin为左、右边的宽度。

- float + overflow

左定宽、设置float：left,右定宽、设置float：right,中间设置overflow 不为 visible 生成BFC。

- flex 

父元素设置 display:flex,左定宽，中间设置 flex:1，右定宽。
