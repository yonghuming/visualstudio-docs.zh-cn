---
title: "如何： 向 Word 文档添加 XMLNodes 控件 |Microsoft 文档"
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
- XMLNodes control, adding to documents
- controls [Office development in Visual Studio], adding to documents
ms.assetid: 315c6def-51f6-4ba6-bd9e-55cdf70f15bf
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 791eabb83ffd020672b7955e0ceb283d5196621f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-xmlnodes-controls-to-word-documents"></a>如何：向 Word 文档添加 XMLNodes 控件
  **重要**提出有关 Microsoft Word 本主题中的信息不提供的以独占方式适合的好处和使用个人和组织用户位于美国和其区域之外，或使用，或开发在运行的程序，在 2010 年 1 月，Microsoft 中删除的特定功能实现的时间之前已授权的 Microsoft 的 Microsoft Word 产品被与 Microsoft Word 自定义 XML。 有关 Microsoft Word 此信息不能读取或使用的个人或美国或其地区熟悉使用，或开发在 Microsoft Word 2010 年 1 月 10 日之后已授权的 Microsoft 的产品运行的程序中的组织;这些产品将无法与产品许可在该日期之前或购买并获得美国以外的使用许可相同。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 当你重复的 XML 架构元素映射到 Microsoft Office Word 文档时，Visual Studio 会自动添加<xref:Microsoft.Office.Tools.Word.XMLNodes>到您的文档的控制。  
  
 有关映射非重复的 XML 架构元素的信息，请参阅[如何： 向 Word 文档添加 XMLNode 控件](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)。  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Word.XMLNodes>控件不能从**工具箱**或**数据源**窗口中，也不以编程方式创建。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-an-xmlnodes-control-to-a-document"></a>若要向文档添加 XMLNodes 控件  
  
1.  在文档中在 Visual Studio 设计器中，在功能区中，单击**开发人员**选项卡。  
  
    > [!NOTE]  
    >  如果看不到 **“开发人员”** 选项卡，则必须首先显示它。 有关详细信息，请参阅 [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)。  
  
2.  在**XML**组中，单击**架构**。  
  
     **模板和外接程序**对话框随即打开。  
  
3.  单击**XML 架构**选项卡。  
  
4.  单击**将架构添加**。  
  
     **添加架构**对话框随即打开。  
  
5.  选择 XML 架构包含重复架构元素和单击**打开**。  
  
     **架构设置**对话框随即出现。  
  
6.  分配一个别名，或单击**确定**以添加别名没有架构。  
  
     该架构添加到**添加架构**对话框。  
  
7.  在**添加架构**对话框中，单击**确定**。  
  
     **XML 结构**任务窗格随即打开。  
  
8.  单击重复架构元素**XML 结构**任务窗格以将其添加到文档。  
  
     <xref:Microsoft.Office.Tools.Word.XMLNodes>创建控件并将其添加到项目。  
  
## <a name="see-also"></a>另请参阅  
 [XMLNodes 控件](../vsto/xmlnodes-control.md)   
 [使用扩展对象实现 Word 自动化](../vsto/automating-word-by-using-extended-objects.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [主机项和主机控件的编程限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  