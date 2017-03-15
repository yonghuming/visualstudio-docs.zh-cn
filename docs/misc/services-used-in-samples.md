---
title: "示例中所用的服务 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "示例中显示的服务"
  - "示例，服务"
ms.assetid: 04864feb-9b8b-45c4-8233-fc2ed9273987
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# 示例中所用的服务
在 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 包括的示例使用多个服务。  下面的列表显示使用它们的若干个常用的服务和示例。  
  
> [!NOTE]
>  如果两个引用，并且不支持的示例是可用的，因此，只有引用示例的列表。  
  
|服务|示例|  
|--------|--------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry>|BscEdit， ProjectSubtype|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>|[如何︰ 使用活动日志](../extensibility/how-to-use-the-activity-log.md)|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsAddProjectItemDlg>|BscPrj， FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject>|BscPrj|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChange>|已否决。  请改用 <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|BscEdit， FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext>|Reference.HelpIntegration 示例。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|SingleViewEditor 示例。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors>|SingleViewEditor 示例。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|BscPrj， FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsResourceManager>|Reference.Package、 Reference.ToolWindow 和许多其他示例|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|SingleViewEditor 示例。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|BscPrj， FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Reference.Package、 Reference.ToolWindow 和许多其他示例|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|BscEdt， BscPrj， FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|BscPrj， FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|BscPrj， FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|BscPrj， FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>|SingleViewEditor， BscPrj， FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Reference.ToolWindow、 BscEdit 和许多其他示例|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|BscEdit， FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsWindowFrame>|Reference.ToolWindow|  
  
## 请参阅  
 [可用服务列表](../extensibility/internals/list-of-available-services.md)   
 [服务基础知识](../extensibility/internals/service-essentials.md)