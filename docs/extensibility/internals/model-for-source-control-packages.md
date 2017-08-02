---
title: "源代码管理包的模型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "源控件 [Visual Studio SDK]，模型"
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 源代码管理包的模型
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

以下方式表示源控件实现的示例。  在设计时，您会看到必须实现的接口和必须调用的环境服务。  与所有服务，实际上调用通过服务中获取特定的接口的方法。  类的名称标识使其更易于查看源代码管理如何执行。  
  
 ![SCC&#95;TUP 示例](~/extensibility/internals/media/scc_tup.gif "SCC\_TUP")  
示例源代码管理项目  
  
## 接口  
 可以实现新项目的源代码管理输入 Visual Studio 使用下表中显示的接口列表。  
  
|接口|使用|  
|--------|--------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|调用和编辑项目，然后在保存或更改 \(已更新之前\) 文件。  使用 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> 服务，此接口访问。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|调用项目请求权限添加，请移除或写入文件或目录重命名为。  ，在批准，添加、移除或向事件重命名完成时，此接口由项目还调用以通知该环境。  使用 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> 服务，它捕获。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|实现由任何实体将通知注册，该项目添加时，对或移除一个文件或目录重命名。  为事件通知的注册，请调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|调用项目到具有源代码管理包注册并获取有关源代码管理状态的信息。  使用 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> 服务，此接口访问。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|实现由项目响应源代码管理请求的文件信息和获取有关项目文件所需的源代码管理设置。|  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 [支持的源控件](../../extensibility/internals/supporting-source-control.md)