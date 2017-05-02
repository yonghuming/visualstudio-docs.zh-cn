---
title: "IDispError 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDispError 接口"
ms.assetid: 3dc7b55e-94ba-4669-b20a-1e011f2d07cf
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError 接口
提供上下文详细错误信息。  
  
> [!NOTE]
>  此接口未实现。  
  
 除了从 `IUnknown` 继承的方法之外，`IDispError` 接口还公开下面的方法。  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|[IDispError::QueryErrorInfo](../../winscript/reference/idisperror-queryerrorinfo.md)|检索错误信息的特定类型。|  
|[IDispError::GetNext](../../winscript/reference/idisperror-getnext.md)|检索下 `IDispError` 对象。|  
|[IDispError::GetHresult](../../winscript/reference/idisperror-gethresult.md)|从 `IDispError` 对象检索错误代码。|  
|[IDispError::GetSource](../../winscript/reference/idisperror-getsource.md)|返回引发此错误的选件类或应用程序的相关语言的编程标识符。|  
|[IDispError::GetHelpInfo](../../winscript/reference/idisperror-gethelpinfo.md)|如果可能返回帮助文件的路径和解释错误主题的上下文ID，。|  
|[IDispError::GetDescription](../../winscript/reference/idisperror-getdescription.md)|返回错误的文本说明。|