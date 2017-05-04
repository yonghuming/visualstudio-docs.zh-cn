---
title: "创建实体之间的关联 | Microsoft Docs"
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
  - "VS.SharePointTools.BDC.Association_Dialog"
dev_langs: 
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
ms.assetid: c908448c-13d3-4d2f-89ad-8d709b2958fb
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 创建实体之间的关联
  您可以通过创建关联来定义业务数据连接 \(BDC\) 模型中的实体之间的关系。  Visual Studio 会生成方法为模型使用者提供每个关联的相关信息。  SharePoint web 部件、列表或自定义应用程序可以使用这些方法在用户界面 \(UI\) 中显示数据关系。  
  
## 创建关联  
 可以通过以下方式创建关联：在 Visual Studio **“工具箱”**中选择**“关联”**控件，选择第一个实体（称为源实体），然后选择第二个实体（称为目标实体）。  可以在**“关联编辑器”**中定义关联的详细信息。  有关详细信息，请参阅[如何：创建实体之间的关联](../sharepoint/how-to-create-an-association-between-entities.md)。  
  
## 关联方法  
 应用程序（如 SharePoint 业务数据 web 部件）通过调用实体的服务类中的方法使用关联。  可以通过在**“关联编辑器”**中选择方法来向实体的服务类添加方法。  
  
 默认情况下，**“关联编辑器”**会向源实体和目标实体添加关联导航方法。  源实体中的关联导航方法允许使用者检索目标实体列表。  目标实体中的关联导航方法允许使用者检索与目标实体关联的源实体。  
  
 必须将代码添加到上述各方法才能返回相应的信息。  还可以添加其他类型的方法以支持更高级的方案。  有关上述各方法的更多信息，请参见 [支持的操作](http://go.microsoft.com/fwlink/?LinkId=169286)。  
  
## 关联的类型  
 可以在 BDC 设计器中创建两种类型的关联：基于外键的关联和无外键的关联。  
  
### 基于外键的关联  
 通过将源实体中的标识符与目标实体中定义的类型描述符相关联，可以创建基于外键的关联。  这种关系使模型的使用者可以为其用户提供增强的 UI。  例如，Outlook 中使用户能够创建以下拉列表形式显示客户的销售订单的窗体；或 SharePoint 中使用户能够打开客户配置页的销售订单列表。  
  
 若要创建基于外键的关联，请关联共享相同的名称和类型的标识符和类型描述符。  例如，您可以在 `Contact` 实体和 `SalesOrder` 实体之间创建基于外键的关联。  `SalesOrder` 实体返回 `ContactID` 类型描述符，作为 Finder 或特定 Finder 方法返回参数的一部分。  这两个类型描述符显示在**“关联编辑器”**中。  若要创建 `Contact` 实体和 `SalesOrder` 实体之间基于外键的关联，请选择每个字段旁边的 `ContactID` 标识符。  
  
 将代码添加到源实体中可返回目标实体集合的关联导航方法。  下面的示例返回一个联系人的销售订单。  
  
 [!code-csharp[SP_BDC#7](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#7)]
 [!code-vb[SP_BDC#7](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#7)]  
  
 将代码添加到目标实中可返回源实体的关联导航方法。  下面的示例返回与销售订单相关的联系人。  
  
 [!code-csharp[SP_BDC#8](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/salesorderservice.cs#8)]
 [!code-vb[SP_BDC#8](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/salesorderservice.vb#8)]  
  
### 无外键的关联  
 可以创建一个无需将标识符映射到字段类型描述符的关联。  当源实体与目标实体没有直接关系时，请创建这种类型的关联。  例如，`SalesOrderDetail` 表没有映射到 `Contact` 表中主键的外键。  
  
 如果要显示与 `Contact` 相关的 `SalesOrderDetail` 表中的信息，可以在 `Contact` 实体和 `SalesOrderDetail` 实体之间创建无外键的关联。  
  
 在 `Contact` 实体的关联导航方法中，可通过联接表或调用存储过程来返回 `SalesOrderDetail` 实体。  
  
 下面的示例通过联接表返回所有销售订单的详细信息。  
  
 [!code-csharp[SP_BDC#9](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#9)]
 [!code-vb[SP_BDC#9](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#9)]  
  
 在 `SalesOrderDetail` 实体的关联导航方法中，将返回相关的 `Contact`。  下面的示例说明了这一点。  
  
 [!code-csharp[SP_BDC#10](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/salesorderdetailservice.cs#10)]
 [!code-vb[SP_BDC#10](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/salesorderdetailservice.vb#10)]  
  
## 请参阅  
 [设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [如何：创建实体之间的关联](../sharepoint/how-to-create-an-association-between-entities.md)  
  
  