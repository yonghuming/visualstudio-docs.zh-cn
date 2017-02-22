---
title: "源控件的设计决策 | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "源代码管理 [Visual Studio SDK]，设计决策"
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 源控件的设计决策
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

，在实现源代码管理时，应为项目考虑以下设计决策。  
  
## 信息是否是共享或私有的?  
 可以进行的最重要的设计决策是哪些信息可共享，以及是私有的。  例如，文件列表该项目的共享，但是，此列表文件，有些用户可能希望有专用文件。  编译器设置共享，但是，启动项目通常是私有的。  设置或纯共享，重写共享或纯粹的私有。  强，专用项目，如解决方案用户选项 \(.suo\) 文件，不签入到 [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]。  确保所有私有信息存储在私有文件 \(如 .suo 文件或您创建的特定私有文件，例如， Visual c\# 中 .csproj.user 文件或 Visual Basic 中 .vbproj.user 文件。  
  
 此决定不包括所有的，可以在一个逐条的基础。  
  
## 该项是否将包括私有文件?  
 另一个重要设计决策是项目结构是否使用专用文件。  私有文件是基础文件是显示在解决方案资源管理器和在签入和签出对话框的隐藏文件。  如果您使用专用文件，请遵循以下准则:  
  
1.  不要将私有文件与项目根节点是，与项目文件。  项目文件必须是一个文件。  
  
2.  当私有文件在项目中，添加、删除或重命名，必须以适当的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> 事件具有指定标志设置为文件是私有文件。  这些事件由环境调用以响应调用相应的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> 方法的项。  
  
3.  此时项目或编辑调用的文件时 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> ，专用文件与该文件不会自动检查。  与父文件。通过专用文件。  该环境将检测和通过在签出 UI 正确隐藏私有文件中的所有文件之间的关系。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [支持的源控件](../../extensibility/internals/supporting-source-control.md)