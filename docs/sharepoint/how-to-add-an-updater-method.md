---
title: "如何：添加 Updater 方法 | Microsoft Docs"
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
  - "BDC [Visual Studio 中的 SharePoint 开发], 更新者"
  - "BDC [Visual Studio 中的 SharePoint 开发], 更新数据"
  - "BDC [Visual Studio 中的 SharePoint 开发], 更新实体实例"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 更新者"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 更新数据"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 更新实体实例"
ms.assetid: c97e443c-58dc-4f8f-8cbd-0d52d8a6a06b
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# 如何：添加 Updater 方法
  您可以使用户通过创建 Updater 方法来更新 SharePoint 外部列表中的业务数据。  有关详细信息，请参阅[设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
### 创建 Updater 方法  
  
1.  在 BDC 设计器中选择一个实体。  
  
2.  在菜单栏上，依次选择 **视图**，**其他窗口**，**BDC 方法详细信息**。  
  
     打开“BDC 方法详细信息”窗口。  有关此窗口的更多信息，请参见 [BDC 模型设计工具概述](../sharepoint/bdc-model-design-tools-overview.md)。  
  
3.  在 **添加方法** 列表中，选择 **创建 Updater 方法**。  
  
     Visual Studio 将以下元素添加到模型中。  这些元素将显示在“BDC 方法详细信息”窗口中。  
  
    -   名为 **更新**的方法。  
  
    -   该方法的输入参数。  
  
    -   参数的类型描述符。  默认情况下，Visual Studio 将使用您为 Finder 方法定义的实体类型描述符（例如：Contact）。  
  
    -   该方法的一个方法实例。  
  
     有关详细信息，请参阅[设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
    > [!NOTE]  
    >  如果实体类型的标识符表示数据库表中非自动生成的字段，则将**“Pre\-Updater 字段”**属性设置为**“True”**。  
  
4.  在**“解决方案资源管理器”**中，打开实体生成的服务代码文件的快捷方式，然后选择**“查看代码”**。  
  
     在代码编辑器中打开实体服务代码文件。  有关文件的更多信息，请参见 [创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
5.  向 Update 方法添加代码以更新数据。  下面的示例更新 SQL Server 的 AdventureWorks 示例数据库中的联系人信息。  
  
    > [!NOTE]  
    >  用您的服务器名称替换 `ServerName` 字段的值。  
  
     [!code-csharp[SP_BDC#5](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#5)]
     [!code-vb[SP_BDC#5](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#5)]  
  
## 请参阅  
 [设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [如何：添加 Finder 方法](../sharepoint/how-to-add-a-finder-method.md)   
 [如何：添加特定的 Finder 方法](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [如何：添加 Creator 方法](../sharepoint/how-to-add-a-creator-method.md)   
 [How to: Add an Updater Method](../sharepoint/how-to-add-an-updater-method.md)   
 [如何：添加 Deleter 方法](../sharepoint/how-to-add-a-deleter-method.md)   
 [BDC 模型设计工具概述](../sharepoint/bdc-model-design-tools-overview.md)   
 [如何：向方法添加参数](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [如何：定义方法实例](../sharepoint/how-to-define-a-method-instance.md)  
  
  