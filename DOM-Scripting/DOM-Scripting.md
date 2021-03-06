### 第一章 JavaScript简史

> Web标准：

1. HTML：超文本标记语言；
2. CSS：层叠样式表，给文档增加样式；
3. DOM：文档对象模型，给文档增加交互能力。

> JavaScript的起源

1. `JavaScript`(Netscape公司，Sun公司) --与ECMA(欧洲计算机制造商协会)一起对其进行标准化--> `ECMAScript`；
2. JavaScript与Java没有任何联系，是一种脚本语言，一般只能在浏览器环境中运行，当然现在有了Node.js；
3. BOM：浏览器对象模型，设置浏览器属性的方法。

> DOM

1. `DOM`是一套对文档的内容进行抽象和概念化的方法；
2. DOM Level 0。

> 浏览器之争

1. DHTML(Dynamic HTML)：一种描述HTML、CSS和JavaScript技术组合的术语；
2. DHTML的含义：(1) 利用HTML把网页标记为各种元素，(2) 利用CSS设置元素样式和它们的显示位置，(3) 利用JavaScript实时地操控页面和改变样式；
3. NetScape与微软使用两种不兼容的DOM，导致要写两份不同脚本，但是目标却是一样的。

> 制定标准

1. W3C推出一个标准化的DOM：一个与系统平台和编程语言无关的接口，程序和脚本可通过该接口动态的访问和修改文档的内容、结构和样式；
2. 现在的各大浏览器都内置了对标准DOM的支持，可以实现“编写一次，随处运行”。

### 第二章 JavaScript语法
> JavaScript

1. 程序设计语言分为解释型和编译型两大类；
2. JavaScript是一种解释型程序语言，一般通过Web浏览器就负责完成相关的解释和执行。
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <title>Just a test</title>
</head>
<body>

    <!-- 这是HTML中的注释 -->
    <!-- <script>标签最好是放到HTML文档的最后，</body>标签之前 -->
    <!-- 因为js文件的加载和执行会阻塞文档的加载和渲染 -->
    <!-- 执行JavaScript代码的方式：
        (1) 直接将JavaScript代码放在<script>标签之间；
        (2) 将JavaScript代码组织为一个独立文件
    -->
    <script type="text/javascript">
        // JavaScript代码
    </script>
    <script type="text/javascript" src="example.js"></script>
</body>
</html>

```

> 语法：语言结构方面的各项规则称之为语法。

> 语句：即指令。

```
first statement;
second statement;
```
> 注释：脚本中仅供自己参考或提醒自己的信息，解释器会忽略这些信息。

```
// 注释
/* 注释 */
```
> 变量(variable)：变量的名字区分大小写，不允许变量名中包含空格或标点符号(美元符号 "$"例外)，可使用字母、数字、美元符号和下划线。

```
// JavaScript允许直接对变量赋值而无需事先声明，如下所示。
mood = "happy";
age = 33;
// 如何声明变量：
var mood;
var age;
var mood, age;
// 声明，赋值
var mood = "happy";
var age = 33;
```

> 命名方式——驼峰格式(camel case)：是函数名、方法名和对象属性名的首选格式。

```
var camelCase;
```
> 数据类型：JavaScript不需要进行类型声明，是一种弱类型(weakly typed)语言，程序员可在任何阶段改变变量的数据类型。

```
// 1. 字符串：由零个或多个字符构成，必须包在引号里，单引号或双引号都可以。不管单引号还是双引号，在同一脚本中最好保持一致
var mood = 'happy';
var mood = "happy";
var mood = "don't ask"; // 字符串中包含单引号
var mood = 'don\'t ask'; // 也可对单引号进行转义，用反斜杠

// 2. 数字：无需限定它必须是一个整数，可以是浮点数(任意位)
var age = 33.25;
var temperature = -20;
var temp = -20.3333;

// 3. 布尔值：true 或 false
```

>  数组：是指一个变量表示一个值的组合
```
var beatles = Array(4); // 声明长度
var beatles = Array(); // 不声明长度
var beatles = [];
var beatles = Array("John", "Paul", "George", "Ringo");
var beatles = ["John", "Paul", "George", "Ringo"];
var lennon = ["John", 1940, false]; // 3中数据类型混在一起存入一个数组
```

> 关联数组，在JavaScript中，所有的变量实际上都是某种类型的对象。一个数组就是一个Array类型的对象。

```
// 所以，以下实际是给lennon数组添加了三个属性，理想情况下，不应该修改Array对象的属性，而应该使用通用的对象(Object)
var lennon = Array();
lennon["name"] = "John";
lennon["year"] = 1940;
lennon["living"] = false;
```

> 对象：与数组类似，对象也是使用一个名字表示一组值，对象的每个值都是对象的一个属性。

```
var lennon = Object();
lennon["name"] = "John";
lennon["year"] = 1940;
lennon["living"] = false;

// 创建对象也可使用花括号法
{propertyName: value, propertyName: value}
```
> 操作(operation)

```
// 1. 算术操作符，加减乘除(+, -, *, /)，赋值(=)
// 赋值运算并非总是返回真值：
if (a = false) {
    alert('hello, world');
}
```
> 条件语句：用做判断。

```
if (condition) { // 条件求值的结果永远是一个布尔值
    statements;
}

// 2. 比较操作符，大于(>)，小于(<)，大于等于(>=)，小于等于(<=)，等于(==)，不等于(!=)，
// 相等操作符==并不表示严格相等，如下所示
var a = false;
var b = ""; // 在JS中，空字符串表示假值
if (a == b) { // 这里会返回true
    alert("a eqauls b");
}
// 我们需要使用严格相等(===)，这不仅会比较值，而且会比较变量的类型，除了严格相等，还有严格不相等(!==)
var a = false;
var b = ""; // 在JS中，空字符串表示假值
if (a === b) { // 这里会返回false
    alert("a eqauls b");
}
// 3. 逻辑操作符， 与(&&)，或(||)，非(!)
```

> 循环语句：重复性的操作

```
// 1. while 循环
while (condition) {
    statements; // while循环内部必须发生一些会影响循环控制条件的事情
}
// 下面这种形式的while循环，循环语句内部的代码至少执行一次
do {
    statements;
} while (condition);
// 2.for 循环，循环控制结构更加清晰，与循环有关的所有内容都包含在for语句的圆括号内
for (initital condition; test condition; alter condition) {
    statements;
}
```

> 函数：就是一组允许在你的代码里随时调用的语句。

```
// 作为良好的编程习惯，应该事先对函数做出定义再调用它们
function shout() {
    var beatles = Array("John", "Paul", "George", "Ringo");
    for (var count = 0; count < beatles.length; count++) {
        alert(beatles[count]);
    }
}
// 还可向函数传递数据，即参数(argument)，函数名可使用驼峰法
function name(arguments) {
    statements;
}
```

> 变量的作用域

```
// 1. 全局变量：可以在脚本中的任何位置被引用，包括函数内部
// 2. 局部变量：只存在于声明它的那个函数的内部
```

> 对象：是一种非常重要的数据类型，是自包含的数据集合，包含在对象里的数据可以通过两种形式方位——属性和方法。
> 属性：是隶属于某个特定对象的变量；
> 方法是只有某个特定对象才能调用的函数。

```
// 1. 用户定义对象
// 2. 内建对象，例如Array对象，Math对象和Date对象等。
// 3. 宿主对象，除了内建对象，还可在JavaScript脚本里使用已经预先定义好的其他对象，这些对象不是有JavaScript语言本身二十由它的运行环境提供。
// 宿主对象包括Form(表单)、Image(图像)和Element(表单元素)等
```

### 第三章 DOM
> document(文档)：DOM中的“D”，当创建了一个网页并把它加载到Web浏览器中时，DOM就产生了，它将你编写的网页文档转换为一个文档对象。

> 对象：DOM总的“O”，

```
// 1. 用户定义对象(user-defined object)：由程序员自行创建的对象；
// 2. 内建对象(native object)：内建在JavaScript语言里的对象，如Array、Math和Date等；
// 3. 宿主对象(host object)：由浏览器提供的对象，如window对象，document对象。
// window对象对应着浏览器窗口本身，这个对象的属性和方法通常统称为BOM(浏览器对象模型)；
// document对象主要功能就是处理网页内容。
```

> 模型：DOM中的“M”，“Model”(模型)。

```
<!-- DOM把一份文档表示为一棵树(家谱树)，节点树 -->
<!-- 示例：购物清单 -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <title>Shopping list</title>
</head>
<body>
    <h1>What to buy</h1>
    <p title="a gengle reminder">Don't forget to buy this stuff.</p>
    <ul id="purchases">
        <li>A tin of beans</li>
        <li class="sale">Cheese</li>
        <li class="sale important">Milk</li>
    </ul>
</body>
</html>
<!-- <html>标签就是根元素，它代表整个文档。 -->
```

> 节点(node)：文档是由节点构成的集合，在DOM里有许多不同类型的节点。

1. 元素节点(element node)：即HTMl标签，例如`<body>`、`<p>`和`<ul>`之类的标签，这些元素节点在文档中的布局形成了文档的结构；
2. 文本节点(text node)：在示例“购物清单”里，`<p>`元素包含着文本“Don't forget to buy this stuff.”，文本节点总是被包含在元素节点里面；
3. 属性节点(attribute node)：用于对元素做出更具体的描述。

```
<p title="a gentle remider">Don't forget to buy this stuff.<p>
// 在DOM中，title="a gentle reminder"是一个属性节点
```

> CSS：告诉浏览器应该如何显示一份文档的内容，节点树上的各个元素将继承其父元素的样式属性。

```
selector {
    property: value;
}

p {
    color: yellow;
    font-family: "arial", sans-serif;
    font-size: 1.2em;
}
```

> class属性：可在所有的元素上任意应用class属性。

```
<p class="special">This paragraph has the special class</p>
<h2 class="special">So does this headline</h2>

.special {
    font-style: italic;
}
h2.special {
    text-transform: upppercase;
}
```

> id属性：是给网页中的某个元素加上一个唯一的标识符。

```
<ul id="purchases">

#purchases {
    border: 1px solid white;
    background-color: #333;
    color: #ccc;
    padding: 1rem;
}

#purchases li {
    font-weight: bold;
}
```

> 获取元素：有3种DOM方法可获取元素节点，分别是通过元素ID、通过标签名和通过class名字来获取。

```
// 1. getElementById：将返回一个与那个有着给定id属性值的元素节点对象的对象，它是document对象特有的函数
document.getElementById(id);
document.getElementById("purchases");

// 2. getElementsByTagName：返回一个对象数组，每个对象分别对应着文档里有着给定标签的一个元素
element.getElementsByTagName(tag);
document.getElementsByTagName("li");
var shopping = document.getElementById("purchases");
var items = shopping.getElementsByTagName("*");

// 3. getElementsByClassName：可通过class属性中的类名来访问元素，返回也是一个数组
getElementsByClassName(class);
document.getElementsByClassName("sale");
// 使用这个方法还可以查找那些带有多个类名的元素，在参数中，类名的示例顺序不重要，就算元素还带有更多类名也没有关系
document.getElementsByClassName("important sale");
        // getElementsByClassName方法可能在比较老的浏览器中并不支持，下面的函数可支持新老浏览器
        function getElementsByClassName(node, classname) {
            if (node.getElementsByClassName) {
                return node.getElementsByClassName(classname);
            } else {
                var res = new Array();
                var elems = node.getElementsByTagName("*");
                for (var i = 0, len = elems.length; i < elems.length; i++) {
                    if (elems[i].classname.indexOf(classname) != -1) {
                        res[res.length] = elems[i];
                    }
                }

                return res;
            }
        }
```
**文章推荐：**[The Ultimate getElementsByClassName](http://robertnyman.com/2008/05/27/the-ultimate-getelementsbyclassname-anno-2008/)。

> 获取和设置属性

1. getAttribute：`object.getAttribute(attribute)`，该方法只能通过元素节点对象调用；
2. setAttribute：`object.setAttribute(attribute, value)`，该方法也只能用于元素节点。

```
// 获取每个<p>元素的title属性，无title属性返回null
var paras = document.getElementsByTagName("p");
for (var i = 0; i < paras.length; i++) {
    var title = paras[i].getAttribute("title");
    if (title) {
        alert(paras[i].getAttribute("title"));
    }
}

// 设置id为purchases的元素的title属性
var shopping = document.getElementById("purchases");
shopping.setAttribute("title", "a list of goods");
alert(shopping.getAttribute("title"));
```
> **DOM的工作模式**：先加载文档的静态内容，在动态刷新，动态刷新不影响文档的静态内容，即对页面内容进行刷新却不需要再浏览器里刷新页面。

### 第四章 案例研究：JavaScript图片库

> DOM是一种适用于多种环境和多种程序设计语言的通用性API

```
```

> Js文件合并：若一个站点用到多个JavaScript文件，为了减少对服务器的请求次数，应把这些.js文件合并到一个文件中

```
```

> 添加事件处理函数的语法：

```
// 事件处理函数：在特定事件发生时调用特定的JavaScript代码
event = "JavaScript statement(s)";
onclick = "showPic(this)"
```
> 阻止默认行为：例如点击链接默认会跳转新页面

```
// 只要时间处理函数返回false
onclick = "showPic(this); return false;"
```
> childNodes属性

```
// 在一棵节点树上，childNodes属性可以用来获取任何一个元素的所有子元素(包含所有类型的节点)，是一个包含这个元素全部子元素的数组
element.childNodes
```
> nodeType属性：节点的类型，一共有12种可取值

1. 元素节点的nodeType属性值是1；
2. 属性节点的nodeType属性值是2；
3. 文本节点的nodeType属性值是3。

```
// 节点类型
node.nodeType
```
> nodeValue属性：用来得到或设置一个节点的值

```
node.nodeValue
```
> firstChild和lastChild属性

```
node.firstChild
node.childNotes[0]
node.lastChild
node.childNotes[node.childNotes.length - 1]
```

> 本章重点：
1. 如何利用DOM所提供的方法去编写图片库脚本；
2. 如何利用事件处理函数把JavaScript代码与网页集成在一起。

### 第五章 最佳实践

> 本章内容：

1. 平稳退化：确保网页在没有JavaScript的情况下也能正常工作；
2. 分离JavaScript：把网页的结构和内容与JavaScript脚本的动作行为分开；
3. 向后兼容性：确保老版本的浏览器不会因为你的JavaScript脚本而挂掉；
4. 性能考虑：确保脚本执行的性能最优。

> 平稳退化：一个在新窗口里打开一个链接的例子。

```
// JavaScript只用window对象的open()方法来创建新的浏览器窗口
window.open(url, name, features)
// url，在新窗口里打开的网页的URL地址，该参数为空时，将弹出一个空白的浏览器窗口
// name，新窗口的名字，可以在代码里通过这个名字与新窗口进行通信
// features，用于设置新窗口的各种属性，是一个以逗号分隔的字符串
function popUp(winURL) {
    window.open(winURL, "popup", "width=320,height=480");
}

// (1) 通过"javascript:"伪协议来调用popUp函数，伪协议让我们通过一个链接来调用JavaScript函数
<a href="javascript:popUp('http://www.qq.com/');">qq.com</a> 
// (2) 内嵌的事件处理函数：把onclick事件处理函数作为属性嵌入<a>标签，"#"符号是一个仅供文档内部使用的链接记号
<a href="#" onclick="popUp('http://www.qq.com/'); return false;"></a>

// (3) 将href属性设置为真实的URL地址，让它成为一个有效的链接
<a href="http://www.qq.com" onclick="popUp(this.href); return false;"></a>
// 总结：第(1)、(2)种方法不能平稳退化，第(3)种方法即使JavaScript已被禁用(或是遇到了搜索引擎)，这个链接也是可用的，虽然不会新开一个窗口
```

> 结构与样式的分离：CSS能够帮助你将Web文档的内容结构(标记)和版面设计(样式)分离开来，这样可以却表网页都能平稳退化

```
<!-- 内联方式 -->
<p style="font-weight: bold; color: red;“>
Be careful!
</p>

<!-- 推荐方式 -->
<p class="warning">
Be careful!
</p>
// 样式
.warning {
    font-weight: bold;
    color: red;
}
```

> 渐进增强：就是用一些额外的信息层去包裹原始数据
> 分离JavaScript：前面将JavaScript函数存入外部文件，貌似已经实现分离，但是问题出现在内嵌的事件处理函数中，类似使用style属性，在HTML文档中使用诸如onclick之类的属性也是一种没有效率又容易引发问题的做法。

```
// 若我们用一个”挂钩“，就像CSS机制中的class或id属性那样，把JavaScript代码调用行为与HTML文档的结构和内容分离开，网页就健壮得多
<a href="http://www.qq.com/" class="popup">qq</a>
element.event = action...
// 上面的关键是怎样才能把应该获得这个事件的元素确定下来？
// 我们可以利用class或id属性
// (1) 用getElementById，添加事件到某个带有特定id属性的元素上
getElementById(id).event = action
// (2) 用getElementsByTagName 和 getAttribute把事件添加到有着特定属性的一组元素上
var links = document.getElementsByTagName("a");
for (var i = 0; i < links.length; i++) {
    if (links[i].getAttribute("class") == "popup") {
        links[i].onclick = function() {
            popUp(this.getAttribute("href"));
            return false;
        }
    }
}

// 为了保证getElementsByTagName正常工作，必须让上述代码在HTML文档全部加载到浏览器之后马上执行
window.onload = prepareLinks;
function prepareLinks() {
    var links = document.getElementsByTagName("a");
    for (var i = 0; i < links.length; i++) {
        if (links[i].getAttribute("class") == "popup") {
            links[i].onclick = function() {
                popUp(this.getAttribute("href"));
                return false;
            }
        }
    }
}

function popUp(winURL) {
    window.open(winURL, "popup", "width=320,height=480");
}
```

> 向后兼容：不同的浏览器(老版本的浏览器)并不一定支持DOM提供的方法和属性，对JavaScript的支持程度也不一样

```
// 解决方案：
// (1) 对象检测
if (method) {
    statements
}

// (2) 浏览器嗅探技术(browser sniffing)：通过提取浏览器供应商提供的信息来解决向后兼容问题
// 存在问题：1.浏览器提供的信息并不准确；2.为了适配各种不同的浏览器，嗅探脚本会越发复杂；3.当浏览器出新版本时，可能需要修改相关脚本
```

> **性能考虑**

```
// (1) 尽量少访问DOM和尽量少较少标记
// (2) 合并及放置脚本于合适位置：一般来说，根据HTTP规范，浏览器每次从同一域名中最多只能同时下载两个文件
// (3) 压缩脚本：将脚本文件中不必要的字节，如空格和注释，统统删除，还有使用更短的变量名，所以你的脚本应该有两个版本，一个是工作副本，可以修改代码并添加注释；另一个是精简副本，用于放在站点上
// 为了区分两个版本，会在精简副本的文件名中加上min字样
<script src="scripts/scriptName.min.js"></script>

```

### 第六章 案例研究：图片库改进版

> 与DOM脚本编程相关的问题不外乎以下几类：

- 平稳退化
- 向后兼容
- 分离JavaScript

> 它支持平稳退化吗？

```
<!-- 代码如下：即使JavaScript功能已被禁用，用户也可以浏览器图片库里的所有图片，网页里的所有连接也都可以正常工作 -->
<li>
    <a href="images/HTML5.png" onclick="showPic(this); return false;" title="HTML5">HTML5</a>
</li>
```

> 它的JavaScript与HTML标记是分离的吗？

```
<!-- 代码如下：两者是没有分离的 -->
<li>
    <a href="images/HTML5.png" onclick="showPic(this); return false;" title="HTML5">HTML5</a>
</li>

<!-- 修改代码如下： 给列表增加一个id属性-->
<ul id="imagegallery">
    <li>
        <a href="images/HTML5.png" title="HTML5">HTML5</a>
    </li>
    <li>
        <a href="images/angular.png" title="angular">angular</a>
    </li>
    <li>
        <a href="images/react.png" title="react">react</a>
    </li>
    <li>
        <a href="images/Firebase.png" title="Firebase">Firebase</a>
    </li>
</ul>

// 添加事件处理函数
function prepareGallery() {
    // 检查点
    if (!document.getElementsByTagName) {
        return false;
    }
    if (!document.getElementById) {
        return false;
    }
    if (!document.getElementById("imagegallery")) {  // 预防性措施，万一以后发生变化导致代码运行错误
        return false;
    }
    // 将列表元素存在一个变量中 
    var gallery = document.getElementById("imagegallery");
    var links = gallery.getElementsByTagName("a");
    for (var i = 0; i < links.length; i++) {
        links[i].onclick = function() {
            showPic(this);
            return false;        
        }
    }
}

// 共享onload事件，在网页加载完毕后立即执行该函数，
// 由于网页加载完毕时会触发一个onload事件，这个事件与window对象相关联,
// 所以，必须将prepareGallery函数绑定到该事件上
window.onload = prepareGallery;

// 问题：如果我们有两个函数需要绑定到onload事件上
// (1) 逐一绑定到onload事件上，那么最后那个才会被实际执行
window.onload = firstFunction;
window.onload = secondFunction;
// (2) 利用匿名函数
window.onload = function() {
    firstFunction();
    secondFunction();
}
// (3) addLoadEvent ，http://simon.incutio.com
function addLoadEvent(func) {
    var oldonload = window.onload;
    if (typeof window.onload != 'function') {
        window.onload = func;   
    } else {
        window.onload = function() {
            oldonload();
            func();
        }
    }
}
```
> 不要做太多的架设

```
// 以下代码：未对某些元素是否存在做任何检查
function showPic(whichpic) {
    var src = whichpic.getAttribute("href");
    var placeholder = document.getElementById("placeholder");
    placeholder.setAttribute("src", src);
    var text = whichpic.getAttribute("title");
    var description = document.getElementById("description");
    description.firstChild.nodeValue = text;
}
// 修改如下：
function showPic(whichpic) {
    if (!document.getElementById("placeholder")) {
        return false;
    }
    var src = whichpic.getAttribute("href");
    var placeholder = document.getElementById("placeholder");
    placeholder.setAttribute("src", src);
    if (document.getElementById("description")) {
        var text = whichpic.getAttribute("title");
        var description = document.getElementById("description");
        description.firstChild.nodeValue = text;
    }
    return true;  // 为什么要增加这句？
}
// 增加 return true; 的原因：让showPic函数的返回值决定是否要禁止点击链接的默认行为，当placeholder元素不存在时，可以使用链接的默认行为
links[i].onclick = function() {
    return !showPic(this);
}
```

> 优化：增加更多的检查，showPic函数里的代码变得更多了，在实际工作中，你要自己决定是否真的需要这些检查。他们针对的是HTML文档有可能不在你控制范围内的情况。

```
function showPic(whichpic) {
    if (!document.getElementById("placeholder")) {
        return false;
    }
    var src = whichpic.getAttribute("href");
    var placeholder = document.getElementById("placeholder");
    if (placeholder.nodeName != "IMG") {
        return false;
    }
    placeholder.setAttribute("src", src);
    if (document.getElementById("description")) {
        var text = whichpic.getAttribute("title") ? whichpic.getAttribute("title") : "";
        var description = document.getElementById("description");
        if (description.firstChild.nodeType == 3) {
            description.firstChild.nodeValue = text;
        }
    }
```
> 键盘访问

```
link[i].onclick = function() {
    if (showPic(this)) {
        return false;
    } else {
        return true;
    }
}
links[i].onkeypress = links[i].onclick; // 专门处理键盘事件，但其实onclick事件对键盘访问的支持相当完美
```

> DOM Core

- getElementById
- getElementsByTagName
- getAttribute
- setAttribute

上述这些都是DOM Core的组成部分，它们并不专属于JavaScript，支持DOM的任何一种程序语言都可以使用它们。它们的用途也并非仅限于处理网页，它们可以用来处理用任何一种标记语言(比如XML)编写出来的文档

>  HTML-DOM：只能处理Web文档，元素的属性属于HTML-DOM，比如`onclick`

```
document.getElementsByTagName("from")  // DOM-Core
document.forms // HTML-DOM

element.getAttribute("src")
element.src
```

> 本章改进点：

- 尽量让JavaScript代码不再依赖于那些没有保证的架设，为此引入了许多项测试和检查——**平稳退化**
- 没有使用onkeypress事件处理函数——**可访问性**
- JavaScript代码与文档分离——**结构与行为分离**

### 第七章 动态创建标记

> 本章内容

- 传统技术：`document.write`和`innerHTML`
- 深入剖析DOM方法：`createElement`、`createTextNode`、`appendChild`和`insertBefore`

> document.write：document对象的write()方法可以方便快捷地把字符串插入到文档里

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <title>Test</title>
</head>
<body>
    <script>
        document.write("<p>This is inserted.</p>");
    </script>
</body>
</html>

// document.write的最大缺点是违背了“行为与表现分离”的原则，
// 即使把document.write语句挪到外部函数里，还是需要在标记的
// <body>部分使用<script>标签才能调用那个函数
function insertParagraph(text) {
    var str = "<p>";
    str += text;
    str += "</p>";
    document.write(str);
}

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <title>Test1</title>
</head>
<body>
    <script src="test1.js" />
    <script>
        insertParagraph("This is inserted.");
    </script>
</body>
</html>
```

> innerHTML属性：目前的浏览器几乎都支持该属性，它并不是W3C DOM标准的组成部分，但现已经包含到HTML5规范中。**用于读或写某给定元素里的HTML内容**

```
// 请把一下代码插入到test.html文档的<body>部分
<div id="testdiv">
    <p>This is <em>my</em> content.</p>
</div>

// 一旦使用了innerHTML属性，它的全部内容都将被替换 
window.onload = function() {
    var testdiv = document.getElementById("testdiv");
    testdiv.innerHTML = "<p>This is <em>my</em> content.</p>";
}
```
> DOM方法

```
<div id="testdiv">
</div>
// 功能：把一段文本插入testdiv元素
// createElement方法
var para = document.createElement("p"); // 文档碎片  不是任何一棵DOM节点树的组成部分
// appendChild方法
var testdiv = document.getElementById("testdiv");
testdiv.appendChild(para);
// createTextNode方法   创建文本节点
var text = document.createTextNode("Hello world");
para.appendChild(text);

// 插入更复杂的组合：<p>This is <em>my</em> content.</p>
window.onload = function() {
    var para = document.createElement("p");
    var txt1 = document.createTextNode("This is ");
    para.appendChild(txt1);
    var emphasis = document.createElement("em");
    var txt2 = document.createTextNode(my);
    emphasis.append(txt2);
    para.appendChild(emphasis);
    var txt3 = document.createTextNode(" content.");
    para.appendChild(txt3);
    var testdiv = document.getElementById("testdiv");
    testdiv.appendChild(para);
}
```

> 重回图片库：还存在问题是在HTML文件中"placeholder"标记和"description"标记仅是为showPic脚本服务的，这导致结构和行为没有彻底分开。

```
// 动态创建
function preparePlaceholder() {
    if (!document.createElement) {
        return false;
    }
    if (!document.createTextNode) {
        return false;
    }
    if (!document.getElementById) {
        return false;
    }
    if (!document.getElementById("imagegallery")) {
        return false;
    }
    var placeholder = document.createElement("img");
    placeholder.setAttribute("id", "placeholder");
    placeholder.setAttribute("src", "images/placeholder.gif");
    placeholder.setAttribute("alt", "my image gallery");
    var description = document.createElement("p");
    description.setAttribute("id", "description");
    var desctext = document.createTextNode("Choose an image.");
    description.appendChild(desctext);
    // (1) 直接用body元素添加元素，那么该元素会是文档中的最后一个元素，这种方式不灵活
    // document.getElementsByTagName("body")[0].appendChild(placeholder);
    // document.getElementsByTagName("body")[0].appdneChild(description);
    // or HTML-DOM提供的属性body
    // document.body.appendChild(placeholder);
    // document.body.appendChild(description);
    // (2) 在已有元素前插入一个新元素，DOM提供了insertBefore()方法
    // parentElement.insertBefore(newElement, targetElement);
    // var gallery = document.getElementById("imagegallery");
    // gallery.parentNode.insertBefore(placeholder, gallery);
    // gallery.parentNode.insertBefore(description, gallery);
    // (3) 在现有元素后插入一个新元素，DOM未提供相应方法，需要自己实现
    var gallery = document.getElementById("imagegallery");
    insertAfter(placeholder, gallery);
    insertAfter(description, placeholder);
}

// 在现有元素后插入一个新元素
function insertAfter(newElement, targetElement) {
    var parent = targetElement.parentNode;
    if (parent.lastChild == targetElement) {
        parent.appendChild(newElement);
    } else {
        // 将新元素插入到目标元素和目标元素的下一个兄弟元素之间
        parent.insertBefore(newElement, targetElement.nextSibling);
    }
}
```

> Ajax：用于概括异步加载页面内容的技术。

```
// Ajax之前，Web应用都要涉及大量的页面刷新：用户点击了某个链接，
// 请求发送回服务器，然后服务器根据用户的操作再返回新页面。
// 使用Ajax就可以做到只更新页面中的一小部分，而不必在此加载整个页面
function getHTTPObject() {
    if (typeof XMLHttpRequest == "undefined") {
        try {
            return new ActiveObject("Msxml2.XMLHTTP.6.0");
        } catch(e) {
        }
        try {
            return new ActiveObject("Msxml2.XMLHTTP.3.0");
        } catch(e) {
        }
        try {
            return new ActiveObject("Msxml2.XMLHTTP");
        } catch(e) {
        }
        return false;
    }
    return new XMLHttpRequest();
}

function getNewContent() {
    var request = getHTTPObject();
    if (request) {
        request.open("GET", "example.txt", true);
        request.onreadystatechange = function() {
            if (request.readyState == 4) {
                var para = document.createElement("p");
                var txt = document.createTextNode(request.responseText);
                para.appendChild(txt);
                document.getElementById("new").appendChild(para);
            }
        }    
        request.send(null);
    } else {
        alert("Sorry, your brower doesn\'t support XMLHTTPRequest");
    }
}
```

> 渐进增强与Ajax

### 第八章 充实文档的内容
> 本章内容：

- 一个为文档创建“缩略语列表”的函数
- 一个为文档创建“文献来源链接”的函数
- 一个为文档创建“快捷键清单”的函数

> 不应该做什么：不要滥用DOM(使用DOM技术把一些重要的内容添加到网页上)

```
// 1. 渐进增强(progressive enhancement)：总是从最核心的部分，也就是从内容开始，应该根据内容使用标记实现良好的结构；然后再逐步加强这些内容
// 2. 平稳退化：渐进增强的实现必然支持平稳退化，如果你按照渐进增强的原则去充实内容，你为内容添加的样式和行为就自然支持平稳退化。
```

> 把“不可见”变为”可见“

```
// 大多数属性值在Web浏览器都是不显示的，只有极少数属性例外，例如title属性，但是不同浏览器的呈现方式并不一样，我们可以利用DOM编程来统一显示这些属性值
// 1. 得到隐藏在属性里的信息
// 2. 创建标记封装这些信息
// 3. 把这些标记插入到文档
```
> 内容

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <title>Explaining the Document Object Model</title>
</head>
<body>
    <h1>What is the Document Object Model?</h1>
    <p>
        The <abbr title="World Wide Web Consortium">W3C</abbr> defines the
        <abbr title="Document Object Model">DOM</abbr> as:
    </p>
    <blockquote cite="http://www.w3.org/DOM/">
        <p>
            A platform- and language-neutral interface that will allow programs
            and scripts to dynamically access and update the content, structure
            and style of documents.
        </p>
    </blockquote>
    <p>
        It is an <abbr title="Application Programing Interface">API</abbr> that
        can be used to navigate <abbr title="HyperText Markup Language">HTML</abbr>
        and <abbr title="eXtensible Markup Language">XML</abbr> documents.
    </p>
</body>
</html>
```

> 显示“缩略语列表”

```
<dl>
    <dt>W3C</dt>
    <dd>World Wide Web Consortium</dd>
    <dt>DOM</dt>
    <dd>Document Object Model</dd>
    <dt>API</dt>
    <dd>Application Programing Interface</dd>
    <dt>HTML</dt>
    <dd>HyperText Markup Language</dd>
    <dt>XML</dt>
    <dd>eXtensible Markup Language</dd>
</dl>

function displayAbbreviations() {
    if (!document.getElementsByTagName) {
        return false;
    }
    if (!document.createElement) {
        return false;
    }
    if (!document.createTextNode) {
        return false;
    }
    // 取得所有缩略词
    var abbreviations = document.getElementsByTagName("abbr");
    if (abbreviations.length < 1) {
        return false;
    }
    // 遍历文档中的所有abbr元素
    var defs = new Array();
    for (var i = 0; i < abbreviations.length; i++) {
        var current_abbr = abbreviations[i];
        if (current_abbr.childNodes.length < 1) {
            // 这里是为了能在IE浏览器中实现平稳退化
            // 因为IE浏览器不支持abbr元素
            continue;
        }
        var definition = current_abbr.getAttribute("title");
        var key = current_abbr.lastChild.nodeValue;
        defs[key] = definition;
    }
    // 创建定义列表
    var dlist = document.createElement("dl"); // dl元素
    for (key in defs) {
        var definition = defs[key];
        // 创建定义标题
        var dtitle = document.createElement("dt");  // dt元素
        var dtitle_text = document.createTextNode(key);
        dtitle.appendChild(dtitle_text);
        // 创建定义描述
        var ddesc = document.createElement("dd"); // dd元素
        var ddesc_text = document.createTextNode(definition);
        ddesc.appendChild(ddesc_text);
        dlist.appendChild(dtitle);
        dlist.appendChild(ddesc);
    }
    if (dlist.childNodes.length < 1) {
        return false;
    }
    // 创建标题
    var header = document.createElement("h2");
    var header_text = document.createTextNode("Abbreviations");
    header.appendChild(header_text);
    // 把标题添加到页面主体
    document.body.appendChild(header);
    // 把定义列表添加到页面主体
    document.body.appendChild(dlist);
}
```

> 显示“文献来源链接表”

```
<blockquote cite="http://www.w3.org/DOM/">
    <p>
        A platform- and language-neutral interface that will allow programs
        and scripts to dynamically access and update the content, structure
        and style of documents.
    </p>
</blockquote>

// blockquote元素包含一个属性cite，用于说明blockquote元素的内容引自哪里，
// 理论上，这是一个把文献资料与相关网页链接起来的好办法；但在实践中，浏览器
// 会完全忽略cite属性的存在
function displayCitations() {
    if (!document.getElementsByTagName || !document.createElement
        || !document.createTextNode) {
            return false;
    }
    var quotes = document.getElementsByTagName("blockquote");
    for (var i = 0; i < quotes.length; i++) {
        var quote = quotes[i];
        if (!quote.getAttribute("cite")) {
            continue;
        }
        var url = quote.getAttribute("cite");
        // 取得引用中的所有元素节点
        var quoteChildren = quote.getElementsByTagName("*");
        if (quoteChildren.length < 1) {
            continue;
        }
        // 取得引用中的最后一个元素节点
        var elem = quoteChildren[quoteChildren.length - 1];
        // 创建标记
        var link = document.createElement("a");
        var link_text = document.createTextNode("source");
        link.appendChild(link_text);
        link.setAttribute("href", url);
        var superscript = document.createElement("sup");
        superscript.appendChild(link);
        elem.appendChild(superscript);
    }
}
```

> **注意**：在编写DOM脚本时，不能想当然地认为某个节点肯定是一个元素节点，没有确切把握，就一定要去检查nodeType属性，有很多DOM方法只能用于元素节点，如果用在了文本节点上，就会出错。

```
<blockquote cite="http://www.w3.org/DOM/">
    <p>
        A platform- and language-neutral interface that will allow programs
        and scripts to dynamically access and update the content, structure
        and style of documents.
    </p>
</blockquote>

// 一般看来，blockquote元素的最后一个子节点应该是p元素，
// 但是在</p>标签和</blockquote>标签之间还存在一个换行符，
// 有些浏览器会把这个换行符解释为一个文本节点
quotes[i].lastChild;
// 我们可能希望有个lastChildElement属性就好了，但是这个属性是没有的，当然可以自己实现
```

> 显示“快捷键清单”

```
// accesskey属性可以把一个元素(如链接)与键盘上的某个特定按键关联在一起
// Windows系统中，快捷键的用法：在键盘上同时按下Alt键和特定按键
// Mac系统中，同时按下Ctrl键和特定按键
<ul id="navigation">
    <li><a href="index.html" accesskey="1">Home</a></li>
    <li><a href="search.html" accesskey="4">Search</a></li>
    <li><a href="contact.html" accesskey="9">Contact</a></li>
</ul>

function displayAccessKeys() {
    if (!document.getElementsByTagName || !document.createElement
        || !document.createTextNode) {
        return false;
    }

    var links = document.getElementsByTagName("a");
    var akeys = new Array();
    for (var i = 0; i < links.length; i++) {
        var current_link = links[i];
        if (!current_link.getAttribute("accesskey")) {
            continue;
        }
        var key = current_link.getAttribute("accesskey");
        var text = current_link.lastChild.nodeValue;
        akeys[key] = text;
    }
    var list = document.createElement("ul");
    for (key in akeys) {
        var text = akeys[key];
        var str = key + ": " + text;
        var item = document.createElement("li");
        var item_text = document.createTextNode(str);
        item.appendChild(item_text);
        list.appendChild(item);
    }

    var header = document.createElement("h3");
    var header_text = document.createTextNode("Accesskeys");
    header.appendChild(header_text);
    document.body.appendChild(header);
    document.body.appendChild(list);
}
```

> 检索和添加信息：用JavaScript函数先把文档结构里的一些现有信息提取出来，再把那些信息以一种清晰和有意义的方式重新插入到文档中。

```
// JavaScript脚本只应该用来充实文档的内容，要避免使用DOM技术来创建核心内容
```

### 第九章 CSS-DOM

> 本章内容

- style属性
- 如何检索样式
- 如何改变样式

> 三位一体的网页

- 结构层(HTML)
- 表示层(CSS)
- 行为层(JavaScript)

> 结构层：由HTML之类的标记语言负责创建，标签(tag)，对网页内容的**语义**含义做出了描述。

```
<!-- <p>标签表达了这样一种语义：这是一个文本端 -->
<p>An example of a paragraph</p>
```
> 表示层：由CSS负责完成，CSS描述页面内容应该如何呈现

```
p {
    color: grey;
    font-family: "Arial", sans-serif;
}
```

> 行为层：负责内容应该如何响应事件这一问题。这是JavaScript和DOM来控制

```
var paras = document.getElementsByTagName("p");
for (var i = 0; i < paras.length; i++) {
    paras[i].onclick = function() {
        alert("You clicked on a paragraph.");
    }
}
```
注：网页的表示层和行为层总是存在的，即使未明确地给出任何具体的指令也是如
此。此时Web浏览器将应用它的默认样式和默认事件处理函数。

> 分离

- 使用HTML去搭建文档的结构
- 使用CSS去设置文档的呈现效果
- 使用DOM脚本去实现文档的行为

但是以上三种技术之前存在一些潜在的重叠区域。

> style属性

```
// 文档的每个元素节点都有一个style属性，包含着元素的样式，style属性也是一个对象
element.style.property

<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />
    <title>Example</title>
</head>
<body>
    <p id="example" style="color: grey; font-family: 'Arial', sans-serif">
        An example of a paragraph
    </p>
    <script>
        window.onload = function() {
            var para = document.getElementById("example");
            alert(typeof para.nodeName);
            alert(typeof para.style);
        }
    </script>
</body>
</html>
```
> 获取样式

```
// style对象的color属性
element.style.color
// font-family属性，DOM采用驼峰命名法
element.style.fontFamily
```

> 内嵌(内联)样式：通过style属性获取样式有很大的局限性，它只能返回内联样式，但是内联样式不是使用CSS的好办法，它将表现信息与结构混杂在一起

```
<p id="example" style="color: grey; font-family: 'Arial', sans-serif">

p#example {
    color: grey;
    font: 12px 'Arial', sans-serif;
}
```

> 设置样式：用DOM设置的样式，就可以用DOM再把它们检索出来

```
window.onload = function() {
    var para = document.getElementById("example");
    // style对象的属性的值必须放在引号里
    para.style.color = "black";
}
```

> 何时该用DOM脚本设置样式

```
// 1. 根据元素在节点树里的位置来设置样式
/**
 * 给h1元素后面的每个元素添加一个class属性
 */
function styleHeaderSiblings() {
    if (!document.getElementsByTagName) {
        return false;
    }
    var headers = document.getElementsByTagName("h1");

    for (var i = 0; i < headers.length; i++) {
        var elem = null;
        elem = getNextElement(headers[i].nextSibling);
        if (elem) {
            elem.style.fontWeight = "bold";
            elem.style.fontSize = "1.2em";
            elem.style.color = "grey";
        }
    }
}

/**
 * 返回某节点的下个元素节点
 * @param node 某节点的下个节点
 */
function getNextElement(node) {
    // 如果是元素节点
    if (node.nodeType == 1) {
        return node;
    }

    if (node.nextSibling) {
        return getNextElement(node.nextSibling);
    }

    return null;
}

// 2. 根据某种条件反复设置某种样式
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8"/>
    <title>Cities</title>
    <link rel="stylesheet" media="screen" href="styles/format.css"/>
</head>
<body>
    <table>
        <caption>Itinerary</caption>
        <thead>
            <tr>
                <th>When</th>
                <th>Where</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <th>June 9th</th>
                <th>Portland, <abbr title="Oregon">OR</abbr></th>
            </tr>
            <tr>
                <th>June 10th</th>
                <th>Seattle, <abbr title="Washington">WA</abbr></th>
            </tr>
            <tr>
                <th>June 12th</th>
                <th>Sacramento, <abbr title="California">CA</abbr></th>
            </tr>
        </tbody>
    </table>
</body>
</html>

// 实现功能：让表格里的行更可读的常用技巧是交替改变它们的背景色
// CSS3方式
tr:nth-child(odd) {
    background-color: #ffc;
}
tr:nth-child(even) {
    background-color: #fff;
}
// DOM方式
function stripeTables() {
    if (!document.getElementsByTagName) {
        return false;
    }

    var tables = document.getElementsByTagName("table");
    var odd, rows;
    for (var i = 0; i < tables.length; i++) {
        odd = false;
        rows = tables[i].getElementsByTagName("tr");
        for (var j = 0; j < rows.length; j++) {
            if (odd) {
                rows[j].style.backgroundColor = "#ffc";
                odd = false;
            } else {
                odd = true;
            }
        }
    }
}

// 3. 响应事件
// 注：在chrome上测试没有作用
function highlightRows() {
    if (!document.getElementsByTagName) {
        return false;
    }
    var rows = document.getElementsByTagName("tr");
    for (var i = 0; i < rows.length; i++) {
        rows[i].onmouseover = function() {
            this.style.fontWeight = "bold";
            this.style.color = "grey";
        }
        rows[i].onmouseout = function() {
            this.style.fontWeight = "normal";
            this.style.color = "black";
        }
    }
}
```

> className属性：是一个可读/可写的属性，凡是元素节点都有这个属性

```
// 与其使用DOM直接改变某个元素的样式，不如通过JavaScript代码来更新这个元素的class属性，这样确保了网页的表示层和行为层分离得更加彻底
/**
 * 给元素节点追加class属性
 */
function addClass(element, value) {
    if (!element.className) {
        element.className = value;
    } else {
        var newClassName = element.className;
        newClassName += " ";
        newClassName += value;
        element.className = newClassName;
    }
}
```
> 对函数进行抽象

```
function styleElementSiblings(tag, theclass) {
    if (!document.getElementsByTagName) {
        return false;
    }
    
    var elems = document.getElementsByTagName(tag);
    var elem;
    for (var i = 0; i < elems.length; i++) {
        elem = getNextElement(elems[i].nextSibling);
        addClass(elem, theclass);   
    }
}
```

### 第十章 用JavaScript实现动画效果

> 动画基础知识：动画就是让元素的位置随着时间而不断地发生变化

```
// 1. 位置
element {
    position: absolute;
    top: 50px;
    left: 100px;
}
element.style.position = "ablolute";
element.style.left = "100px";
element.style.top = "50px";

// 2. 时间
// JavaScript函数setTimeout能够让某个函数在经过一段预定的时间之后才开始执行
setTimeout("function", interval)
variable = setTimeout("function", interval);
// 取消等待执行队列里的某个函数
clearTimeout(variable)

// 3. 时间递增量
// 真正的动画效果是一个渐变的过程，元素应该从出发点逐步地移动到目的地，而不是从出发点一下子跳跃到目的地

// 抽象：拒绝硬编码
function moveElement(elementID, final_x, final_y, interval) {
    if (!document.getElementById) {
        return false;
    }
    if (!document.getElementById(elementID)) {
        return false;
    }
    var elem = document.getElementById(elementID);
    var xpos = parseInt(elem.style.left);
    var ypos = parseInt(elem.style.top);

    if (xpos == final_x && ypos == final_y) {
        return true;
    }

    if (xpos < final_x) {
        xpos++;
    }
    if (xpos > final_x) {
        xpos--;
    }
    if (ypos < final_y) {
        ypos++;
    }
    if (ypos > final_y) {
        ypos--;
    }

    elem.style.left = xpos + "px";
    elem.style.top = xpos + "px";
    var repeat = "moveElement('" + elementID + "'," + final_x+ "," + final_y + "," + interval + ")";
    movement = setTimeout(repeat, interval);
}
```

> 实用的动画：关键在于用户能不能控制，即根据用户行为移动一个页面元素可能起到增强网页的效果

### 第十一章 HTML5
> HTML5简介

- [HTML5 开发指南](https://developer.mozilla.org/zh-CN/docs/Web/Guide/HTML/HTML5)

> 来自朋友的忠告

- [Modernizr](https://modernizr.com/)：是一个开源的JavaScript库，利用它的富特性检测功能，可以对HTML5文档进行更好的控制。

> 几个示例

```
// 1. Canvas
// 只有在基于用户操作实现交互时，使用<canvas>的优势才会显现出来
// 2. 音频和视频
// 3. 表单
```

> **视频容器**：mp4、m4v、avi、flv(Flash Video)，每个视频容器中，音频和视频轨道都使用的编解码器来编码。编解码器决定了浏览器在播放时应该如何解码音频和视频

> **编解码器**：编解码器(视频：H.264、Theora、VP8，音频：mp3、aac、ogg)的核心就是一个算法，用于压缩和存储视频，已减小原始文件的大小，同时可能也可能不会损失品质


### 第十二章 综合示例
