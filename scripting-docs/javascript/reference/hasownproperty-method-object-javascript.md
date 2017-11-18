---
title: "hasOwnProperty 方法 (Object) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: hasOwnProperty
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: hasOwnProperty method
ms.assetid: 3eb69d69-486f-4792-9518-4452aef369ca
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 397b68fc87bf730886c928e099037ff0183a7f63
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="hasownproperty-method-object-javascript"></a>hasOwnProperty 方法 (Object) (JavaScript)
确定对象是否具有具有指定名称的属性。  
  
## <a name="syntax"></a>语法  
  
```  
  
object.hasOwnProperty(proName)  
```  
  
## <a name="parameters"></a>参数  
 `object`  
 必需。 对象的实例。  
  
 `proName`  
 必需。 属性名称的字符串值。  
  
## <a name="remarks"></a>备注  
 `hasOwnProperty`方法返回`true`如果`object`具有指定名称、 属性`false`如果它不存在。 此方法不会检查对象的原型链; 中的属性属性必须是对象本身的成员。  
  
 对 Internet Explorer 8 和更低版本的主机对象不支持此属性。  
  
## <a name="example"></a>示例  
 在下面的示例中，所有`String`对象共享一个公共 split 方法。 以下代码将显示**false**和**true**。  
  
```JavaScript  
var s = new String("Sample");  
document.write(s.hasOwnProperty("split"));  
document.write("<br/>");  
document.write(String.prototype.hasOwnProperty("split"));  
  
// Output:  
// false  
// true  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [In 运算符](../../javascript/reference/in-operator-decrementjavascript.md)