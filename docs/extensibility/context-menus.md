---
title: "上下文菜单 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，旧的上下文菜单"
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 上下文菜单
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

上下文菜单显示，当用户在工作区并清除时的活动区域右击，释放鼠标右键。  
  
## 编辑上下文菜单  
 通过截获 `ECMD_SHOWCONTEXTMENU`，语言服务可以控制在编辑器中显示的上下文菜单。  显示拥有上下文菜单，请处理此命令，在传递到 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>。  如果未处理此命令，则 IDE 显示为编辑器提供的标准上下文菜单。  还可以控制上下文菜单的内容根据每个标记的基类型。  有关此操作的更多信息，请参见[使用旧 API 使用文本标记](../extensibility/using-text-markers-with-the-legacy-api.md)和[截获旧语言服务命令](../extensibility/internals/intercepting-legacy-language-service-commands.md)。  
  
## 请参阅  
 [开发语言服务](../extensibility/internals/developing-a-legacy-language-service.md)   
 [扩展的菜单和命令](../extensibility/extending-menus-and-commands.md)