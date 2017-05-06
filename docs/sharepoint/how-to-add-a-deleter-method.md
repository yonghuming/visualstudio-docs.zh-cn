---
title: "如何：添加 Deleter 方法"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [Visual Studio 中的 SharePoint 开发], 删除者"
  - "BDC [Visual Studio 中的 SharePoint 开发], 删除数据"
  - "BDC [Visual Studio 中的 SharePoint 开发], 删除实体实例"
  - "BDC [Visual Studio 中的 SharePoint 开发], 删除数据"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 删除者"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 删除数据"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 删除实体实例"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 删除数据"
ms.assetid: 3362eaf4-5dc7-4450-9009-b296308ae61f
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# 如何：添加 Deleter 方法
  您可以使最终用户通过向模型添加 Deleter 方法从 SharePoint 网站上的外部列表中删除数据记录。  有关详细信息，请参阅[设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
### 创建 Deleter 方法  
  
1.  在 BDC 设计器中选择一个实体。  
  
2.  在菜单栏上，依次选择 **视图**，**其他窗口**，**BDC 方法详细信息**。  
  
     将打开**“BDC 方法详细信息”**窗口。  有关此窗口的更多信息，请参见 [BDC 模型设计工具概述](../sharepoint/bdc-model-design-tools-overview.md)。  
  
3.  在 **添加方法** 列表中，选择 **创建 Deleter 方法**。  
  
     Visual Studio 将以下元素添加到模型中。  这些元素将显示在**“BDC 方法详细信息”**窗口中。  
  
    -   一个名为**“Delete”**的方法。  
  
    -   该方法的输入参数。  
  
    -   参数的类型描述符。  
  
    -   该方法的一个方法实例。  
  
     有关详细信息，请参阅[设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
4.  在**“解决方案资源管理器”**中，打开实体生成的服务代码文件的快捷方式，然后选择**“查看代码”**。  
  
     在代码编辑器中打开实体服务代码文件。  有关实体服务代码文件的更多信息，请参见[创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
5.  向 Deleter 方法添加代码以删除记录。  下面的示例使用 SQL Server 的 AdventureWorks 示例数据库从销售订单中删除某个行项。  
  
    > [!NOTE]  
    >  该方法在此示例中使用两个输入参数。  
  
    > [!NOTE]  
    >  用您的服务器名称替换 `ServerName` 字段的值。  
  
     [!code-csharp[SP_BDC#6](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/salesorderdetailservice.cs#6)]
     [!code-vb[SP_BDC#6](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/salesorderdetailservice.vb#6)]  
  
## 请参阅  
 [设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [如何：添加 Finder 方法](../sharepoint/how-to-add-a-finder-method.md)   
 [如何：添加特定的 Finder 方法](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [如何：添加 Creator 方法](../sharepoint/how-to-add-a-creator-method.md)   
 [如何：添加 Updater 方法](../sharepoint/how-to-add-an-updater-method.md)   
 [BDC 模型设计工具概述](../sharepoint/bdc-model-design-tools-overview.md)   
 [如何：向方法添加参数](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [如何：定义方法实例](../sharepoint/how-to-define-a-method-instance.md)  
  
  