---
title: "Object.defineProperties 函数 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Object.defineProperties function [JavaScript]
ms.assetid: 2dae6658-a1c9-495f-bf06-bb3e964e6762
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 65f4f5817a105283a26c971bd98869d000ca0bc2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="objectdefineproperties-function-javascript"></a>Object.defineProperties 函数 (JavaScript)
将一个或多个属性添加到对象，和/或修改现有属性的特性。  
  
## <a name="syntax"></a>语法  
  
```  
  
object.defineProperties(object, descriptors)  
```  
  
## <a name="parameters"></a>参数  
 `object`  
 必需。 在其上添加或修改的属性对象。 这可能是一个本机[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]对象或 DOM 对象。  
  
 `descriptors`  
 必需。 A[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]对象，其中包含一个或多个描述符对象。 每个描述符对象描述数据属性或访问器属性。  
  
## <a name="return-value"></a>返回值  
 已传递给函数的对象。  
  
## <a name="remarks"></a>备注  
 `descriptors`自变量是一个对象，包含一个或多个描述符对象。  
  
 A*数据属性*是一个属性，可以存储和检索一个值。 数据属性描述符包含`value`属性，`writable`和 / 或属性。 有关详细信息，请参阅[数据属性和访问器属性](../../javascript/advanced/data-properties-and-accessor-properties.md)。  
  
 *访问器属性*调用用户提供的函数，每次设置或检索属性值。 访问器属性描述符包含`set`属性，`get`和 / 或属性。  
  
 如果对象已具有指定的名称的属性，则会修改属性特性。 有关详细信息，请参阅[Object.defineProperty 函数](../../javascript/reference/object-defineproperty-function-javascript.md)。  
  
 若要创建一个对象，并将属性添加到新的对象，可以使用[Object.create 函数](../../javascript/reference/object-create-function-javascript.md)。  
  
## <a name="adding-properties"></a>添加属性  
 在下面的示例中，`Object.defineProperties`函数向用户定义的对象添加数据属性和访问器属性。  
  
 该示例使用对象文字创建`descriptors`对象`newDataProperty`和`newAccessorProperty`描述符对象。  
  
```JavaScript  
var newLine = "<br />";  
  
var obj = {};  
Object.defineProperties(obj, {  
    newDataProperty: {  
        value: 101,  
        writable: true,  
        enumerable: true,  
        configurable: true  
    },  
    newAccessorProperty: {  
        set: function (x) {  
            document.write("in property set accessor" + newLine);  
            this.newaccpropvalue = x;  
        },  
        get: function () {  
            document.write("in property get accessor" + newLine);  
            return this.newaccpropvalue;  
        },  
        enumerable: true,  
        configurable: true  
    }});  
  
// Set the accessor property value.  
obj.newAccessorProperty = 10;  
document.write ("newAccessorProperty value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// newAccessorProperty value: 10  
  
```  
  
 前面的示例中，如下面的示例中添加文本的对象而不是动态属性。  
  
```JavaScript  
  
var newLine = "<br />";  
  
// Create the descriptors object.  
var descriptors = new Object();  
  
// Add a data property descriptor to the descriptors object.  
descriptors.newDataProperty = new Object();  
descriptors.newDataProperty.value = 101;  
descriptors.newDataProperty.writable = true;  
descriptors.newDataProperty.enumerable = true;  
descriptors.newDataProperty.configurable = true;  
  
// Add an accessor property descriptor to the descriptors object.  
descriptors.newAccessorProperty = new Object();  
descriptors.newAccessorProperty.set = function (x) {  
    document.write("in property set accessor" + newLine);  
    this.newaccpropvalue = x;  
};  
descriptors.newAccessorProperty.get = function () {  
    document.write("in property get accessor" + newLine);  
    return this.newaccpropvalue;  
};  
descriptors.newAccessorProperty.enumerable = true;  
descriptors.newAccessorProperty.configurable = true;  
  
// Call the Object.defineProperties function.  
var obj = new Object();  
Object.defineProperties(obj, descriptors);  
  
// Set the accessor property value.  
obj.newAccessorProperty = 10;  
document.write ("newAccessorProperty value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// newAccessorProperty value: 10  
  
```  
  
## <a name="modifying-properties"></a>修改属性  
 若要修改的对象的属性特性，添加以下代码。 `Object.defineProperties`函数修改`writable`属性`newDataProperty`，并修改`enumerable`属性`newAccessorProperty`。 它将添加`anotherDataProperty`到对象因为该属性名称不存在。  
  
```  
Object.defineProperties(obj, {  
    newDataProperty: { writable: false },  
    newAccessorProperty: { enumerable: false },  
    anotherDataProperty: { value: "abc" }  
});  
```  
  
## <a name="requirements"></a>要求  
 支持在 Internet Explorer 9 标准中，Internet Explorer 10 标准和[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]应用。 支持数据的 DOM 对象仅，Internet Explorer 8 否则不支持。  
  
## <a name="see-also"></a>另请参阅  
 [Object.getOwnPropertyDescriptor 函数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Object.getOwnPropertyNames 函数](../../javascript/reference/object-getownpropertynames-function-javascript.md)   
 [Object.defineProperty 函数](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Object.create 函数](../../javascript/reference/object-create-function-javascript.md)   
 [Object 对象](../../javascript/reference/object-object-javascript.md)