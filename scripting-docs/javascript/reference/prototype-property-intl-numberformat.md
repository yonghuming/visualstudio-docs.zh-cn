---
title: "prototype 属性 (Intl.NumberFormat) |Microsoft 文档"
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
ms.assetid: 7f6a7e26-108b-4b32-97c2-7f96b9252c50
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b037ce7476574252966e17fcf64246beeaaea1e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-intlnumberformat"></a>prototype 属性 (Intl.NumberFormat)
返回一个格式化程序原型的引用。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
numberFormat.prototype  
```  
  
## <a name="remarks"></a>备注  
 `numberFormat`参数是一个格式化程序的名称。  
  
 使用 `prototype` 属性，从而向对象的类提供基本功能集。 对象的新实例“继承”了分配给该对象的原型的行为。  
  
 例如，要将方法添加到返回集的最大元素值的 `Intl.NumberFormat` 对象，则声明该函数，将其添加至 `Intl.NumberFormat.prototype`，然后再使用它。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]