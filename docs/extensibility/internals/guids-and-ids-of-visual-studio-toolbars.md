---
title: "Guid 和 Id 的 Visual Studio 工具栏 | Microsoft Docs"
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
  - "visual studio 组"
  - "工具栏"
  - "visual studio 工具栏"
  - "id"
  - "toolgar 组"
  - "工具窗口工具栏"
  - "guid"
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Guid 和 Id 的 Visual Studio 工具栏
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

本主题枚举在 Visual Studio 集成开发环境 \(ide\) 包括工具栏的 GUID 和 ID 值 \(IDE\)，因此，它们包含组。  这些值在为 Visual Studio SDK 的一部分，安装的 .vsct 文件中定义的。  有关更多信息，请参见 [IDE 定义的命令、 菜单和组](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)。  
  
> [!NOTE]
>  许多工具栏可用于 Visual Studio 未定义的由 Visual Studio，并且，它们的 GUID 和 ID 值不是公共的。  本主题列出了 Visual Studio SDK .vsct 文件定义的工具栏。  
  
 有关如何安装的更多信息与 .vsct 文件中定义的 IDE 对象，请参见 [扩展的菜单和命令](../../extensibility/extending-menus-and-commands.md)。  
  
 Visual Studio IDE 提供的默认工具栏使用 GUID `guidSHLMainMenu`，除此之外，否则通过使用 GUID 的位置: ID 语法。  
  
## IDE 工具栏  
 Visual Studio IDE 提供以下工具栏。  工具栏可以通过选择行显示在 **工具** 菜单的 **工具栏** 子菜单。  在工具窗口的工具栏本节中包含。  
  
 只有组可以放置直接工具栏。  若要添加组，请将其父至工具栏的 GUID 和 ID。  若要将按钮添加到工具栏，请将其父到工具栏上的某个组。  
  
|工具栏|ID|  
|---------|--------|  
|标准版|IDM\_VS\_TOOL\_STANDARD|  
|Build|IDM\_VS\_TOOL\_BUILD|  
|文本编辑器|IDM\_VS\_TOOL\_TEXTEDITOR|  
|调试|guidVSDebugGroup: IDM\_DEBUG\_TOOLBAR|  
|" 调试位置|guidVSDebugGroup: IDM\_DEBUG\_CONTEXT\_TOOLBAR|  
  
### 特定工具栏  
 这些工具栏由 Visual Studio IDE 中定义的，但是，它们提供专用功能，并且不承载命令组。  
  
|工具栏|ID|  
|---------|--------|  
|添加命令|IDM\_VS\_TOOL\_ADDCOMMAND|  
|未定义|IDM\_VS\_TOOL\_UNDEFINED|  
|XML 架构|IDM\_VS\_TOOL\_SCHEMA|  
|XML 数据|IDM\_VS\_TOOL\_DATA|  
  
## IDE 工具栏的组  
 若要将按钮添加到标准工具栏，找到以下组之一个作为其父级。  按父工具栏排序。  
  
### 标准工具栏组  
  
|名称|ID|  
|--------|--------|  
|保存\/打开|IDG\_VS\_TOOLSB\_SAVEOPEN|  
|剪切\/复制|IDG\_VS\_TOOLSB\_CUTCOPY|  
|撤消\/重做|IDG\_VS\_TOOLSB\_UNDOREDO|  
|运行\/生成|IDG\_VS\_TOOLSB\_RUNBUILD|  
|搜索|IDG\_VS\_TOOLSB\_SEARCH|  
|窗口|IDG\_VS\_TOOLSB\_WINDOWS|  
|新窗口|IDG\_VS\_TOOLSB\_NEWWINDOWS|  
|加载\/保存|IDG\_VS\_WINDOWUI\_LOADSAVE|  
|测量仪|IDG\_VS\_TOOLSB\_GAUGE|  
  
### 生成工具栏组  
  
|名称|ID|  
|--------|--------|  
|生成栏|IDG\_VS\_BUILDBAR|  
|取消|IDG\_VS\_BUILD\_CANCEL|  
  
### 文本编辑器 " 工具栏组  
  
|名称|ID|  
|--------|--------|  
|完成|IDM\_VS\_TOOL\_TEXTEDITOR|  
|缩进|IDG\_VS\_EDITTOOLBAR\_INDENT|  
|注释|IDG\_VS\_EDITTOOLBAR\_COMMENT|  
|书签|IDG\_VS\_EDITTOOLBAR\_TEMPBOOKMARKS|  
  
### 调试工具栏组  
  
|名称|ID|  
|--------|--------|  
|执行|IDM\_DEBUG\_TOOLBAR|  
|单步执行|IDG\_DEBUG\_TOOLBAR\_STEPPING|  
|Watch|IDG\_DEBUG\_TOOLBAR\_WATCH|  
|窗口|IDG\_DEBUG\_TOOLBAR\_WINDOWS|  
  
### 调试位置 " 工具栏组  
  
|名称|ID|  
|--------|--------|  
|" 调试位置|IDG\_DEBUG\_CONTEXT\_TOOLBAR|  
  
## 工具窗口工具栏  
 工具栏可能会直接应用于 IDE 或在工具窗口 \(如 **解决方案资源管理器**。  由于工具窗口。 .vsct 文件未定义，工具窗口工具栏尚未定义的父级。  相反，它们在代码中放置。  下表显示在 IDE 中的工具窗口的工具栏及其包含的命令组。  
  
> [!NOTE]
>  工具栏和组使用 GUID `guidSHLMainMenu`，除此之外，否则通过使用 GUID 的位置: ID 语法。  其中 GUID 为工具栏指定，它也适用于放置该工具栏的组。  
  
|工具窗口|工具栏|Groups|  
|----------|---------|------------|  
|解决方案资源管理器|IDM\_VS\_TOOL\_PROJWIN|IDG\_VS\_PROJ\_TOOLBAR1..5|  
|服务器资源管理器|guid\_SE\_MenuGroup: IDM\_SE\_TOOLBAR\_SERVEREXPLORER|IDG\_SE\_TOOLBAR\_REFRESH|  
|属性|IDM\_VS\_TOOL\_PROPERTIES|IDG\_VS\_PROPERTIES\_SORT<br /><br /> IDG\_VS\_PROPERTIES\_PAGES|  
|类视图|IDM\_VS\_TOOL\_CLASSVIEW|IDG\_VS\_CLASSVIEW\_FOLDERS<br /><br /> IDG\_VS\_CLASSVIEW\_SEARCH<br /><br /> IDG\_VS\_CLASSVIEW\_SETTINGS|  
|类视图|IDM\_VS\_TOOL\_CLASSVIEW\_GO|IDG\_VS\_CLASSVIEW\_SEAR CH2|  
|对象浏览器|IDM\_VS\_TOOL\_OBJBROWSER|IDG\_VS\_OBJBROWSER\_SUBSETS<br /><br /> IDG\_VS\_OBJBROWSER\_SEARCH<br /><br /> IDG\_VS\_OBJBROWSER\_ADDREFERENCE<br /><br /> IDG\_VS\_OBJBROWSER\_BROWSERSETTINGS|  
|对象浏览器|IDM\_VS\_TOOL\_OBJECT\_BROWSER\_GO|IDG\_VS\_OBJBROWSER\_SEAR CH2|  
|Output|IDM\_VS\_TOOL\_OUTPUTWINDOW|IDG\_VS\_OUTPUTWINDOW\_SELECT<br /><br /> IDG\_VS\_OUTPUTWINDOW\_GOTO<br /><br /> IDG\_VS\_OUTPUTWINDOW\_NEXTPREV<br /><br /> IDG\_VS\_OUTPUTWINDOW\_CLEAR<br /><br /> IDG\_VS\_OUTPUTWINDOW\_WORDWRAP|  
|查找和替换|IDM\_VS\_TOOL\_UNIFIEDFIND|IDG\_VS\_FINDTAB<br /><br /> IDG\_VS\_REPLACETAB|  
|查找结果 1|IDM\_VS\_TOOL\_FINDRESULTS1|IDG\_VS\_FINDRESULTS1\_GOTO<br /><br /> IDG\_VS\_FINDRESULTS1\_NEXTPREV<br /><br /> IDG\_VS\_FINDRESULTS1\_CLEAR<br /><br /> IDG\_VS\_FINDRESULTS1\_STOPFIND|  
|查找结果 2|IDM\_VS\_TOOL\_FINDRESULTS2|IDG\_VS\_FINDRESULTS2\_GOTO<br /><br /> IDG\_VS\_FINDRESULTS2\_NEXTPREV<br /><br /> IDG\_VS\_FINDRESULTS2\_CLEAR<br /><br /> IDG\_VS\_FINDRESULTS2\_STOPFIND|  
|Snippet|IDM\_VS\_TOOL\_SNIPPETMENUS|IDG\_VS\_SNIPPET\_REPL<br /><br /> IDG\_VS\_SNIPPET\_REF<br /><br /> IDG\_VS\_SNIPPET\_PROP|  
|书签|IDM\_VS\_TOOL\_BOOKMARKWIND|IDG\_VS\_BWNEWFOLDER<br /><br /> IDG\_VS\_BWNEXTBM<br /><br /> IDG\_VS\_BWNEXTBMF<br /><br /> IDG\_VS\_BWENABLE<br /><br /> IDG\_VS\_BWDELETE|  
|任务列表|IDM\_VS\_TOOL\_TASKLIST|IDG\_VS\_TASKLIST\_PROVIDERLIST|  
|用户任务|IDM\_VS\_TOOL\_USERTASKS|IDG\_VS\_TASKLIST\_PROVIDERLIST<br /><br /> IDG\_VS\_USERTASKS\_EDIT|  
|错误列表|IDM\_VS\_TOOL\_ERRORLIST|IDG\_VS\_ERRORLIST\_ERRORGROUP<br /><br /> IDG\_VS\_ERRORLIST\_WARNINGGROUP<br /><br /> IDG\_VS\_ERRORLIST\_MESSAGEGROUP|  
|调用浏览器|IDM\_VS\_TOOL\_ CALLBROWSER1。.16|IDG\_VS\_TOOLBAR\_ CALLBROWSER1 \_ACTIONS<br /><br /> IDG\_VS\_TOOLBAR\_ CALLBROWSER1 \_TYPE<br /><br /> IDG\_VS\_TOOLBAR\_ CALLBROWSER1 \_CBSETTINGS|  
|断点|guidVSDebugGroup: IDM\_BREAKPOINTS\_WINDOW\_TOOLBAR|IDG\_BREAKPOINTS\_WINDOW\_NEW<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_DELETE<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_ALL<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_VIEW<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_EDIT<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_COLUMNS|  
|反汇编|guidVSDebugGroup: IDM\_DISASM\_WINDOW\_TOOLBAR|IDG\_DISASM\_WINDOW\_TOOLBAR|  
|内存 1\-4|guidVSDebugGroup: IDM\_MEMORY\_WINDOW\_TOOLBAR1… 4|IDG\_MEMORY\_EXPRESSION1..4<br /><br /> IDG\_MEMORY\_ COLUMNS1。.4|  
|进程|guidVSDebugGroup: IDM\_ATTACHED\_PROCS\_TOOLBAR|IDG\_ATTACHED\_PROCS\_EXECCNTRL IDG\_ATTACHED\_PROCS\_STEPPING<br /><br /> IDG\_ATTACHED\_PROCS\_EXE CCNTRL2<br /><br /> IDG\_ATTACHED\_PROCS\_ATTACH<br /><br /> IDG\_ATTACHED\_PROCS\_COLUMNS|  
  
## 请参阅  
 [将菜单控制器添加到工具栏](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)   
 [将工具栏添加到工具窗口](../../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [Guid 和 Id 的 Visual Studio 菜单](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)