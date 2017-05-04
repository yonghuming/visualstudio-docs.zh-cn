---
title: "如何：向模型添加实体 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EntityTool"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [Visual Studio 中的 SharePoint 开发], 添加实体"
  - "BDC [Visual Studio 中的 SharePoint 开发], 实体"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 添加实体"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 实体"
ms.assetid: 139a6639-dabe-4e14-bb64-e5f4efb6f2fb
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# 如何：向模型添加实体
  若要创建实体，请将实体从 Visual Studio 的**“工具箱”**加到业务数据连接 \(BDC\) 设计器上。  
  
### 向模型添加实体  
  
1.  创建一个 BDC 项目，或者打开一个现有的 BDC 项目。  有关详细信息，请参阅[创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
2.  在“工具箱”的“BusinessDataCatalog”组中，将“实体”拖到设计器中。  
  
     新实体随即显示在该设计器中。  Visual Studio 将 `<Entity>` 元素添加到项目中 BDC 模型文件的 XML 中。  有关 Entity 元素的特性的更多信息，请参见 [实体](http://go.microsoft.com/fwlink/?LinkId=169296)。  
  
3.  在屏幕设计器中，打开实体的快捷菜单，选择“添加”，然后选择“Identifier”。  
  
     新标识符随即显示在该实体中。  
  
    > [!NOTE]  
    >  可以在**“属性”**窗口中更改实体和标识符的名称。  
  
4.  在类中定义实体的字段。  您可以向项目添加新类，也可以使用通过“对象关系设计器（O\/R 设计器）”等其他工具创建的现有类。  下面的示例显示了一个名为“Contact”的实体类。  
  
     [!code-csharp[SP_BDC_Entity_Data_Class#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc_entity_data_class/cs/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc_entity_data_class/vb/bdcmodel1/contact.vb#1)]  
  
## 请参阅  
 [如何：添加 Creator 方法](../sharepoint/how-to-add-a-creator-method.md)   
 [如何：添加 Deleter 方法](../sharepoint/how-to-add-a-deleter-method.md)   
 [如何：添加 Updater 方法](../sharepoint/how-to-add-an-updater-method.md)   
 [如何：添加 Finder 方法](../sharepoint/how-to-add-a-finder-method.md)   
 [如何：添加特定的 Finder 方法](../sharepoint/how-to-add-a-specific-finder-method.md)  
  
  