---
title: "prototype 属性 (WeakMap) |Microsoft 文档"
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
ms.assetid: d28b8a9b-38c9-443d-9586-7cc74784bd99
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cc1bff0d62f2aeb8d6fb78a0857f287fb34078c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-weakmap"></a>prototype 属性 (WeakMap)
返回对原型的引用`WeakMap`对象。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
weakmap.prototype  
```  
  
## <a name="remarks"></a>备注  
 `weakmap`自变量是名称`WeakMap`对象。  
  
 使用 `prototype` 属性，从而向对象的类提供基本功能集。 对象的新实例“继承”了分配给该对象的原型的行为。  
  
 例如，若要将方法添加到`WeakMap`返回的最大元素的值的对象`WeakMap`，声明该函数，将其添加到`WeakMap.prototype`，然后使用它。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]