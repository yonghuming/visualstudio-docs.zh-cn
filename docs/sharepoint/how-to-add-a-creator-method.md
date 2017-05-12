---
title: "如何：添加 Creator 方法"
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
  - "BDC [Visual Studio 中的 SharePoint 开发], 添加实体"
  - "BDC [Visual Studio 中的 SharePoint 开发], 添加实体实例"
  - "BDC [Visual Studio 中的 SharePoint 开发], 创建者"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 添加实体"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 添加实体实例"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 创建者"
ms.assetid: 52f0382f-10a0-4a51-83fe-6f22f4647df8
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# 如何：添加 Creator 方法
  Creator 方法向实体的数据源添加新数据。  当用户选择基于模型的列表功能区上的**“新建项”**按钮时，业务数据连接 \(BDC\) 服务将调用此方法。  有关详细信息，请参阅[设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
### 添加 Creator 方法  
  
1.  在 BDC 设计器中选择一个实体。  
  
2.  在菜单栏上，依次选择 **视图**，**其他窗口**，**BDC 方法详细信息**。  
  
     将打开**“BDC 方法详细信息”**窗口。  有关此窗口的更多信息，请参见 [BDC 模型设计工具概述](../sharepoint/bdc-model-design-tools-overview.md)。  
  
3.  在 **添加方法** 列表中，选择 **创建 Creator 方法**。  
  
     Visual Studio 将以下元素添加到模型，因此，这些元素将显示在 **BDC 方法详细信息** 窗口。  
  
    -   一个名为**“Create”**的方法。  
  
    -   该方法的输入参数。  
  
    -   该方法的返回参数。  
  
    -   参数的类型描述符。  
  
    -   该方法的一个方法实例。  
  
     有关详细信息，请参阅[设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
4.  在**“解决方案资源管理器”**中，打开实体生成的服务代码文件的快捷方式，然后选择**“查看代码”**。  
  
     在代码编辑器中打开实体服务代码文件。  有关实体服务代码文件的更多信息，请参见[创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
5.  在 Creator 方法中添加用于向数据源添加数据的代码。  下面的示例向 SQL Server 的 AdventureWorks 示例数据库添加联系人。  
  
    > [!NOTE]  
    >  用您的服务器名称替换 `ServerName` 字段的值。  
  
     [!code-csharp[SP_BDC#4](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#4)]
     [!code-vb[SP_BDC#4](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#4)]  
  
## 请参阅  
 [设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [如何：添加 Finder 方法](../sharepoint/how-to-add-a-finder-method.md)   
 [如何：添加特定的 Finder 方法](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [如何：添加 Deleter 方法](../sharepoint/how-to-add-a-deleter-method.md)   
 [如何：添加 Updater 方法](../sharepoint/how-to-add-an-updater-method.md)   
 [BDC 模型设计工具概述](../sharepoint/bdc-model-design-tools-overview.md)   
 [如何：向方法添加参数](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [如何：定义方法实例](../sharepoint/how-to-define-a-method-instance.md)  
  
  