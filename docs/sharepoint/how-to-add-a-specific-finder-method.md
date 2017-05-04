---
title: "如何：添加特定的 Finder 方法 | Microsoft Docs"
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
  - "BDC [Visual Studio 中的 SharePoint 开发], 获取实体"
  - "BDC [Visual Studio 中的 SharePoint 开发], 返回实体"
  - "BDC [Visual Studio 中的 SharePoint 开发], 特定的 Finder"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 获取实体"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 返回实体"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 特定的 Finder"
ms.assetid: 7bbc5986-2828-4755-96fa-9f1dc0f8dc75
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# 如何：添加特定的 Finder 方法
  可以通过创建特定的 Finder 方法返回单个实体实例。  如果用户在业务数据 Web 部件或外部列表中选择了一个实体，则业务数据连接 \(BDC\) 服务将执行特定的 Finder 方法。  有关详细信息，请参阅[设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
### 创建特定的 Finder 方法  
  
1.  在 BDC 设计器中选择一个实体。  
  
     有关如何在 Visual Studio 中将实体添加到 BDC 设计器的更多信息，请参见[如何：向模型添加实体](../sharepoint/how-to-add-an-entity-to-a-model.md)。  
  
2.  在菜单栏上，依次选择 **视图**，**其他窗口**，**BDC 方法详细信息**。  
  
     将打开**“BDC 方法详细信息”**窗口。  有关此窗口的更多信息，请参见 [BDC 模型设计工具概述](../sharepoint/bdc-model-design-tools-overview.md)。  
  
3.  在 **添加方法** 列表中，选择 **创建特定的查找方法**。  
  
     Visual Studio 将以下元素添加到模型中。  这些元素将显示在**“BDC 方法详细信息”**窗口中。  
  
    -   方法。  
  
    -   该方法的输入参数。  
  
    -   该方法的返回参数。  
  
    -   每个参数的类型描述符。  
  
    -   该方法的一个方法实例。  
  
     有关详细信息，请参阅[设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
4.  打开 Visual Studio 的**“属性”**窗口。  
  
5.  将返回参数的类型说明符配置为实体类型说明符。  有关如何创建实体类型说明符的信息，请参见[如何：定义参数的类型描述符](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)。  
  
    > [!NOTE]  
    >  如果已向实体添加特定的 Finder 方法，则不必执行此步骤。  Visual Studio 将使用您在特定的 Finder 方法中定义的类型说明符。  
  
    > [!NOTE]  
    >  如果实体类型的标识符字段表示数据库表中自动生成的字段，则将该标识符字段的**“只读”**属性设置为**“True”**。  
  
6.  在**“方法详细信息”**窗口中，选择方法的方法实例。  
  
7.  在**“属性窗口”**中，将**“返回参数名称”**属性设置为该方法的返回参数的名称。  有关方法实例属性的更多信息，请参见 [方法实例](http://go.microsoft.com/fwlink/?LinkID=169282)。  
  
8.  在**“解决方案资源管理器”**中，打开实体生成的服务代码文件的快捷方式，然后选择**“查看代码”**。  
  
     在代码编辑器中打开实体服务代码文件。  有关实体服务代码文件的更多信息，请参见[创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
9. 将代码添加到特定的 Finder 方法。  这段代码执行下列任务：  
  
    -   从数据源中检索记录。  
  
    -   将实体返回到 BDC 服务。  
  
     下面的示例返回 SQL Server 的 AdventureWorks 示例数据库中的联系人。  
  
    > [!NOTE]  
    >  用您的服务器名称替换 `ServerName` 字段的值。  
  
     [!code-csharp[SP_BDC#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#3)]  
  
## 请参阅  
 [设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [如何：添加 Finder 方法](../sharepoint/how-to-add-a-finder-method.md)   
 [如何：添加 Creator 方法](../sharepoint/how-to-add-a-creator-method.md)   
 [如何：添加 Deleter 方法](../sharepoint/how-to-add-a-deleter-method.md)   
 [如何：添加 Updater 方法](../sharepoint/how-to-add-an-updater-method.md)   
 [BDC 模型设计工具概述](../sharepoint/bdc-model-design-tools-overview.md)   
 [如何：向方法添加参数](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [如何：定义方法实例](../sharepoint/how-to-define-a-method-instance.md)  
  
  