---
title: "文档窗口 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio SDK，文档窗口"
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# 文档窗口
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在 Visual Studio 中， *文档窗口* 是与多文档界面 \(MDI\) 窗口相关联的组帧的子窗口。 文档窗口通常用于显示和修改源代码或文本，但它们也可以承载其他功能的类型。 文档窗口︰  
  
-   可以组织中的父 MDI 单独的水平或垂直选项卡组中，以便可以同时查看多个文件。  
  
-   可以按任意顺序在父 MDI 停靠。  
  
-   可以自由浮动。  
  
-   将链接到其他 MDI 窗口 tab 键顺序。  
  
 用于分组的命令，一个文档窗口选项卡的快捷菜单上可以找到停靠和浮动。  
  
 有关在 Visual Studio 中的窗口行为的详细信息，请参阅 [自定义窗口布局](../../ide/customizing-window-layouts-in-visual-studio.md)。  
  
## 文档窗口实现  
 通过实现一个编辑器创建文档窗口。<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 接口用于创建实例化一个编辑器的一部分的文档窗口。 有关更多信息，请参见[在编辑器中的旧接口](../../extensibility/legacy-interfaces-in-the-editor.md)。  
  
> [!NOTE]
>  若要提供向后和向前导航点在窗口中的，实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> 接口。 文本编辑器中使用文本标记来标识文档中的导航点。  
  
## 运行 Document 表  
 IDE 将使用正在运行的 document 表 \(RDT\) 来跟踪每个文档窗口的状态。 RDT 是哪个文档通过 windows 通知的事件，如关闭时，一种解决方案或编辑文件的机制。 有关更多信息，请参见[正在运行的 Document 表](../../extensibility/internals/running-document-table.md)。  
  
## 请参阅  
 [延迟加载文档](../../extensibility/internals/delayed-document-loading.md)