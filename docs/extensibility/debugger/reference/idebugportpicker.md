---
title: "IDebugPortPicker | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugPortPicker 接口"
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPortPicker
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

表示选择的端口自定义 UI。  
  
## 语法  
  
```  
IDebugPortPicker : IUnknown  
```  
  
## 实现者说明  
 此接口由端口提供程序实现。  端口提供程序通过将其显示为 CLSID 和点 `metricPortPickerCLSID` 定义它们的端口选择器指标中显示的 CLSID。  
  
## 方法  
 下表显示 `IDebugPortPicker`方法。  
  
|方法|说明|  
|--------|--------|  
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|显示允许用户选择端口的指定对话框。|  
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|设置服务提供程序。|  
  
## 要求  
 标题:Msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll