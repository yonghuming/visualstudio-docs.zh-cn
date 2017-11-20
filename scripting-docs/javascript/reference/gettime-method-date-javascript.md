---
title: "getTime 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getTime
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- GetTime method
- time method
ms.assetid: f0da1d4e-337c-497d-9205-093defbc6d3d
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a31e542445e89a0e2f3364d36ae44f8d2d4cf9bb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="gettime-method-date-javascript"></a>getTime 方法 (Date) (JavaScript)
获取以毫秒为单位的时间值。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.getTime()   
```  
  
#### <a name="parameters"></a>参数  
 所需 `dateObj` 引用是 `Date` 对象。  
  
## <a name="return-value"></a>返回值  
 返回自 1970 年 1 月 1 日午夜和中的时间值之间的毫秒数`Date`对象。 日期范围是从 1970 年 1 月 1 日午夜的任何一侧大约 285616 年。 负数表示 1970 年之前的日期。  
  
## <a name="remarks"></a>备注  
 在执行多个日期和时间计算时，你可能想要在一天、 小时或分钟定义变量等于的毫秒数。 例如:   
  
```JavaScript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
```  
  
 请参阅[计算日期和时间 (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)详细了解如何使用`getTime`方法。  
  
## <a name="example"></a>示例  
 下面的示例显示如何使用 `getTime` 方法。  
  
```JavaScript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
  
date = new Date("1/1/2001");  
var time = date.getTime();  
  
document.write(Math.round(time / day) + " days from 1/1/1970 to 1/1/2001");  
  
// Output: 11323 days from 1/1/1970 to 1/1/2001  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [setTime 方法 (Date)](../../javascript/reference/settime-method-date-javascript.md)