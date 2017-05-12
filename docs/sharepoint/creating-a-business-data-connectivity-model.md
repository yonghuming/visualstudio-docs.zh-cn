---
title: "创建业务数据连接模型"
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
  - "BDC [Visual Studio 中的 SharePoint 开发], 创建模型"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 创建模型"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 模型"
  - "Visual Studio 中的 SharePoint 开发, 业务数据连接服务"
ms.assetid: 19fd12d0-a51a-4da4-98ac-918542e84507
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# 创建业务数据连接模型
  通过使用 Visual Studio，您可以创建业务数据连接 \(BDC\) 模型或自定义现有的 BDC 模型。  每个 SharePoint 项目只能包含一个模型。  有关详细信息，请参阅[将业务数据集成到 SharePoint 中](../sharepoint/integrating-business-data-into-sharepoint.md)。  
  
## 创建新模型  
 若要创建新模型，请创建一个**“业务数据连接模型”**项目，或者向**“空 SharePoint 项目”**添加一个**“业务数据连接模型”**项。  
  
> [!NOTE]  
>  您的计算机上必须安装有 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]。  
  
 Visual Studio 向项目添加一个文件夹。  此文件夹的名称是您在**“添加新项”**对话框中为**“业务数据连接模型”**项指定的名称。  如果您创建了新的**“业务数据连接模型”**项目，Visual Studio 则将该文件夹命名为**“BdcModel1”**。  
  
 Visual Studio 向新文件夹添加以下文件：  
  
|文件|说明|  
|--------|--------|  
|模型定义文件|包含定义实体、方法、行业 \(LOB\) 系统对象的 XML 以及描述模型的其他元数据。<br /><br /> 通过使用 BDC 设计器、**“BDC 资源管理器”**、**“BDC 方法详细信息”**窗口和**“属性”**窗口修改此文件中的元数据。|  
|实体服务代码文件|包含用于检索、更新和删除默认实体实例的方法。|  
  
 若要定义实体的属性，请编辑实体代码文件。  有关详细信息，请参阅[如何：向模型添加实体](../sharepoint/how-to-add-an-entity-to-a-model.md)。  
  
 若要检索、更新和删除实体的实例，请向实体服务代码文件中添加代码。  有关详细信息，请参阅[设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
 编译项目时，Visual Studio 会创建一个程序集。  对于向项目程序集添加代码的项目，请确保不要向该项目添加其他项（例如：**“顺序工作流”**项或**“Web 部件”**项）。  部署解决方案时将不会运行该项的代码，这是因为解决方案包不会将程序集复制到全局程序集缓存。解决方案包仅在 SharePoint 中将程序集部署到 BDC 数据库。  
  
> [!NOTE]  
>  调试项目时，Visual Studio 会将程序集同时复制到本地计算机上的两个位置。  
  
## 添加现有模型  
 您可以导入使用 SharePoint 设计器等其他工具创建的模型。  在以下情况下，您可以选择向项目中导入现有模型：  
  
-   自定义已部署到 SharePoint 服务器场的模型。  
  
-   将现有模型打包并部署到多个 SharePoint 服务器场。  
  
 在任何一种情况下，导入模型中定义的 LOB 系统都不会受到影响，并将继续按预期方式工作。  若要向 SharePoint 项目添加现有模型，请使用 Visual Studio 的**“添加现有项”**对话框。  有关详细信息，请参阅[如何：向 SharePoint 项目添加现有 BDC 模型文件](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)。  
  
 通过选择**“添加 .NET 程序集 LobSystem”**中的相应选项，您可以向导入的模型添加 .NET Framework 程序集类型的 LOB 系统。  这使得您可以编写自定义代码，并使用设计器定义导入模型的元数据。  
  
## 相关主题  
  
|标题|说明|  
|--------|--------|  
|[如何：创建 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)|演示如何创建新的 BDC 模型。|  
|[如何：向 SharePoint 项目添加现有 BDC 模型文件](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|演示如何向 SharePoint 项目导入现有模型。|  
|[如何：使用资源文件指定本地化名称、属性和权限](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|描述模型由 Web 部件或网页使用时如何提供与模型元数据合并在一起的字符串。|  
|[如何：在 BDC 功能中引入自定义程序集](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|演示如何在功能中引入自定义程序集。|  
  
  