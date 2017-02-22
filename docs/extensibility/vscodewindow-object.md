---
title: "VSCodeWindow 对象 | Microsoft Docs"
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
  - "VSCodeWindow"
helpviewer_keywords: 
  - "视图 [Visual Studio SDK]，VSCodeWindow 对象"
  - "VsCodeWindow 对象"
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# VSCodeWindow 对象
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

代码窗口为专用的文档窗口中可以包含一个或多个文本视图通常 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> 对象。  
  
 体系结构方面，代码窗口中是位于窗口框架的文档窗口。 就功能而言，代码窗口则只需具有其他功能的文档窗口。 在多文档界面 \(MDI\) 模式下，代码窗口是 MDI 子框架。 有关详细信息，请参阅[通过使用旧 API 的自定义代码窗口](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)。  
  
 下表包含中的接口 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> 对象。  
  
|方法|描述|  
|--------|--------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|提供了通用访问机制，以定位全局唯一标识符 \(GUID\) 标识一个服务。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|表示包含一个或多个代码视图的多文档界面 \(MDI\) 子。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|填满窗口框架。|  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Figures Edit](http://msdn.microsoft.com/zh-cn/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)