# HTML

#### 请解释一下 DOCTYPE 的作用，有 DOCTYPE 和没有 DOCTYPE 有什么区别？

答：!DOCTYPE 指定了 HTML 文档遵循的文档类型定义。<!DOCTYPE>声明位于文档中的最前面的位置，处于<html>标签之前。此标签可告知浏览器文档使用哪种 HTML 或者 XHTML 规范。

#### 写一个三栏的布局，要求中间栏最先加载？

答：中间优先加载，按照 HTML 顺序解释的原则，即中间放在文档前面。而中间放在前又会影响文档流的布局，所以在此改变一下元素的相对位置即可。
[实例](./demo/middle_demo.html)

#### 树的遍历方式有哪些，简单介绍下方法？

答：树的遍历方式有两种：深度优先和广度优先。深度优先是先遍历层级关系，广度优先是先遍历同层次的节点

#### 使用addEventListener点击li弹出内容，并且动态添加li之后有效   
```JS
<ul>
    <li>1</li>
    <li>2</li>
    <li>3</li>
    <li>4</li>
</ul>

//JS
var ulNode = document.getElementById("ul");
    ulNode.addEventListener('click', function (e) {
        if (e.target && e.target.nodeName.toUpperCase() == "LI") {
            alert(e.target.innerHTML);
        }
    }, false);
```   
[实例](./demo/addEventListener.html)