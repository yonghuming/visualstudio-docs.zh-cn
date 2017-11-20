---
title: "getVarDate 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getVarDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- getVarDate method
- dates, VT_DATE format
ms.assetid: 561238de-5c91-45a3-b839-a16910d3a1cf
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d21394a5381653997a6b406537a6bde4f5266b97
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="getvardate-method-date-javascript"></a>getVarDate 方法 (Date) (JavaScript)
从 `Date` 对象返回 VT_DATE 值。  
  
> [!WARNING]
>  只有 Internet Explorer 支持此方法。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.getVarDate()   
```  
  
#### <a name="parameters"></a>参数  
 所需 `dateObj` 引用是 `Date` 对象。  
  
## <a name="return-value"></a>返回值  
 返回 VT_DATE 值。  
  
## <a name="remarks"></a>备注  
 JavaScript 代码与 COM 对象、ActiveX 对象或其他可接收和返回 VT_DATE 格式日期值的对象交互时，使用 `getVarDate` 方法。 其中包括 Visual Basic 和 Visual Basic Scripting Edition (VBScript) 中的对象。 返回值的实际格式取决于区域设置。  
  
## <a name="requirements"></a>要求  
 在以下文档模式中受支持：Quirks、Internet Explorer 6 标准模式、Internet Explorer 7 标准模式、Internet Explorer 8 标准模式、Internet Explorer 9 标准模式和 Internet Explorer 10 标准模式。 在 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 应用中不受支持。 请参阅 [版本信息](../../javascript/reference/javascript-version-information.md)。  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [getDate 方法 (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Date.parse 函数](../../javascript/reference/date-parse-function-javascript.md)