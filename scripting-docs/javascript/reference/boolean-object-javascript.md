---
title: "Boolean 对象 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: boolean_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Boolean object
- Boolean data type, Boolean object
ms.assetid: d67748f2-7bf5-4889-8269-e777616cc5f0
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20695376e4935cf6ddc34f30e373df19575ece3f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="boolean-object-javascript"></a>Boolean 对象 (JavaScript)
创建新的布尔值。  
  
## <a name="syntax"></a>语法  
  
```  
  
boolObj = new Boolean([boolValue])  
```  
  
## <a name="parameters"></a>参数  
 `boolObj`  
 必需。 `Boolean` 对象分配到的变量名称。  
  
 `boolValue`  
 可选。 新对象的初始布尔值。 如果`boolvalue`省略，或者它是`false`，0， `null`， `NaN`，或为空字符串，Boolean 对象的初始值是`false`。 否则，默认值是`true`。  
  
## <a name="remarks"></a>备注  
 `Boolean`对象是布尔数据类型的包装器。 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]隐式使用`Boolean`对象每当布尔数据类型转换为`Boolean`对象。  
  
 极少数情况下实例化`Boolean`显式对象。  
  
## <a name="properties"></a>属性  
 下表列出了 `Boolean` 对象的属性。  
  
|属性|描述|  
|--------------|-----------------|  
|[constructor 属性](../../javascript/reference/constructor-property-boolean.md)|指定创建一个布尔值的函数。|  
|[prototype 属性](../../javascript/reference/prototype-property-boolean.md)|为布尔值返回对原型的引用。|  
  
<a name="js56jsobjarraymeth"></a>   
## <a name="methods"></a>方法  
 下表列出了 `Boolean` 对象的方法。  
  
|方法|描述|  
|------------|-----------------|  
|[toString 方法](../../javascript/reference/tostring-method-boolean-1.md)|返回一个布尔值的字符串表示。|  
|[valueOf 方法](../../javascript/reference/valueof-method-boolean.md)|获取为布尔值的引用。|  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]