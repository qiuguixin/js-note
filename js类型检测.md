#js类型检测
> 为什么呢？js是弱类型语言，很多时候我们需要明确知道变量的具体类型，这几乎关系到代码执行的安全。幸运的是，js为我们提供了多种方法来检测变量的真实类型，下面简单做一整理。

**Js中的数据类型分为***原始类型（或基本类型）***和***引用类型*

* 原始类型：string、number、boolean、null和undefined
* 引用类型：Object、Array、Date、Error和Function
* 其实Js总共就6中数据类型

###检测原始值(string、number、boolean、null和undefined)
>**typeof**运算符，主要用于检测值类型，返回值的类型的字符串，例如

* 对于字符串 name: *typeof name === 'string'*
* 对于数字 count: *typeof count === 'number'*
* 对于布尔值 found：*typeof found === 'boolean'*
* 对于undefined myApp：*typeof myApp === 'undefined'*

>由于**标准规范的严重bug**:*typeof null === 'object'*,检测null可通过直接使用恒等运算符（===）和费恒等运算福（!==）

>*typeof*的独特之处：

* 将其用于一个为声明的变量也不会报错。未定义的变量和值为undefined的变量通过typeof都将返回'undefined'
* 奇怪的是检测函数最好的方法也是使用*typeof*，例如对于函数myFunc，**typeof myFunc === 'function'**

###检测引用值（Object、Array、Date、RegExp、Error和Function）
> 不能使用typeof来检测，因为所有对象都会返回'object'

* console.log(typeof {});  //'object'
* console.log(typeof []);  //'object'
* console.log(typeof new Date());  //'object'
* console.log(typeof new RegExp());  //'object'

>因此**instanceof**运算符，主要用于检测引用值类型，检测构造某个对象的构造器（而且还检测原型链）语法如下：

**value instanceof constructor**

* 对于日期 value instanceof Date === true
* 对于正则表达式 value instanceof RegExp === true
* 对于Error value instanceof Error === true

* 对于自定义类型 value instanceof constructor === true

>检测函数，前面说过用**typeof myFunc === 'function'**

> 检测数组，用Array.isArray()方法，例如Array.isArray(arr) === true

>**到此为止，所有的类型都检测完毕，不过还有一个比较常见的场景是检测对象的属性，首先有个概念：**

>*假值*：会被认为是判断句中会被当做false的值，有：**0、NaN、""、false、null和undefined**共6个

* 如果实例对象的属性存在、或继承自对象的原型，in运算符都会返回true
* 如果只想检查实例对象的某个属性是否存在，则使用hasOwnproperty()方法

#END




