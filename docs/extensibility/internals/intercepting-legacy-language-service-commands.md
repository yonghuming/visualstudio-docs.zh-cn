---
title: "截获旧语言服务命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "截获语言服务的命令"
  - "语言服务，侦听命令"
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 截获旧语言服务命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，可以截获命令的语言服务文本视图原本处理。  对于文本视图不托管语言特定的行为非常有用。  可以通过将一个或多个截获这些命令顺序筛选器将从语言服务的文本视图。  
  
## 获取和路由命令  
 命令筛选器是 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 对象的监视器特定字符序列或键顺序。  您可以将多个命令筛选器与单个文本视图。  每个文本视图维护指挥系统筛选器。  在创建新的命令筛选器后，可以添加筛选器到相应的文本视图的链。  
  
 调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> 方法将命令添加筛选器到链。  当您调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>时， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 返回通过指令筛选器无法处理的其他指令筛选器。  
  
 有命令处理的以下选项:  
  
-   处理命令然后传递命令到个链中的下一条指令筛选器。  
  
-   处理命令，并且不管命令到下一条指令筛选器。  
  
-   不处理命令，但是，传递命令到下一条指令筛选器。  
  
-   忽略命令。  不处理它在当前筛选器和不传递给下筛选器。  
  
 有关哪些命令的信息语言服务应处理，请参见 [重要的语言服务筛选器的命令](../../extensibility/internals/important-commands-for-language-service-filters.md)。