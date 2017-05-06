---
title: "如何：自定义 SharePoint 解决方案包"
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
  - "VS.SharePointTools.RAD.PackageDesignerAdvanced"
  - "VS.SharePointTools.RAD.PackageDesigner.Manifest"
  - "VS.SharePointTools.RAD.PackageDesignerProperties"
  - "VS.SharePointTools.RAD.PackageDesigner.SwitchView"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 开发, 包"
ms.assetid: fd365f8c-8a80-4ce8-8e28-c0eb609f12f3
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# 如何：自定义 SharePoint 解决方案包
  可以使用包设计器来创建并自定义包 \(.wsp\)。  例如，可以添加 SharePoint 项目项和功能，指定在部署解决方案时是否重置 Web 服务器，以及设置部署服务器类型。  
  
## 打开“包设计器”  
  
#### 打开“包设计器”  
  
-   在 **解决方案资源管理器**中，双击 **包**或选择快捷菜单上的 **查看设计器** 中的 **包**。  
  
## 查看打包的清单文件  
 可以使用包设计器来修改并生成打包的清单文件。  然后，可以在 Visual Studio 中查看此文件的 XML 代码。  
  
#### 查看 XML 源文件  
  
1.  在 **包设计器**中，选择 **清单**。  
  
#### 使用解决方案资源管理器查看打包的清单文件  
  
1.  在**“解决方案资源管理器”**中选择**“显示所有文件”**。  
  
2.  展开包，展开 Package.package，然后打开 Package.Template.xml 文件。  
  
    > [!NOTE]  
    >  当打开包模板清单 XML 文件时，将自动验证这些文件，您可以忽略“错误列表”窗口中显示的警告。  
  
## 更改清单模板  
 可以在 Visual Studio XML 编辑器或“清单模板”窗格中更改打包的清单文件的 XML 代码。  对 XML 代码所做的任何更改都将合并到打包的清单文件中。  
  
#### 使用 XML 编辑器更改清单模板  
  
1.  在 **包设计器**中，选择 **清单** 选项卡，展开 **编辑选项** 节点，然后选择 **在 XML 编辑器中打开** 链接。  
  
     对 XML 所做的更改将合并到打包的清单文件中。  
  
#### 使用“清单模板”窗格更改清单模板  
  
1.  在 **包设计器**中，选择 **清单** 选项卡，展开 **编辑选项** 节点，然后更改"清单模板"窗格中显示的 XML。  
  
     对 XML 所做的更改将显示在**“预览打包的清单”**窗格中。  
  
## 覆盖打包的清单文件  
 可以禁用包设计器并手动创建 manifest.xml 文件。  第一次执行此过程时，包设计器中的当前设置将保存到包模板 XML 文件中。  然后，可以修改或覆盖 XML 代码。  
  
> [!NOTE]  
>  如果在禁用包设计器的情况下，在 XML 文件中添加或移除 SharePoint 项目项和功能，则不会对这些项目项和功能打包。  
  
#### 通过禁用设计器覆盖打包的清单文件  
  
1.  在“包设计器”中，选择"清单"选项卡。  
  
2.  .  
  
3.  展开 **编辑选项** 节点，选择 **覆盖生成的 XML，并在 XML 编辑器中编辑清单** 链接，然后选择 **是** 按钮。  
  
     使用当前打包的清单文件更新模板。  
  
## 启用包设计器  
 可以重新启用包设计器来自定义 manifest.xml 文件。  
  
#### 重新启用设计器  
  
1.  在 **包设计器**中，选择 **丢弃标记编辑并重新启用设计器** 链接，然后选择 **是** 按钮。  
  
     将使用原始文本刷新模板，对 XML 所做的任何更改都将丢失。  
  
## 请参阅  
 [打包和部署 SharePoint 解决方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  