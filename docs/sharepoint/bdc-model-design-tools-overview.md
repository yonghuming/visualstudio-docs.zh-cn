---
title: "BDC 模型设计工具概述 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.BDC.Method_Details
- VS.SharePointTools.BDC.Explorer
- VS.SharePointTools.BDC.Diagram
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], method details
- Business Data Connectivity service [SharePoint development in Visual Studio], designer
- Business Data Connectivity service [SharePoint development in Visual Studio], method details
- BDC [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], designer
ms.assetid: dbd7b746-9e93-4ed4-a546-4a6f17a4725f
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: eaf6871f7ad9316ba2dbdaa8fa29b4810b1d6a3d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="bdc-model-design-tools-overview"></a>BDC 模型设计工具概述
  你可以通过使用 BDC 设计器中，设计业务数据连接 (BDC) 模型**BDC 方法详细信息**窗口中，与**BDC 资源管理器**。  
  
 **BDC 资源管理器**使您能够浏览模型，搜索模型，并定义类型描述符。  
  
## <a name="bdc-designer"></a>BDC 设计器  
 BDC 设计器可以在你的模型中定义实体，并以可视方式与另一个中排列它们之间的关系。 BDC 设计器用于完成以下任务：  
  
-   将实体添加到模型。  
  
-   从模型中删除实体。  
  
-   定义实体之间的关系。  
  
 若要打开 BDC 设计器中，双击你的项目中的模型文件或打开模型文件的快捷菜单，然后选择**打开**。 将实体添加到模型中，通过拖动或复制**实体**从**工具箱**拖动到设计器。 若要创建两个实体之间的关联，请选择**关联**中控制**工具箱**，选择第一个实体，，然后选择第二个实体。  
  
## <a name="bdc-method-details-window"></a>BDC 方法详细信息窗口  
 使用**BDC 方法详细信息**窗口，以定义参数、 实例和筛选器的一种方法的描述符。  
  
 你可以快速生成中查找程序、 特定的 Finder、 创建者、 更新程序，和删除器方法**BDC 方法详细信息**窗口。 在生成这些方法时，Visual Studio 会将元数据，例如参数、 实例和类型描述符添加到方法。 你可以修改此元数据以满足你的特定方案。  
  
 若要打开**BDC 方法详细信息**窗口，请在菜单栏上，选择**视图**，**其他窗口**， **BDC 方法详细信息**。  
  
 若要查看中的方法**BDC 方法详细信息**窗口中，在 BDC 设计器中选择的实体。 所选实体的方法显示在**BDC 方法详细信息**窗口。 如果没有在 BDC 设计器中，选择实体**BDC 方法详细信息**窗口会显示任何信息。  
  
 展开或折叠中的节点**BDC 方法详细信息**窗口，以定义参数、 实例和筛选器描述符。 使用**BDC 资源管理器**定义类型描述符。  
  
## <a name="bdc-explorer"></a>BDC 资源管理器  
 **BDC 资源管理器**显示构成的模型的元素。 若要打开**BDC 资源管理器**，在菜单栏上，选择**视图**，**其他窗口**， **BDC 资源管理器**。 若要浏览该模型，请展开中的节点**BDC 资源管理器**。 每个节点表示模型文件的 XML 中的元素。  
  
 当您选择中的节点**BDC 资源管理器**，你选择每个节点的属性将显示在**属性**窗口。 其中的许多属性对应于模型文件中的特性。 通过在顶部搜索框中，可以搜索模型**BDC 资源管理器**。  
  
> [!NOTE]  
>  **BDC 资源管理器**不会显示标识符、 自定义属性、 本地化的字符串、 关联组、 操作、 筛选器描述符、 操作控制列表和默认参数值。  
  
### <a name="defining-type-descriptors"></a>定义类型描述符  
 使用**BDC 资源管理器**定义类型描述符。 BDC 资源管理器，可将类型描述符定义一次，然后重复使用该模型中其他位置的类型描述符。 若要实现此目的，复制的类型描述符并将其粘贴到任何其他参数或类型描述符。  
  
> [!NOTE]  
>  到原始的类型描述符的更改不会影响该类型描述符的副本。  
  
 有关详细信息，请参阅[如何： 定义参数的类型描述符](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 创建 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)   
 [如何： 向模型添加实体](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [如何： 添加 Finder 方法](../sharepoint/how-to-add-a-finder-method.md)   
 [如何： 添加特定的 Finder 方法](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [如何： 添加 Creator 方法](../sharepoint/how-to-add-a-creator-method.md)   
 [如何： 添加 Deleter 方法](../sharepoint/how-to-add-a-deleter-method.md)   
 [如何： 添加 Updater 方法](../sharepoint/how-to-add-an-updater-method.md)   
 [创建实体之间的关联](../sharepoint/creating-an-association-between-entities.md)   
 [演练： 使用业务数据在 SharePoint 中创建外部列表](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)   
 [将业务数据集成到 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)   
 [创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  