---
title: "实现命令处理嵌套项目 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a71da10ee4473f3fb542e0ce0e03891d60b75d34
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="implementing-command-handling-for-nested-projects"></a>实现处理嵌套的项目的命令
IDE 将通过传递的命令可以传递<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>和<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>接口向嵌套的项目或父项目可以筛选或重写命令。  
  
> [!NOTE]
>  只有命令通常由父项目可以进行筛选。 命令如**生成**和**部署**由处理 IDE 不能进行筛选。  
  
 以下步骤描述了用于实施命令处理的过程。  
  
## <a name="procedures"></a>过程  
  
#### <a name="to-implement-command-handling"></a>来实现命令处理  
  
1.  当用户选择嵌套的项目或节点中嵌套的项目：  
  
    1.  IDE 调用<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法。  
  
     — 或 —  
  
    1.  如果在层次结构窗口中，如在解决方案资源管理器的快捷方式菜单命令的命令产生 IDE 调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>项目的父方法。  
  
2.  父项目可以检查传递给参数`QueryStatus`，如`pguidCmdGroup`和`prgCmds`，以确定父项目是否应筛选命令。 如果父项目实现来筛选命令，它应设置：  
  
    ```  
    prgCmds[0].cmdf = OLECMDF_SUPPORTED;  
    // make sure it is disabled  
    prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;  
    ```  
  
     然后父项目应返回`S_OK`。  
  
     如果父项目不筛选该命令，它应只返回`S_OK`。 在这种情况下，IDE 自动将命令传送到子项目。  
  
     父项目不需要将命令传送到子项目。 IDE 执行此任务...  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [命令、 菜单和工具栏](../../extensibility/internals/commands-menus-and-toolbars.md)   
 [嵌套项目](../../extensibility/internals/nesting-projects.md)