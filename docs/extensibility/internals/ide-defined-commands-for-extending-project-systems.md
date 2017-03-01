---
title: "IDE 定义的命令，用于扩展项目系统 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 8ef8f9d3bd75057708f7e1d380da83a38d7efb4b
ms.lasthandoff: 02/22/2017

---
# <a name="ide-defined-commands-for-extending-project-systems"></a>IDE 定义用于扩展项目系统的命令
当您想要扩展项目系统时，可以使用命令和命令通过提供组[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE。  
  
 以下各节列出的特别有用的扩展项目系统命令项。  
  
## <a name="command-menus"></a>命令菜单  
 下表显示的是您可以让调用项目扩展程序的高级命令很有用的地方的命令菜单。  
  
|命令菜单|说明|  
|------------------|-----------------|  
|IDM_VS_MENU_PROJECT|**项目**顶级菜单。|  
|IDM_VS_TOOL_PROJWIN|**解决方案资源管理器**工具栏。|  
  
## <a name="shortcut-menus"></a>快捷菜单  
 下表显示中选择单个节点时应用的快捷菜单**解决方案资源管理器**，或者有多个同构选择中的时**解决方案资源管理器**，这是所有选定的节点时相同的类型。  
  
|快捷菜单|描述|  
|-------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|在选择项目节点时适用。|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|在选定一个文件时适用。|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|在选定一个文件夹时适用。|  
|IDM_VS_CTXT_WEBREFFOLDER|在选择 Web 引用文件夹时适用。|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|在选择引用根节点名为"引用"时适用。|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|适用于引用节点处于选中状态;其中包括程序集、 COM 和项目的引用。 不包括 Web 引用。|  
  
 下表显示了应用时的快捷菜单中的选定内容**解决方案资源管理器**跨越多个层次结构  
  
|快捷菜单|说明|  
|-------------------|-----------------|  
|IDM_VS_CTXT_XPROJ_SLNPROJ|在当前选定内容中包含了解决方案节点和根项目节点时适用。|  
|IDM_VS_CTXT_XPROJ_SLNITEM|在当前选定内容中包含的解决方案节点和项目项时适用。|  
|IDM_VS_CTXT_XPROJ_MULTIPROJ|在当前所选内容包含仅多个根项目节点时适用。|  
|IDM_VS_CTXT_XPROJ_PROJITEM|在当前所选内容中包含的根项目节点和项目项混合时适用。 此外，所选内容可能包含解决方案节点。|  
|IDM_VS_CTXT_XPROJ_MULTIITEM|当前所选内容包含在解决方案中，多个项目中的项目项或者在同一个项目中选择不同类型的项时适用。|  
  
## <a name="command-groups"></a>命令组  
 下表显示了扩展项目中，并且您可以通过访问时，可以使用的命令组<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>快捷菜单。</xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>  
  
|命令组|说明|  
|-------------------|-----------------|  
|IDG_VS_CTXT_PROJECT_BUILD|用于生成、 重新生成和部署项目的命令。|  
|IDG_VS_CTXT_COMPILELINK|用于编译和链接项目的命令。|  
|IDG_VS_CTXT_PROJECT_CONFIG|将项目配置设置和生成顺序的命令。|  
|IDG_VS_CTXT_PROJECT_ADD|向项目添加项的命令。|  
|IDG_VS_CTXT_PROJECT_START|设置启动项目的 F5 键关联的命令。|  
|IDG_VS_CTXT_PROJECT_SAVE|用于保存项目项的命令。|  
|IDG_VS_CTXT_PROJECT_DEBUG|用于调试的命令。|  
|IDG_VS_CTXT_PROJECT_SCC|用于源代码管理命令。|  
|IDG_VS_CTXT_PROJECT_TRANSFER|命令为剪切、 复制和粘贴操作。|  
|IDG_VS_CTXT_PROJECT_PROPERTIES|提供访问权限的命令**项目属性**对话框。|  
  
## <a name="see-also"></a>另请参阅  
 [VSPackages 迁移将用户界面元素的添加](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [MenuCommands 与OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)   
 [创建可重用的按钮的组](../../extensibility/creating-reusable-groups-of-buttons.md)
