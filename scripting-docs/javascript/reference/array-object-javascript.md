---
title: "Array 对象 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Array"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Array 对象"
  - "constructor 属性"
ms.assetid: 08e5f552-0797-4b48-8164-609582fc18c9
caps.latest.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 27
---
# Array 对象 (JavaScript)
支持创建任何数据类型的数组。  
  
## 语法  
  
```  
  
        arrayObj = new Array()  
arrayObj = new Array([size])  
arrayObj = new Array([element0[, element1[, ...[, elementN]]]])  
```  
  
## 参数  
 `arrayObj`  
 必需。  `Array` 对象分配到的变量名称。  
  
 `size`  
 可选。  数组大小。  当数组基于零时，所创建的元素将具有从零到 `size` \-1 的索引。  
  
 `element0,...,elementN`  
 可选。  要置于数组中的元素。  这将创建一个具有 *n* \+ 1 个元素且 `length` 为 *n* \+ 1 的数组。  一旦使用此语法，你必须提供多个元素。  
  
## 备注  
 在创建数组后，你可以通过使用 \[ \] 表示法来访问数组的各个元素。  注意，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中的数组是从零开始的。  
  
```javascript  
var my_array = new Array();  
for (i = 0; i < 10; i++) {  
    my_array[i] = i;  
}  
x = my_array[4];  
document.write(x);  
  
// Output: 4  
```  
  
 你可以将无符号 32 位整数传递到 `Array` 构造函数以指定数组的大小。  如果该值为负或不是整数，则会发生运行时错误。  如果你运行以下代码，则应会看到控制台中出现此错误。  
  
```javascript  
var arr = new Array(10);  
document.write(arr.length);  
  
// Output: 10  
  
// Don't do this  
var arr = new Array(-1);  
arr = new Array(1.50);   
```  
  
 如果将单个值传递到 `Array` 构造函数，并且该值不是数字，则将 `length` 属性设置为 1，并且唯一元素的值将成为单个传入的参数。  
  
```npl  
var arr = new Array("one");  
document.write(arr.length);  
document.write("<br/>");  
document.write(arr[0]);  
  
// Output:  
1  
one  
  
```  
  
 JavaScript 数组是稀疏数组，即，并非数组内的所有元素都可能包含数据。  在 JavaScript 中，数组中仅存在实际包含数据的元素。  这将减少数组所使用的内存量。  
  
## 要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 更高版本中已引入以下列表中的某些成员。  有关详细信息，请参阅 [版本信息](../../javascript/reference/javascript-version-information.md)或单个成员对应的文档。  
  
## 属性  
 下表列出了 `Array` 对象的属性。  
  
|属性|描述|  
|--------|--------|  
|[constructor 属性](../../javascript/reference/constructor-property-array.md)|指定创建数组的函数。|  
|[length 属性（数组）](../../javascript/reference/length-property-array-javascript.md)|返回一个整数值，此整数比数组中所定义的最高位元素大 1。|  
|[prototype 属性](../../javascript/reference/prototype-property-array.md)|返回对数组的原型的引用。|  
  
## 函数  
 下表介绍了 `Array` 对象的函数。  
  
|函数|描述|  
|--------|--------|  
|[Array.from 函数](../../javascript/reference/array-from-function-array-javascript.md)|从类似数组的对象或可迭代的对象返回一个数组。|  
|[Array.isArray 函数](../../javascript/reference/array-isarray-function-javascript.md)|返回一个布尔值，该值指示对象是否为数组。|  
|[Array.of 函数](../../javascript/reference/array-of-function-array-javascript.md)|从传入的参数返回一个数组。|  
  
<a name="js56jsobjarraymeth"></a>   
## 方法  
 下表列出了 `Array` 对象的方法。  
  
|方法|描述|  
|--------|--------|  
|[concat 方法（数组）](../../javascript/reference/concat-method-array-javascript.md)|返回由两个数组组合而成的新数组。|  
|[entries 方法](../../javascript/reference/entries-method-array-javascript.md)|返回包含数组的键\/值对的迭代器。|  
|[every 方法](../../javascript/reference/every-method-array-javascript.md)|检查定义的回调函数是否为数组中的所有元素返回 `true`。|  
|[fill 方法](../../javascript/reference/fill-method-array-javascript.md)|使用指定值填充数组。|  
|[filter 方法](../../javascript/reference/filter-method-array-javascript.md)|对数组的每个元素调用定义的回调函数，并返回回调函数为其返回 `true` 的值的数组。|  
|[findIndex 方法](../../javascript/reference/findindex-method-array-javascript.md)|返回满足回调函数中指定的测试条件的第一个数组元素的索引值。|  
|[forEach 方法](../../javascript/reference/foreach-method-array-javascript.md)|为数组中的每个元素调用定义的回调函数。|  
|[hasOwnProperty 方法](../../javascript/reference/hasownproperty-method-object-javascript.md)|返回一个布尔值，该值指示某个对象是否具有指定名称的属性。|  
|[indexOf 方法（数组）](../../javascript/reference/indexof-method-array-javascript.md)|返回某个值在数组中的第一个匹配项的索引。|  
|[isPrototypeOf 方法](../../javascript/reference/isprototypeof-method-object-javascript.md)|返回一个布尔值，该值指示某个对象是否存在于另一个对象的原型链中。|  
|[join 方法](../../javascript/reference/join-method-array-javascript.md)|返回由一个数组的所有元素串联而成的 `String` 对象。|  
|[keys 方法](../../javascript/reference/keys-method-array-javascript.md)|返回包含数组的索引值的迭代器。|  
|[lastIndexOf 方法（数组）](../../javascript/reference/lastindexof-method-array-javascript.md)|返回指定值在数组中的最后一个匹配项的索引。|  
|[map 方法](../../javascript/reference/map-method-array-javascript.md)|对数组的每个元素调用定义的回调函数并返回包含结果的数组。|  
|[pop 方法](../../javascript/reference/pop-method-array-javascript.md)|从数组中移除最后一个元素并将该元素返回。|  
|[propertyIsEnumerable 方法](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|返回一个布尔值，该值指示指定属性是否为对象的一部分且是否可枚举。|  
|[push 方法](../../javascript/reference/push-method-array-javascript.md)|将新元素追加到一个数组中，并返回数组的新长度。|  
|[reduce 方法](../../javascript/reference/reduce-method-array-javascript.md)|通过对数组中的所有元素调用定义的回调函数来累积单个结果。  回调函数的返回值是累积的结果，并且作为对回调函数的下一个调用中的参数提供。|  
|[reduceRight 方法](../../javascript/reference/reduceright-method-array-javascript.md)|通过对数组中的所有元素调用定义的回调函数来按降序顺序累积单个结果。  回调函数的返回值是累积的结果，并且作为对回调函数的下一个调用中的参数提供。|  
|[reverse 方法](../../javascript/reference/reverse-method-javascript.md)|将元素顺序被反转的 `Array` 对象返回。|  
|[shift 方法](../../javascript/reference/shift-method-array-javascript.md)|从数组中移除第一个元素并将返回该元素。|  
|[slice 方法（数组）](../../javascript/reference/slice-method-array-javascript.md)|返回一个数组中的一部分。|  
|[some 方法](../../javascript/reference/some-method-array-javascript.md)|检查定义的回调函数是否为数组的任何元素返回 `true`。|  
|[sort 方法](../../javascript/reference/sort-method-array-javascript.md)|返回一个元素已经进行了排序的 `Array` 对象。|  
|[splice 方法](../../javascript/reference/splice-method-array-javascript.md)|从一个数组中移除元素，如有必要，在所移除元素的位置上插入新元素，并返回所移除的元素。|  
|[toLocaleString 方法](../../javascript/reference/tolocalestring-method-object-javascript.md)|返回使用当前区域设置的字符串。|  
|[toString 方法](../../javascript/reference/tostring-method-array.md)|返回数组的字符串表示形式。|  
|[unshift 方法](../../javascript/reference/unshift-method-array-javascript.md)|在数组的开头插入新元素。|  
|[valueOf 方法](../../javascript/reference/valueof-method-array.md)|获取对数组的引用。|  
|[values 方法](../../javascript/reference/values-method-array-javascript.md)|返回包含数组的值的迭代器。|  
  
## 请参阅  
 [滚动、平移和缩放示例应用](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)