---
title: "toString 方法 (Date) |Microsoft 文档"
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
ms.assetid: d3037289-d805-409b-8781-045c59a2c404
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67b6dce74e3796c8b54431b56809473e3c5e59a5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="tostring-method-date"></a>toString 方法（日期）
返回的字符串表示形式的日期。 字符串的格式取决于区域设置。 适用于美国英语 (en-我们)，它是，如下所示：  
  
 *一周中的天**月**天**小时*:*分钟*:*第二个* *时区**年*  
  
## <a name="syntax"></a>语法  
  
```  
  
date.toString()  
```  
  
## <a name="parameters"></a>参数  
 `date`  
 必需。 要以字符串形式表示的日期。  
  
## <a name="return-value"></a>返回值  
 返回的字符串表示形式的日期。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`toString`日期的方法。  
  
```JavaScript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
var dateString = myDate.toString();  
document.write(dateString);  
  
// Output: <date>  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]