---
title: "如何： 向功能区组添加对话框启动器 |Microsoft 文档"
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
- dialog box launcher [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], dialog box launcher
ms.assetid: 5972664f-4e37-4dc6-90d0-69cedd057e60
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a8b5158bb17470ce63dbc22dc5b501a314ebda8b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>如何：向功能区组添加对话框启动器
  你可以向功能区上的任何组添加对话框启动器。 对话框启动器是一组中出现一个小图标。 用户单击此图标以打开相关的对话框或提供更多选项与组相关的任务窗格。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>若要向功能区组添加对话框启动器  
  
1.  在选择功能区代码文件 （.vb 或.cs 文件）**解决方案资源管理器**。  
  
2.  上**视图**菜单上，单击**设计器**。  
  
3.  在功能区设计器中，右键单击任何组，然后单击**添加 DialogBoxLauncher**。  
  
     将代码添加到<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick>要打开自定义或内置对话框中的组的事件。  
  
## <a name="see-also"></a>另请参阅  
 [功能区概述](../vsto/ribbon-overview.md)   
 [Accessing the Ribbon at Run Time](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Office 开发示例和演练](../vsto/office-development-samples-and-walkthroughs.md)   
 [功能区设计器](../vsto/ribbon-designer.md)   
 [功能区对象模型概述](../vsto/ribbon-object-model-overview.md)   
 [功能区 XML](../vsto/ribbon-xml.md)   
 [如何： 将功能区从功能区设计器导出到功能区 XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [如何： 更改的功能区上的选项卡位置](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [如何： 自定义内置选项卡](../vsto/how-to-customize-a-built-in-tab.md)   
 [如何： 将控件添加到 Backstage 视图](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [自定义 Outlook 功能区](../vsto/customizing-a-ribbon-for-outlook.md)   
 [如何： 开始自定义功能区](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [如何： 显示外接程序用户界面错误](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [演练： 使用功能区设计器创建自定义选项卡](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [演练： 在运行时更新功能区上的控件](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [演练：使用功能区 XML 创建自定义选项卡](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  