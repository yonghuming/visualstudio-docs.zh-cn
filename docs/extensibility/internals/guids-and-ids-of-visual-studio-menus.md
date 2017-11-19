---
title: "Guid 和 Id 的 Visual Studio 菜单 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- visual studio menus
- visual studio groups
- id
- existing menus
- guid
- menus
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1cf196a227e5cb92cae48dd1eeceace25ffc0295
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>Guid 和 Id 的 Visual Studio 菜单
本主题枚举菜单和 Visual Studio 菜单栏上的组的 GUID 和 ID 的值。 在 Visual Studio SDK 的一部分安装的.vsct 文件中定义这些值。 有关详细信息，请参阅[IDE-Defined 命令、 菜单和组](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)。  
  
 有关如何使用在.vsct 文件中定义的集成的开发环境 (IDE) 对象的详细信息，请参阅[扩展菜单和命令](../../extensibility/extending-menus-and-commands.md)。  
  
 菜单和 Visual Studio 菜单栏上的组使用的 GUID `guidSHLMainMenu`。 菜单栏本身的 ID 为`IDM_VS_TOOL_MAINMENU`。  
  
## <a name="groups-on-the-visual-studio-menu-bar"></a>在 Visual Studio 菜单栏上的组  
 若要将菜单添加到菜单栏中，设置为其父级其中某个组。  
  
|Group|Id|  
|-----------|--------|  
|文件 / 编辑 / 视图|IDG_VS_MM_FILEEDITVIEW|  
|重构|IDG_VS_MM_REFACTORING:|  
|Project|IDG_VS_MM_PROJECT|  
|生成|IDG_VS_MM_BUILDDEBUGRUN|  
|格式/工具|IDG_VS_MM_TOOLSADDINS|  
|窗口 / 帮助 / 社区|IDG_VS_MM_WINDOWHELP|  
|外接程序|IDG_VS_MM_MACROS|  
|FullScreenBar|IDG_VS_MM_FULLSCREENBAR|  
  
## <a name="menus-on-the-visual-studio-menu-bar"></a>在 Visual Studio 菜单栏上的菜单  
 若要将组添加到现有 Visual Studio 菜单中，设置为其父级以下菜单之一。 此列表中不包括子菜单。  
  
|菜单|Id|  
|----------|--------|  
|文件|IDM_VS_MENU_FILE|  
|Edit|IDM_VS_MENU_EDIT|  
|视图|IDM_VS_MENU_VIEW|  
|重构|IDM_VS_MENU_REFACTORING|  
|Project|IDM_VS_MENU_PROJECT|  
|生成|IDM_VS_MENU_BUILD|  
|格式|IDM_VS_MENU_FORMAT|  
|工具|IDM_VS_MENU_TOOLS|  
|窗口|IDM_VS_MENU_WINDOW|  
|外接程序|IDM_VS_MENU_ADDINS|  
|社区|IDM_VS_MENU_COMMUNITY|  
|帮助|IDM_VS_MENU_HELP|  
  
## <a name="groups-on-visual-studio-menus"></a>在 Visual Studio 菜单上的组  
 以下列表显示源自直接菜单在 Visual Studio 菜单栏的组。 将命令添加到 Visual Studio 菜单的最快方法是将其中某个组设置与父项。 在本部分中不显示源自子菜单的组。  
  
### <a name="file-menu-groups"></a>文件菜单组  
  
|Group|Id|  
|-----------|--------|  
|打开新 /|IDG_VS_FILE_FILE|  
|添加|IDG_VS_FILE_ADD|  
|解决方案|IDG_VS_FILE_SOLUTION|  
|杂项|IDG_VS_FILE_MISC|  
|保存|IDG_VS_FILE_SAVE|  
|重命名|IDG_VS_FILE_RENAME|  
|浏览者|IDG_VS_FILE_BROWSER|  
|的|IDG_VS_FILE_PRINT|  
|最近使用|IDG_VS_FILE_MRU|  
|移动|IDG_VS_FILE_MOVE|  
|Exit|IDG_VS_FILE_EXIT|  
  
### <a name="edit-menu-groups"></a>编辑菜单组  
  
|Group|Id|  
|-----------|--------|  
|撤消/重做|IDG_VS_EDIT_UNDOREDO|  
|剪切/复制/粘贴|IDG_VS_EDIT_CUTCOPY|  
|选择|IDG_VS_EDIT_SELECT|  
|转到|IDG_VS_EDIT_GOTO|  
|查找|IDG_VS_EDIT_FIND|  
|对象|IDG_VS_EDIT_OBJECTS|  
|OLE 谓词|IDG_VS_EDIT_OLEVERBS|  
|很好地命令|IDG_VS_EDIT_COMMANDWELL|  
  
### <a name="refactor-menu-groups"></a>重构菜单组  
  
|Group|Id|  
|-----------|--------|  
|公共|IDG_REFACTORING_COMMON|  
|高级|IDG_REFACTORING_ADVANCED|  
  
### <a name="view-menu-groups"></a>查看菜单组  
  
|Group|Id|  
|-----------|--------|  
|窗体代码|IDG_VS_VIEW_FORMCODE|  
|浏览者|IDG_VS_VIEW_BROWSER|  
|定义视图|IDG_VS_VIEW_DEFINEVIEWS|  
|Windows|IDG_VS_VIEW_WINDOWS|  
|架构师 Windows|IDG_VS_VIEW_ARCH_WINDOWS|  
|组织 Windows|IDG_VS_VIEW_ORG_WINDOWS|  
|代码浏览器|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|  
|开发人员 Windows|IDG_VS_VIEW_DEV_WINDOWS|  
|工具栏|IDG_VS_VIEW_TOOLBARS|  
|符号|IDG_VS_VIEW_SYMBOLNAVIGATE|  
|导航|IDG_VS_VIEW_NAVIGATE|  
|小型导航|IDG_VS_VIEW_SMALLNAVIGATE|  
|对象浏览器|IDG_VS_VIEW_OBJBRWSR|  
|很好地命令|IDG_VS_VIEW_COMMANDWELL|  
|属性页|IDG_VS_VIEW_PROPPAGES|  
|刷新|IDG_VS_VIEW_REFRESH|  
  
### <a name="project-menu-groups"></a>项目菜单组  
  
|Group|Id|  
|-----------|--------|  
|杂项添加|IDG_VS_PROJ_MISCADD|  
|添加|IDG_VS_PROJ_ADD|  
|文件夹|IDG_VS_PROJ_FOLDER|  
|卸载/重新加载|IDG_VS_PROJ_UNLOADRELOAD|  
|参考|IDG_VS_PROJ_REFERENCE|  
|选项|IDG_VS_PROJ_OPTIONS|  
|设置|IDG_VS_PROJ_SETTINGS|  
  
### <a name="build-menu-groups"></a>生成菜单组  
  
|Group|Id|  
|-----------|--------|  
|解决方案|IDG_VS_BUILD_SOLUTION|  
|选择|IDG_VS_BUILD_SELECTION|  
|按配置优化|IDG_VS_PGO_SELECTION|  
|杂项|IDG_VS_BUILD_MISC|  
|取消|IDG_VS_BUILD_CANCEL|  
  
### <a name="tools-menu-groups"></a>工具菜单组  
  
|Group|Id|  
|-----------|--------|  
|命令行|IDG_VS_TOOLS_CMDLINE|  
|代码段|IDG_VS_TOOLS_SNIPPETS|  
|对象子集|IDG_VS_TOOLS_OBJSUBSET|  
|选项|IDG_VS_TOOLS_OPTIONS|  
|其他 2|IDG_VS_TOOLS_OTHER2|  
|外部工具|IDG_VS_TOOLS_EXT_TOOLS|  
|外部自定义项|IDG_VS_TOOLS_EXT_CUST|  
  
### <a name="window-menu-groups"></a>窗口菜单组  
  
|Group|Id|  
|-----------|--------|  
|新建|IDG_VS_WINDOW_NEW|  
|停靠/关闭|IDG_VS_DOCKCLOSE|  
|停靠/隐藏|IDG_VS_DOCKHIDE|  
|排列|IDG_VS_WINDOW_ARRANGE|  
|导航|IDG_VS_WINDOW_NAVIGATION|  
|列表|IDG_VS_WINDOW_LIST|  
  
### <a name="help-menu-groups"></a>帮助菜单组  
  
|Group|Id|  
|-----------|--------|  
|示例|IDG_VS_HELP_SAMPLES|  
|支持|IDG_VS_HELP_SUPPORT|  
|关于|IDG_VS_HELP_ABOUT|  
  
## <a name="submenus-of-visual-studio-menus"></a>Visual Studio 菜单的子菜单  
 以下层次结构显示了与在 Visual Studio 菜单栏上的菜单的子菜单。 由于仅允许一组可作为其父菜单，因此每个子菜单必须降从组在菜单上，而不是直接从菜单。 有关菜单、 组和子菜单之间的关系的详细信息，请参阅[将子菜单添加到菜单](../../extensibility/adding-a-submenu-to-a-menu.md)。  
  
> [!NOTE]
>  在 Visual Studio 菜单栏上的菜单的名称不单独显示，此层次结构中因为它们可以推断出从在 IDE 中的组的命名约定，如下所示： IDG_VS_*菜单名称*_*组名称*.  
  
|父组|子菜单|子组|  
|------------------|-------------|------------------|  
|IDG_VS_FILE_FILE|IDM_VS_CSCD_NEW|IDG_VS_FILE_NEW_CASCADE|  
||IDM_VS_CSCD_OPEN|IDG_VS_FILE_OPENP_CASCADE|  
|||IDG_VS_FILE_OPENF_CASCADE|  
|IDG_VS_FILE_ADD|IDM_VS_CSCD_ADD|IDG_VS_FILE_ADD_PROJECT_NEW|  
|||IDG_VS_FILE_ADD_PROJECT_EXI|  
|IDG_VS_FILE_MRU|IDM_VS_CSCD_FILEMRU|IDG_VS_FILE_FMRU_CASCADE|  
||IDM_VS_CSCD_PROJMRU|IDG_VS_FILE_PMRU_CASCADE|  
|IDG_VS_FILE_MOVE|IDM_VS_CSCD_MOVETOPRJ|IDG_VS_FILE_MOVE_CASCADE|  
|||IDG_VS_FILE_MOVE_PICKER|  
|IDG_VS_VIEW_DEV_WINDOWS|IDM_VS_CSCD_FINDRESULTS|IDG_VS_WNDO_FINDRESULTS|  
||IDM_VS_CSCD_WINDOWS|IDG_VS_VIEW_CALLBROWSER|  
|||IDG_VS_WNDO_OTRWNDWS1...6|  
|||IDG_VS_WNDO_WINDOWS2|  
|IDG_VS_VIEW_TOOLBARS|IDM_VS_CSCD_COMMANDBARS||  
|IDG_VS_EDIT_GOTO|IDM_VS_EDITOR_FIND_MENU||  
|IDG_VS_EDIT_OBJECTS|IDM_VS_CSCD_MNUDES|IDG_VS_MNUDES_INSERT|  
|||IDG_VS_MNUDES_EDITNAMES|  
||IDM_VS_CSCD_OLEVERBS|IDG_VS_EDIT_OLEVERBS|  
|IDG_VS_BUILD_SELECTION|IDM_VS_CSCD_BUILD|IDG_VS_BUILD_CASCADE|  
|||IDG_VS_BUILD_PROJPICKER|  
||IDM_VS_CSCD_REBUILD|IDG_VS_REBUILD_CASCADE|  
|||IDG_VS_REBUILD_PROJPICKER|  
||IDM_VS_CSCD_PROJONLY|IDG_VS_PROJONLY_CASCADE|  
||IDM_VS_CSCD_CLEAN|IDG_VS_CLEAN_CASCADE|  
|||IDG_VS_CLEAN_PROJPICKER|  
||IDM_VS_CSCD_DEPLOY|IDG_VS_DEPLOY_CASCADE|  
|||IDG_VS_DEPLOY_PROJPICKER|  
|IDG_VS_PGO_SELECTION|IDM_VS_CSCD_PGO_BUILD|IDG_VS_PGO_BUILD_CASCADE_BUILD|  
|||IDG_VS_PGO_BUILD_CASCADE_RUN|  
  
## <a name="see-also"></a>另请参阅  
 [Guid 和 Id 的 Visual Studio 工具栏](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)   
 [Guid 和 Id 的 Visual Studio 命令](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)   
 [Visual Studio 命令表格 (.Vsct) 文件](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)