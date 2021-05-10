## css权重

!important 无穷大
第一等级： 内敛样式，style=""，权重1000
第二等级： id选择器，id="text", 权重为100
第三等级： class|伪类|属性选择器 .class| :hover,:link,:visisted|[type] 权重 10
第四等级： 标签|伪元素选择器 a,span,b,div|:after,:before 权重1
其他选择器 *(通配符)  > (子选择器)  +(相邻选择器) 他们的权重值为0


## 盒模型
### content-box 标准(w3c)
盒子的总宽度 = 设置的宽度 + padding宽度 + border宽度
盒子的总高度 = 设置的高度 + padding高度 + border高度

### border-box IE
盒子的总宽度 = 内容区域的宽度 + padding宽度 + border宽度 = 设置的宽度
盒子的总高度 = 内容区域的高度 + padding高度 + border高度 = 设置的高度


## BFC
> 块级格式化上下文（block formatting context）是Web页面的可视化CSS渲染的一部分。它是块盒子的布局发生，浮动互相交互的区域。

**具有 BFC 特性的元素可以看作是隔离了的独立容器，容器里面的元素不会在布局上影响到外面的元素，并且 BFC 具有普通容器所没有的一些特性。**

通俗一点来讲，可以把 BFC 理解为一个封闭的大箱子，箱子内部的元素无论如何翻江倒海，都不会影响到外部。

**触发 BFC：**

- body 根元素
- 浮动元素：float 除 none 以外的值
- 绝对定位元素：position (absolute、fixed)
- display 为 inline-block、table-cells、flex
- overflow 除了 visible 以外的值 (hidden、auto、scroll)

**用途**

- 清除浮动
- 解决外边距合并
- 布局(两边固定宽度，中间自适应宽度)


## 水平垂直居中

### 定宽高 
> 1 定宽高 使用定位+margin
```
div {
    position: absolute;
    left: 50%;
    top: 50%;
    margin-left: -250px;
    margin-top: -250px;
    width: 500px;
    height: 500px;
    background: yellow;
    z-index: 1;
}
```  
> 使用定位+transfrom
```
div {
    position: absolute;
    left: 50%;
    top: 50%;
    width: 500px;
    height: 500px;
    background: yellow;
    z-index: 1;
    transform: translate3d(-50%,-50%,0);
}
```
### 不定宽高 不定宽高的方法基本都适用于定宽
> 使用定位+transform同样是适用的
```
element.style {
    position: absolute;
    left: 50%;
    top: 50%;
    background: yellow;
    z-index: 1;
    transform: translate3d(-50%,-50%,0);
}
```

> 使用grid

```
div.parent {
    display: grid;
    height: 200px;
}
div.child {
    justify-self: center;
    align-self: center;
}
```

> flex

```
div.parent {
    display: flex;
    height: 200px;
}
div.child {
    margin: auto;
}
```
> table
```
div.parent {
    display: table;
    width: 100%;
    height: 300px;
}
div.child {
    display: table-cell;
    vertical-align: middle;
    text-align: center;
}
```

> table-cell
```
.parent {
    display: table-cell;
    background-color: orange;
    text-align: center;
    vertical-align: middle;
    width: 300px;
    height: 300px;
}
.child {
    display: inline-block;
    background-color: blue;
}
```
