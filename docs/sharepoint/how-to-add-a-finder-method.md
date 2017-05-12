---
title: "如何：添加 Finder 方法"
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
  - "BDC [Visual Studio 中的 SharePoint 开发], Finder 方法"
  - "BDC [Visual Studio 中的 SharePoint 开发], 获取实体"
  - "BDC [Visual Studio 中的 SharePoint 开发], 返回实体"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], Finder 方法"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 获取实体"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 返回实体"
ms.assetid: 5de2cae3-d1f7-4a68-aac0-458967aca692
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# 如何：添加 Finder 方法
  若要启用业务数据连接服务以显示 Web 部件或列表中实体的列表，必须创建“查找” 方法。  Finder 方法是一个用于返回实体实例集合的特殊方法。  有关详细信息，请参阅[设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
### 创建 Finder 方法  
  
1.  在 BDC 设计器中选择一个实体。  
  
     有关详细信息，请参阅[如何：向模型添加实体](../sharepoint/how-to-add-an-entity-to-a-model.md)。  
  
2.  在菜单栏上，依次选择 **视图**，**其他窗口**，**BDC 方法详细信息**。  
  
     将打开**“BDC 方法详细信息”**窗口。  有关**“BDC 方法详细信息”**窗口的更多信息，请参见 [BDC 模型设计工具概述](../sharepoint/bdc-model-design-tools-overview.md)。  
  
3.  在 **添加方法** 列表中，选择 **创建查找方法**。  
  
     Visual Studio 将添加一个方法、一个返回参数和一个类型描述符。  
  
4.  将类型描述符配置为实体集合类型描述符。  有关如何创建实体集合类型描述符的更多信息，请参见[如何：定义参数的类型描述符](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)。  
  
    > [!NOTE]  
    >  如果已向实体添加特定的 Finder 方法，则不必执行此步骤。  Visual Studio 将使用您在特定的 Finder 方法中定义的类型描述符。  
  
5.  在**“解决方案资源管理器”**中，打开实体生成的服务代码文件的快捷方式，然后选择**“查看代码”**。  有关服务代码文件的更多信息，请参见[创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
6.  将代码添加到 Finder 方法。  这段代码执行下列任务：  
  
    -   从数据源中检索数据。  
  
    -   将实体列表返回到 BDC 服务。  
  
     下面的示例使用 SQL Server 的 AdventureWorks 示例数据库中的数据，返回 `Contact` 实体的集合。  
  
    > [!NOTE]  
    >  用您的服务器名称替换 `ServerName` 字段的值。  
  
     [!code-csharp[SP_BDC#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#2)]  
  
## 请参阅  
 [BDC 模型设计工具概述](../sharepoint/bdc-model-design-tools-overview.md)   
 [设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [如何：添加特定的 Finder 方法](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [如何：添加 Creator 方法](../sharepoint/how-to-add-a-creator-method.md)   
 [如何：添加 Deleter 方法](../sharepoint/how-to-add-a-deleter-method.md)   
 [如何：添加 Updater 方法](../sharepoint/how-to-add-an-updater-method.md)   
 [如何：向方法添加参数](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [如何：定义方法实例](../sharepoint/how-to-define-a-method-instance.md)  
  
  