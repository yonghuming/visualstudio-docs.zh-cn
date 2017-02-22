---
title: "如何: 触发事件; 当编辑器失去焦点 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，旧的激发失去焦点的事件"
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# 如何: 触发事件; 当编辑器失去焦点
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

有时知道需要的编辑何时失去在窗架的焦点。  例如，在中，在编辑器不再侧重于之后，可能需要从代码窗口中提取代码。  下面的过程提供有关步骤按照接收编辑失去焦点的通知。  
  
### 激发事件以响应编辑失去焦点  
  
1.  通过从 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>的一 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> 对象将监视选择事件。  
  
2.  调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> 并为其 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> 对象。  
  
3.  在对 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>的调用中，找到 `elementid==SEID_WindowFrame`。  
  
4.  测试两点的 `varValueNew` 参数:  
  
    1.  要查找的窗架。  
  
    2.  程序丢失选定内容到该窗架的点。