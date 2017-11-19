---
title: "如何： 添加 Finder 方法 |Microsoft 文档"
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
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], get entities
- Business Data Connectivity service [SharePoint development in Visual Studio], return entities
- BDC [SharePoint development in Visual Studio], return entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Finder method
- Business Data Connectivity service [SharePoint development in Visual Studio], get entities
- BDC [SharePoint development in Visual Studio], Finder method
ms.assetid: 5de2cae3-d1f7-4a68-aac0-458967aca692
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f0aa8888456d75554b2270058b844c7f76cb63fb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-finder-method"></a>如何：添加 Finder 方法
  若要启用业务数据连接服务，以显示 web 部件或列表中的实体的列表，你必须创建*Finder*方法。 Finder 方法是返回的实体实例的集合的特殊方法。 有关详细信息，请参阅[设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
### <a name="to-create-a-finder-method"></a>若要创建 Finder 方法  
  
1.  在 BDC 设计器中，选择实体。  
  
     有关详细信息，请参阅[如何： 向模型添加实体](../sharepoint/how-to-add-an-entity-to-a-model.md)。  
  
2.  在菜单栏上，选择**视图**，**其他窗口**， **BDC 方法详细信息**。  
  
     **BDC 方法详细信息**窗口随即打开。 有关详细信息**BDC 方法详细信息**窗口中，请参阅[BDC 模型设计工具概述](../sharepoint/bdc-model-design-tools-overview.md)。  
  
3.  在**添加一个方法**列表中，选择**创建 Finder 方法**。  
  
     Visual Studio 添加方法、 返回的参数，并将类型描述符。  
  
4.  将类型描述符配置为实体集合类型描述符。 有关如何创建实体集合类型描述符的详细信息，请参阅[如何： 定义参数的类型描述符](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)。  
  
    > [!NOTE]  
    >  无需执行此步骤，如果你已向该实体添加特定的 Finder 方法。 Visual Studio 将使用特定的 Finder 方法中定义的类型描述符。  
  
5.  在**解决方案资源管理器**，打开实体，已生成的服务代码文件的快捷菜单，然后选择**查看代码**。 有关服务代码文件的详细信息，请参阅[创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
6.  将代码添加到 Finder 方法。 这段代码执行下列任务：  
  
    -   从数据源检索数据。  
  
    -   到 BDC 服务返回实体的列表。  
  
     下面的示例返回的集合`Contact`通过使用用于 SQL Server 的 AdventureWorks 示例数据库中的数据的实体。  
  
    > [!NOTE]  
    >  值替换`ServerName`字段替换为你的服务器的名称。  
  
     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]  
  
## <a name="see-also"></a>另请参阅  
 [BDC 模型设计工具概述](../sharepoint/bdc-model-design-tools-overview.md)   
 [设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [如何： 添加特定的 Finder 方法](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [如何： 添加 Creator 方法](../sharepoint/how-to-add-a-creator-method.md)   
 [如何： 添加 Deleter 方法](../sharepoint/how-to-add-a-deleter-method.md)   
 [如何： 添加 Updater 方法](../sharepoint/how-to-add-an-updater-method.md)   
 [如何： 向方法添加参数](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [如何：定义方法实例](../sharepoint/how-to-define-a-method-instance.md)  
  
  