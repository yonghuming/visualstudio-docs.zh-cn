---
title: "Visual Studio Shell |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 63b8420b3941114f8edd1e494c8469ae4b81ba79
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]外壳是中的集成主代理[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 Shell 提供必要的功能，以允许 Vspackage 共享公共服务。 因为的体系结构目标[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]是在 Vspackage，vest 主功能命令行程序是一个框架，以提供基本功能，并且支持 Vspackage 其组件之间的跨通信。  
  
## <a name="shell-responsibilities"></a>Shell 职责  
 在 shell 具有以下密钥责任：  
  
-   （通过 COM 接口） 支持基本的用户界面 (UI) 元素。 其中包括默认菜单和工具栏、 文档窗口框架或多文档界面 (MDI) 子窗口和工具窗口框架和停靠支持。  
  
-   维护正在运行的正在运行的文档表 (RDT) 中的所有当前打开的文档的列表，来协调文档的持久性，以及若要确保不能打开该一个文档，在多个单向方法，或以不兼容的方式。  
  
-   支持的命令路由和命令处理的接口， `IOleCommandTarget`。  
  
-   在适当的时间加载 Vspackage。 延迟加载 VSPackage 对是 shell 的必需的提高性能。  
  
-   管理某些共享服务，如<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>，该属性提供基本 shell 功能和<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>，其中提供基本窗口化功能。  
  
-   管理解决方案 (.sln) 文件。 解决方案包含组的相关项目，类似于 Visual c + + 6.0 中的工作区 (.dsw) 文件。  
  
-   跟踪 shell 范围内所选内容、 上下文和货币。 Shell 跟踪以下类型的项：  
  
    -   当前项目  
  
    -   当前项目项或 ItemID 当前<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
    -   为当前所选内容**属性**窗口或`SelectionContainer`  
  
    -   UI 上下文 Id 或控制的可见性命令、 菜单和工具栏的 CmdUIGuids  
  
    -   当前处于活动状态的元素，如活动窗口、 文档和撤消管理器  
  
    -   驱动器动态帮助的用户上下文属性  
  
 Shell 还调解安装的 Vspackage 和当前服务之间的通信。 它支持 shell 的核心功能，使数据库可用于在中的集成的所有 Vspackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 这些核心功能包括以下各项：  
  
-   **有关**对话框框和初始屏幕  
  
-   **添加新功能和添加现有项**对话框  
  
-   **类视图**窗口和**对象浏览器**  
  
-   **引用**对话框  
  
-   **文档大纲**窗口  
  
-   **动态帮助**窗口  
  
-   **查找**和**替换**  
  
-   **打开项目**和**打开的文件**对话框上**新建**菜单  
  
-   **选项**对话框中，在**工具**菜单  
  
-   **属性**窗口  
  
-   **解决方案资源管理器**  
  
-   **任务列表**窗口  
  
-   **工具箱**  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>   
 [VSPackage](../../extensibility/internals/vspackages.md)