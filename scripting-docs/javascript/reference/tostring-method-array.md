---
title: "toString 方法 （数组） |Microsoft 文档"
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
ms.assetid: 71fbea85-3e00-41b0-b167-25e4281e5e8a
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6dc7cbf843e47ffc2d21f5a2b1d03c43e675a130
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="tostring-method-array"></a>toString 方法 (Array)
返回数组的字符串表示形式。  
  
## <a name="syntax"></a>语法  
  
```  
  
array.toString()  
```  
  
## <a name="parameters"></a>参数  
 `array`  
 必需。 要将其表示为一个字符串的数组。  
  
## <a name="return-value"></a>返回值  
 数组的字符串表示形式。  
  
## <a name="remarks"></a>备注  
 元素`Array`将转换为字符串。 对结果字符串串联在一起并用逗号隔开。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用**toString**与非数组的方法。  
  
```JavaScript  
var arr = [1, 2, 3, 4];  
var s = arr.toString();  
document.write(s);  
  
// Output: 1,2,3,4  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]