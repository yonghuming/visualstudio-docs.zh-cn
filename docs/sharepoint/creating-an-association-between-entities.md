---
title: "创建实体之间的关联 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.BDC.Association_Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associations between entities
- BDC [SharePoint development in Visual Studio], associations between entities
- Business Data Connectivity service [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associate external content types
- Business Data Connectivity service [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], associate external content types
ms.assetid: c908448c-13d3-4d2f-89ad-8d709b2958fb
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 11cf0d01c14506c3328c5d9e24456090360d4d58
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="creating-an-association-between-entities"></a>创建实体之间的关联
  你可以定义您通过创建关联的业务数据连接 (BDC) 模型中的实体之间的关系。 Visual Studio 生成的模型的使用者提供有关每个关联的信息的方法。 SharePoint Web 部件、列表或自定义应用程序可以使用这些方法在用户界面 (UI) 中显示数据关系。  
  
## <a name="creating-an-association"></a>创建的关联  
 通过选择创建关联**关联**Visual Studio 中的控件**工具箱**、 选择 （称为源实体） 的第一个实体，并选择第二个实体 (调用目标实体）。 你可以定义在中的关联的详细信息**关联编辑器**。 有关详细信息，请参阅[如何： 创建实体之间的关联](../sharepoint/how-to-create-an-association-between-entities.md)。  
  
## <a name="association-methods"></a>关联方法  
 应用程序，如 SharePoint 业务数据 web 部件使用关联的实体的服务类中调用方法。 你也可以通过选择在与服务的实体类添加方法**关联编辑器**。  
  
 默认情况下，**关联编辑器**将关联的导航方法添加到源和目标实体。 源实体中的关联导航方法允许使用者检索目标实体的列表。 目标实体中的关联导航方法允许使用者检索与目标实体相关的源实体。  
  
 必须将代码添加到每个这些方法以返回相应的信息。 你还可以添加其他类型的方法，以支持更高级的方案。 有关上述每种方法的详细信息，请参阅[支持的操作](http://go.microsoft.com/fwlink/?LinkId=169286)。  
  
## <a name="types-of-associations"></a>类型的关联  
 你可以在 BDC 设计器中创建两种类型的关联： 外基于密钥的关联和外键的关联。  
  
### <a name="foreign-key-based-association"></a>外基于密钥的关联  
 可以通过相关目标实体中定义的类型描述符的源实体中的标识符来创建外基于密钥的关联。 此关系使模型的使用者要为其用户提供增强的用户界面。 例如，在使用户能够创建可以在下拉列表; 中显示客户的销售订单的 Outlook 窗体或使用户能够为客户打开配置文件页面上的 SharePoint 中的销售订单的列表。  
  
 若要创建外基于密钥的关联，请键入共享相同的名称和类型的描述符和相关标识符。 例如，您可能创建之间外基于密钥的关联`Contact`实体和`SalesOrder`实体。 `SalesOrder`实体返回`ContactID`类型描述符 Finder 或特定的 Finder 方法的返回参数的一部分。 这两个类型描述符显示在**关联编辑器**。 若要创建之间的外键基于关系`Contact`实体和`SalesOrder`实体，选择`ContactID`旁边的各个字段的标识符。  
  
 将代码添加到返回目标实体的集合的源实体的关联导航器方法。 下面的示例返回联系人的销售订单。  
  
 [!code-csharp[SP_BDC#7](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#7)]
 [!code-vb[SP_BDC#7](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#7)]  
  
 将代码添加到目标实体返回源实体的关联导航器方法。 下面的示例返回与销售订单相关的联系人。  
  
 [!code-csharp[SP_BDC#8](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#8)]
 [!code-vb[SP_BDC#8](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#8)]  
  
### <a name="foreign-keyless-association"></a>外键的关联  
 你可以创建关联而将标识符映射到字段的类型描述符。 当源实体没有直接关系的目标实体时，请创建这种类型的关联。 例如，`SalesOrderDetail`表没有映射到中的主键的外键`Contact`表。  
  
 如果你想要信息将显示在`SalesOrderDetail`与相关的表`Contact`，你可以创建外键之间的关联`Contact`实体和`SalesOrderDetail`实体。  
  
 中的关联导航方法`Contact`实体，返回`SalesOrderDetail`实体通过联接表，或通过调用存储的过程。  
  
 下面的示例返回通过联接表的所有销售订单的详细信息。  
  
 [!code-csharp[SP_BDC#9](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#9)]
 [!code-vb[SP_BDC#9](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#9)]  
  
 中的关联导航方法`SalesOrderDetail`实体，返回相关`Contact`。 下面的示例演示这一操作。  
  
 [!code-csharp[SP_BDC#10](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#10)]
 [!code-vb[SP_BDC#10](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#10)]  
  
## <a name="see-also"></a>另请参阅  
 [设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [如何： 创建实体之间的关联](../sharepoint/how-to-create-an-association-between-entities.md)  
  
  