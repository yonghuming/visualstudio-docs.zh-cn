---
title: "文档窗口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 63cbb04310dba0bddea4f6730a6ae5095cbe2612
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="document-windows"></a>文档窗口
在 Visual Studio 中，*文档窗口*是与多文档界面 (MDI) 窗口相关联的组帧的子窗口。 文档窗口通常用于显示和修改的源代码或文本，但它们也可以承载其他功能的类型。 文档窗口：  
  
-   可以组织中的父 MDI 单独水平或垂直选项卡组中，以便可以同时查看多个文件。  
  
-   可以按任何顺序的父代 MDI 中停靠。  
  
-   可以自由浮动。  
  
-   链接到其他 MDI 窗口的 tab 键顺序。  
  
 分组的命令，在文档窗口选项卡的快捷菜单上可以找到停靠和浮动。  
  
 有关 Visual Studio 中的窗口行为的详细信息，请参阅[自定义窗口布局](../../ide/customizing-window-layouts-in-visual-studio.md)。  
  
## <a name="document-window-implementation"></a>文档窗口的实现  
 通过实现编辑器创建文档窗口。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>接口创建的实例化编辑器一部分的文档窗口。 有关详细信息，请参阅[在编辑器中的旧接口](../../extensibility/legacy-interfaces-in-the-editor.md)。  
  
> [!NOTE]
>  若要提供向后和向前导航点在窗口中的，实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation>接口。 文本编辑器中使用文本标记来标识在文档中的导航点。  
  
## <a name="the-running-document-table"></a>运行文档表  
 IDE 使用正在运行的 document 表 (RDT) 来跟踪每个文档窗口的状态。 RDT 是哪个文档通过 windows 通知的事件，如关闭解决方案时或在编辑文件的机制。 有关详细信息，请参阅[运行 Document 表](../../extensibility/internals/running-document-table.md)。  
  
## <a name="see-also"></a>另请参阅  
 [文档加载延迟](../../extensibility/internals/delayed-document-loading.md)