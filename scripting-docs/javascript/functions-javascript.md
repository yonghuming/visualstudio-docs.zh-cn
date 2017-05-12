---
title: "函数 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "内部 JavaScript 函数"
ms.assetid: e2a72b5a-3edd-43d8-95e8-91721b38c1c1
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# 函数 (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 函数执行操作，还可返回值。  有时返回的是计算或比较的结果。  函数也称为“全局方法”。  
  
 函数将多个操作合并到一个名称下。  这样可以简化你的代码。  还可以写出一组语句并对其命名，然后通过调用它并向它传递其所需的任何信息来执行整个组。  
  
 通过将信息放入函数名后的括号内，将信息传递给函数。  传递给函数的信息片段称为形参或实参。  某些函数不采用任何参数，而另一些则采用一个或多个参数。  在某些函数中，参数的数量取决于函数的使用方式。  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 支持两种类型的函数：内置于语言的函数和你自行创建的函数。  
  
## 内置函数  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 语言包含几个内置函数。  一些用于处理表达式和特殊字符，另一些则用于将字符串转换为数值。  
  
 请参阅 [JavaScript 方法](../javascript/reference/javascript-methods.md)，获取这些内置函数的相关信息。  
  
## 创建你自己的函数  
 可以创建你自己的函数，并在适当位置使用它们。  函数定义由 function 语句和 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 语句块组成。  
  
 以下示例中的 **checkTriplet** 函数采用三角形的边长作为其参数。  它通过检查三个数字是否构成毕达哥拉斯三元数组（直角三角形斜边长度的平方等于其余两边长度的平方和）来计算此三角形是否为直角三角形。  checkTriplet 函数通过调用另外两个函数中的一个来进行实际测试。  
  
 请注意，在测试的浮点版本中，使用极小的数字 \("epsilon"\) 作为测试变量。  由于浮点计算中的不确定性和舍入误差，直接测试三个数字是否构成毕达哥拉斯三元数组并不可行，除非已知待测试的三个值都是整数。  由于直接测试更准确，所以此示例中的代码将确定是否适合直接测试，如果适合则使用它。  
  
```javascript  
var epsilon = 0.00000000001; // Some very small number to test against.  
  
// The test function for integers.  
function integerCheck(a, b, c)   
{  
   // The test itself.  
   if ( (a*a) == ((b*b) + (c*c)) )     
      return true;  
  
   return false;  
} // End of the integer checking function.  
  
// The test function for floating-point numbers.  
function floatCheck(a, b, c)     
{  
   // Make the test number.  
   var delta = ((a*a) - ((b*b) + (c*c)))  
  
   // The test requires the absolute value  
   delta = Math.abs(delta);  
  
   // If the difference is less than epsilon, then it's pretty close.  
   if (delta < epsilon)     
      return true;  
  
   return false;  
} // End of the floating-poing check function.  
  
// The triplet checker.   
function checkTriplet(a, b, c)  
{   
   // Create a temporary variable for swapping values  
   var d = 0;   
  
   // First, move the longest side to position "a".  
  
   // Swap a and b if necessary  
   if (b > a)  
   {  
      d = a;  
      a = b;  
      b = d;  
   }  
  
   // Swap a and c if necessary  
   if (c > a)  
   {  
      d = a;  
      a = c;  
      c = d;  
   }  
  
   // Test all 3 values. Are they integers?  
   if (((a % 1) == 0) && ((b % 1) == 0) && ((c % 1) == 0))  
   {   
      // If so, use the precise check.  
      return integerCheck(a, b, c);   
   }  
   else  
   {  
      // If not, get as close as is reasonably possible.  
      return floatCheck(a, b, c);   
   }  
} // End of the triplet check function.  
  
// The next three statements assign sample values for testing purposes.  
var sideA = 5;  
var sideB = 5;  
var sideC = Math.sqrt(50.001);  
  
// Call the function. After the call, 'result' contains the result.  
var result = checkTriplet(sideA, sideB, sideC);  
```  
  
<a name="Arrow"></a>   
## 箭头函数  
 箭头函数语法 `=>` 提供了一种指定匿名函数的速记方法。  箭头函数语法如下所示。  
  
```javascript  
([arg] [, arg]) => {  
    statements  
}  
```  
  
 箭头左侧的值（可能由括号括起）指定传递给函数的参数。  函数的单个参数不要求使用括号。  如果未传入任何参数，则要求使用括号。  箭头右侧的函数定义可以是表达式（如 `v + 1`）或括在大括号 \({}\) 中的语句块。  
  
> [!IMPORTANT]
>  箭头函数语法仅在 [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] 中受支持。  
  
 不能将 `new` 运算符和箭头函数一起使用。  
  
 下面的代码示例显示了如何将箭头函数与作为函数定义的表达式一起使用。  在第一个示例中，v 作为参数传递给表达式。  在第二个示例中，v 和 i 作为参数传递给表达式。  
  
```  
var evens = [2, 4, 6, 8];  
  
// Using standard syntax.  
var odds = evens.map(function(v) { return v + 1; });  
  
// Using arrow function syntax.  
// Add one to each value to produce output.  
var odds = evens.map(v => v + 1);  
  
// The following line of code adds the index value to the passed  
// in value to produce output.  
// Note: the second argument to the callback function in the map   
// method is the index value (i).  
var nums = evens.map((v, i) => v + i);  
  
console.log(odds);  
console.log(nums);  
  
// Output:  
// [object Array] [3, 5, 7, 9]  
// [object Array] [2, 5, 8, 11]  
```  
  
 下面的代码示例显示如何将箭头函数与语句块一起使用。  
  
```javascript  
var fives = new Array();  
  
// Statement block, re-using nums array from previous example.  
// Note: The first argument to the callback function in forEach  
// is the value of the array element (v).  
nums.forEach(v => {  
  if (v % 5 === 0)  
    fives.push(v);  
});  
  
console.log(fives);  
  
// Output:  
// [object Array] [5]  
```  
  
 与标准函数不同，箭头函数与外层代码共享相同的词法 `this` 对象，由此不再需要 `var self = this;` 等运算。  
  
 以下示例演示了箭头函数内 `this` 对象的值与外层代码中的相同（仍引用 `bob` 变量）。  
  
```javascript  
var bob = {  
  _name: "Bob",  
  _friends: ["Pete", "Joe", "Larry"],  
  printFriends() {  
    this._friends.forEach(f =>  
      console.log(this._name + " knows " + f));  
  }  
}  
  
// Output:  
// Bob knows Pete  
// Bob knows Joe  
// Bob knows Larry  
```  
  
 箭头函数也与外层代码共享相同的词法 `arguments` 对象（类似于 `this` 对象）。  
  
<a name="Default"></a>   
## 默认参数  
 可以通过为参数分配初始值，指定它在函数中的默认值。  默认值可能是常数值或表达式。  
  
> [!IMPORTANT]
>  默认参数仅在 [!INCLUDE[jsv12textExp](../javascript/includes/jsv12textexp-md.md)] 中受支持。  
  
 在以下示例中，y 的默认值为 10，z 的默认值为 20。  函数将使用 10 作为 y 的值，除非调用方传入不同值（或未定义的值）作为第二个参数。  函数将使用 20 作为 z 的值，除非调用方传入不同值（或未定义的值）作为第三个参数。  
  
```javascript  
var val = 20;  
  
function f(x, y=10, z=val) {  
  return x + y + z;  
}  
  
console.log(f(3));  
console.log(f(3, 3));  
console.log(f(3, 3, 3));  
  
// Output:  
// 33  
// 26  
// 9  
```  
  
<a name="Rest"></a>   
## Rest 参数  
 通过 Rest 参数（由 spread 运算符                       ``  指定），可以将函数调用中的连续参数转换为数组。  
  
 Rest 参数使不再需要 `arguments` 对象。  Rest 参数与 `arguments` 对象有几个方面的区别，例如：  
  
-   Rest 参数是实际数组实例，因此支持可在数组上执行的操作。  
  
-   Rest 参数仅包含未作为单独（已命名）参数传入的连续参数（与之相反，`arguments` 对象包含传入函数的所有参数）。  
  
> [!IMPORTANT]
>  Rest 参数和 spread 算符仅在 [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)]中受支持。  
  
 在以下代码示例中，“hello”和 true 作为数组值传入并存储在 y 参数中。  Rest 参数必须为函数的最后一个参数。  
  
```javascript  
function f(x, ...y) {  
  // y is an array.  
  return x * y.length;  
}  
  
console.log(f(3, "hello", true));  
  
// Output:  
// 6  
  
```  
  
 有关 Spread 运算符的其他用法，请参阅 [Spread 运算符](../javascript/reference/spread-operator-decrement-dot-dot-dot-javascript.md)。  
  
## 请参阅  
 [JavaScript 语言参考](../javascript/javascript-language-reference.md)