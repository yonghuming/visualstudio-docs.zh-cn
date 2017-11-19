---
title: "将业务数据集成到 SharePoint |Microsoft 文档"
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
- Business Data Connectivity service [SharePoint development in Visual Studio], business data
- BDC [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], business data
- Business Data Connectivity service [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], data
- BDC [SharePoint development in Visual Studio], data
ms.assetid: e092e3d6-2c5f-4060-ae86-d37db8967559
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ece3128c2d6850a1d1dd22d0328a4ee2c46da2b1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="integrating-business-data-into-sharepoint"></a>将业务数据集成到 SharePoint 中
  可以将业务数据集成到 SharePoint。 业务数据可以来自从后端服务器应用程序，如[!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)]，Siebel 和 SAP，或 Web 服务。 用户可以查看、 添加、 更新或通过使用外部列表或业务数据 Web 部件在 SharePoint 中删除业务数据。  用户还可以访问此数据的 Microsoft Office 应用程序，例如 Microsoft Outlook 中脱机。 有关详细信息，请参阅[其中可以你显示外部数据](http://go.microsoft.com/fwlink/?LinkId=169295)。  
  
 若要将数据集成到 SharePoint，创建业务数据连接 (BDC) 服务的型号。 BDC 服务是将数据的信息存储在业务应用程序中的 SharePoint 中的应用程序。 有关详细信息，请参阅[业务数据连接 (BDC) 服务](http://go.microsoft.com/fwlink/?LinkID=169276)。  
  
## <a name="models-in-visual-studio"></a>Visual Studio 中的模型  
 Visual Studio 中的模型，可以编写自定义代码，以检索和更新后端数据源中的数据。 你还可以从多个数据源的聚合数据。 例如，可以显示一个包含中的数据的客户列表[!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)]数据库和 Web 服务。  
  
 你还可以导入已部署到 SharePoint 的模型。 导入模型后，你可以添加自定义代码或只需使用 Visual Studio 打包和部署到多个 SharePoint 服务器场的模型。 有关详细信息，请参阅[创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
## <a name="designing-a-model-in-visual-studio"></a>设计 Visual Studio 中的模型  
 你可以通过使用设计器和多个工具窗口设计一个模型。 设计模型时，Visual Studio 将生成模型 XML。 有关详细信息，请参阅[BDC 模型设计工具概述](../sharepoint/bdc-model-design-tools-overview.md)。  
  
 模型包含实体和方法。  
  
### <a name="entities"></a>实体  
 实体描述字段的集合。 例如，实体可以表示数据库中的表。 实体显示为在 SharePoint 中的外部内容类型。 有关外部内容类型的详细信息，请参阅[外部内容类型是什么？](http://go.microsoft.com/fwlink/?LinkId=169293)  
  
### <a name="methods"></a>方法  
 要执行的操作的实体字段上的外部内容类型的使用者可以使用方法。 例如，Updater 方法可能会使用户能够更改地址，并出生日期客户其中`Address`和`BirthDate`是字段的`Customer`实体。  
  
 Visual Studio 生成在模型中的每个实体的服务代码文件。 当你将方法添加到您的模型时，Visual Studio 将生成在服务代码文件中相应的方法。 将代码添加到每个方法来执行相应的任务。 例如，如果向模型添加 Creator 方法，Visual Studio 在你的服务代码文件中生成的创建者方法。 当用户单击时，调用此方法由 BDC 服务**新项**基于模型的列表中的按钮。 因此，将代码添加到将新数据添加到数据源的创建者方法。 有关详细信息，请参阅[设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
## <a name="related-topics"></a>相关主题  
  
|标题|描述|  
|-----------|-----------------|  
|[创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)|演示如何创建新模型或导入从 SharePoint 导出模型。|  
|[设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)|说明如何通过使用 Visual Studio 设计工具来设计模型的元素。|  
|[何时使用 SharePoint Designer vs。使用 BCS 的 visual Studio 在生成解决方案](http://go.microsoft.com/fwlink/?LinkID=183448)|帮助您决定是否要使用 Visual Studio 或 SharePoint Designer 用于创建为 BDC 模型。|  
  
  