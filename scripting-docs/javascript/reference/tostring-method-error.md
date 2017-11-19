---
title: "toString 方法 （错误） |Microsoft 文档"
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
ms.assetid: 5d6d9712-c06d-4b31-9bc9-e46f6bb5cd38
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d774ff8c0f5338f4178b2262bf8ac8cadc074453
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="tostring-method-error"></a>toString 方法（错误）
返回的字符串表示形式出错。  
  
## <a name="syntax"></a>语法  
  
```  
  
error.toString()  
```  
  
## <a name="parameters"></a>参数  
 `date`  
 必需。 要将其表示为一个字符串的错误。  
  
## <a name="return-value"></a>返回值  
 返回"错误:"加上的错误消息。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`toString`方法并显示错误。  
  
```JavaScript  
var myError = new Error();  
myError.message = "My Error";  
var errorString = myError.toString();  
document.write(errorString);  
  
// Output: Error: My Error  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]