---
title: "constructor 属性 （日期） |Microsoft 文档"
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
ms.assetid: 5db153a1-788b-4a61-bfc8-2d2ec38f36ea
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 798064117e17ee5b2988396de3c6545917373b10
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-date"></a>constructor 属性（日期）
指定创建日期的函数。  
  
## <a name="syntax"></a>语法  
  
```  
  
date.constructor  
```  
  
## <a name="remarks"></a>备注  
 所需`date`是 date 对象的名称。  
  
 `constructor` 属性是具有原型的每个对象的原型的成员。 `constructor` 属性包含对构造特定对象实例的函数的引用。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用构造函数属性。  
  
```JavaScript  
var x = new Date("Hi");  
  
if (x.constructor == Date)  
    document.write("Object is a date.");  
  
// Output:  
// Object is a date.  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]