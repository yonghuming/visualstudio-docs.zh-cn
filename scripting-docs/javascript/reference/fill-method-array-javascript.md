---
title: "fill 方法 (Array) (JavaScript) |Microsoft 文档"
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
ms.assetid: 11526627-c0bb-4157-a8c4-0a039079b4a1
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4546bafb3fa3a8c242b8b7ef4ef2863ea86bf179
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="fill-method-array-javascript"></a>fill 方法（数组）(JavaScript)
使用指定值填充数组。  
  
## <a name="syntax"></a>语法  
  
```  
arrayObj.fill(value [ , start [ , end ] ]);  
```  
  
#### <a name="parameters"></a>参数  
 `arrayObj`  
 必需。 数组对象。  
  
 `value`  
 必需。 用于填充数组的值。  
  
 `start`  
 可选。 用于填充数组值的起始索引。 默认值为 0。  
  
 `end`  
 可选。 用于填充数组值的结束索引。 默认值是 `this` 对象的 length 属性。  
  
## <a name="remarks"></a>备注  
 如果`start`为负，`start`将被视为`length` + `start`，其中`length`是数组的长度。 如果`end`为负，`end`将被视为`length` + `end`。  
  
## <a name="example"></a>示例  
 以下代码示例用值填充数组。  
  
```JavaScript  
[0, 0, 0].fill(7, 1);  
// Array contains [0,7,7]  
  
[0, 0, 0].fill(7);  
// Array contains [7,7,7]  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]