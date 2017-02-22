---
title: "实现处理嵌套项目命令 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "嵌套的项目中，实现命令处理"
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# 实现处理嵌套项目命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

IDE 会通过 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 和 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 接口对嵌套的项目的命令，或者父项目可筛选或重写命令。  
  
> [!NOTE]
>  父项目通常处理的唯一的顺序进行筛选。  由 IDE 处理指令例如 **Build** 和 **Deploy** 无法筛选。  
  
 以下步骤介绍实现的命令处理。  
  
## 过程  
  
#### 为实现 " 命令处理  
  
1.  当用户选择一个嵌套的项目或一个节点在嵌套的项:  
  
    1.  IDE 调用 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 方法。  
  
     \- 或 \-  
  
    1.  如果命令则源自一层次结构 " 窗口，例如在解决方案资源管理器中的一个快捷菜单命令， IDE 对项的父级的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> 方法。  
  
2.  父项目可以检查将传递的参数传递给 `QueryStatus`，例如 `pguidCmdGroup` 和 `prgCmds`，确定父项是否应筛选命令。  如果父项目实现筛选命令，则应设置:  
  
    ```  
    prgCmds[0].cmdf = OLECMDF_SUPPORTED;  
    // make sure it is disabled  
    prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;  
    ```  
  
     单击父项应返回 `S_OK`。  
  
     如果父项目不筛选命令，则应返回 `S_OK`。  在这种情况下， IDE 会自动路由命令为子项。  
  
     父项目不必路由命令到子项。  IDE 执行此任务。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [命令、 菜单和工具栏](../../extensibility/internals/commands-menus-and-toolbars.md)   
 [嵌套项目](../../extensibility/internals/nesting-projects.md)