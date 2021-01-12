## 学习 css 页面布局(已废弃, 待重构结构)
#### [1 基础](#base)
#### [2 样式布局](#style)
#### <a name='base'>1.基础</a>
**子选择器：**
.food>li{border:1px solid red;}
只选择food的一级子标签li而对其孙子没有影响

**包含（后代）选择器：**.food li{}food 下面的所有li标签

**伪类选择器：** a:hover{}

**分组选择符：** h1,h2{}

**css样式优先级：** 可以从层叠的角度来看，即后面的覆盖前面的样式

**权重：** 标签：1 类：10 id：100

**重要性：**
```
p{
    color:red!important;
    font-size:10px!important;
}
```
可以让该样式具有最高权值

**字体：**

italic：斜体

下划线和删除线：
```
a {
    text-decoration:underline;
    text-decoration:line-through;
}
```

段落缩进：
```
p{
    text-indent:2em;//2em就是字体的两倍大小
}
```

字体之间的间距：
```
h1{
    letter-spacing:50px;//中英文单个文字之间的间距
    word-spacing:50px;//英文单词之间的间距
}
```

**元素分类：**

[点此查看元素含义](http://www.w3school.com.cn/tags/tag_dl.asp)

块级元素：
```
<div>、<p>、<h1>...<h6>、<ul>、<ol>、<dl>、<table>、<address>、<blockquote>、<form>
```

特点：
<ol>
    <li>每个元素独占一行</li>
    <li>相当于一个盒子</li>
    <li>宽度默认为父元素的100%</li>
</ol>


内联(行内)元素：
```
<a>、<span>、<br>、<i>、<em>、<strong>、<label>、<q>、<var>、<cite>、<code>
```

特点：
<ol>
    <li>和其他元素在同一行</li>
    <li>不可设置宽高及上下margin</li>
    <li>宽度默认为包含内容的宽度</li>
</ol>


内联块状元素：
```
<img>、<input>
```

特点：
<ol>
    <li>和其他元素在同一行</li>
    <li>相当于一个盒子</li>
</ol>


**盒子模型：**

![](./img/boxModel.jpg)

**层模型：**

三种形式：
<ol>
    <li>绝对定位(position: absolute)
    <p>如果想为元素设置层模型中的绝对定位，需要设置 position:absolute (表示绝对定位)，
    这条语句的作用将元素从文档流中拖出来，然后使用 left、right、top、bottom 属性相对于
    其最接近的一个具有定位属性(position:relative)的父包含块进行绝对定位。如果不存在
    这样的包含块，则相对于 body 元素，即相对于浏览器窗口。</p>
    </li>
    <li>相对定位(position: relative)
    <p>它通过 left、right、top、bottom 属性确定元素在正常文档流中的偏移位置。相对定位完成的过程是首先按 static(float) 方式生成一个元素(并且元素像层一样浮动了起来)，然后相对于以前的位置移动，移动的方向和幅度由left、right、top、bottom属性确定，偏移前的位置保留不动。</p>
    </li>
    <li>固定定位(position: fixed)
    <p>表示固定定位，与absolute定位类型类似，但它的相对移动的坐标是视图（屏幕内的网页窗口）本身。</p>
    </li>
</ol>

**字体缩写：**

```
body{
    font-size:12px;
    font-family:"宋体",sans-serif；
    font-style:italic;//字体样式为斜体
    font-variant:small-caps; //把段落设置为小型大写字母字体：(variant转化)
    font-weight:bold;
    line-height:1.5em;//1.5倍字体大小
}
```
上述代码可以缩写为一句：
```
body{
    font:italic  small-caps  bold  12px/1.5em  "宋体",sans-serif;
}
```

注意：
<ol>
    <li>在所写的时候至少要填写font-size和font-family两个属性</li>
    <li>font-size和line-height要用'/'隔开</li>
</ol>

常用情况(只有字体、行间距、中文字体、英文字体设置)：
```
body{
    font:12px/1.5em "宋体",sans-serif;
}
```

#### <a name="style">2.样式布局</a>

**不定宽块状元素水平居中方法：**

1. 将元素放入 table>td 标签中，然后设置 table 的 ```margin:0 auto``` 这是因为 table 的宽度等于其内容的长度，即可以看做一个定宽的元素，从而进行定宽块的居中方法
2. 设置元素为inline类型，后设置其父元素 ```text-aline:center```
3. 父元素： ```position:relative;margin-left:50%;``` 子元素: ```position:absolute;left:-50%;```
4. 父元素位置不变 ```position:relative;``` 子元素: ```position:absolute;left:50%;transform:translate(50%,0)```
此处也可用 css3 简写为 ```position:absolute;left:calc(50%, -50%);```

**垂直居中方法：**

1. 父元素高度确定的单行文本：父元素 line-height＝height
2. 父元素高度确定的多行文本：

> 将元素放在 table>tbody>tr>td 中, td 相当于父元素;
> 将元素设置为 display:table-cell 类型，激活其 vertical-align 属性并设置其为 middle.

3. 相对于视图的居中方法： ```margin: 50vh auto 0;transform:translateY(-50%, 0);```

**flexbox居中：**

将父元素设置为: ```display:flex``` 子元素： ```margin:auto```

**隐性改变 display 类型:**

当元素设置为以下两种情况的时候:

1. position:absolute
2. float:left or right

元素会默认设置成： display:inline-block 类型