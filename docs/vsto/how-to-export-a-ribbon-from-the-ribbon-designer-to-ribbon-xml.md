---
title: "如何： 将功能区从功能区设计器导出到功能区 XML |Microsoft 文档"
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
- custom Ribbon, XML
- customizing the Ribbon, XML
- Ribbon [Office development in Visual Studio], XML
- Ribbon [Office development in Visual Studio], exporting
- XML [Office development in Visual Studio], Ribbon
- Ribbon Designer [Office development in Visual Studio]
- exporting Ribbon
ms.assetid: 96e0e9ed-4392-4f45-ac33-b6f7c22ea321
caps.latest.revision: "37"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b73bff8170e351e9e22e95d53ae446895cfdbd2b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>如何：将功能区从功能区设计器导出为功能区 XML
  **功能区 （可视化设计器）**项不支持的功能区自定义的所有可能类型。 若要以高级方式自定义功能区，可以将功能区从设计器导出到功能区 XML，并直接编辑 XML。  
  
> [!NOTE]  
>  并非所有属性值将都显示在功能区 XML 文件中。 有关详细信息，请参阅[功能区概述](../vsto/ribbon-overview.md)。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>若要将功能区从功能区设计器导出到功能区 XML  
  
1.  右键单击功能区代码文件中的**解决方案资源管理器**，然后单击**视图设计器**。  
  
2.  右键单击功能区设计器中，并依次**功能区导出到 XML**。  
  
     Visual Studio 将功能区 XML 文件和一个功能区 XML 代码文件添加到你的项目。  
  
3.  在功能区代码类中，找到以开头的注释`TODO:`。  
  
4.  将代码块复制到这些注释内**ThisAddin**， **ThisWorkbook**，或**ThisDocument**类，具体取决于你开发哪种类型的解决方案。  
  
     此代码使 Microsoft Office 应用程序能够发现和加载你的自定义功能区。 有关更多信息，请参见 [Ribbon XML](../vsto/ribbon-xml.md)。  
  
5.  在**ThisAddin**， **ThisWorkbook**，或**ThisDocument**类，请取消注释代码块。  
  
     取消注释的代码后，它应类似于下面的示例。 在此示例中，功能区类称为`MyRibbon`。  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
6.  切换到功能区 XML 代码文件并查找`Ribbon Callbacks`区域。  
  
     这是你在其中编写回调方法以处理用户操作，例如单击按钮。  
  
7.  创建回调方法，以在功能区设计器代码中编写每个事件处理程序。  
  
8.  将所有事件处理程序代码从事件处理程序都移动到回调方法，并修改代码以使用功能区扩展性 (RibbonX) 编程模型。  
  
     有关编写回调方法和使用 RibbonX 编程模型的信息，请参阅[功能区 XML](../vsto/ribbon-xml.md)。  
  
## <a name="see-also"></a>另请参阅  
 [功能区概述](../vsto/ribbon-overview.md)   
 [功能区设计器](../vsto/ribbon-designer.md)   
 [功能区 XML](../vsto/ribbon-xml.md)   
 [演练： 使用功能区设计器创建自定义选项卡](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [演练：使用功能区 XML 创建自定义选项卡](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  