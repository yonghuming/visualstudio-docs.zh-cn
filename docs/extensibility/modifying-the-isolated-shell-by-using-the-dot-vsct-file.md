---
title: "通过使用修改独立的 Shell。Vsct 文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode, .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: 8
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
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: a20b546c6e8d6d70a17d3d0bae575a5b2898d781
ms.lasthandoff: 02/22/2017

---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>通过使用修改独立的 Shell。Vsct 文件
Visual Studio 独立的 shell 项目的用户界面项目包含一个.vsct 文件，您可以指定哪些应用程序组和个别命令在应用程序中可用。 以下是未修改的.vsct 文件的摘录。  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 默认情况下，大多数命令和命令组均包括在内。 若要排除的命令或命令组，只需取消注释该命令或组。  
  
 例如，若要删除的下一个窗格和上一个窗格命令，取消注释`No_PaneNextPaneCommand`和`No_PanePrevPaneCommand`条目︰  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 有关更详细的示例这些自定义设置，请参阅[演练︰ 创建基本隔离的 Shell 应用程序](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
## <a name="referenced-files"></a>引用的文件  
 为应用程序的默认.vsct 文件引用了以下文件。 这些文件位于 Visual Studio SDK 安装目录的 \VisualStudioIntegration\Common\Inc\ 子目录中。  
  
|文件|描述|  
|----------|-----------------|  
|wbids.h|Web 浏览包的用户界面标识。|  
|AppIDCmdUsed.vsct|主要的 Visual Studio UI 元素的命令表。|  
|EmulatorCmdUsed.vsct|Emacs 和简述编辑器仿真 UI 元素的命令表。|  
|Vsdebugguids.h|定义命令、 选项页中和其他功能的 Visual Studio 调试器的 Guid。|  
|VsDbgCmdUsed.vsct|调试器的命令表。|  
  
 AppIDCmdUsed.vsct 文件包括基于应用程序.vsct 文件中定义的符号在 Visual Studio UI 元素。  
  
 有关详细信息，请参阅[设计 XML 命令表 (。Vsct) 文件](../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)和[VSCT XML 架构参考](../extensibility/vsct-xml-schema-reference.md)。  
  
## <a name="see-also"></a>另请参阅  
 [Visual Studio 独立 Shell](../extensibility/visual-studio-isolated-shell.md)
