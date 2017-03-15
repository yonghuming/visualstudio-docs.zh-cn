---
title: "Guid 和 Id 的 Visual Studio 菜单 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "visual studio 菜单"
  - "visual studio 组"
  - "id"
  - "现有的菜单"
  - "guid"
  - "菜单"
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Guid 和 Id 的 Visual Studio 菜单
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

本主题枚举菜单和 Visual Studio 菜单栏上的组的 GUID 和 ID 的值。 作为 Visual Studio SDK 的一部分安装的.vsct 文件中定义了这些值。 有关详细信息，请参阅[IDE 定义的命令、 菜单和组](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)。  
  
 有关如何使用.vsct 文件中定义的集成的开发环境 \(IDE\) 对象的详细信息，请参阅 [扩展的菜单和命令](../../extensibility/extending-menus-and-commands.md)。  
  
 菜单和 Visual Studio 菜单栏上的组使用的 GUID `guidSHLMainMenu`。 菜单栏本身的 ID 为 `IDM_VS_TOOL_MAINMENU`。  
  
## 在 Visual Studio 菜单栏上的组  
 若要添加到菜单栏的菜单，其中某个组作为其父项进行设置。  
  
|Group|ID|  
|-----------|--------|  
|文件 \/ 编辑 \/ 视图|IDG\_VS\_MM\_FILEEDITVIEW|  
|重构|IDG\_VS\_MM\_REFACTORING:|  
|Project|IDG\_VS\_MM\_PROJECT|  
|生成|IDG\_VS\_MM\_BUILDDEBUGRUN|  
|格式\/工具|IDG\_VS\_MM\_TOOLSADDINS|  
|窗口 \/ 帮助 \/ 社区|IDG\_VS\_MM\_WINDOWHELP|  
|外接程序|IDG\_VS\_MM\_MACROS|  
|FullScreenBar|IDG\_VS\_MM\_FULLSCREENBAR|  
  
## 在 Visual Studio 菜单栏上的菜单  
 若要将组添加到现有的 Visual Studio 菜单中，将显示以下菜单之一作为其父项进行设置。 此列表中不包括子菜单。  
  
|菜单|ID|  
|--------|--------|  
|文件|IDM\_VS\_MENU\_FILE|  
|Edit|IDM\_VS\_MENU\_EDIT|  
|视图|IDM\_VS\_MENU\_VIEW|  
|重构|IDM\_VS\_MENU\_REFACTORING|  
|Project|IDM\_VS\_MENU\_PROJECT|  
|生成|IDM\_VS\_MENU\_BUILD|  
|格式|IDM\_VS\_MENU\_FORMAT|  
|工具|IDM\_VS\_MENU\_TOOLS|  
|窗口|IDM\_VS\_MENU\_WINDOW|  
|外接程序|IDM\_VS\_MENU\_ADDINS|  
|社区|IDM\_VS\_MENU\_COMMUNITY|  
|帮助|IDM\_VS\_MENU\_HELP|  
  
## 在 Visual Studio 菜单上的组  
 以下列表显示向下查看到直接从菜单中的 Visual Studio 菜单栏的组。 将命令添加到 Visual Studio 菜单的最快方法是其中某个组设置为父级。 在本部分中不显示源自子菜单的组。  
  
### 文件的菜单组  
  
|Group|ID|  
|-----------|--------|  
|新 \/ 打开|IDG\_VS\_FILE\_FILE|  
|添加|IDG\_VS\_FILE\_ADD|  
|解决方案|IDG\_VS\_FILE\_SOLUTION|  
|杂项|IDG\_VS\_FILE\_MISC|  
|保存|IDG\_VS\_FILE\_SAVE|  
|重命名|IDG\_VS\_FILE\_RENAME|  
|浏览者|IDG\_VS\_FILE\_BROWSER|  
|打印|IDG\_VS\_FILE\_PRINT|  
|最近使用过|IDG\_VS\_FILE\_MRU|  
|移动|IDG\_VS\_FILE\_MOVE|  
|Exit|IDG\_VS\_FILE\_EXIT|  
  
### 编辑菜单组  
  
|Group|ID|  
|-----------|--------|  
|撤消\/重做|IDG\_VS\_EDIT\_UNDOREDO|  
|剪切\/复制\/粘贴|IDG\_VS\_EDIT\_CUTCOPY|  
|选择|IDG\_VS\_EDIT\_SELECT|  
|转到|IDG\_VS\_EDIT\_GOTO|  
|查找|IDG\_VS\_EDIT\_FIND|  
|对象|IDG\_VS\_EDIT\_OBJECTS|  
|OLE 谓词|IDG\_VS\_EDIT\_OLEVERBS|  
|也命令|IDG\_VS\_EDIT\_COMMANDWELL|  
  
### 重构菜单组  
  
|Group|ID|  
|-----------|--------|  
|公共|IDG\_REFACTORING\_COMMON|  
|高级|IDG\_REFACTORING\_ADVANCED|  
  
### 查看菜单组  
  
|Group|ID|  
|-----------|--------|  
|窗体代码|IDG\_VS\_VIEW\_FORMCODE|  
|浏览者|IDG\_VS\_VIEW\_BROWSER|  
|定义视图|IDG\_VS\_VIEW\_DEFINEVIEWS|  
|Windows|IDG\_VS\_VIEW\_WINDOWS|  
|架构师 Windows|IDG\_VS\_VIEW\_ARCH\_WINDOWS|  
|组织 Windows|IDG\_VS\_VIEW\_ORG\_WINDOWS|  
|代码浏览器|IDG\_VS\_VIEW\_CODEBROWSENAV\_WINDOWS|  
|适用于开发人员 Windows|IDG\_VS\_VIEW\_DEV\_WINDOWS|  
|工具栏|IDG\_VS\_VIEW\_TOOLBARS|  
|符号|IDG\_VS\_VIEW\_SYMBOLNAVIGATE|  
|导航|IDG\_VS\_VIEW\_NAVIGATE|  
|小导航|IDG\_VS\_VIEW\_SMALLNAVIGATE|  
|对象浏览器|IDG\_VS\_VIEW\_OBJBRWSR|  
|也命令|IDG\_VS\_VIEW\_COMMANDWELL|  
|属性页|IDG\_VS\_VIEW\_PROPPAGES|  
|刷新|IDG\_VS\_VIEW\_REFRESH|  
  
### 项目菜单组  
  
|Group|ID|  
|-----------|--------|  
|杂项添加|IDG\_VS\_PROJ\_MISCADD|  
|添加|IDG\_VS\_PROJ\_ADD|  
|文件夹|IDG\_VS\_PROJ\_FOLDER|  
|卸载\/重新加载|IDG\_VS\_PROJ\_UNLOADRELOAD|  
|引用|IDG\_VS\_PROJ\_REFERENCE|  
|选项|IDG\_VS\_PROJ\_OPTIONS|  
|设置|IDG\_VS\_PROJ\_SETTINGS|  
  
### 生成的菜单组  
  
|Group|ID|  
|-----------|--------|  
|解决方案|IDG\_VS\_BUILD\_SOLUTION|  
|选择|IDG\_VS\_BUILD\_SELECTION|  
|按配置优化|IDG\_VS\_PGO\_SELECTION|  
|杂项|IDG\_VS\_BUILD\_MISC|  
|取消|IDG\_VS\_BUILD\_CANCEL|  
  
### 工具菜单组  
  
|Group|ID|  
|-----------|--------|  
|命令行|IDG\_VS\_TOOLS\_CMDLINE|  
|代码段|IDG\_VS\_TOOLS\_SNIPPETS|  
|对象子集|IDG\_VS\_TOOLS\_OBJSUBSET|  
|选项|IDG\_VS\_TOOLS\_OPTIONS|  
|另外 2|IDG\_VS\_TOOLS\_OTHER2|  
|外部工具|IDG\_VS\_TOOLS\_EXT\_TOOLS|  
|外部自定义项|IDG\_VS\_TOOLS\_EXT\_CUST|  
  
### 窗口的菜单组  
  
|Group|ID|  
|-----------|--------|  
|新建|IDG\_VS\_WINDOW\_NEW|  
|停靠 \/ 关闭|IDG\_VS\_DOCKCLOSE|  
|停靠\/隐藏|IDG\_VS\_DOCKHIDE|  
|排列|IDG\_VS\_WINDOW\_ARRANGE|  
|导航|IDG\_VS\_WINDOW\_NAVIGATION|  
|列表|IDG\_VS\_WINDOW\_LIST|  
  
### 帮助菜单组  
  
|Group|ID|  
|-----------|--------|  
|示例|IDG\_VS\_HELP\_SAMPLES|  
|支持|IDG\_VS\_HELP\_SUPPORT|  
|关于|IDG\_VS\_HELP\_ABOUT|  
  
## Visual Studio 菜单的子菜单  
 下面的层次结构显示在 Visual Studio 菜单栏上的菜单与相关联的子菜单。 因为只有一个组可以有作为其父菜单，每一个子菜单必须向下查看从一组在菜单上，而不是直接从菜单。 有关菜单、 组和子菜单之间的关系的详细信息，请参阅 [将子菜单添加到菜单](../../extensibility/adding-a-submenu-to-a-menu.md)。  
  
> [!NOTE]
>  只有因为它们可以推断出从在 IDE 中，组的命名约定，如下所示，此层次结构中不单独显示这些菜单栏上的 Visual Studio 菜单的名称: IDG\_VS\_*菜单名*\_*组名*。  
  
|父组|子菜单|子组|  
|--------|---------|--------|  
|IDG\_VS\_FILE\_FILE|IDM\_VS\_CSCD\_NEW|IDG\_VS\_FILE\_NEW\_CASCADE|  
||IDM\_VS\_CSCD\_OPEN|IDG\_VS\_FILE\_OPENP\_CASCADE|  
|||IDG\_VS\_FILE\_OPENF\_CASCADE|  
|IDG\_VS\_FILE\_ADD|IDM\_VS\_CSCD\_ADD|IDG\_VS\_FILE\_ADD\_PROJECT\_NEW|  
|||IDG\_VS\_FILE\_ADD\_PROJECT\_EXI|  
|IDG\_VS\_FILE\_MRU|IDM\_VS\_CSCD\_FILEMRU|IDG\_VS\_FILE\_FMRU\_CASCADE|  
||IDM\_VS\_CSCD\_PROJMRU|IDG\_VS\_FILE\_PMRU\_CASCADE|  
|IDG\_VS\_FILE\_MOVE|IDM\_VS\_CSCD\_MOVETOPRJ|IDG\_VS\_FILE\_MOVE\_CASCADE|  
|||IDG\_VS\_FILE\_MOVE\_PICKER|  
|IDG\_VS\_VIEW\_DEV\_WINDOWS|IDM\_VS\_CSCD\_FINDRESULTS|IDG\_VS\_WNDO\_FINDRESULTS|  
||IDM\_VS\_CSCD\_WINDOWS|IDG\_VS\_VIEW\_CALLBROWSER|  
|||IDG\_VS\_WNDO\_OTRWNDWS1...6|  
|||IDG\_VS\_WNDO\_WINDOWS2|  
|IDG\_VS\_VIEW\_TOOLBARS|IDM\_VS\_CSCD\_COMMANDBARS||  
|IDG\_VS\_EDIT\_GOTO|IDM\_VS\_EDITOR\_FIND\_MENU||  
|IDG\_VS\_EDIT\_OBJECTS|IDM\_VS\_CSCD\_MNUDES|IDG\_VS\_MNUDES\_INSERT|  
|||IDG\_VS\_MNUDES\_EDITNAMES|  
||IDM\_VS\_CSCD\_OLEVERBS|IDG\_VS\_EDIT\_OLEVERBS|  
|IDG\_VS\_BUILD\_SELECTION|IDM\_VS\_CSCD\_BUILD|IDG\_VS\_BUILD\_CASCADE|  
|||IDG\_VS\_BUILD\_PROJPICKER|  
||IDM\_VS\_CSCD\_REBUILD|IDG\_VS\_REBUILD\_CASCADE|  
|||IDG\_VS\_REBUILD\_PROJPICKER|  
||IDM\_VS\_CSCD\_PROJONLY|IDG\_VS\_PROJONLY\_CASCADE|  
||IDM\_VS\_CSCD\_CLEAN|IDG\_VS\_CLEAN\_CASCADE|  
|||IDG\_VS\_CLEAN\_PROJPICKER|  
||IDM\_VS\_CSCD\_DEPLOY|IDG\_VS\_DEPLOY\_CASCADE|  
|||IDG\_VS\_DEPLOY\_PROJPICKER|  
|IDG\_VS\_PGO\_SELECTION|IDM\_VS\_CSCD\_PGO\_BUILD|IDG\_VS\_PGO\_BUILD\_CASCADE\_BUILD|  
|||IDG\_VS\_PGO\_BUILD\_CASCADE\_RUN|  
  
## 请参阅  
 [Guid 和 Id 的 Visual Studio 工具栏](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)   
 [Guid 和 Id 的 Visual Studio 命令](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)   
 [Visual Studio 命令表 \(。Vsct\) 文件](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)