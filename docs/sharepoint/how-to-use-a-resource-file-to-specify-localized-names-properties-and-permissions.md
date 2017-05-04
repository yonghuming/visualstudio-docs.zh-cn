---
title: "如何：使用资源文件指定本地化名称、属性和权限 | Microsoft Docs"
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
  - "BDC [Visual Studio 中的 SharePoint 开发], 本地化字符串"
  - "BDC [Visual Studio 中的 SharePoint 开发], 属性"
  - "BDC [Visual Studio 中的 SharePoint 开发], 资源文件"
  - "BDC [Visual Studio 中的 SharePoint 开发], 资源字符串"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 本地化字符串"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 属性"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 资源文件"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 资源字符串"
ms.assetid: 72bb744d-818b-4e5a-9da2-295412025680
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# 如何：使用资源文件指定本地化名称、属性和权限
  通过使用资源文件，您可以在业务数据连接 \(BDC\) 模型中定义的器对象，提供本地化名称，定义属性和应用权限。  若要指定此信息，请您向包含**“业务数据连接模型”**项的项目添加**“业务数据连接资源”**项。  然后您通过编辑 XML 资源文件，指定名称、属性和权限。  
  
### 将 BDC 资源文件添加到 SharePoint 项目  
  
1.  在**“解决方案资源管理器”**中，在 SharePoint 项目展开文件夹，然后选择包含 BDC 模型的文件夹。  
  
2.  在菜单栏上，依次选择**“项目”**、**“添加新项”**。  
  
3.  展开 **SharePoint** 节点，然后选择 **2010** 节点。  
  
4.  在**“添加新项”**对话框中，选择**“业务数据连接资源项”**。  
  
5.  在**“名称”**框中，指定资源文件的名称，然后选择**“添加”**按钮。  
  
     已将扩展名为 .bdcr 的资源文件添加到项目中打开并编辑。  
  
6.  添加 XML 以定义要应用 BDC 模型的本地化名称、属性和访问权限。  
  
     有关如何定义这些元素的信息，请参见 [模型和资源文件](http://go.microsoft.com/fwlink/?LinkID=169283)。  
  
## 请参阅  
 [如何：向 SharePoint 项目添加现有 BDC 模型文件](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [如何：创建 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)   
 [如何：在 BDC 功能中引入自定义程序集](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [将业务数据集成到 SharePoint 中](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  