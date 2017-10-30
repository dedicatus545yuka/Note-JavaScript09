# Note-JavaScript09
DOM概念，节点树，Document对象,初步认识事件
### DOM
`最大的作用，允许JS操作Html和CSS`
#### 什么是DOM
1. `W3C`对`DOM`的定义    
> `DOM`是一个独立于任何语言和平台的接口，允许任何语言或脚本动态地访问和更新`HTML`文档的内容、结构和样式。该 HTML 页面可以进一步处理，并且该处理的结果可以被合并到所呈现的 HTML 页面中。  

2. 为什么要使用`DOM`    
> DHTML（动态的 HTML）是一些厂商为了宣传所使用的术语，用来描述 HTML、CSS 和 JavaScript 的组合，允许 HTML 文档实现动态化。W3C 已经收到一些成员公司提交的关于 HTML 文档的对象模型应该暴露在 JavaScript 中的方法。这些建议中没有建议任何新的 HTML 标签或样式技术。W3C 正在努力确保动态交互和脚本语言的解决方案是一致的。          
3. DOM发展历程   
-  DOM level 0 定义了 Document 对象的一些属性和方法。     
    - DOM level 0 并不是 W3C 的标准
-  DOM level 1 是 W3C 在 1998 年 10 月提出的第一个正式的 W3C DOM 标准。    
    - DOM Core: 提供了 DOM 模型、内存管理、命名约定等方便访问和操作 HTML 页面的内容。
    - DOM HTML: 提供了一些与 HTML 页面相关的对象以及 HTML 标签的属性和方法等。
    - DOM level 1 中忽略了事件模型。
-  DOM level 2 是基于 DOM level 1 并且扩展了 DOM level 1，还添加了视图、事件以及 CSS 样式的内容。 
    - DOM View: 描述 HTML 文档的各种视图的接口。
    - DOM Events: 描述了事件流、事件监听注册、事件接口以及文档事件接口等内容。
    - DOM Style: 描述了 CSS 样式的接口。
    - DOM Traversal and Range: 描述遍历和操作 HTML 文档的接口。
-  DOM level 3 引入了统一的文档读取和保存的方法，以及文档验证的内容等。 
    - DOM Load and Save: 描述了文档的读取和保存的接口。
    - DOM Validation: 描述了文档验证的接口。
    - DOM level 3 引入的主要是对 XML 文档的支持，对于 HTML 文档的用处并不大。
4. DOM 的组成   
- DOM Core: 指定类属类型，将带有标记的文档看成树状结构并据此对文档进行相关操作。
- DOM HTML: 提供用于操作 HTML 文档以及类似于 JavaScript 对象模型语法的功能部件，在核心 DOM 的基础上支持对所有 HTML 元素对象进行操作。
- DOM CSS: 提供脚本编程实现 CSS 的接口。
- DOM XML（这里不谈这个，而是谈事件）
#### 详解DOM
![DOM的概念解析图](http://a4.qpic.cn/psb?/V118JuTr0BKcy7/BX*CYHupeLg3HFc60.inD01CzHlu3kkXYE3FPWyBPLU!/m/dPMAAAAAAAAA&bo=GwWAAgAAAAADB74!&rf=photolist)
#### 节点树
1. DOM树结构  
- DOM 将 HTML 页面表示为一个树形结构，方便访问和操作 HTML 页面中的内容  
- 当浏览器加载 HTML 页面时，会创建这个 HTML 页面的模型，保存到浏览器的内存中。  
2. 节点  
>节点（node）是个网络术语，表示网络中的连接点。一个网络是由一些节点构成的集合。

- 在 DOM 树结构中主要由以下 4 种节点组成
    - 文档节点: 表示整个 HTML 页面（相当于 document 对象）。当需要访问任何标签、属性或文本时，都可以通过文档节点进行导航。
    - 元素节点: 表示 HTML 页面中的标签（即 HTML 页面的结构）。当访问 DOM 树时，需要从查找元素节点（标签）开始。
    - 文本节点: 表示 HTML 页面中的标签所包含的文本内容。
    - 属性节点: 表示 HTML 页面中的开始标签包含的属性。

![DOM节点树结构](http://a3.qpic.cn/psb?/V118JuTr0BKcy7/aTcgwFsdhWTBL9XewebDn*H67BAbOEZLODtip*BuUls!/m/dPIAAAAAAAAA&bo=GwWAAgAAAAADB74!&rf=photolist)


#### 初识事件
>所谓事件，就是 HTML 页面或者浏览器窗口发生的一些交互瞬间。简单来说用户操作页面，页面返回一个反应，这就叫做事件
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>事件的概念</title>
</head>
<body>
<button id="btn">按钮</button>
<script>
    // 用户点击按钮时，给出对应提示
    // 1. 定位到HTML页面中的按钮
    var btn = document.getElementById('btn');// HTMLButtonElement
    // 2. 为这个按钮绑定(注册)事件
    btn.onclick = function(){// 事件属性
        // 事件的处理函数

        // 3. 提供事件触发后的处理逻辑
        alert('你终于点中了我...');
    }

</script>
</body>
</html>
```
![事件的执行流程图](http://a4.qpic.cn/psb?/V118JuTr0BKcy7/a.FJxcvgmVtLX1QibZhSboSHlRC5Vn.H8Ez36ckagWU!/m/dPMAAAAAAAAA&bo=GwWAAgAAAAADB74!&rf=photolist)   
#### Document对象  
>Document 对象表示浏览器加载的 HTML 页面，并作为查找 HTML 页面内容的入口。它提供了全局函数，例如如何从 HTML 页面中查找指定标签或者在 HTML 页面中如何创建标签等。
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document对象</title>
</head>
<body>
<a href="#">链接</a>
<script>
    // document对象是DOM提供，作为解析的入口
    console.log(document);
    /*
        document对象提供了属性和方法
        * document对象 -> 提供给我们可以直接使用的对象
        * document对象应该是Document类型的 - Document是一个构造函数
        * Document是构造函数 -> 具有原型prototype属性
          * DOM底层代码并不是JavaScript -> 被封装成了JavaScript代码
          * DOM的底层代码不允许直接查看
        * document对象的属性和方法 -> 多源于Document的prototype原型上
     */
    console.log(typeof document);// object
    console.log(document instanceof Document);
    console.log(Document);
    console.log(Document.prototype);
</script>
</body>
</html>
```
- DOM的Document对象的属性和方法
    - 不需要去了解为什么可以实现这样的效果
    - Document对象具有哪些属性和方法
    - Document对象的属性和方法如何使用
    - Document对象的属性和方法使用时，需要注意哪些问题
1.  Document查询   
> 获取 HTML 标签就是查找 HTML 页面中的元素节点，也可以称为 DOM 查询。基本有6种方式可以使用。 
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>DOM查询</title>
    <style>
        .myclass {
            color: lightcoral;
        }
    </style>
</head>
<body>
<p id="p1">这是一个段落测试内容.</p>
<p name="p2">这是一个段落测试内容.</p>
<p name="p2">这是一个段落测试内容.</p>
<p name="p2">这是一个段落测试内容.</p>
<p class="myclass">这是一个段落测试内容.</p>
<p class="myclass">这是一个段落测试内容.</p>
<p class="myclass">这是一个段落测试内容.</p>
<script>
    // 1.通过id属性值定位HTML页面的元素
    var p1 = document.getElementById('p1');
    /*
        定位的内容 -> 打印的是HTML的源代码
        * 得到的真正的内容是 -> HTML对应元素的DOM对象
     */
    console.log(p1);
    console.log(typeof p1);
    /*
        2. 通过name属性值定位HTML页面的元素
           * name属性值允许重复，得到的元素可能是多个
           * 返回值是一个数组 -> 用于存储多个元素
      */
    var p2 = document.getElementsByName('p2');
    console.log(p2);
    /*
        3. 通过元素的名称定位HTML页面的元素
           * 返回值是一个数组 -> 用于存储多个元素
     */
    var pElements = document.getElementsByTagName('p');
    console.log(pElements.length);// 4
    /*
        4. 通过class属性值定位HTML页面的元素
           * 返回值是一个数组 -> 用于存储多个元素
           * 浏览器兼容问题
             * IE 8及之前版本不支持该方法
     */
    var pclass = document.getElementsByClassName('myclass');
    console.log(pclass.length);
    // 自定义getElementsByClassName()函数
    function getElementsByClassName(){

    }
    /*
        5.通过CSS选择器方式获取
          在HTML5新特性中提供了两个可以通过CSS选择器方式来获取HTML页面标签的方法:
            *querySelector(selector): 返回第一个选择器匹配的HTML页面元素。
            *querySelectorAll(selector): 返回全部选择器匹配的HTML页面元素。
          注意：这两个方法只能是IE8版本之后才执行。 
/*var p1 = document.querySelector('#p1');
    console.log(p1);
  var p2 = document.querySelector('.myclass');
    console.log(p2);
 */ //这里只会匹配一个Html元素  

    var p1 = document.querySelectorAll('#p1');
    console.log(p1);// 就算是只有一个，也是数组的形式
    var p2 = document.querySelectorAll('.myclass');
    console.log(p2);
</script>
</body>
</html>
```
- 兼容IE8及之前版本的浏览器   
>这里我们要优先使用 W3C 规范的方法。所以，需要先判断当前浏览器环境是否存在 getElementsByClassName() 方法。如果存在，就使用原本的 getElementsByClassName() 方法。如果不存在，就使用自定义代码来实现。
```JS
function getElementsByClassName(element, names) {
    // 检测 getElementsByClassName() 是否可用
    if (element.getElementsByClassName) {
        // 优先使用 W3C 规范
        return element.getElementsByClassName(names);
    }else {
        // 人为解决 IE 8 之前版本不兼容问题
        
        // 获取所有后代元素节点
        var elements = element.getElementsByTagName('*');
        // 定义空数组
        var result = [];
        var element, classNameStr, flag;
        // 将样式名称改为数组类型
        names = names.split(' ');
        // 循环遍历所有元素节点
        for (var i=0; element = elements[i]; i++) {
        	  // 获取每个元素节点的样式名称
            classNameStr = ' ' + element.className + ' ';
            // 开启开关
            flag = true; 
            // 循环遍历所有的样式名称
            for (var j=0, name; name = names[j]; j++) {
                // 判断当前元素节点的样式名称中是否包含指定的样式名称
                if (classNameStr.indexOf(' ' + name + ' ') == -1){
                    // 如果不包含，则关闭开关，并且结束循环
                    flag = false;
                    break;
                }
            } 
            // 判断当前元素节点是否包含指定样式名称
            if (flag) {
                // 如果包含，则将当前元素节点添加到数组中
                result.push(element);
            }
        } 
        // 返回数组(所有包含指定样式名称的元素节点)
        return result;
    }
}
```
- DOM查询的对比一  
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>DOM查询对比</title>
    <style>
        .myclass {
            color: lightcoral;
        }
    </style>
</head>
<body>
<p id="p1">这是一个段落测试内容.</p>
<p name="p2">这是一个段落测试内容.</p>
<p name="p2">这是一个段落测试内容.</p>
<p name="p2">这是一个段落测试内容.</p>
<p class="myclass">这是一个段落测试内容.</p>
<p class="myclass">这是一个段落测试内容.</p>
<p class="myclass">这是一个段落测试内容.</p>
<script>
    /*
        * getElementById()方法
        * querySelector()方法
     */
    /*var start1 = new Date().getTime();
    for (var i=0;i<100000;i++){
        var p1 = document.getElementById('p1');
    }
    var end1 = new Date().getTime();
    console.log('getElementById的执行时间: '+(end1-start1));

    var start2 = new Date().getTime();
    for (var i=0;i<100000;i++){
        var p2 = document.querySelector('#p1');
    }
    var end2 = new Date().getTime();
    console.log('querySelector的执行时间: '+(end2-start2));*/

    /*
        * getElementsByClassName()方法
        * querySelectorAll()方法
     */
    var start1 = new Date().getTime();
    for (var i=0;i<100000;i++){
        var p1 = document.getElementsByClassName('myclass');
    }
    var end1 = new Date().getTime();
    console.log('getElementById的执行时间: '+(end1-start1));

    var start2 = new Date().getTime();
    for (var i=0;i<100000;i++){
        var p2 = document.querySelectorAll('.myclass');
    }
    var end2 = new Date().getTime();
    console.log('querySelector的执行时间: '+(end2-start2));

</script>
</body>
</html>
```
>结论是 - CSS选择器的方式获取所消耗的时间更长，也就是说这个方式的性能比较差

- DOM查询的对比二
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>DOM查询对比</title>
</head>
<body>
<ul id="parent">
    <li>苹果</li>
    <li>小米</li>
    <li>锤子</li>
</ul>
<script>
    /*// 1. 获取所有的<li>标签
    var lis = document.getElementsByTagName('li');
    // 在未添加任何新标签之前的输出结果
    console.log(lis.length);// 3
    // 2. 为<ul>添加一个新的<li>子标签
    var parent = document.getElementById('parent');
    var newLi = document.createElement('li');
    parent.appendChild(newLi);
    // 在添加之后输出的结果
    console.log(lis.length);// 4*/

    // 1. 获取所有的<li>标签
    var lis = document.querySelectorAll('li');
    // 在未添加任何新标签之前的输出结果
    console.log(lis.length);// 3
    // 2. 为<ul>添加一个新的<li>子标签
    var parent = document.getElementById('parent');
    var newLi = document.createElement('li');
    parent.appendChild(newLi);
    // 在添加之后输出的结果
    console.log(lis.length);// 3

</script>
</body>
</html>
```
>结论 - CSS选择器得到的结果与Html页面无关

![DOM查询的对比图](http://a4.qpic.cn/psb?/V118JuTr0BKcy7/Muo*13E2pvYQrPSdwLX0aF997698yxO2jac0ABvpdCQ!/m/dPMAAAAAAAAA&bo=GwWAAgAAAAADB74!&rf=photolist)   

2. NodeList对象  
>NodeList 是一组元素节点的集合，每个节点都有索引值（从 0 开始的数字，类似数组）。元素节点在 NodeList 中保存的顺序和它们在 HTML 页面中出现的顺序一致
- 动态 NodeList  
    - 在动态 NodeList 中，当脚本更新 HTML 页面之后，NodeList 也会同样进行更新。
- 静态 NodeList 
    - 当脚本更新 HTML 页面之后，NodeList 不会进行更新
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>NodeList对象</title>
    <style>
        .myclass {
            color: lightcoral;
        }
    </style>
</head>
<body>
<p class="myclass">这是一个段落测试内容.</p>
<p class="myclass">这是一个段落测试内容.</p>
<p class="myclass">这是一个段落测试内容.</p>
<script>
    // NodeList
    /*var nodeList = document.querySelectorAll('.myclass');
    console.log(nodeList);

    console.log(typeof nodeList);// object
    console.log(nodeList instanceof Object);// true
    console.log(nodeList instanceof Array);// false
    console.log(nodeList instanceof NodeList);// true

    // 数组
    var arr = new Array(1,2,3,4,5);
    console.log(arr);*/

    var htmlCollection = document.getElementsByClassName('myclass');
    console.log(htmlCollection);

    console.log(htmlCollection instanceof Object);// true
    console.log(htmlCollection instanceof HTMLCollection);// true

    console.log(HTMLCollection);
    console.log(HTMLCollection.prototype);

    console.log(HTMLCollection instanceof NodeList);// false
    console.log(HTMLCollection.prototype instanceof NodeList);// false

</script>
</body>
</html>
```
 
3. 缓存DOM查询
- 当我们通过 DOM 查询获取 HTML 页面中指定的标签后，如果需要多次操作同一个标签时，应该使用一个变量来保存 DOM 查询的结果。 
- 当把 DOM 查询的结果保存在一个变量后，实际上是把获取的指定标签在 DOM 节点树中的位置保存在变量中。这个元素节点（标签）的属性和方法可以通过这个变量来使用。    
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>缓存DOM查询</title>
</head>
<body>
<p id="p1">这是一个段落内容.</p>
<script>
    var p1 = document.getElementById('p1');
    console.log(p1);

    console.log(document.getElementById('p1'));
</script>
</body>
</html>
```
![缓存查询](http://a4.qpic.cn/psb?/V118JuTr0BKcy7/27rbjFMsc49RtUyuDQlGxqXu66CCMmybHTIoZS*7V08!/m/dPMAAAAAAAAA&bo=GwWAAgAAAAADB74!&rf=photolist) 
    
4. Document对象的属性查询  
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document对象的属性</title>
</head>
<body>
<form action="#"></form>
<script>
    // documentElement属性 -> 获取当前HTML页面的根标签(<html>)
    console.log(document.documentElement);
    // head属性 -> 获取当前HTML页面的<head>标签
    console.log(document.head);
    // body属性 -> 获取当前HTML页面的<body>标签
    console.log(document.body);
    // forms属性 -> 获取当前HTML页面的所有表单元素
    console.log(document.forms);
    // images属性 -> 获取当前HTML页面的所有图片元素
    console.log(document.images);

</script>
</body>
</html>
```
#### 脚本代码的位置   
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>脚本代码的位置</title>
    <script>
        /*
            在<body>之前获取页面元素时 -> 获取失败
            * 结果 - 1.null；2.可能直接报错
            * 原因 - 先加载代码，后加载HTML元素

            window.onload = function(){}
            * window对象 -> 是浏览器环境中的全局(顶级)对象，是BOM提供的
              * 译为浏览器窗口
            * load事件 -> 表示加载完毕时，触发当前事件
            * window.onload - window对象绑定load事件
              * 表示当前浏览器窗口加载HTML页面完毕时，执行指定的代码
         */
        window.onload = function(){
            var p1 = document.getElementById('p1');
            console.log(p1);
        }
    </script>
</head>
<body>
<p id="p1">这是一段段落内容.</p>
<!--<script>
    var p1 = document.getElementById('p1');
    console.log(p1);
</script>-->
</body>
</html>
```
#### 创建节点  
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>创建节点</title>
</head>
<body>
<ul id="parent">
    <li>苹果</li>
    <li>西瓜</li>
    <li>香蕉</li>
</ul>
<script>
    // 向<ul>标签下添加一个新的<li>子标签 - <li id="mg">木瓜</li>
    // 1. 创建元素节点 -> 空标签(没有属性和文本内容)
    var newLi = document.createElement('li');
    console.log(newLi);
    // 2. 创建文本节点
    var textNode = document.createTextNode('木瓜');
    console.log(textNode);
    // 将文本节点作为子节点添加到元素节点上 - parentNode.appendChild(childNode)
    newLi.appendChild(textNode);
    console.log(newLi);
    /*
        3. 创建属性节点
           a. createAttribute(attrName)方法 - 表示创建属性节点
           * attrName参数 - 表示属性的名称
           b. attrNode.nodeValue = value; - 为属性节点设置对应的值
           注意 - 属性节点不是父级节点，也不是子级节点
           c. setAttributeNode(attr)方法 - 元素节点设置属性节点
      */
    var attrNode = document.createAttribute('id');
    attrNode.nodeValue = 'mg';
    console.log(attrNode);
    // 元素节点设置属性节点
    newLi.setAttributeNode(attrNode);
    console.log(newLi);

    var ul = document.getElementById('parent');
    ul.appendChild(newLi);
</script>
</body>
</html>
```
![创建节点的流程图](http://a4.qpic.cn/psb?/V118JuTr0BKcy7/Rzt*kC.W0TH9whNYecZdCIpoTAAciPJzkdvPWXShEB0!/m/dPMAAAAAAAAA&bo=GwWAAgAAAAADB74!&rf=photolist)
