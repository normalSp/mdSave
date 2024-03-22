# 1.语法

## 1.1 JavaScript 字面量

数字

字符串

表达式

数组：[40, 100]

对象：{firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"}

函数：

function myFunction(a, b) {

​	 return a * b;

}

## 1.2 JavaScript 变量( var 、let 、const)



JavaScript 使用关键字 **var** 、**let**来定义变量（不用var也可以，这样就可以使用delete来删除）， 使用等号来为变量赋值：

var x, length

x = 5

length = 6

可以在一条语句中声明很多变量。该语句以 var 开头，并使用逗号分隔变量即可：

var lastname="Doe", age=30, job="carpenter";

- `let`声明的变量具有块级作用域，即只在声明的代码块内有效。
- `var`声明的变量具有函数作用域，即在声明的函数内有效。如果在函数外部声明，它将成为全局变量。



const 的本质: const 定义的变量并非常量，并非不可变，它定义了一个常量引用一个值。使用 const 定义的对象或者数组，其实是可变的。下面的代码并不会报错：

```javascript
    // 创建常量对象
const car = {type:"Fiat", model:"500", color:"white"};

// 修改属性:
    car.color = "red";

// 添加属性
    car.owner = "Johnson";
```

但不能重新赋值

```javascript
const car = {type:"Fiat", model:"500", color:"white"};
    car = {type:"Volvo", model:"EX60", color:"red"};    // 错误
```

在相同的作用域或块级作用域中，不能使用 **const** 关键字来重置 **var** 和 **let**关键字声明的变量；

## 1.3 JavaScript 数据类型

------

**所有 JavaScript 数字均为 64 位**

**值类型(基本类型)**：字符串（String）、数字(Number)、布尔(Boolean)、空（Null）、未定义（Undefined 如var x;）、Symbol。

**引用数据类型（对象类型）**：对象(Object)、数组(Array)、函数(Function)，还有两个特殊的对象：正则（RegExp）和日期（Date）。

### 1.3.1 数组：

```javascript
var cars=new Array();
cars[0]="Saab";
cars[1]="Volvo";
cars[2]="BMW";
```

或

```javascript
var cars=new Array("Saab","Volvo","BMW");
```

或：

```javascript
var cars=["Saab","Volvo","BMW"];
```

### 1.3.2 对象

象由花括号分隔。在括号内部，对象的属性以名称和值对的形式 (name : value) 来定义。属性由逗号分隔：

```javascript
var person={firstname:"John", lastname:"Doe", id:5566};
```

上面例子中的对象 (person) 有三个属性：firstname、lastname 以及 id。

空格和折行无关紧要。声明可横跨多行：

```javascript
var person={
    firstname : "John",
    lastname : "Doe",
    id    : 5566
};
```

对象属性有两种寻址方式：

```javascript
name=person.lastname;
name=person["lastname"];
```

重置类型：

```javascript
var carname=new String;
var x=      new Number;
var y=      new Boolean;
var cars=   new Array;
var person= new Object;
```



**添加属性和方法**

要在所有已经存在的对象添加新的属性或方法。

另外，有时候我们想要在对象的构造函数中添加属性或方法。

使用 prototype 属性就可以给对象的构造函数添加新的属性：

```javascript
    function Person(first, last, age, eyecolor) {
        this.firstName = first;
        this.lastName = last;
        this.age = age;
        this.eyeColor = eyecolor;
    }
 
Person.prototype.nationality = "English";

Person.prototype.name = function() {
  return this.firstName + " " + this.lastName;
};
```

#### 1.3.2.1 Date 日期对象

[Date()](https://www.runoob.com/try/try.php?filename=tryjsref_date)
如何使用 Date() 方法获得当日的日期。

[getFullYear()](https://www.runoob.com/try/try.php?filename=tryjsref_getfullyear)
使用 getFullYear() 获取年份。

[getTime()](https://www.runoob.com/try/try.php?filename=tryjsref_gettime)
getTime() 返回从 1970 年 1 月 1 日至今的毫秒数。

[setFullYear()](https://www.runoob.com/try/try.php?filename=tryjsref_setfullyear2)
如何使用 setFullYear() 设置具体的日期。

[toUTCString()](https://www.runoob.com/try/try.php?filename=tryjsref_toutcstring)
如何使用 toUTCString() 将当日的日期（根据 UTC）转换为字符串。

[getDay()](https://www.runoob.com/try/try.php?filename=tryjsref_date_weekday)
如何使用 getDay() 和数组来显示星期，而不仅仅是数字。

[Display a clock](https://www.runoob.com/try/try.php?filename=tryjs_timing_clock)
如何在网页上显示一个钟表。



**实例化**

```javascript
new Date();
        new Date(value);
        new Date(dateString);
        new Date(year, monthIndex [, day [, hours [, minutes [, seconds [, milliseconds]]]]]);

var today = new Date()
var d1 = new Date("October 13, 1975 11:13:00")
var d2 = new Date(79,5,24)
var d3 = new Date(79,5,24,11,33,0)

//设置日期
var myDate=new Date();
myDate.setFullYear(2010,0,14);// 第二个参数为月份， 0 到 11 之间的整数值，表示从一月到十二月
var myDate=new Date();
myDate.setDate(myDate.getDate()+5);//
在下面的例子中，我们将日期对象设置为 5 天后的日期：
```



**日期比较**

```javascript
    var x=new Date();
x.setFullYear(2100,0,14);
        var today = new Date();

        if (x>today)
        {
            alert("今天是2100年1月14日之前");
        }
        else
        {
            alert("今天是2100年1月14日之后");
        }
```



#### 1.3.2.2 Array 数组对象

```javascript
   var mycars = new Array();
mycars[0] = "Saab";
           mycars[1] = "Volvo";
           mycars[2] = "BMW";
//or
var myCars=new Array("Saab","Volvo","BMW");

//or

var myCars=["Saab","Volvo","BMW"];

```


所有的JavaScript变量都是对象。数组元素是对象。函数是对象。

因此，你可以在数组中有不同的变量类型。

你可以在一个数组中包含对象元素、函数、数组：

```javascript
myArray[0]=Date.now;
myArray[1]=myFunction;
myArray[2]=myCars;
```



### 1.3.3 字符串

字符串方法：

| 方法                | 描述                                                         |
| :------------------ | :----------------------------------------------------------- |
| charAt()            | 返回指定索引位置的字符                                       |
| charCodeAt()        | 返回指定索引位置字符的 Unicode 值                            |
| concat()            | 连接两个或多个字符串，返回连接后的字符串                     |
| fromCharCode()      | 将 Unicode 转换为字符串                                      |
| **indexOf()**       | 返回字符串中检索指定字符第一次出现的位置                     |
| lastIndexOf()       | 返回字符串中检索指定字符最后一次出现的位置                   |
| localeCompare()     | 用本地特定的顺序来比较两个字符串                             |
| match()             | 找到一个或多个正则表达式的匹配                               |
| replace()           | 替换与正则表达式匹配的子串                                   |
| search()            | 检索与正则表达式相匹配的值                                   |
| slice()             | 提取字符串的片断，并在新的字符串中返回被提取的部分           |
| split()             | 把字符串分割为子字符串数组                                   |
| substr()            | 从起始索引号提取字符串中指定数目的字符                       |
| substring()         | 提取字符串中两个指定的索引号之间的字符                       |
| toLocaleLowerCase() | 根据主机的语言环境把字符串转换为小写，只有几种语言（如土耳其语）具有地方特有的大小写映射 |
| toLocaleUpperCase() | 根据主机的语言环境把字符串转换为大写，只有几种语言（如土耳其语）具有地方特有的大小写映射 |
| toLowerCase()       | 把字符串转换为小写                                           |
| toString()          | 返回字符串对象值                                             |
| toUpperCase()       | 把字符串转换为大写                                           |
| trim()              | 移除字符串首尾空白                                           |
| valueOf()           | 返回某个字符串对象的原始值                                   |

### 1.3.4 模板字符串

用反引号（**`**）分隔的字面量，允许多行字符串、带嵌入表达式的字符串插值和一种叫带标签的模板的特殊结构。

```javascript
let text = `Hello RUNOOB!`;
```

## 1.4 函数

使用function定义

```javascript
function myFunction(a,b)
{
    return a*b;
}
//使用
document.getElementById("demo").innerHTML=myFunction(4,3);
```

### 1.4.1 函数表达式（匿名函数

```javascript
var x = function (a, b) {return a * b};
var z = x(4, 3);
```

### 1.4.2 箭头函数

```javascript
// ES5
var x = function(x, y) {
        return x * y;
}

// ES6
const x = (x, y) => x * y;
```

### 1.4.3 默认函数参数

若没有传入对应参数则默认为 undefined ，也可以进行默认赋值

```javascript
function myFunction(x, y = 10) {
    // y is 10 if not passed or undefined
    return x + y;
}

myFunction(0, 2) // 输出 2
myFunction(5); // 输出 15, y 参数的默认值
```

### 1.4.4 闭包

用 var 在方法外部定义的属性即使不传入也能被方法使用，在方法内部定义属性要累计改变则要闭包：

```javascript
    var add = (function () {
        var counter = 0;
        return function () {return counter += 1;}
    })();

    add();
    add();
    add();

// 计数器为 3
```

### 1.4.4 arguments 对象

JavaScript 函数有个内置的对象 arguments 对象。

arguments 对象包含了函数调用的参数数组。

通过这种方式你可以很方便的找到最大的一个参数的值：

```javascript
x = findMax(1, 123, 500, 115, 44, 88);

function findMax() {
    var i, max = arguments[0];

    if(arguments.length < 2) return max;

    for (i = 0; i < arguments.length; i++) {
        if (arguments[i] > max) {
            max = arguments[i];
        }
    }
    return max;
}
```

### 1.4.5 函数的方法调用

```javascript
var myObject = {
    firstName:"John",
    lastName: "Doe",
    fullName: function () {
        return this.firstName + " " + this.lastName;
    }
}
myObject.fullName();         // 返回 "John Doe"
```

## 1.5 运算符

可以对字符串相加，字符串和数字也行，会都变成字符串。

## 1.6 if else

```javascript
if (time<10){
    document.write("<b>早上好</b>");
}
else if (time>=10 && time<20){
    document.write("<b>今天好</b>");
}
else{
    document.write("<b>晚上好!</b>");
}
```

## 1.7 switch

```javascript
switch(n)
{
    case 1:
        执行代码块 1
        break;
    case 2:
        执行代码块 2
        break;
    default:
        与 case 1 和 case 2 不同时执行的代码
}
```

## 1.8 for

```javascript
for (var i=0; i<5; i++){
        x=x + "该数字为 " + i + "<br>";
}
```

## 1.9 while

一样

## 1.10 数据类型

### 1.10.1 typeof

```javascript
typeof "John"
// 返回 string 
typeof 3.14
// 返回 number
typeof NaN
// 返回 number
typeof false                  // 返回 boolean
typeof [1,2,3,4]              // 返回 object
typeof {name:'John', age:34}
// 返回 object
typeof new Date()             
// 返回 object
typeof function () {}         // 返回 function
typeof myCar
// 返回 undefined (如果 myCar 没有声明)
typeof null
// 返回 object
```

### 1.10.2 类型转换

-->string

.toString

```jj
String(x)         // 将变量 x 转换为字符串并返回
String(123)       // 将数字 123 转换为字符串并返回
String(100 + 23)  // 将数字表达式转换为字符串并返回
```

```javascript
Date()      // 返回 Thu Jul 17 2014 15:38:19 GMT+0200 (W. Europe Daylight Time)
String(new Date())      // 返回 Thu Jul 17 2014 15:38:19 GMT+0200 (W. Europe Daylight Time)
```

-->number

```javascript
Number() //空返回0; 非数字返回NaN
```

**有自动转换机制**

## 1.11 try catch and throw

```javascript
try {
...    //异常的抛出
} catch(e) {
...    //异常的捕获与处理
} finally {
...    //结束处理
}
```

```javascript
function myFunction() {
    var message, x;
    message = document.getElementById("message");
    message.innerHTML = "";
    x = document.getElementById("demo").value;
    try {
        if(x == "")  throw "值为空";
        if(isNaN(x)) throw "不是数字";
        x = Number(x);
        if(x < 5)    throw "太小";
        if(x > 10)   throw "太大";
    }
    catch(err) {
        message.innerHTML = "错误: " + err;
    }
}
```

很方便的不用自定义错误类型

# 2. 调试（todo）

https://www.runoob.com/js/js-debugging.html

再说

# 3. 类

```javascript
class ClassName {
    constructor() { ... }
}
let x = new ClassName(x1, x2 ,x3, ......)
```

**construtor 是构造方法**

## 3.1 继承

```javascript
// 基类
class Animal {
    // eat() 函数
    // sleep() 函数
};


//派生类
class Dog extends Animal {
    // bark() 函数
};
```

super() 方法引用父类的构造方法。

## 3.2 getter / setter

```javascript
    class Runoob {
        constructor(name) {
            this.sitename = name;
        }
        get s_name() {
            return this.sitename;
        }
        set s_name(x) {
            this.sitename = x;
        }
    }

    let noob = new Runoob("菜鸟教程");
 
document.getElementById("demo").innerHTML = noob.s_name;
```

**类中添加 getter 和 setter 使用的是 get 和 set 关键字。**

**注意：**即使 getter、setter 是一个方法，当你使用时也不要使用括号。

```javascript
const obj = {
        _propertyName: '',

        set propertyName(value) {
            // setter逻辑
            this._propertyName = value;
        }
    	get propertyName() {
    		// getter逻辑
   			return this._propertyName;
  		}
    };

obj.propertyName = 'New Value'; // 调用setter方法，设置属性的值
console.log(obj.propertyName); // 调用getter方法，输出属性的新值
```

## 3.3 静态方法

```javascript
    class Runoob {
        constructor(name) {
            this.name = name;
        }
        static hello() {
            return "Hello!!";
        }
    }

    let noob = new Runoob("菜鸟教程");

// 可以在类中调用 'hello()' 方法
document.getElementById("demo").innerHTML = Runoob.hello();

// 不能通过实例化后的对象调用静态方法
// document.getElementById("demo").innerHTML = noob.hello();
// 以上代码会报错
```

**static** 不能实例化后在对象中调用

# 4. HTML DOM

------

通过 HTML DOM，可访问 JavaScript HTML 文档的所有元素。

------

**HTML DOM (文档对象模型)**

当网页被加载时，浏览器会创建页面的文档对象模型（Document Object Model）。

## 4.1 改变HTML

在 JavaScript 中，document.write() 可用于直接向 HTML 输出流写内容。

```html
        <!DOCTYPE html><html>
<body>
    <script>
        document.write(Date());
    </script>
</body>
</html>
```


如需改变 HTML 元素的内容，请使用这个语法：

```javascript
document.getElementById(*id*).innerHTML=*新的 HTML*
```

```html
<html>
<body>
    <p id="p1">Hello World!</p>
    <script>
        document.getElementById("p1").innerHTML="新文本!";
    </script>
</body>
</html>
```




如需改变 HTML 元素的属性，请使用这个语法：

```javascript
document.getElementById(*id*).*attribute=新属性值*
```

```html
        <!DOCTYPE html><html>
<body>
    <img id="image" src="smiley.gif">
    <script>
        document.getElementById("image").src="landscape.jpg";
    </script>
</body>
</html>
```

## 4.2 改变CSS


如需改变 HTML 元素的样式，请使用这个语法：

```javascript
document.getElementById(*id*).style.*property*=*新样式*
```

```html
    <!DOCTYPE html>
<html>
<body>
    
    <h1 id="id1">我的标题 1</h1>
<button type="button" onclick="document.getElementById('id1').style.color='red'">
    点我!</button>
    
</body>
</html>
```

## 4.3 HTML DOM事件



# 5. Window

