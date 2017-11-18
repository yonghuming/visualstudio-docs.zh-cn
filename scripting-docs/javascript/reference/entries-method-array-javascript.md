---
title: "entries 方法 (Array) (JavaScript) |Microsoft 文档"
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
ms.assetid: 9bc46afb-74d2-4f99-8c95-f46475acf21d
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff1e32ba0782d637ea1418daf5b3a56203d7e34b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="entries-method-array-javascript"></a>entries 方法（数组）(JavaScript)
返回一个迭代器，它返回数组的键/值对。  
  
## <a name="syntax"></a>语法  
  
```  
arrayObj.entries();  
```  
  
#### <a name="parameters"></a>参数  
 `arrayObj`  
 必需。 数组对象。  
  
## <a name="remarks"></a>备注  
  
## <a name="example"></a>示例  
 下面的示例演示如何获取数组的键/值对。  
  
```JavaScript  
var entries = ["a", "b", "c"].entries();  
// entries.next().value == [0, "a"]  
// entries.next().value == [1, "b"]  
// entries.next().value == [2, "c"]   
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]