---
title: "如何: 提供适用于 Windows 的自动化 | Microsoft Docs"
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
  - "自动化 [Visual Studio SDK]，工具窗口"
  - "工具窗口自动化"
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# 如何: 提供适用于 Windows 的自动化
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

可以提供自动为文档和工具窗口。  提供自动化可行，每当您在窗口中使用自动化对象可用，因此，该环境已不提供一个现成的自动化对象，，因为它执行与任务列表。  
  
## 工具窗口的自动化  
 环境将处于工具窗口提供自动化通过返回标准 <xref:EnvDTE.Window> 对象遵循以下过程声明:  
  
#### 为工具窗口提供自动化  
  
1.  通过使用 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> 环境称为 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 方法作为 `VSFPROPID` 参数来获取 `Window` 对象。  
  
2.  当调用方请求的 VSPackage 特定的自动化对象的工具窗口通过 <xref:EnvDTE.Window.Object%2A>时，环境调用 `IExtensibleObject`、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>或 `IDispatch` 接口的 `QueryInterface` 。  `IExtensibleObject` 和 `IVsExtensibleObject` 提供一个 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> 方法。  
  
3.  当环境然后调用通过 `NULL`时的 `GetAutomationObject` 方法，请通过将一些特定对象响应。  
  
4.  如果调用 `IExtensibleObject` 和 `IVsExtensibleObject` 的 `QueryInterface` 失败，则环境调用 `IDispatch`的 `QueryInterface` 。  
  
## 自动为文档窗口  
 标准 <xref:EnvDTE.Document> 对象从该环境还可用，不过，可编辑通过实现 `IExtensibleObject` 接口和响应其 `T:EnvDTE.Document` 对象的实现 `GetAutomationObject`。  
  
 此外，可编辑提供了一些特定的自动化对象，检索通过 <xref:EnvDTE.Document.Object%2A> 方法，通过实现 `IVsExtensibleObject` 或 `IExtensibleObject` 接口。  [VSSDK 示例](../../misc/vssdk-samples.md) 提供 RTF 文档特定的自动化对象。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>