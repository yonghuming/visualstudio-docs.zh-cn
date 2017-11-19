---
title: "如何： 自定义内置选项卡 |Microsoft 文档"
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
- built-in tabs [Office development in Visual Studio]
ms.assetid: 197a7aaa-a51d-496c-b904-b9421849fad9
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1161af5501ebd0df8137293b137600697af91516
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-customize-a-built-in-tab"></a>如何：自定义内置选项卡
  可以将组和控件添加到内置选项卡。内置选项卡是已在 Microsoft Office 应用程序功能区的选项卡。 例如，**数据**选项卡是 Excel 中的内置选项卡。 创建自定义组时，它显示在选项卡末尾，但可以在选项卡上任意移动你的组。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  可以将组添加到内置选项卡，但不能删除内置选项卡中的内置组。  
  
### <a name="to-add-groups-to-a-built-in-tab"></a>将组添加到内置选项卡  
  
1.  右键单击功能区代码文件中的**解决方案资源管理器**，然后单击**视图设计器**。  
  
    > [!NOTE]  
    >  如果功能区代码文件未出现在**解决方案资源管理器**，必须添加**功能区项**到你的项目。 请参阅[如何： 开始自定义功能区](../vsto/how-to-get-started-customizing-the-ribbon.md)。  
  
2.  右键单击功能区设计器中，在任何选项卡，然后单击**属性**。  
  
3.  在**属性**窗口中，展开**ControlId**属性，且然后将其设置**ControlIdType**属性**Office**。  
  
4.  设置**OfficeId**属性*控制 ID*想要自定义的内置选项卡。  
  
     控件 ID 是唯一标识 Microsoft Office 应用程序中内置的选项卡、组和控件的名称。  
  
     有关控件 Id 的列表，请参阅[Office 2010 帮助文件： Office Fluent 用户界面控件标识符](http://go.microsoft.com/fwlink/?LinkID=181052)。  
  
5.  从**Office 功能区控件**选项卡**工具箱**，将组拖到选项卡。  
  
    > [!NOTE]  
    >  设计器中不显示内置组。 因此，确定是否正在使用的内置选项卡的唯一方法是检查**ControlId**的选项卡的属性。  
  
### <a name="to-position-groups-on-a-built-in-tab"></a>若要在内置选项卡上定位组  
  
1.  在“功能区设计器”中，选择自定义组。  
  
2.  在**属性**窗口中，展开**位置**属性。  
  
3.  设置**PositionType**为适当的值的属性：  
  
    -   **BeforeOfficeId**定位所指定内置组之前。  
  
    -   **AfterOfficeId**定位所指定内置组之后。  
  
4.  设置**OfficeId**内置组的控件 id 的属性。  
  
     有关控件 Id 的列表，请参阅[Office 2010 帮助文件： Office Fluent 用户界面控件标识符](http://go.microsoft.com/fwlink/?LinkID=181052)。  
  
## <a name="see-also"></a>另请参阅  
 [功能区概述](../vsto/ribbon-overview.md)   
 [功能区设计器](../vsto/ribbon-designer.md)   
 [功能区 XML](../vsto/ribbon-xml.md)   
 [演练： 使用功能区设计器创建自定义选项卡](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [演练： 使用功能区 XML 创建自定义选项卡](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)   
 [如何： 开始自定义功能区](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [如何： 更改的功能区上的选项卡位置](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [如何： 将控件添加到 Backstage 视图](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [如何：显示外接程序用户界面错误](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  