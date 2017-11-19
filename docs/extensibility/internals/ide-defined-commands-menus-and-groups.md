---
title: "IDE 定义命令、 菜单和组 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 032baaa57dd91cb07eac547da810d16e708f0828
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ide-defined-commands-menus-and-groups"></a>IDE 定义命令、 菜单和组
许多菜单、 命令和命令组已定义以供[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE。 扩展时，可能也包括可供你使用这些命令[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="finding-environment-defined-commands"></a>查找环境定义命令  
 一组四个.vsct 文件中定义的环境命令：  
  
-   SharedCmdDef.vsct  
  
-   SharedCmdPlace.vsct  
  
-   ShellCmdDef.vsct  
  
-   ShellCmdPlace.vsct  
  
 这些文件位于 *\<Visual Studio SDK 安装路径 >*\VisualStudioIntegration\Common\Inc\\。 这些文件提供定义和菜单和可用于你的 VSPackage 的命令表 (.vsct) 配置文件中作为容器你自己的菜单、 组和命令的组的 Guid。  
  
## <a name="in-this-section"></a>本节内容  
 [Visual Studio 菜单中的 GUID 和 ID](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 提供在 Visual Studio 菜单栏上，菜单和它们所包含的组的 GUID 和 ID 值。  
  
 [Visual Studio 工具栏中的 GUID 和 ID](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 提供在 Visual Studio IDE 中的工具栏和它们所包含的组的 GUID 和 ID 值。  
  
 [Visual Studio 命令中的 GUID 和 ID](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 提供由 Visual Studio IDE 的命令的 GUID 和 ID 值。  
  
## <a name="see-also"></a>另请参阅  
 [Visual Studio 命令表 (。Vsct) 文件](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [用于扩展项目系统 IDE 定义命令](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [VSPackage 如何添加用户界面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)