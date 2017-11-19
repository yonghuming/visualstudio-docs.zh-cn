---
title: "用于扩展项目系统 IDE 定义命令 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a5e6f4caf8466100763b6a4ae11f6760a3d4c655
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>用于扩展项目系统 IDE 定义命令
如果你想要扩展项目系统，可以使用命令和命令提供的组[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE。  
  
 下列部分列出用于扩展项目系统尤其有用的命令项目。  
  
## <a name="command-menus"></a>命令菜单  
 下表显示的是你可以放置调用项目扩展程序的高级命令有用位置的命令菜单。  
  
|命令菜单|描述|  
|------------------|-----------------|  
|IDM_VS_MENU_PROJECT|**项目**顶级菜单。|  
|IDM_VS_TOOL_PROJWIN|**解决方案资源管理器**工具栏。|  
  
## <a name="shortcut-menus"></a>快捷菜单  
 下表显示中选择单个节点时应用的快捷菜单**解决方案资源管理器**，或在多个同构选择时**解决方案资源管理器**，即时所选的所有节点都均为相同的类型。  
  
|快捷菜单|描述|  
|-------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|在选择项目节点时适用。|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|在选定一个文件时适用。|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|在选择文件夹时适用。|  
|IDM_VS_CTXT_WEBREFFOLDER|在选择 Web 引用文件夹时适用。|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|在选择引用根节点称为"引用"时适用。|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|将应用时引用节点处于选中状态;其中包括程序集、 COM 和项目的引用。 不包括 Web 引用。|  
  
 下表显示时应用的快捷菜单中的选定**解决方案资源管理器**跨越多个层次结构  
  
|快捷菜单|描述|  
|-------------------|-----------------|  
|IDM_VS_CTXT_XPROJ_SLNPROJ|在当前所选内容包含的解决方案节点和根项目节点时适用。|  
|IDM_VS_CTXT_XPROJ_SLNITEM|在当前所选内容包含解决方案节点和项目项时适用。|  
|IDM_VS_CTXT_XPROJ_MULTIPROJ|在当前所选内容包含仅多个根项目节点时适用。|  
|IDM_VS_CTXT_XPROJ_PROJITEM|在当前所选内容包含多种根项目节点和项目项时适用。 此外，所选内容可能包含解决方案节点。|  
|IDM_VS_CTXT_XPROJ_MULTIITEM|适用时当前所选内容包含从解决方案中、 多个项目的项目项或同一项目中选择的不同类型的项目时。|  
  
## <a name="command-groups"></a>命令组  
 下表显示你扩展项目中，并且可以通过访问时，可以使用的命令组<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>快捷菜单。  
  
|命令组|描述|  
|-------------------|-----------------|  
|IDG_VS_CTXT_PROJECT_BUILD|用于构建、 重新生成和部署项目的命令。|  
|IDG_VS_CTXT_COMPILELINK|用于编译和链接项目的命令。|  
|IDG_VS_CTXT_PROJECT_CONFIG|将项目配置设置和生成顺序的命令。|  
|IDG_VS_CTXT_PROJECT_ADD|向项目添加项的命令。|  
|IDG_VS_CTXT_PROJECT_START|设置启动项目与 F5 的键关联的命令。|  
|IDG_VS_CTXT_PROJECT_SAVE|用于保存项目项的命令。|  
|IDG_VS_CTXT_PROJECT_DEBUG|用于调试的命令。|  
|IDG_VS_CTXT_PROJECT_SCC|用于源代码管理命令。|  
|IDG_VS_CTXT_PROJECT_TRANSFER|命令进行剪切、 复制和粘贴操作。|  
|IDG_VS_CTXT_PROJECT_PROPERTIES|提供对访问权限的命令**项目属性**对话框。|  
  
## <a name="see-also"></a>另请参阅  
 [Vspackage 如何添加用户界面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [MenuCommands 与OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)   
 [创建可重复使用的按钮组](../../extensibility/creating-reusable-groups-of-buttons.md)