---
title: "如何： 更改的功能区上的选项卡位置 |Microsoft 文档"
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
helpviewer_keywords: Ribbon [Office development in Visual Studio], tabs
ms.assetid: 3f0906e3-9708-4136-ac49-986bc4c92ea4
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 40907d71bae8c8c25f06b3b1f3d4af8b9f79c385
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-change-the-position-of-a-tab-on-the-ribbon"></a>如何：更改功能区上选项卡的位置
  你可以通过更改功能区上的自定义选项卡的顺序**选项卡集合编辑器**。 之前或之后在功能区上的内置选项卡，您可以将自定义选项卡。 内置选项卡是已在 Microsoft Office 应用程序的功能区的选项卡。 例如，**数据**选项卡是 Excel 中的内置选项卡。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-change-the-order-of-tabs-on-the-ribbon"></a>若要更改功能区上的选项卡的顺序  
  
1.  在选择功能区代码文件 （.vb 或.cs 文件）**解决方案资源管理器**。  
  
2.  上**视图**菜单上，单击**设计器**。  
  
3.  右键单击功能区设计器中，并依次**属性**。  
  
4.  在**属性**窗口中，选择**选项卡**属性，然后单击省略号按钮 (![ASP.NET 移动设计器椭圆](../sharepoint/media/mwellipsis.gif "ASP.NET 移动设计器椭圆"))。  
  
     **选项卡集合编辑器**显示。  
  
5.  在**选项卡集合编辑器**中**成员**列表中，选择你想要移动和单击向上或向下箭头可以更改 tab 键顺序选项的卡。  
  
### <a name="to-position-a-tab-before-or-after-a-built-in-tab-on-the-ribbon"></a>若要定位的选项卡上之前, 或之后在功能区上的内置选项卡  
  
1.  在功能区设计器中，选择自定义选项卡。  
  
2.  在**属性**窗口中，展开**ControlId**属性，请确保和的值**ControlIdType**属性设置为**自定义**.  
  
3.  在**属性**窗口中，展开**位置**属性。  
  
4.  设置**PositionType**为适当的值的属性：  
  
    -   **BeforeOfficeId**定位之前指定的内置选项卡组。  
  
    -   **AfterOfficeId**置于指定的内置选项卡后面的组。  
  
5.  设置**OfficeId**到内置选项卡上的控件 ID 的属性。  
  
     有关控件 Id 的列表，请参阅[Office 2010 帮助文件： Office Fluent 用户界面控件标识符](http://go.microsoft.com/fwlink/?LinkID=181052)。  
  
## <a name="see-also"></a>另请参阅  
 [功能区概述](../vsto/ribbon-overview.md)   
 [功能区设计器](../vsto/ribbon-designer.md)   
 [功能区 XML](../vsto/ribbon-xml.md)   
 [演练： 使用功能区设计器创建自定义选项卡](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [演练：使用功能区 XML 创建自定义选项卡](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  