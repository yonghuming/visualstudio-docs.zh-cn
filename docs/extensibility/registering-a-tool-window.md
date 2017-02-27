---
title: "注册一个工具窗口 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "注册托管工具窗口"
  - "工具窗口注册"
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# 注册一个工具窗口
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以注册您使用的工具窗口 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> 和  <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>  
  
## 示例  
  
```c#  
  
      [ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")] [ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)] [ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]  
[ProvideMenuResource(1000, 1)]  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]  
public class PackageToolWindow : Package  
{  
```  
  
 在上面的代码中 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> 注册 Visual Studio 的 PersistedWindowPane 和 DynamicWindowPane 工具窗口。 保留的工具窗口停靠，并使用选项卡式 **解决方案资源管理器**, ，并且动态窗口中将提供默认开始位置和大小。 动态窗口是由暂时的指示在启动时未创建。 这将 DontForceCreate 值写入系统注册表中的 ToolWindows 项。 有关详细信息，请参阅[工具窗口中显示配置](../extensibility/tool-window-display-configuration.md)。