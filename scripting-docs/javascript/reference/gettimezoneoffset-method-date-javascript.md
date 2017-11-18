---
title: "getTimezoneOffset 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getTimeZoneOffset
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- getTimezoneOffset method
- time zones [Visual Studio]
ms.assetid: 58ee22b0-4688-45bd-a337-cc23119b09ce
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e49a3c8b7060e6097300f8aaf99b2ef869833018
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="gettimezoneoffset-method-date-javascript"></a>getTimezoneOffset 方法 (Date) (JavaScript)
获取本地计算机上的时间与协调世界时 (UTC) 之间的差异以分钟为单位。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.getTimezoneOffset()   
```  
  
#### <a name="parameters"></a>参数  
 所需 `dateObj` 引用是 `Date` 对象。  
  
## <a name="return-value"></a>返回值  
 返回当前计算机上的时间之间的分钟数 (客户端计算机或从服务器脚本中的服务器计算机中调用此方法) 和 UTC。 如果当前计算机的本地时间是 UTC （例如，太平洋夏令时） 和负后面，如果当前计算机的本地时间早于 UTC （例如，日语），它为正。 如果在纽约的服务器已连接则洛杉矶中的客户端年 12 月 1 日，`getTimezoneOffset`返回 480，如果客户端或执行 300 如果在服务器上执行。  
  
## <a name="remarks"></a>备注  
  
## <a name="example"></a>示例  
 下面的示例显示如何使用 `getTimezoneOffset` 方法。  
  
```JavaScript  
var date =  new Date();  
var minutes = date.getTimezoneOffset();  
  
if (minutes < 0)  
    document.write(minutes / 60 + " hours after UTC");  
else  
    document.write(minutes / 60 + " hours before UTC");  
  
// Output (for example, where local time is PST):   
7 hours before UTC  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [getTime 方法 (Date)](../../javascript/reference/gettime-method-date-javascript.md)