---
title: "如何： 在功能区上显示开发人员选项卡 |Microsoft 文档"
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
- Ribbon [Office development in Visual Studio], tabs
- Developer tab [Office development in Visual Studio]
ms.assetid: ce7cb641-44f2-4a40-867e-a7d88f8e98a9
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cad7fb4fe49df9688a0b9e7b3baa1f1108694136
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-show-the-developer-tab-on-the-ribbon"></a>如何：在功能区上显示“开发人员”选项卡
  访问**开发人员**选项卡功能区中的 Office 应用程序，你必须将它配置为显示该选项卡，因为它不会显示默认情况下。 例如，如果要向 Word 的文档级自定义项添加一个 <xref:Microsoft.Office.Tools.Word.GroupContentControl>，则必须显示该选项卡。  
  
> [!NOTE]  
>  本指南仅适用于 Office 2010 或更高版本的应用程序。 如果你想要在 2007 Microsoft Office System 中显示此选项卡，请参阅本主题的以下版本[如何： 在功能区上显示开发人员选项卡](http://msdn.microsoft.com/library/bb608625(v=vs.90).aspx)。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  Access 没有**开发人员**选项卡。  
  
### <a name="to-show-the-developer-tab"></a>显示“开发工具”选项卡  
  
1.  启动本主题支持的任何 Office 应用程序。 请参阅**适用于：**本主题前面的注意。  
  
2.  上**文件**选项卡上，选择**选项**按钮。  
  
     下图显示**文件**选项卡和**选项**Office 2010 中的按钮。  
  
     ![选择文件，Outlook 2010 中的选项](../vsto/media/vsto-office-file-tab.png "Outlook 2010 中选择文件，选项")  
  
     下图显示**文件**Office 2013 中的选项卡。  
  
     ![Outlook 2013 中的文件选项卡](../vsto/media/vsto-office2013-filetab.png "Outlook 2013 中的文件选项卡")  
  
     下图显示**选项**Office 2013 中的按钮。  
  
     ![Outlook 2013 Preview 中的选项按钮](../vsto/media/vsto-office2013-optionsbutton.png "Outlook 2013 Preview 中的选项按钮")  
  
3.  在*ApplicationName***选项**对话框框中，选择**自定义功能区**按钮。  
  
     下图显示**选项**对话框中和**自定义功能区**Excel 2010 中的按钮。 此按钮的位置在本主题顶部附近“适用于”部分中列出的所有其他应用程序中是类似的。  
  
     ![自定义功能区按钮](../vsto/media/vsto-office2010-customizeribbonbutton.png "在自定义功能区按钮")  
  
4.  在主选项卡的列表中，选择**开发人员**复选框。  
  
     下图显示**开发人员**Word 2010 中的复选框和[!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]。 此复选框的位置在本主题顶部附近“适用于”部分中列出的所有其他应用程序中是类似的。  
  
     ![Word 选项对话框中的开发人员复选框](../vsto/media/vsto-office2010-developercheckbox.png "Word 选项对话框中的开发人员复选框")  
  
5.  选择**确定**按钮以关闭**选项**对话框。  
  
## <a name="see-also"></a>另请参阅  
 [Office UI 自定义](../vsto/office-ui-customization.md)  
  
  