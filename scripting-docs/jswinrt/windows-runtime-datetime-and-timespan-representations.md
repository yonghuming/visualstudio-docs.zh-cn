---
title: "Windows 运行时 DateTime 和 TimeSpan 表示形式 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime dates and times
- TimeSpan [JavaScript]
- DateTime [JavaScript]
ms.assetid: 9743e9ac-9054-463e-8264-427183e4905f
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3d7c394b57eb0215e3dff857d935b367e602c2b0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="windows-runtime-datetime-and-timespan-representations"></a>Windows 运行时 DateTime 和 TimeSpan 表示形式
JavaScript 对于日期和时间的表示形式与 Windows 运行时版本不同。 Windows 运行时 [DateTime](http://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx) 结构在 JavaScript 中表示为 [Date](../javascript/reference/date-object-javascript.md)，具有与 `DateTime` 数据（具有与 JavaScript `Date` 不同的范围和精度）相匹配的后备存储。 如果你修改此自定义 `Date` 对象，它将成为标准 JavaScript `Date` 并且失去精度。 JavaScript `Date` 值可以传递到 Windows 运行时 `DateTime` 并且将接受范围校验，这可能导致封送异常。  
  
 Windows 运行时 [TimeSpan](http://msdn.microsoft.com/en-us/c5defb66-819c-4796-85b5-07ed249a5d86) 结构将转换为毫秒并且作为 JavaScript 数值返回。  
  
## <a name="see-also"></a>另请参阅  
 [在 JavaScript 中使用 Windows 运行时](../jswinrt/using-the-windows-runtime-in-javascript.md)