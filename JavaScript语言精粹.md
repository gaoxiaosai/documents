# JavaScript 语言精粹

## 第 2 章 语法

#### 空白

空白可能表现为被格式化的字符或注释的形式.

**JavaScript提供两种注释形式**

- 一种是用 /*  */包围的块注释
- 另一种是以 // 为开头的行注释

**块注释容易出错**

/*

​	var	rm_a = /a*/.match(s)	;

*/

上面的注释导致了一个语法错误.

#### 标识符

标识符: 由一个(字母\下画线\美元符)开头, 其后可选择性地加上一个或多个字母, 数字或下画线.

标识符不能使用关键字

JavaScript 不允许在对象字面量中, 或者用点运算符提取对象属性时, 使用保留字作为对象的属性名.

标识符被用于语句 \ 变量 \ 参数 \ 属性名 \ 运算符 和 标记.

#### 数字

JavaScript 只有一个数字类型. 它在内部被表示为64位的浮点数.

NaN 是一个数值, 它表示一个不能产生正常结果的运算结果.NaN不等于任何值, 包括它自己.你可以用函数 isNaN(number) 检测 NaN.

Infinity 表示所有大于 1.79769313486231570e+308 的值.

数字拥有方法. Javascript 有一个对象Math, 它包含一套作用于数字的方法.

#### 字符串

字符串字面量可以被包在一对单引号或双引号中,它可能包含 0 个或多个字符.

\ (反斜线符号) 是转义字符.

JavaScript 在被创建的时候, Unicode 是一个16 位的字符集,所以 JavaScript 中的所有字符都是16位的.

JavaScript 没有字符类型.要表示一个字符, 只需创建仅包含一个字符的字符串即可.

转义字符用来把那些正常情况下不被允许的字符插入到字符串中, 比如反斜线 , 引号和控制字符. 

字符串有一个length 属性.

字符串是不可变的.

两个包含着完全相同的字符且字符顺序也相同的字符串被认为是相同的字符串.

字符串有一些方法.

#### 语句

当 var 语句被用在函数内部时, 它定义的是这个函数的私有变量.

语句通常按照从上到下的顺序被执行.

JavaScript可以通过条件语句 (if 和 switch ), 循环语句(while ,for 和do), 强制跳转语句(break , return 和 throw) 和函数调用来改变执行序列.

代码块是包在一对花括号中的一组语句.

JavaScript 中的代码块不会创建新的作用域.

下面列出的值被当作假(false):

- false
- null
- undefined
- 空字符串''
- 数字 0 
- 数字 NaN

其他所有的值都被当作真, 包括 true , 字符串"false",以及所有的对象.

运算符优先级

| 运算符                        | 说明                 |
| ----------------------------- | -------------------- |
| .   []   (  )                 | 提取属性与调用函数   |
| delete   new  typeof  +  -  ! | 一元运算符           |
| *    /    %                   | 乘法   除法   求余   |
| +   -                         | 加法/连接       减法 |
| >=   <=    >     <            | 不等式运算符         |
| ===     !==                   | 等式运算符           |
| &&                            | 逻辑与               |
| \|\|                          | 逻辑或               |
| ? :                           | 三元运算符           |

#### 字面量

对象字面量是一种可以方便地按指定规格创建新对象的表示法.

- 属性名可以是标识符或字符串.
- 这些名字被当作字面量名而不是变量名来对待.
- 属性的值就是表达式.

数组字面量是一种可以方便地按指定规格创建新数组地表示法.

#### 函数

函数字面量定义了函数值.

- 它可以有一个可选地名字
- 可以指定一个参数列表(在调用时由传递地实际参数初始化)
- 函数的主体包括变量定义和语句.

---

## 第 3 章 对象

**简介**

JavaScript 的简单数据类型包括数字 , 字符串, 布尔值(true和false) ,null值和 undfined值.

其他所有的值都是对象.

数字, 字符串和布尔值 "貌似" 对象,因为它们拥有方法,但它们是不可变的.

JavaScript 中的对象是可变的键控集合.

对象是属性的容器, 其中每个属性都拥有名字和值. 

- 属性的名字可以是包括空字符串在内的任意字符串.
- 属性值可以是除 underfined 值之外的任何值.

JavaScript 里的对象是无类型的.

JavaScript 包含一种原型链的特性, 允许对象继承另一个对象的属性.

#### 对象字面量

对象字面量提供了一种非常方便的创建新对象值的表示法.

对象字面量: 就是包围在一对花括号中的零或多个"名/值"对.

属性名可以是包括空字串在内的任何字符串. (在对象字面量中, 如果属性名是一个合法的 JavaScript 标识符且不是保留字, 则并不强制要求用引号括住属性名)

属性的值可以是从包括另一个对象字面量在内的任意表达式中获得.

#### 检索

要检索对象里包含的值, 可以采用在` [] `后缀中括住一个字符串表达式的方式.

如果字符串表达式是一个字符串字面量,而且它是一个合法的 JavaScript 标识符且不失保留字,那么也可以用` . `表示法代替.

如果你尝试检索一个并不存在的成员属性的值,将返回 undefined.

`||`运算符可以用来填充默认值:

```javascript
var middle = stooge["middle-name"] || "(none)"
```

尝试从 undefined 的成员属性中取值将会导致 TypeError 异常

通过 && 运算发来避免错误

```javascript
flight.equipment && flight.equipment.model
```

#### 更新

对象里的值可以通过复制语句来更新.

- 如果属性名存在,属性的值会被替换.
- 如果属性名不存在, 该属性就被扩充到对象中.

#### 引用

对象通过引用来传递.它们永远不会被复制.

#### 原型

每个对象都连接到一个原型对象， 并且它可以从中继承属性。

所有通过对象字面量创建的对象都连接到 `Object.prototype`，它是 JavaScript 中的标配对象。

原型关系是一种动态的关系。如果我们添加一个新的属性到原型中，该属性会立即对所有基于该原型创建的对象可见。

#### 反射

`typeof` 操作符对确定属性的类型很有帮助。

原型链中的任何属性都会产生值。

`hasOwnProperty `方法，如果对象拥有独有的属性，它将返回 true。` hasOwnProperty `方法不会检查原型链。

#### 枚举

`for in `语句可用来遍历一个对象中的所有属性名。

属性名出现的顺序是不确定的。

如果想要确保属性以特定的顺序出现，最好的办法就是完全避免使用 `for in `语句，而是创建一个数组，在其中以正确的顺序包含属性名。

通过使用 `for` 而不是`for in`，可以得到我们想要的属性，而不用担心可能发掘出原型链中的属性，并且我们按正确的顺序取得了它们的值。

#### 删除

`delete`运算符可以用来删除对象的属性。

- 如果对象包含该属性，那么该属性就会被移除。
- 它不会触及原型链中的任何对象。

删除对象的属性可能会让来自原型链中的属性透现出来。

#### 减少全局变量污染

最小化使用全局变量的方法之一是为你的应用只创建一个唯一的全局变量。

只要把全局性的资源都纳入一个名称空间之下，你的程序与其他应用程序、组件或类库之间发生冲突的可能性就会显著降低。

使用闭包来进行信息隐藏的方式，它是另一种有效减少全局污染的方法。

---

## 第 4 章 函数

#### 简介

函数包含一组语句，它们是 JavaScript 的基础模块单元，用于代码复用、信息隐藏和组合调用。

#### 函数对象

 JavaScript 中的函数就是对象。

对象是 “名/值” 对的集合并拥有一个连到原型对象的隐藏连接。

对象字面量产生的对象连接到 Object.prototype.

函数对象连接到 Function。prototype （该原型对象本身连接到 Object.prototype)

每个函数在创建时会附加两个隐藏属性：函数的上下文和实现函数行为的代码。

每个函数对象在创建时也随配有一个 prototype 属性。它的值是一个拥有 constructor 属性且值即为该函数的对象。

因为函数是对象，所以它们可以像任何其他的值一样被使用。函数可以保存在变量、对象和数组中。函数可以被当做参数传递给其他函数，函数也可以在返回函数。而且， 因为函数是对象，所以函数可以拥有方法。

函数的与众不同之处在于它们可以被调用。

#### 函数字面量

函数对象通过函数字面量来创建：

```javascript
//创建一个名为 add 的变量，并用来把两个数字相加的函数赋值给它。
var add = function(a, b){
    return a + b;
};
```

函数字面量包括 4 个部分。

- 第 1 部分是保留字 function
- 第 2 部分是函数名，它可以被省略。（如果没有给函数命名，它被称为匿名函数。）
- 函数的第 3 个部分是包围在圆括号中的一组参数。
- 第 4 个部分是包围在花括号中的一组语句。

函数字面量可以出现在任何允许表达式出现的地方。函数也可以被定义在其他函数中。一个内部函数除了可以访问自己的参数和变量，同时它也能自由访问把它嵌套在其中的父函数的参数与变量。通过函数字面量创建的函数包含一个连到外部上下文的连接。这被称为闭包。

#### 调用

调用一个函数会暂停当前函数的执行，传递控制权和参数给新函数。

除了声明时定义的形式参数，每个函数还接收两个附加的参数：this 和 arguments。

参数 this 在面向对象编程中非常重要，它的值取决于调用的模式。

JavaScript 中一共有 4 种调用模式;

- 方法调用模式
- 函数调用模式
- 构造器调用模式
- apply 调用模式

调用运算符是跟在任何产生一个函数值的表达式之后的一对圆括号。

当实际参数的个数与形式参数的个数不匹配时不会导致运行时错误。多了会被忽略，少了缺失的值会被替换为 undefined。

对参数值不会进行类型检查。

#### 方法调用模式

当一个函数被保存为对象的一个属性时，我们称它为一个方法。当一个方法被调用时，this 被绑定到该对象。

方法可以使用this访问自己所属的对象，所以它能从对象中取值或对对象进行修改。

this 到对象的绑定发生在调用的时候。这个延迟绑定使得函数可以对 this 高度复用。通过 this 可取得它们所属对象的上下文的方法称为公共方法。

#### 函数调用模式

当一个函数并非一个对象的属性时，那么它就是被当做一个函数来调用的。

以此模式调用函数时，this被绑定到全局对象。

#### 构造器调用模式

JavaScript 是一门基于原型继承的语言。

如果在一个函数前面带上 new 来调用，那么背地里将会创建一个连接到该函数的prototype 成员的新对象，同时 this 会被绑定到那个新对象上。

一个函数，如果创建的目的就是希望结合 new 前缀来调用，那么它就被称为构造器函数。

#### Apply 调用模式

apply 方法让我们构建一个参数数组传递给调用函数。它也允许我们选择 this 的值。apply 方法接收两个参数，第一个是要绑定到 this 的值，第 2 个就是一个参数数组。

#### 参数

当函数被调用时，会得到一个“免费” 配送的参数，那就是 arguments 数组。函数可以通过此参数访问所有它被调用时传递给它的参数列表，包括那些没有被分配给函数声明时定义的形式参数的多余参数。

arguments 并不是一个真正的数组。 arguments 拥有一个length 属性，但它没有任何数组的方法。

#### 返回

当一个函数被调用时，它从第一个语句开始执行，并在遇到关闭函数体的 } 时结束。然后函数把控制权交还给调用该函数的程序。

return 语句可用来使函数提前返回。

一个函数总是会返回一个值。如果没有指定返回值，则返回 undefined。

如果函数调用时在前面加上了 new 前缀，且返回值不是一个对象，则返回 this（该新对象）。

#### 异常

JavaScript 提供了一套异常处理机制。

一个 try 语句只会有一个捕获所有异常的 catch 代码块。如果你的处理手段取决于异常的类型，那么异常处理器必须检查异常对象的 name 属性来确定异常的类型。

#### 扩充类型的功能

JavaScript 允许给语言的基本类型扩充功能。

#### 递归

递归函数就是会直接或间接地调用自身的一种函数。

递归是一种强大的编程技术，它把一个问题分解为一组相似的子问题，每一个都有一个寻常解去解决。

递归函数可以非常高效地操作树形结构，比如浏览器端地文档对象模型。

一些语言提供了尾递归优化。

JavaScript 没有提供尾优化。

#### 作用域 

作用域控制着变量与参数地可见性及生命周期。

JavaScript 不支持块级作用域。

JavaScript 有函数作用域。

#### 闭包

作用域的好处是内部函数可以访问定义它们的外部函数的参数和变量（除了 this 和 arguments）。

#### 回调

异步请求，提供一个当服务器的响应到达时随即触发的回调函数。

#### 模块

我们可以使用函数和闭包来构造模块。

模块是一个提供接口却隐藏状态与实现的函数或对象。

#### 级联

有一些方法没有返回值。

如果我们让这些方法返回 this 而不是 undefined，就可以启用级联。

级联技术可以产生出极富表现力的接口。

#### 柯里化（局部套用）

函数也是值，从而我们可以用有趣的方式去操作函数值。

柯里化允许我们把函数与传递给它的参数相结合，产生一个新的函数。

curry 方法通过创建一个保存着原始函数和要被套用的参数的闭包来工作。它返回另一个函数，该函数被调用时，会返回调用原始函数的结果，并传递调用 curry时的参数加上当前调用的参数。它使用 Array 的 concat 方法连接两个参数数组。

#### 记忆

函数可以将先前操作的结果记录在某个对象里，从而避免无谓的重复运算。

这种优化被称为记忆。

JavaScript 的对象和数组要实现这种优化是非常方便的。

---

## 第 5 章 继承

#### 简介

继承提供了两个有用的服务

- 首先，它是代码重用的一种形式。
- 另一个好处是引入了一套类型系统的规范。

#### 伪类

通过构造器函数产生对象。

调用构造函数时忘记了在前面加上 new 前缀，那么 this 将不会被绑定到一个新对象上。

#### 对象说明符

JSON 文本只能描述数据，但有时数据表示的是一个对象，把该数据与它的方法关联起来是有用的。

#### 原型

基于原型的继承相比基于类的继承在概念上更为简单：一个新对象可以继承一个旧对象的属性。

通过 `Object.create`方法构造出更多实例。

#### 函数化

继承模式的一个弱点就是没法保护隐私。

私有变量和私有函数，使用应用模块模式。

函数化构造器的伪代码模板：

```javascript
var constructor = function (spec, my){
    var that , 其他私有实例变量；
    my = my || {};
    把共享的变量和函数添加到my中
    that = 一个新对象
    添加给 that 的特权方法
    return that；
}；
```

如果我们用函数化的样式创建一个对象，并且该对象的所有方法都不使用 this 或 that，那么该对象就是持久性的。

#### 部件

---

## 第 6 章 数组

#### 简介

数组是一段线性分配的内存，它通过整数计算偏移并访问其中的元素。

JavaScript 拥有一些类数组特性的对象。

#### 数组字面量

数组字面量是在一对方括号中包围零个或多个用逗号分隔的值的表达式。

数组继承自 Array.prototype

对象继承自 Object.prototype

#### 长度

每个数组都有一个length 属性。

JavaScript 数组的 length 是没有上界的。

length 属性的值是这个数组的最大整数属性名加上 1。它不一定等于数组里的属性的个数。

设置更大的 length 不会给数组分配更多的空间。而把 length 设小导致所有下标大于等于新 length 的属性被删除。

#### 删除

JavaScript 的数组其实就是对象，所以 delete 运算符可以用来从数组中移除元素：

`numbers = ['zero', 'one', 'two', 'shi', 'go']`

```javascript 
delete numbers[2]
// numbers 是['zero', 'one', 'undefined', 'shi','go']
```

缺陷是被删除元素之后的元素保留着它们最初的属性。

splice 方法

```javascript
numbers.splice(2, 1);
// numbers 是 ['zero', 'one', 'shi', 'go']
```

缺点是效率不高

#### 枚举

```javascript
var i;
for (i = 0; i < myArray.length; i += 1){
    document.writeln(myArray[i]);
}
```

#### 容易混淆的地方

规则：当属性名是小而连续的整数时，你应该使用数组。否则，使用对象。

判断一个对象是否为数组：

```javascript
var is_array = function(value){
    return Object.prototype.toString.apply(value) === '[object Array]';
}
```

#### 方法

JavaScript 提供了一套数组可用的方法。这些方法是被储存在 Array.prototype中的函数。

#### 指定初始值

JavaScript 的数组通常不会预设值。

访问一个不存在的值返回 undefined。

---

## 第 7 章 正则表达式

#### 简介

正则表达式是一门简单语言的语法规范。它应用在一些方法中，对字符串中的信息实现查找、替换和提取操作。

可处理正则表达式的方法有：

- regexp.exec
- regexp.test
- string.match
- string.replace
- string.search
- string.split
#### 一个例子

```javascript
var parse_url = /^(?:([A-Za-z]+):)?(\/{0,3})([0-9.\-A-Za-z]+)(?::(\d+))?(?:\/([^?#]*))?(?:\?([^#]*))?(?:#(.*))?$/;
```

`^`字符表示此字符串的开始。 它是一个锚，指引 exec 不要跳过那些不像 URL的前缀，只匹配那些从开头就像 URL 一样的字符串：

`(?:([A-Za-z]+):)?`

`(?: . . .)`表示一个非捕获型分组。

`(. . . . )`表示一个捕获型分组.

后缀`?` 表示这个分组是可选的。

#### 结构

有两种方法来创建一个`RegExp`对象.

- 正则表达式字面量被包围在一对斜杠中`/   /`.
- 创建一个正则表达式的另一个方法是使用`RegExp`构造器`new RegExp(,)`.

正则表达式标识

| 标识 | 含义                                                |
| ---- | --------------------------------------------------- |
| g    | 全局的(匹配多次; 不同的方法对 g 标识的处理各不相同) |
| i    | 大小写不敏感(忽略字符大小写)                        |
| m    | 多行(^和$能匹配行结束符)                            |

RegExp 对象的属性

| 属性       | 用法                                   |
| ---------- | -------------------------------------- |
| global     | 如果标识 g 被使用, 值为 true           |
| ignoreCase | 如果标识 i 被使用, 值为 true           |
| lastIndex  | 下一次 exec 匹配开始的索引. 初始值为 0 |
| multiline  | 如果标识 m 被使用, 指为 true           |
| source     | 正则表达式源码文本                     |

#### 正则表达式分支

一个正则表达式分支包含一个或多个正则表达式序列.

这些序列被`|(竖线)`字符分隔.

如果这些序列中的任何一项符合匹配条件, 那么这个选择就被匹配.

#### 正则表达式序列

一个正则表达式序列包含一个或多个正则表达式因子.

每个因子能选择是否跟随一个量词, 这个量词决定着这个因子被允许出现的次数.默认为1次.

#### 正则表达式因子

一个正则表达式因子可以是一个字符, 一个由圆括号包围的组, 一个字符类, 或者是一个转义序列.

控制字符和特殊字符: `\`   `/`   `[`  `]`  `(`  `)` `{`  `}`  `?`  `+`  `*`  ` |` `.`  `^`  `$`

希望上面的列出的字符按字面去匹配,那么必须要用一个 `\ `  前缀进行转义.

`\` 前缀不能使字母或数字字面化.

一个未被转义的`.` 会匹配除行结束符以外的任何字符.

#### 正则表达式转义

`\d` 等同于[0-9],它匹配一个数字.

`\D` 则表示与其相反的: [^0-9\]

`\s` 等同于[\f\n\r\t\u000B\u0020\u00A0\u2028\u2029].Unicode 空白符的一个不完全子集.

`\S`  则表示与其相反的:[^\f\n\r\t\u000B\u0020\u00A0\u2028\u2029\].

`\w`  等同于[0-9A-Z_a-z].

`\W` 则表示与其相反的: [^0-9A-Z_a-z\]

#### 正则表达式分组

**捕获型**

一个捕获型分组是一个被包围在圆括号中的正则表达式分支.

任何匹配这个分组的字符都会被捕获.

```javascript
//先看用捕获性分组匹配会返回什么
var str1 = '000aaa111';             
var pattern = /([a-z]+)(\d+)/; //捕获性分组匹配
var arr = pattern.exec(str1);  
console.log(arr) //['aaa111','aaa','111']
```

**非捕获型**

非捕获型分组有一个`(?:` 前缀 .非捕获型分组仅做简单的匹配, 并不会捕获所匹配的文本.

```JavaScript
//非捕获性分组
var str2 = '000aaa111';
var pattern2 = /(?:[a-z]+)(?:\d+)/; //非捕获性分组匹配
var arr2 = pattern.exec(str2);  
console.log(arr2) //['aaa111']  结果正确
```

**向前正向匹配**

向前正向匹配分组有一个`(?=` 前缀. 它类似于非捕获型分组, 但在这个组匹配后, 文本会倒回到它开始的地方, 实际上并不匹配任何东西.

```JavaScript
//正向前瞻，匹配.jpg后缀文件名
var str = '123.jpg,456.gif,abc.jpg';
var partern = /\w+(?=\.jpg)/g; //正向前瞻匹配
console.log(str.match(partern)); //['123', 'abc']   返回结果正确，没有匹配456.gif
```

**向前负向匹配**

向前负向匹配分组有一个`(?!`前缀.它类似于向前正向匹配分组, 但只有当它匹配失败时它才继续向前进行匹配.

```JavaScript
//反向前瞻，匹配3个及以上的a，而且后面不能有000的字符
var str = 'aaa000 aaaa111 aaaaaaa222';
var partern = /a{3,}(?!000)/g; //反向前瞻匹配
console.log(str.match(partern)); //['aaaa', 'aaaaaaa']   返回结果正确，没有匹配aaa000
```

#### 正则表达式量词

正则表达式因子可以用一个正则表达式量词后缀来决定这个因子应该被匹配的次数.

`?` 等同于 {0, 1}

`*` 等同于 {0, }

`+` 等同于 {1, }

---

## 第 8 章 方法

#### Array

**array.concat(item...)**

concat 方法产生一个新数组, 它包含一份 array 的浅复制并把一个或多个参数item附加在其后. 如果参数 item 是一个数组, 那么它的每个元素会被分别添加.

```JavaScript 
var a = ['a', 'b', 'c'];
var b = ['x', 'y', 'z'];
var c = a.concat(b, true);
//c 变成 ['a', 'b', 'c', 'x', 'y', 'z', true]
```

**array.join(separator)**

join 方法把一个array 构造成一个字符串. 它先把array中的每个元素构造成一个字符串,接着用一个 separator 分隔符把它们连接在一起. 默认的 separator 是逗号 ','

```JavaScript
var a = ['a', 'b', 'c'];
a.push('d');
var c = a.join('');  //c 是 'abcd'
```

**array.pop()**

pop 和 push 方法使得数组 array 可以像堆栈一样工作. pop 方法移除 array 中的最后一个元素并返回该元素.如果该 array 是empty , 它会返回 undefined.

```JavaScript
var a = ['a', 'b', 'c'];
var c = a.pop();    // a 是 ['a','b'] & c 是 'c'

// pop 可以像这样实现
Array.method('pop', function(){
	return this.splice(this.length - 1, 1)[0];
});
```

**array.push(item...)**

push 方法把一个或多个参数 item 附加到一个数组的尾部.和 concat 方法不同的是, 他会修改 array, 如果参数 item 是一个数组, 它会把参数数组作为单个元素整个添加到数组中, 并返回这个 array 的新长度值.

```JavaScript
var a = ['a', 'b', 'c'];
var b = ['x', 'y', 'z'];
var c = a.push(b, true);
// a 是 ['a', 'b', 'c', ['x', 'y', 'z'], true]
// c 是 5

// push 可以像这样实现
Array.method('push',function(){
    this.splice.apply(
    	this,
        [this.length, 0].
        	concat(Array.prototype.slice.apply(arguments)));
    return this.length;
});
```

**array.reverse()**

reverse 方法反转 array里的元素的顺序, 并返回 array 本身:

```JavaScript 
var a = ['a', 'b', 'c'];
var b = a.reverse();
// a 和 b 都是 ['c', 'b', 'a']
```

**array.shift()**

shift 方法移除数组 array 中的第 1 个元素并返回该元素. 如果这个数组 array 是空的, 它会返回 undefined. shift 通常比 pop 慢的多.

```JavaScript
var a = ['a', 'b', 'c']
var c = a.shift();	// a 是 ['b', 'c'] & c 是 'a'

//shift 可以这样实现
Array.method('shift', function(){
    return this.splice(0, 1)[0];
)};
```



**array.slice(start, end)**

slice 方法对 array 中的一段做浅复制. 首先复制 array[start], 一直复制到 array[end]为止(不包括array[end]). end参数是可选的, 默认值是该数组的长度 array.length. 如果两个参数中的任何一个是负数, array.length 会和它们相加, 试图让它们成为非负数.

```JavaScript
var a = ['a', 'b', 'c'];
var b = a.slice(0, 1);	// b 是['a']
var c = a.slice(1);   	// c 是 ['b', 'c']
var d = a.slice(1, 2);	// d 是 ['b']
```

**array.sort(comparefn)**

sort 方法对 array 中的内容进行排序.

它不能正确地给一组数字排序:

```JavaScript
var n = [4, 8, 15, 16, 23, 42]
n.sort();
// n 是 [15, 16, 23, 4, 42, 8]
```

JavaScript 地默认比较函数把要被排序地元素都视为字符串.

使用自己的比较函数来替换默认的比较函数.

```JavaScript
n.sort(function(a,b){
    return a-b;
});
// n 是 [4, 8, 15, 16, 23,42];
```

如果我们想要给任何包含简单值的数组排序

```JavaScript
var m = ['aa', 'bb', 4, 8, 15, 16, 23, 42];
m.sort(function(a, b){
    if(a === b){
        return 0;
    }
    if(typeof a === typeof b){
        return a < b ? -1 : 1;
    }
    return typeof a < typeof b ? -1 :1;
});
// m 是 [4, 8, 15, 16, 23, 42, 'a', 'aa', 'bb']
```

**array.splice(start, deleteCount, item...)**

splice 方法从 array 中移除一个或多个元素, 并用新的 item 替换它们. 参数 start 是从数组 array 中移除元素的开始位置. 参数 deleteCount 是要移除的元素个数.如果有额外的参数, 那些 item 会插入到被移除元素的位置上. 它返回一个包含被移除元素的数组.

splice 最主要的用处是从一个数组中删除元素.

```javascript
var a = ['a', 'b', 'c'];
var r = a.splice(1, 1, 'ache', 'bug');
// a是['a', 'ache', 'bug', 'c']
// r是['b']
```

**array.unshift(item...)**

unshift 方法像 push 方法一样, 用于把元素添加到数组中, 但它是把 item 插入到 array的开始部分而不是尾部.它返回 array 的新的 length

```JavaScript
var a = ['a', 'b', 'c'];
var r = a.unshift('?', '@');
// a 是['?', '@', 'a', 'b', 'c']
// r 是 5
```

#### Function

**function.apply(thisArg, argArray)**

apply 方法调用 function, 传递一个会被绑定到 this 上的对象和一个可选的数组作为参数.

#### Number

**number.toExponential(fractionDigits)**

toExponential 方法把这个number 转换成一个指数形式的字符串. 可选参数 fractionDigits 控制其小数点后的数字位数.它的值必须在0~20;

**number.toFixed(fractionDigits)**

toFixed 方法把这个 number 转换成为一个十进制数形式的字符串.可选参数 fractionDigits 控制其小数点后的数字位数.它的值必须在0~20,默认为0;

**number.toPrecision(precision)**

toPrecision 方法把这个 number 转换成为一个十进制数形式的字符串.可选参数precision控制数字的精度.它的值必须在0~21;

**number.toString(radix)**

toString 方法把这个 number 转换成为一个字符串. 可选参数 radix 控制基数. 它的值必须在2~36. 默认的 radix 是以 10 为基数的.

#### Object

**object.hasOwnProperty(name)**

如果这个 object 包含一个名为 name 的属性,那么 hasOwnProperty 方法返回 true.

#### RegExp

**regexp.exec(string)**

成功匹配返回数组

**regexp.test(string)**

test 方法是使用正则表达式的最简单(和最快) 的方法. 如果该 regexp 匹配 string, 它返回 true; 否则, 它返回 false.不要对这个方法使用g标识.

#### String

**string.charAt(pos)**

charAt 方法返回在 string 中 pos 位置处的字符. 如果 pos 小于0或大于等于字符串的长度 string.length, 它会返回空字符串.

```javascript
var name = 'Curly'
var initial = name.charAt(0);   //initial 是 'C'
```

**string.charCodeAt(pos)**

charCodeAt 方法同 charAt 一样, 只不过它返回的不是一个字符串, 而是以整数形式表示的在 string 中的 pos 位置处的字符的字符码位. 如果 pos 小于0或大于等于字符串的长度 string.length, 它返回 NaN.

```JavaScript
var name = 'Curly';
var initial = name.charCodeAt(0); // initial 是 67
```

**string.concat(string...)**

concat 方法把其他的字符串连接在一起来构造一个新的字符串.`+`连接符更方便

```JavaScript
var s = 'C'.concat('a', 'c')
```

**string.indexOf(searchString, position)**

indexOf 方法在 string 内查找另一个字符串searchString.找到返回第一个匹配字符的位置,否则返回 -1. position 可设置从string的某个指定位置开始查找.

**string.lastIndexOf(searchString, position)**

lastIndexOf 方法和 indexOf 方法类似,只不过它是从该字符串的末尾开始查找而不是从开头.

**string.localeCompare(that)**

localeCompare 方法比较两个字符串.

如果 string 比字符串that小,那么结果为负数.如果相等的,那么结果为0;

**string.match(regexp)**

match 方法让字符串和一个正则表达式进行匹配.它依据 g 标识来决定如何进行匹配.如果没有 g 标识, 那么调用 string.match ( regexp ) 的结果与调用regexp.exec(string) 的结果相同. 然而, 如果 regexp 带有 g 标识, 那么它生成一个包含所有匹配(除捕获分组之外)的数组.

**string.replace(searchValue, replaceValue)**

replace 方法对 string 进行查找和替换操作,并返回一个新的字符串. 参数 searchValue可以是一个字符串或一个正则表达式对象. 如果它是一个字符串, 那么 searchValue 只会在第一次出现的地方被替换.如果 searchValue 是一个正则表达式并且带有 g 标识, 它会替换所有的匹配.

**string.search(regexp)**

search 方法和 indexOf 方法类似, 只是它接受一个正则表达式对象作为参数而不是一个字符串.如果找到匹配, 它返回第 1 个匹配的首字符位置, 如果没有找到匹配, 则返回 -1.此方法会忽略 g 标识.

**string.slice(start, end)**

slice 方法复制 string 的一部分来构造一个新的字符串.

**string.split(separator, limit)**

split 方法把这个 string 分割成片段来创建一个字符串数组.可选参数 limit 可以限制被分割的片段数量. separator 参数可以是一个字符串或一个正则表达式.

**string.toLowerCase()**

toLowerCase 方法返回一个新的字符串,这个string中的所有字母都被转换为小写格式.

**string.toUpperCase()**

toUpperCase 方法返回一个新的字符串,这个 string 中的所有字母都被转换为大写格式.

**String.fromCharCode(char...)**

String.fromCharCode函数根据一串数字编码返回一个字符串.

```javascript
var a = String.fromCharCode(67, 97, 116);
// a 是 'Cat'
```

---

## 第 9 章 代码风格

优秀的程序拥有一个前瞻性的结构, 它会预见到在未来才可能需要的修改,但不会让其成为过度的负担.

优秀的程序还会具备一种清晰的表达方式.

---

## 第 10 章 优美的特性

函数是顶级对象

​	函数是有词法作用域的闭包.

基于原型继承的动态对象

​	对象是无类别的.

对象字面量和数组字面量

​	这对创建新的对象和数组来说是一种非常方便的标识法. JavaScript 字面量是数据交换格式 JSON 的灵感之源.