---
title: "创建业务数据连接模型 |Microsoft 文档"
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
- Business Data Connectivity service [SharePoint development in Visual Studio], model
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- SharePoint development in Visual Studio, Business Data Connectivity service
ms.assetid: 19fd12d0-a51a-4da4-98ac-918542e84507
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6661ca48321b1a19b5076beceb435e1f0c798ee0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="creating-a-business-data-connectivity-model"></a>创建业务数据连接模型
  你可以创建业务数据连接 (BDC) 模型，或通过使用 Visual Studio 中自定义现有 BDC 模型。 每个 SharePoint 项目可以包含仅有一个模型。 有关详细信息，请参阅[将业务数据集成到 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)。  
  
## <a name="creating-a-new-model"></a>创建新模型  
 若要创建新模型，创建**业务数据连接模型**项目或添加**业务数据连接模型**项以**空 SharePoint 项目**。  
  
> [!NOTE]  
>  你必须具有[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]在计算机上安装。  
  
 Visual Studio 将文件夹添加到项目。 此文件夹包含为指定的名称**业务数据连接模型**中项**添加新项**对话框。 如果你创建一个新**业务数据连接模型**项目，Visual Studio 将该文件夹命名**BdcModel1**。  
  
 Visual Studio 将以下文件添加到新文件夹：  
  
|文件|描述|  
|----------|-----------------|  
|模型定义文件|包含定义实体、 方法、 业务线 (LOB) 系统对象和其他元数据描述模型的 XML。<br /><br /> 通过使用 BDC 设计器中，修改此文件中的元数据**BDC 资源管理器**， **BDC 方法详细信息**窗口中，和**属性**窗口。|  
|实体服务代码文件|包含检索、 更新和删除默认实体的实例的方法。|  
  
 若要定义实体的属性，请编辑实体代码文件。 有关详细信息，请参阅[如何： 向模型添加实体](../sharepoint/how-to-add-an-entity-to-a-model.md)。  
  
 若要检索、 更新和删除实体的实例，请将代码添加到实体服务代码文件。 有关详细信息，请参阅[设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
 编译项目时，Visual Studio 创建程序集。 确保您希望向将代码添加到项目程序集的项目添加其他项 (例如：**顺序工作流**项或**Web 部件**项)。 因为解决方案包不会复制到全局程序集缓存的程序集部署解决方案时，将不会运行该项目的代码。  解决方案包将程序集部署到仅在 SharePoint 中的 BDC 数据库。  
  
> [!NOTE]  
>  在调试项目时，visual Studio 将程序集复制到本地计算机上的这两个位置。  
  
## <a name="adding-an-existing-model"></a>添加现有模型  
 你可以导入已通过使用其他工具，如 SharePoint Designer 创建的模型。 你可以选择要将现有模型导入你的项目在以下情况：  
  
-   若要自定义已部署到 SharePoint 服务器场的模型。  
  
-   若要打包并将现有模型部署到多个 SharePoint 服务器场。  
  
 在任一情况下，你导入模型中定义的 LOB 系统不会受到影响，并将继续按预期方式工作。 若要将现有模型添加到 SharePoint 项目中，使用 Visual Studio**添加现有项**对话框。 有关详细信息，请参阅[如何： 向 SharePoint 项目中添加现有 BDC 模型文件](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)。  
  
 你可以通过选择中的一个选项添加到导入模型类型的.NET Framework 程序集的 LOB 系统**添加.NET 程序集 LobSystem**。 这使你可以编写自定义代码和使用设计器来定义导入模型的元数据。  
  
## <a name="related-topics"></a>相关主题  
  
|标题|描述|  
|-----------|-----------------|  
|[如何：创建 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)|演示如何创建新的 BDC 模型。|  
|[如何：将现有 BDC 模型文件添加到 SharePoint 项目](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|演示如何将现有模型导入到 SharePoint 项目。|  
|[如何：使用资源文件指定本地化名称、属性和权限](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|描述如何的模型元数据时模型由 Web 部件或网页提供合并的字符串。|  
|[如何：在 BDC 功能中引入自定义程序集](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|演示如何将自定义程序集包含在该功能。|  
  
  