## em vs rem

em作为font-size单位时，代表父元素的font-size大小，作为其他属性单位时代表自身font-size大小；

rem作用与非根元素时，相对于根元素font-size大小；rem作用与根元素font-size时，代表了它的初始值；



## rem布局分析

为了达到移动端自适应的效果，即元素和字体都能随着屏幕的宽度变化而变化，我们需要自适应布局的解决方案。

**场景分析：**

当你使用宽度为750的设计稿时，其中一个元素是640px, 你不可能直接写`width: 640px`因为你的屏幕宽度不是750px, 但这里有一个不变的比例：

`640/750 = 元素真实宽度/clientWidth`，

即`元素真实宽度 = 640 * （clientWidth/750）`

那么此时rem就可以闪亮登场了，当我们把html元素的font-size设置为`clientWidth/750`，640rem就是元素的真实宽度了。

**一句话总结：**

rem布局的本质是等比缩放，通常情况下我们设置根节点font-size为`clientWidth/设计稿宽度`



**实现方式**

~~~js
// 方式1
const el = document.documentElement;
const remVal = el.clientWidth / 750 + 'px';
el.style.fontSize = remVal;
~~~

~~~css
// 方式2 但注意安卓4.4以下不支持vw单位
html{
	font-size: calc(100vw / 750);
}
~~~

