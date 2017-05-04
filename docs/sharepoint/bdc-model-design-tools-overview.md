---
title: "BDC 模型设计工具概述 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.BDC.Method_Details"
  - "VS.SharePointTools.BDC.Explorer"
  - "VS.SharePointTools.BDC.Diagram"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [Visual Studio 中的 SharePoint 开发], BDC 资源管理器"
  - "BDC [Visual Studio 中的 SharePoint 开发], 设计器"
  - "BDC [Visual Studio 中的 SharePoint 开发], 方法详细信息"
  - "BDC [Visual Studio 中的 SharePoint 开发], 可视化工具"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], BDC 资源管理器"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 设计器"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 方法详细信息"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 可视化工具"
ms.assetid: dbd7b746-9e93-4ed4-a546-4a6f17a4725f
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# BDC 模型设计工具概述
  可以通过使用 BDC 设计器、**“BDC 方法详细信息”**窗口和**“BDC 资源管理器”**来设计业务数据连接 \(BDC\) 模型。  
  
 **“BDC 资源管理器”**可用于浏览模型、搜索模型和定义类型描述符。  
  
## BDC 设计器  
 BDC 设计器可用于定义模型中的实体，并且直观地排列实体之间的关系。  使用 BDC 设计器可完成下列任务：  
  
-   向模型添加实体。  
  
-   从模型中移除实体。  
  
-   定义实体之间的关系。  
  
 打开 BDC 设计器，请双击项目中的模型文件或打开模型文件的快捷菜单，然后选择 **打开**。  通过将**“实体”**从**“工具箱”**拖动或复制到设计器，可将实体添加到模型。  若要创建两个实体之间的关联，请选择**“工具箱”**中的**“关联组”**，选择第一个实体，然后选择第二个实体。  
  
## “BDC 方法详细信息”窗口  
 使用**“BDC 方法详细信息”**窗口定义方法的参数、实例和筛选器描述符。  
  
 在**“BDC 方法详细信息”**中，可以快速生成 Finder 方法、特定的 Finder 方法、Creator 方法、Updater 方法和 Deleter 方法。  生成这些方法时，Visual Studio 将向方法添加参数、实例和类型描述符等元数据。  您可以修改此元数据以满足具体方案的要求。  
  
 若要打开**“BDC 方法详细信息”**窗口，在菜单栏上，选择**“视图”**，**“其他窗口”**，**“BDC 方法详细信息”**。  
  
 若要查看**“BDC 方法详细信息”**窗口中的方法，请在 BDC 设计器中选择实体。  所选实体的方法显示在**“BDC 方法详细信息”**窗口中。  如果没有在 BDC 设计器中选择实体，则**“BDC 方法详细信息”**窗口不会显示任何信息。  
  
 展开或折叠**“BDC 方法详细信息”**窗口中的节点以定义参数、实例和筛选器描述符。  使用**“BDC 资源管理器”**定义类型描述符。  
  
## BDC 资源管理器  
 **“BDC 资源管理器”**可显示模型的组成元素。  若要打开 **BDC 资源管理器**，请在菜单栏上，依次选择 **视图**，**其他窗口**，**BDC 资源管理器**。  若要浏览模型，请展开**“BDC 资源管理器”**中的节点。  每个节点表示模型文件的 XML 中的一个元素。  
  
 在**“BDC 资源管理器”**中选择节点时，**“属性”**窗口中将显示所选节点的属性。  这些属性中的许多属性对应于模型文件中的特性。  通过使用**“BDC 资源管理器”**顶部的搜索框，可以搜索模型。  
  
> [!NOTE]  
>  **“BDC 资源管理器”**不显示标识符、自定义属性、已本地化的字符串、关联组、操作、筛选器描述符、操作控件列表和默认参数值。  
  
### 定义类型描述符  
 使用**“BDC 资源管理器”**定义类型描述符。  使用 BDC 资源管理器，只需将类型描述符定义一次，然后就可在模型中的其他位置重用该类型描述符。  若要实现此目的，请复制类型描述符并将其粘贴到任何其他参数或类型描述符。  
  
> [!NOTE]  
>  对原始类型描述符所做的更改不会影响该类型描述符的副本。  
  
 有关详细信息，请参阅[如何：定义参数的类型描述符](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)。  
  
## 请参阅  
 [如何：创建 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)   
 [如何：向模型添加实体](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [如何：添加 Finder 方法](../sharepoint/how-to-add-a-finder-method.md)   
 [如何：添加特定的 Finder 方法](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [如何：添加 Creator 方法](../sharepoint/how-to-add-a-creator-method.md)   
 [如何：添加 Deleter 方法](../sharepoint/how-to-add-a-deleter-method.md)   
 [如何：添加 Updater 方法](../sharepoint/how-to-add-an-updater-method.md)   
 [创建实体之间的关联](../sharepoint/creating-an-association-between-entities.md)   
 [演练：使用业务数据在 SharePoint 中创建外部列表](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)   
 [将业务数据集成到 SharePoint 中](../sharepoint/integrating-business-data-into-sharepoint.md)   
 [创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  