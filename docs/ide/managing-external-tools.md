---
title: "管理外部工具 | Microsoft Docs"
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- Create GUID tool
- RC (Resource Compiler)
- ReBase tool
- Windows NT Message Compiler
- Windows NT C++ Symbol Undecorator
- tstcon32.exe
- Type Library Generator
- Windows NT Image Binder
- tools [Visual Studio], external
- RowsetViewer tool
- utilities, external tools
- Local Test Manager
- OLE DB Rowset Viewer
- Midlc (IDL Compiler)
- ATL Trace Tool
- Odbcte32w.exe
- IDL Compiler
- HCW (Help Workshop)
- Message Compiler [Visual Studio]
- UUID Generator
- MIDL, external tools
- ErrLook tool
- MAKEHM tool
- Error lookup tool
- OLEVIEW (Object Viewer)
- Uuidgen.exe
- WebDbg tool
- OLE/COM Object Viewer
- LTM (Local Test Manager)
- ATLTraceTool.exe
- Bind tool
- Vsvars32.bat
- external tools [Visual Studio]
- ODBC Test
- Windows NT Image Rebaser
- undname.exe
- Vcspawn.exe
- ActiveX Control Test Container
- mc (Message Compiler)
- GUIDGEN tool
- Odbcte32.exe
- DisableMsg tool
- MkTypLib tool
- Help Workshop
- Resource Compiler
ms.assetid: f382fd40-a98f-4934-8c9a-5aeae881acde
caps.latest.revision: 38
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 07dfd26933090708cf40adff5f7ceb4785686245
ms.lasthandoff: 04/05/2017

---
# <a name="manage-external-tools"></a>管理外部工具
可以使用“工具”菜单从 Visual Studio 内部调用外部工具。 “工具”菜单上提供了几个默认工具，但你可以添加自己的其他可执行文件。  

## <a name="tools-available-on-the-visual-studio-tools-menu"></a>Visual Studio Tools 菜单中提供的工具
 “工具”菜单包含若干内置命令，如：

*  用于[管理 Visual Studio 扩展](finding-and-using-visual-studio-extensions.md)的“扩展和更新”
*  用于[整理代码片段](code-snippets.md#code-snippet-manager)的“代码片段管理器...”
*  用于启动 [Dotfuscator Community Edition (CE)](dotfuscator/index.md)（如果[已安装](dotfuscator/install.md)）的 **PreEmptive Protection - Dotfuscator**
*  用于[自定义菜单和工具栏](how-to-customize-menus-and-toolbars-in-visual-studio)的“自定义...”
*  用于[为 Visual Studio IDE 和其他工具设置各种不同选项](reference/options-dialog-box-visual-studio.md)的“选项...”

## <a name="add-new-tools-to-the-tools-menu"></a>将新工具添加到“工具”菜单 
 可将外部工具添加到“工具”菜单。 打开“外部工具...”对话框并单击“添加”，然后填写信息。 例如，以下条目会导致 Windows 资源管理器在当前已在 Visual Studio 中打开的文件目录中打开：  
  
1.  标题：打开文件位置
  
2.  命令：`explorer.exe`  
  
3.  参数：`/root, "$(ItemDir)"`  
  
 以下是在定义外部工具时可以使用的参数的完整列表。
  
> [!NOTE]
>  IDE 状态栏会显示当前行和当前列变量，以指示插入点在活动代码编辑器中的位置。 当前文本变量返回在该位置选择的文本或代码。  
  
|名称|参数|描述|  
|----------|--------------|-----------------|  
|项路径|$(ItemPath)|当前文件的完整文件名（驱动器 + 路径 + 文件名）。|  
|项目录|$(ItemDir)|当前文件的目录（驱动器 + 路径）。|  
|项文件名|$(ItemFilename)|当前文件的文件名（文件名）。|  
|项扩展名|$(ItemExt)|当前文件的文件扩展名。|  
|当前行|$(CurLine)|代码窗口中光标的当前行位置。|  
|当前列|$(CurCol)|代码窗口中光标的当前列位置。|  
|当前文本|$(CurText)|选定的文本。|  
|目标路径|$(TargetPath)|要生成的项的完整文件名（驱动器 + 路径 + 文件名）。|  
|目标目录|$(TargetDir)|要生成的项的目录。|  
|Target Name|$(TargetName)|要生成的项的文件名。|  
|目标扩展名|$(TargetExt)|要生成的项的文件扩展名。|  
|二进制目录|$(BinDir)|正在生成的二进制文件的最终位置（定义为驱动器 + 路径）。 例如：**\\...\My Documents\Visual Studio \<Version>\\<ProjectName\>\bin\debug**|  
|项目目录|$(ProjDir)|当前项目的目录（驱动器 + 路径）。|  
|项目文件名|$(ProjFileName)|当前项目的文件名（驱动器 + 路径 + 文件名）。|  
|解决方案目录|$(SolutionDir)|当前解决方案的目录（驱动器 + 路径）。|  
|解决方案文件名|$(SolutionFileName)|当前解决方案的文件名（驱动器 + 路径 + 文件名）。|  

## <a name="see-also"></a>另请参阅  
 [C/C++ 生成工具](/cpp/build/reference/c-cpp-build-tools)

