---
title: "Office 项目中的辅助功能 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, accessibility
- shortcut keys [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], shortcut keys
- accessibility [Office development in Visual Studio]
ms.assetid: 48efcf1f-ca49-47ce-99f0-cc99f051aeae
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4636e55fa2bc20ba9ff958a897ef7898099cb5c2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="accessibility-in-office-projects"></a>Office 项目中的辅助功能
  Microsoft Visual Studio 和 Microsoft Office 包括许多辅助功能，使您能够生成符合标准的可访问性要求的自定义解决方案。 Microsoft 将发布在 Web 上找到的可访问性的准则。 有关详细信息，请参阅[辅助功能网站](http://go.microsoft.com/fwlink/?LinkID=37113)。  
  
 在大多数情况下，Visual Studio 中的 Office 项目满足可以设置以使你的解决方案可访问的辅助功能标准或公开属性。 但是，有一些功能具有受限制的可访问性。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="accessibility-at-design-time"></a>在设计时的可访问性  
  
### <a name="using-shortcut-keys-in-document-level-projects"></a>在文档级项目中使用键盘快捷方式  
 在 Visual Studio 中打开 Microsoft Office Word 文档或 Microsoft Office Excel 工作簿时，一次只有一个应用程序接收的快捷键命令。 默认情况下，Visual Studio 接收所有快捷键命令，但可以 Word 或 Excel 文档通过选择具有焦点时接收它们**动态键盘方案**上**键盘设置**页**选项**对话框。 有关详细信息，请参阅[Microsoft Office Word 键盘，Microsoft Office 键盘设置选项对话框](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)和[Microsoft Office Excel 键盘，Microsoft Office 键盘设置选项对话框](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md).  
  
### <a name="displaying-shortcut-keys-for-the-ribbon-in-document-level-projects"></a>有关文档级项目中的功能区中显示键盘快捷方式  
 在 Visual Studio 中打开 Word 文档或 Excel 工作簿时，不能按 Alt 键可查看的选项卡和功能区上的控件的键盘快捷方式。 若要在设计器中打开的文档或工作簿时，请查看键盘快捷方式，请执行以下步骤。  
  
##### <a name="to-view-shortcut-keys-for-ribbon-tabs-and-controls-in-the-designer"></a>若要在设计器中查看功能区选项卡和控件的键盘快捷方式  
  
1.  在 Visual Studio 中，在**工具**菜单上，单击**选项**。  
  
2.  展开**Office 工具**节点，然后选择**Microsoft Office Excel 键盘**或**Microsoft Office Word 键盘**适当。  
  
3.  选择**动态键盘方案**。  
  
     将出现一条表明必须重新启动 Visual Studio 以使更改生效。  
  
4.  单击“确定”。  
  
5.  重新启动 Visual Studio 中，并重新打开你的项目。  
  
6.  打开你的项目的文档或工作簿设计器。  
  
7.  按 F6 以在功能区中显示的快捷键。  
  
## <a name="accessibility-at-run-time"></a>在运行时的可访问性  
  
### <a name="windows-forms-controls-on-office-documents"></a>Windows 窗体 Office 文档上的控件  
 Windows 窗体控件公开可访问性属性，以提供有关控件的辅助功能，如屏幕读取器的信息。 文档级自定义项中的 Office 文档上控件时，可以充分利用这些辅助功能属性。 有关详细信息，请参阅[提供 Windows 窗体上控件的辅助功能信息](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form)。  
  
 但是，有一些可访问性限制在当 Excel 工作簿或 Word 文档承载 Windows 窗体控件的运行时：  
  
-   不能到另一个控件从选项卡。  
  
-   文档的缩放设置更改为 100%以外的任何内容，在文档上的控件将停用。  
  
 有关限制的文档上的 Windows 窗体控件的信息，请参阅[限制的 Windows 窗体控件 Office 文档上](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)。  
  
### <a name="actions-panes-and-custom-task-panes"></a>操作窗格和自定义任务窗格  
 如果操作窗格或自定义任务窗格具有焦点，则访问控件相同的方式来访问 Windows 窗体应用程序上的控件。 若要在操作窗格和文档之间移动光标，你可以按**F6**。  
  
 有关操作窗格和自定义任务窗格的详细信息，请参阅[操作窗格概述](../vsto/actions-pane-overview.md)和[自定义任务窗格](../vsto/custom-task-panes.md)。  
  
### <a name="display-modes"></a>显示模式  
 Visual Studio 具有以下限制与相关显示模式：  
  
-   文档的缩放设置更改为 100%以外的任何内容，在 Word 文档或 Excel 工作表上的控件将停用。  
  
-   **新项目**对话框不会正确显示控件如果用户更改到的计算机的辅助功能选项**使用高对比度**。  
  
 您可以使用放大镜来克服这些限制。 放大镜是创建一个单独的窗口，显示放大屏幕的一部分的 Windows 中的显示实用工具。  
  
## <a name="see-also"></a>另请参阅  
 [开发 Office 解决方案](../vsto/developing-office-solutions.md)   
 [Office 文档上的控件](../vsto/controls-on-office-documents.md)   
 [针对残障人士的辅助功能](/visualstudio/ide/reference/accessibility-for-people-with-disabilities)   
 [Visual Studio 的辅助功能](/visualstudio/ide/reference/accessibility-features-of-visual-studio)  
  
  