---
title: "如何：自定义 SharePoint 功能"
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
  - "VS.SharePointTools.RAD.FeatureDesigner.SwitchView"
  - "VS.SharePointTools.RAD.featureDesigner.Manifest"
  - "VS.SharePointTools.RAD.FeatureDesignerProperties"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 开发, 功能"
ms.assetid: e624c546-564b-4c73-9f1b-dc3675e76a55
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# 如何：自定义 SharePoint 功能
  通过使用 Visual Studio 中的功能设计器，可以创建并自定义 SharePoint 功能。  例如，可以设置功能作用域，并将其他功能添加为依赖项。  默认情况下，当您在解决方案资源管理器或 SharePoint 包资源管理器中添加新功能时，将会打开“功能设计器”。  
  
## 打开“功能设计器”  
 可以使用功能设计器在一个功能中添加或移除 SharePoint 项目项。  
  
#### 打开“功能设计器”  
  
1.  在**“解决方案资源管理器”**中展开**“功能”**。  
  
2.  双击 *Feature1* 项或打开 *Feature1* 项的快捷菜单，然后选择 **查看设计器**。  
  
## 查看打包的清单文件  
 可以使用功能设计器来修改并生成功能的打包的清单文件 \(feature.xml\)。  然后，可以在 Visual Studio 中查看此文件的 XML 代码。  
  
#### 查看打包的清单文件  
  
1.  在“功能设计器”中，选择“清单”选项卡。  
  
#### 使用解决方案资源管理器查看打包的清单文件  
  
1.  在**“解决方案资源管理器”**中，选择**“显示所有文件”**标志。  
  
2.  扩展功能，展开 FeatureName，展开 FeatureName.feature，然后打开 *FeatureName*Template.xml 文件。  
  
    > [!NOTE]  
    >  当打开功能模板清单 XML 文件时，将自动验证这些文件，您可以忽略“错误列表”窗口中显示的警告。  
  
## 更改清单模板  
 可以在 Visual Studio XML 编辑器或“清单模板”窗格中更改功能清单文件的 XML 代码。  对 XML 代码所做的任何更改都将合并到功能的打包的清单文件中。  例如，您可能想更改清单模板以自定义功能属性。  
  
#### 使用 XML 编辑器更改清单模板  
  
1.  在 **功能设计器**中，选择 **清单** 选项卡，展开 **编辑选项** 节点，然后选择 **在 XML 编辑器中打开** 链接。  
  
     对 XML 所做的更改将合并到打包的清单文件中。  
  
#### 使用“清单模板”窗格更改清单模板  
  
1.  在 **功能设计器**中，选择 **清单** 选项卡，展开 **编辑选项** 节点，然后更改"清单模板"窗格中显示的 XML。  
  
     对 XML 所做的更改将显示在**“预览打包的清单”**窗格中。  
  
## 覆盖打包的清单文件  
 可以禁用功能设计器并手动创建 feature.xml 文件。  第一次执行此过程时，功能设计器中的当前设置将保存到功能模板 XML 文件中。  然后，可以修改或覆盖 XML 代码。  
  
> [!NOTE]  
>  如果在禁用功能设计器的情况下在 XML 文件中添加或移除 SharePoint 项目项，则不会对这些项目项打包。  
  
#### 通过禁用设计器覆盖打包的清单文件  
  
1.  在“功能设计器”中，选择“清单”选项卡。  
  
2.  展开 **编辑选项** 节点，选择 **覆盖生成的 XML，并在 XML 编辑器中编辑清单** 链接，然后选择 **是** 按钮。  
  
     使用当前打包的清单文件更新模板。  
  
## 启用功能设计器  
 可以重新启用功能设计器来自定义 feature.xml 文件。  
  
#### 重新启用设计器  
  
1.  在 **功能设计器**中，选择 **丢弃标记编辑并重新启用设计器** 链接，然后选择 **是** 按钮。  
  
2.  将使用原始文本刷新模板，对 XML 所做的任何更改都将丢失。  
  
## 请参阅  
 [打包和部署 SharePoint 解决方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  