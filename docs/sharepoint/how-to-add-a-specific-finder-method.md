---
title: "如何： 添加特定的 Finder 方法 |Microsoft 文档"
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
- Business Data Connectivity service [SharePoint development in Visual Studio], Specific Finder
- BDC [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], get an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], Specific Finder
- Business Data Connectivity service [SharePoint development in Visual Studio], get an entity
ms.assetid: 7bbc5986-2828-4755-96fa-9f1dc0f8dc75
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c7b2277d725259fb5f95c186825773b5460ec17d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-specific-finder-method"></a>如何：添加特定的 Finder 方法
  你可以通过创建返回单个实体实例*特定的 Finder*方法。 业务数据连接 (BDC) 服务执行特定的 Finder 方法，当用户在业务数据 web 部件或外部列表中选择实体。 有关详细信息，请参阅[设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
### <a name="to-create-a-specific-finder-method"></a>若要创建特定的 Finder 方法  
  
1.  在 BDC 设计器中，选择实体。  
  
     有关如何将实体添加到 BDC 设计器在 Visual Studio 中的信息，请参阅[如何： 向模型添加实体](../sharepoint/how-to-add-an-entity-to-a-model.md)。  
  
2.  在菜单栏上，选择**视图**，**其他窗口**， **BDC 方法详细信息**。  
  
     **BDC 方法详细信息**窗口随即打开。 有关该窗口的详细信息，请参阅[BDC 模型设计工具概述](../sharepoint/bdc-model-design-tools-overview.md)。  
  
3.  在**添加一个方法**列表中，选择**创建特定的 Finder 方法**。  
  
     Visual Studio 将以下元素添加到模型。 这些元素出现在**BDC 方法详细信息**窗口。  
  
    -   方法。  
  
    -   输入的参数的方法。  
  
    -   返回参数的方法。  
  
    -   每个参数类型描述符。  
  
    -   方法实例的方法。  
  
     有关详细信息，请参阅[设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
4.  打开 Visual Studio**属性**窗口。  
  
5.  将返回参数的类型描述符配置为实体类型描述符。 有关如何创建实体类型描述符的信息，请参阅[如何： 定义参数的类型描述符](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)。  
  
    > [!NOTE]  
    >  你无需执行此步骤，如果你已向该实体添加 Finder 方法。 Visual Studio 将使用你在 Finder 方法中定义的类型描述符。  
  
    > [!NOTE]  
    >  如果实体类型的标识符字段所代表的字段自动生成的数据库表中，设置**只读**属性的标识符字段**True**。  
  
6.  在**方法详细信息**窗口中，选择该方法的方法实例。  
  
7.  在**属性窗口**，将其设置**返回参数名称**为该方法的返回参数的名称的属性。 方法实例属性的详细信息，请参阅[实例，但](http://go.microsoft.com/fwlink/?LinkID=169282)。  
  
8.  在**解决方案资源管理器**，打开实体，已生成的服务代码文件的快捷菜单，然后选择**查看代码**。  
  
     实体服务代码文件将在代码编辑器中打开。 有关实体服务代码文件的详细信息，请参阅[创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
9. 将代码添加到特定的 Finder 方法。 这段代码执行下列任务：  
  
    -   从数据源检索一条记录。  
  
    -   到 BDC 服务返回实体。  
  
     下面的示例适用于 SQL Server 返回从 AdventureWorks 示例数据库的联系人。  
  
    > [!NOTE]  
    >  值替换`ServerName`字段替换为你的服务器的名称。  
  
     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]  
  
## <a name="see-also"></a>另请参阅  
 [设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [如何： 添加 Finder 方法](../sharepoint/how-to-add-a-finder-method.md)   
 [如何： 添加 Creator 方法](../sharepoint/how-to-add-a-creator-method.md)   
 [如何： 添加 Deleter 方法](../sharepoint/how-to-add-a-deleter-method.md)   
 [如何： 添加 Updater 方法](../sharepoint/how-to-add-an-updater-method.md)   
 [BDC 模型设计工具概述](../sharepoint/bdc-model-design-tools-overview.md)   
 [如何： 向方法添加参数](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [如何：定义方法实例](../sharepoint/how-to-define-a-method-instance.md)  
  
  