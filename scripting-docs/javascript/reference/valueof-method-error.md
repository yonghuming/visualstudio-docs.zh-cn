---
title: "valueOf 方法 （错误） |Microsoft 文档"
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
ms.assetid: ca25c57d-c9ad-445b-8235-561390de680c
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c7593937530469142265f8081bf3472fa4935aee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="valueof-method-error"></a>valueOf 方法（错误）
返回错误的字符串的值。  
  
## <a name="syntax"></a>语法  
  
```  
  
error.valueOf()  
```  
  
#### <a name="parameters"></a>参数  
 `error`对象是错误的任何实例。  
  
## <a name="return-value"></a>返回值  
 字符串"错误:"加上的错误消息。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`valueOF`日期的方法。  
  
```JavaScript  
var myError = new Error();  
myError.message = "This is an error.";  
var value = myError.valueOf();  
document.write(value);  
  
// Output: Error: This is an error.  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]