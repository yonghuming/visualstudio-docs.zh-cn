---
title: "includes 方法 （字符串） (JavaScript) |Microsoft 文档"
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
ms.assetid: 2639e4e5-23ba-424a-80ea-be067a4cd65e
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 848143b64d3e32452aea41f08b6f5c57879d3e17
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="includes-method-string-javascript"></a>includes 方法（字符串）(JavaScript)
返回一个布尔值，该值指示传入字符串是否包含在字符串对象中。  
  
## <a name="syntax"></a>语法  
  
```  
stringObj.includes(substring [, position]);  
```  
  
#### <a name="parameters"></a>参数  
 `stringObj`  
 必需。 要对照测试的字符串对象。  
  
 `substring`  
 必需。 要测试的字符串。  
  
 `position`  
 可选。 字符串对象中要测试的以 0 开头的第一个字符的位置。  
  
## <a name="return-value"></a>返回值  
 如果传入的字符串包含在字符串对象中，则 `includes` 方法返回 `true`；否则返回 `false`。  
  
## <a name="remarks"></a>备注  
  
## <a name="example"></a>示例  
  
```JavaScript  
// Returns true   
"abcde".includes("cd")  
"abcde".includes("cd", 2)  
  
// Returns false  
"abcde".includes("CD")  
"abcde".includes("cd", 3)  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]