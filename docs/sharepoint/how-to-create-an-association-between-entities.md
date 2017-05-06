---
title: "如何：创建实体之间的关联"
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
  - "AssociationGroupTool"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [Visual Studio 中的 SharePoint 开发], 关联外部内容类型"
  - "BDC [Visual Studio 中的 SharePoint 开发], 实体之间的关联"
  - "BDC [Visual Studio 中的 SharePoint 开发], 创建关联"
  - "BDC [Visual Studio 中的 SharePoint 开发], 相关实体"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 关联外部内容类型"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 实体之间的关联"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 创建关联"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 相关实体"
ms.assetid: 0c095df8-1f40-4c4d-9fed-e125a8429724
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# 如何：创建实体之间的关联
  您可以通过创建关联来定义业务数据连接 \(BDC\) 模型中的实体之间的关系。  Visual Studio 会生成方法为模型使用者提供每个关联的相关信息。  SharePoint web 部件、列表或自定义应用程序可以使用这些方法在用户界面 \(UI\) 中显示数据关系。  
  
 可以在 BDC 设计器中创建两种类型的关联：基于外键的关联和无外键的关联。  有关详细信息，请参阅[创建实体之间的关联](../sharepoint/creating-an-association-between-entities.md)。  
  
### 创建实体之间的关联  
  
1.  在“工具箱”的“BusinessDataConnectivity”选项卡中，单击“关联”项。  
  
2.  在 BDC 设计器中，单击源实体，然后单击目标实体。  
  
     此时将显示**“关联编辑器”**。  
  
3.  如果要创建基于外键的关联，请选中**“是外键关联”**复选框。  
  
    1.  在“标识符映射”表的“源 ID”列中，选择“字段”列中显示的每个匹配的类型描述符旁边的标识符。  
  
         例如，在**“源 ID”**列中，选择 `ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID` 类型描述符和 `ReadItem.salesOrder.SalesOrder.ContactID` 类型描述符旁边的 `ContactID`。  
  
4.  如果要创建无外键的关联，请清除**“是外键关联”**复选框。  
  
5.  选择**“确定”**按钮。  
  
6.  在 BDC 设计器上，源实体与目标实体之间会显示一条表示关联的直线。  
  
     Visual Studio 会向目标实体的服务类和源实体的服务类添加关联导航方法。  有关关联导航方法的更多信息，请参见 [支持的操作](http://go.microsoft.com/fwlink/?LinkId=169286)。  
  
7.  在源实体的关联导航方法中，添加返回目标实体集合的代码。  
  
8.  在目标实体的关联导航方法中，添加返回相关源实体的代码。  
  
     有关关联导航方法的示例，请参见[创建实体之间的关联](../sharepoint/creating-an-association-between-entities.md)。  
  
## 请参阅  
 [创建实体之间的关联](../sharepoint/creating-an-association-between-entities.md)   
 [设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [如何：添加 Finder 方法](../sharepoint/how-to-add-a-finder-method.md)   
 [如何：添加特定的 Finder 方法](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [如何：添加 Creator 方法](../sharepoint/how-to-add-a-creator-method.md)   
 [如何：添加 Deleter 方法](../sharepoint/how-to-add-a-deleter-method.md)   
 [如何：添加 Updater 方法](../sharepoint/how-to-add-an-updater-method.md)   
 [BDC 模型设计工具概述](../sharepoint/bdc-model-design-tools-overview.md)   
 [如何：向方法添加参数](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [如何：定义方法实例](../sharepoint/how-to-define-a-method-instance.md)   
 [如何：定义参数的类型描述符](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [演练：使用业务数据在 SharePoint 中创建外部列表](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)  
  
  