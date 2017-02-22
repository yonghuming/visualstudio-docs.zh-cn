---
title: "IDebugProperty3 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty3"
helpviewer_keywords: 
  - "IDebugProperty3 接口"
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProperty3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口提供支持:  
  
-   检索一个任意长度的字符串与属性。  
  
-   关联的唯一 ID 与属性。  
  
-   检索自定义浏览器中列出的属性。  
  
-   设置属性的值能够报告任何出现的错误。  
  
## 语法  
  
```  
IDebugProperty3 : IDebugProperty2  
```  
  
## 实现者说明  
 调试引擎 \(DE\)实现在同一对象的此接口实现提供的 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 为长字符串、属性 ID 和自定义浏览器支持。  
  
## 调用方的说明  
 调用 `IDebugProperty2` 接口的 [QueryInterface](/visual-cpp/atl/queryinterface) 获取此接口。  
  
## 方法按 Vtable 顺序  
 除了从 `IDebugProperty2` 继承的方法之外，`IDebugProperty3` 接口还公开下面的方法。  
  
|方法|说明|  
|--------|--------|  
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|返回字符串的长度与属性。|  
|[GetStringChars](../Topic/IDebugProperty3::GetStringChars.md)|返回在用户提供的缓冲区的字符串。|  
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|创建此属性的唯一 ID。|  
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|销毁此属性的唯一 ID。|  
|[GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md)|返回自定义浏览器数此属性可查看。|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|返回自定义浏览器的列表此属性可查看。|  
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|，如果任何发生错误，设置此属性的值，则返回错误消息。|  
  
## 备注  
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) 是会议的首选方式调试管理器 \(SDM\)设置属性值。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)