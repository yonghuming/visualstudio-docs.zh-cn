---
title: "如何: 承载在另一个编辑器编辑器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，旧的承载嵌套的编辑器"
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何: 承载在另一个编辑器编辑器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 Visual Studio 通过指定承载的窗口承载一个编辑隔开的为父窗口。  为此，请将子窗架的参数 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> 和 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> 。  
  
### 设置窗架承载编辑  
  
1.  指定一个编辑器将作为一个承载的编辑通过创建子窗口窗格。  
  
     此窗格是编辑的文本将为的位置。  
  
2.  使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 或 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> 方法，创建承载的编辑器。  
  
3.  通过将这些属性设置在编辑器中承载的编辑窗架实现的 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> 和 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> 属性作为参数传递给 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> 方法，它们。  
  
     如果需要检索这些参数，请将这些属性是 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 方法。  
  
4.  调用编写包含的编辑 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> 方法。  
  
     编辑器显示一个包含版本的承载的窗格。  
  
## 可靠编程  
 在 Visual Studio team edition 的 **应用程序设计器** 的处于编辑窗架的示例承载其他编辑器的架构师。  **应用程序设计器** 承载其右侧窗格的其他设计器上。  一个设计器面板 \(或 **属性** 页\) 每个包含的设计器添加到包含的窗架。