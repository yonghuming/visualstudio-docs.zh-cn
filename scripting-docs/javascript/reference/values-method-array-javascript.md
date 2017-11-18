---
title: "values 方法 (Array) (JavaScript) |Microsoft 文档"
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
ms.assetid: b20699d6-f8b1-4744-8551-9e81c82850dd
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1a90dfd81ae8baf6590f69f0126adc97d42c20e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="values-method-array-javascript"></a>values 方法（数组）(JavaScript)
返回一个迭代器，它返回数组的值。  
  
## <a name="syntax"></a>语法  
  
```  
arrayObj.values();  
```  
  
#### <a name="parameters"></a>参数  
 `arrayObj`  
 必需。 数组对象。  
  
## <a name="remarks"></a>备注  
  
## <a name="example"></a>示例  
 下面的示例演示如何获取数组的值。  
  
```JavaScript  
var v = ["a", "b", "c"].values();  
// v.next().value == "a"  
// v.next().value == "b"  
// v.next().value == "c"   
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]