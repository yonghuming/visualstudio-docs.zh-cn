---
title: "constructor 属性 （布尔值） |Microsoft 文档"
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
ms.assetid: b67ca875-23c6-4687-a5ce-1cdd25d1c923
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 091da5342c4713c8eba646a8bd78c315a6a0fa48
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-boolean"></a>constructor 属性（布尔值）
指定创建一个布尔值的函数。  
  
## <a name="syntax"></a>语法  
  
```  
  
boolean.constructor([[value])  
```  
  
#### <a name="parameters"></a>参数  
 `boolean`  
 布尔值的名称。  
  
 `value`  
 可选。 指定的布尔值的值。 这可以是 1 或 0，数字或字符串"true"false"。  
  
## <a name="remarks"></a>备注  
 `constructor`属性包含对布尔对象的实例构造函数的引用。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用构造函数属性。  
  
```JavaScript  
var x = new Boolean("true");  
  
if (x.constructor == Boolean)  
    document.write("Object is a Boolelan.");  
  
// Output:  
// Object is a Boolean.  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]