---
title: "有关卸载和重新加载嵌套项目的注意事项 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "嵌套的项目中，卸载并重装"
  - "项目 [Visual Studio SDK]，卸载并重装嵌套"
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 有关卸载和重新加载嵌套项目的注意事项
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在实现嵌套的项目类型时，则必须执行附加步骤，在卸载并重新加载项目时。  正确地向侦听器添加到解决方案事件，必须正确地引发 `OnBeforeUnloadProject` 和 `OnAfterLoadProject` 事件。  
  
 必须引发这些事件这样的一个原因是您不希望源代码管理 \(SCC\)从服务器删除项并将它们作为新的操作，如果具有从 SCC 的 `Get` 操作。  在这种情况下，新文件中加载不足 SCC，您必须卸载并重新加载所有文件，以防它们是不同的。  SCC 调用 `ReloadItem`。  实现该调用是删除该项并再次重新创建它通过实现 `IVsFireSolutionEvents` 调用 `OnBeforeUnloadProject` 和 `OnAfterLoadProject`。  当您执行此实现时， SCC 通告的项目中临时删除并重新添加了。  因此， SCC 不对该项目，如同将项目从服务器实际上已删除然后再次添加了。  
  
## 重新加载项目  
 若要支持重载嵌套的项目，则执行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> 方法。  在 `ReloadItem`的实现，请关闭嵌套的项并重新创建它们。  
  
 通常，当重新加载项目时， IDE 会引发 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> 和 `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` 事件。  但是，对于要删除并重新加载的嵌套项目，父项目启动处理，而不是 IDE。  因为父项目不会引发解决方案事件，并且， IDE 没有有关进程的初始化的信息，不引发任何事件。  
  
 处理此过程，项目对 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> 接口的 `QueryInterface`<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> 接口的父级。  `IVsFireSolutionEvents` 具有通知 IDE 引发事件 `OnBeforeUnloadProject` 卸载该嵌套的项目功能，然后引发 `OnAfterLoadProject` 事件重新加载同一个项目。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [嵌套项目](../../extensibility/internals/nesting-projects.md)