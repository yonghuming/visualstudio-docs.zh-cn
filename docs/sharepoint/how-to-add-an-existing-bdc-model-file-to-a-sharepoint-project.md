---
title: "如何：向 SharePoint 项目添加现有 BDC 模型文件 | Microsoft Docs"
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
  - "VS.SharePointTools.BDC.ImportDialog"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [Visual Studio 中的 SharePoint 开发], 导入模型"
  - "BDC [Visual Studio 中的 SharePoint 开发], 删除模型"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 导入模型"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 重用模型"
ms.assetid: e843738a-f936-4dcd-be35-249407573b74
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# 如何：向 SharePoint 项目添加现有 BDC 模型文件
  您可以自定义包，通过使用 Visual Studio ，重部署业务数据连接 \(BDC\) 模型，添加模型文件 \(.bdcm\) 到任何 SharePoint 场项目。  有关详细信息，请参阅[创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
### 将 BDC 模型文件添加到 SharePoint 项目  
  
1.  在 **解决方案资源管理器**中，选择 SharePoint 项目中的文件夹。  
  
2.  在菜单栏上，选择“项目”，“添加存在项”。  
  
3.  在**“添加现有项”**对话框中，浏览到要添加到项目中的模型定义文件所在的位置，选择文件，然后选择**“添加”**按钮。  
  
     如果该模型没有定义 “.NET 程序集类型的业务线 \(LOB\) 系统”，则会打开**“添加 .NET 程序集 LobSystem”**对话框。  
  
4.  如果出现一个对话框，请执行以下步骤之一：  
  
    -   如果要编写自定义代码和使用设计器定义导入模型的元数据，请选择按钮，**是** 按钮，命名系统，然后选择 **确定** 按钮。  
  
    -   否则，选择**“不”**按钮，然后选择**“确定”**按钮。  
  
     **“业务数据连接模型”**项便添加到项目中。  
  
## 请参阅  
 [创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [如何：创建 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)   
 [如何：使用资源文件指定本地化名称、属性和权限](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [如何：在 BDC 功能中引入自定义程序集](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [将业务数据集成到 SharePoint 中](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  