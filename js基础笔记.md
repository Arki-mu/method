#### 基本语法

```javascript
alert(""); //弹出窗口
document.write(""); //让计算机在页面输出一个内容 （向body中输出一个内容）
console.log("");//向控制台输出一个内容
```

----

#### a++ 和 ++a 的区别：

（1）a++ ：存储新值，用旧值（上一个值）来计算，也就是输出旧值；

（2）++a ：存储新值，用新值（当前的值）来计算，也就是输出新值；

----------------------

#### 在JS中一共有六种数据类型（数据类型指的就是字面量的类型）

###### 基本数据类型

​	String 字符串

​	Number 数值

​	Boolean 布尔值

​	Null 空值

​	Undefined 未定义

###### 引用数据类型

​	Object 对象

###### 扩展

Symbol  生成一个全局唯一的值（但并不是字符串）。

BigInt	一种新的数据类型， 用于当整数值大于Number数据类型支 持的范围时。这种数据类型允许我们安全地对大整数执行算术操作，表示高分辨率的时间戳，使用大整数id,等等，而不需要使用库。
	重要的是要记住，不能使用Number和BigInt操作数的混合执行算术运算，需要通过显式转换其中的一种类型。此外，出于兼容性原因,不允许在BigInt上使用一元加号(+)运算符。

------------------------------------------

typeof 变量  //typeof检测一个变量的数据类型

typeof会将该值的类型以字符串的形式返回

-----------------------------------

##### String字符串相关：

在字符串中可以使用\作为转义字符，当表示一些特殊符号时可以使用\进行转义

```javascript
/*
 *   \"   表示"
 *   \'   表示'
 *   \n   表示换行
 *   \t   表示制表符
  *   \\  表示\
**/
```



##### Number数值相关：

###### 在JS中所有数值都是Number类型，包括整数和浮点数。

###### JS中可以表示的数值的最大值：

​		Number. MAX-VALUE			//1.7976931348623157e+308

###### 	大于0的最小值：

​		Number. MIN-VALUE 			//5e-324

###### 如果使用Number表示的数字超过了最大值，则会返回

​	Infinity 表示正无穷

​	-Infinity 表示负无穷

​		PS：使用typeof检查Infinity也会返回number

###### NaN 是一个特殊的数字，表示Not a Number  

​	PS：使用typeof检查NaN也会返回number

###### 在JS中整数的运算基本可以保证精确

###### 如果使用JS进行浮点（小数）运算，可能得到一个不精确的结果，所以千万不要使用JS进行精确度要求比较的运算



##### Boolean 布尔值相关

###### 布尔值只有两个，主要用来做逻辑判断

​	true - 表示真

​	false - 表示假

​	 使用typeof检查一个布尔值时会返回boolean



##### Null 空值相关

Null类型的值只有一个，就是null

null这个值专门用来表示为一个空的对象

使用typeof检查一个null值时，会返回object



##### Undefined未定义相关

Undefined类型的值只有一个，就是undefined

当声明一个变量，但是并不给变量赋值时，它的值就是undefined

使用typeof检查一个undefined时也会返回undefined

----------

#### 强制类型转换

###### 将其他数据类型转化为string

1）调用被转换数据类型的toString()方法

​		该方法不会影响到原变量，它会将转换的结果返回（null和undefined这两个值没有toString()方法，如果调用则会报错）

2）调用String()函数，并将被转换的数据作为参数传递给函数

​	  使用String()函数做强制类型转换时

​			对于Number和Boolean实际上是调用的toString()方法

​			但是对于null和undefined，就不会调用toString()方法

​					它会将null(字面量)直接转换为"null"(字符串)

​					它会将undefined(字面量)直接转换为"undefined"(字符串)

###### 将其他数据类型转化为number

1）使用Number函数

​	字符串--->数字

​			纯数字-->数字

​			含非数字内容-->NAN

​	布尔值--->数字

​			true-->1

​			false-->0

​	null--->0

​	undefined--->NAN

2）parseInt()把一个字符串转化为一个整数

```javascript
alert(parseInt('1000px'))    //1000 返回我整数部分
alert(parseInt('px1000'))     //NaN 如果第⼀个不是整型，就返回NaN
alert(parseInt('1000px1000')) //1000 返回我整数部分 从第⼀个数值开始取值，，到最后⼀个连续数值结
alert(parseInt('100.55')) //100 返回我整数部分 从第⼀个数值开始取值，，到最后⼀个连续数值结束
alert(parseInt(''))    //NaN
```

parseInt()函数除了可以识别⼗进制，也可以识别八进制和⼗六进制

```javascript
var num1 = parseInt("1234blue"); // 1234
var num2 = parseInt(""); // NaN
var num3 = parseInt("0xA"); // 10（⼗六进制数）
var num4 = parseInt(22.5); // 22
var num5 = parseInt(070); // 56（八进制数） ECMAScript 5规则
var num5 = parseInt("070"); // 56（八进制数） ECMAScript 3规则
var num6 = parseInt("70"); // 70（⼗进制数）
var num7 = parseInt("0xf"); // 15（⼗六进制数）
```

3）parseFloat()把一个字符串转换为一个浮点数

```javascript
var num1 = parseFloat("1234blue"); //1234 （整数）
var num2 = parseFloat("0xA"); //0 不认⼗六进制
var num3 = parseFloat("22.5"); //22.5
var num4 = parseFloat("22.34.5"); //22.34 只认第⼀个数点
var num5 = parseFloat("0908.500"); //908.5 去掉前导0后导0
var num6 = parseFloat("3.125e7"); //31250000 把科学计数法转换成普通的数值
```

###### 将其他数据类型转化为boolean

使用Boolean()函数

1. 数字--->布尔值

   除了NaN和0转成false，其余全为true

2. 字符串--->布尔值

   除了空串（a=""），其余都是true（包括a=" "）

3. null和undefined都会转换为false
4. 对象也会转换为true

---

#### JS  new Date(); 获取图片

```javascript
var date = new Date();//会将当前日期和时间保存为其初始值
//参数形式
new Date('month day,year hour:min:second');
new Date('month day,year');
new Date(year,month,day,hour,min,second);
new Date(year,month,day);
new Date(ms);
```

---

#### forEach()

增强版的for循环，用于遍历数组

```javascript
var arr = [6,7,5,4,1,9];
arr.forEach(function(correntvalue,index,array){
	console.log(correntvalue); //当前项
	console.log(index);//当前项索引
	console.log(array);//调用forEach的数组
})
```

#### filter()

filter也是一个常用的操作，它用于把Array的某些元素过滤掉，然后返回剩下的元素。

和map()类似，Array的filter()也接收一个函数。和map()不同的是，filter()把传入的函数依次作用于每个元素，然后根据返回值是`true`还是`false`决定保留还是丢弃该元素。

```javascript
var arr = [6,7,5,4,1,9];
//filter()接收的回调函数，其实可以有多个参数。通常我们仅使用第一个参数，表示Array的某个元素。回调函数还可以接收另外两个参数，表示元素的位置和数组本身
var newArr = arr.filter(function(correntvalue,index,array){
	console.log(correntvalue); //当前项
	console.log(index);//当前项索引
	console.log(array);//调用filter的数组
	return true;
});

//在一个Array中，删掉偶数，只保留奇数
var newArr = arr.filter(function(num){
    return num%2!==0;
})
```

#### match()

match() 方法可在字符串内检索指定的值，或找到一个或多个正则表达式的匹配。

该方法类似 `indexOf()` 和` lastIndexOf()`，但是它返回指定的值，而不是字符串的位置。

```javascript
var regexp = /[0-9]/g;//例子
//语法
//stringObject.match(searchvalue)
//stringObject.match(regexp) //检索stringObject内所有的[0-9]
```

`onblur`元素失去焦点时

##### `call()`,`apply()`,`bind()`用来改变this的指向

```javascript
fn.call(obj,1,2);//第一个参数为作用对象,第二个以后传递进来的实参传递给函数
fn.aply(obj,[1,2]);//第一个参数为作用对象，第二个参数是数组传入fn
fn.bind(obj,1,2)();//返回仍是函数(bind不兼容IE6~8)
```

1. 相同点：

    三个函数都会改变this的指向（调用这三个函数的函数内部的this）

2. 不同点：

   1）bind会产生新的函数，（把对象和函数绑定死后，产生新的函数）

   2）call和apply不会产生新的函数，只是在调用时，绑定一下而已。

   3）call和apply的区别，第一个参数都是要绑定的this，apply第二个参数是数组（是函数的所有参数），call把apply的第二个参数单列出来。

   

#### reduce() 

##### arr.reduce(callback,[initialValue])

   callback （执行数组中每个值的函数，包含四个参数）

1. previousValue （上一次调用回调返回的值，或者是提供的初始（initialValue））
2. currentValue （数组中当前被处理的元素）
3. index （当前元素在数组中的索引）
4. array （调用 reduce 的数组）

   initialValue （作为第一次调用 callback 的第一个参数。）

   //https://www.jianshu.com/p/e375ba1cfc47

-------------

##### arr.reduce(function(prev,cur,index,arr){

#####       ...

#####  }, init);

1. arr 表示原数组；
2. prev 表示上一次调用回调时的返回值，或者初始值 init;
3. cur 表示当前正在处理的数组元素；
4. index 表示当前正在处理的数组元素的索引，若提供 init 值，则索引为0，否则索引为1；
5. init 表示初始值。

https://www.jianshu.com/p/541b84c9df90

-------------------------------------------------



```javascript
//例子
//1. 求和
var arr = [1, 2, 33, 4, 5, 5, 1, 2];
var sum = arr.reduce(function (pre, cur) {
    return pre + cur;
});
console.log(arr, sum);
//2.最大值
var max = arr.reduce(function (pre, cur) {
    return Math.max(pre, cur);
});
console.log(arr, max);
//3.数组去重
let newArr = arr.reduce(function (pre, cur) {
    if (!pre.includes(cur)) {
        return pre.concat(cur);
    } else {
        return pre;
    }
}, []);
console.log(newArr);
```

