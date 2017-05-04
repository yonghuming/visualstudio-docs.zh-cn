---
title: "如何：使用 MSBuild 任务创建 SharePoint 解决方案包 | Microsoft Docs"
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
  - "Visual Studio 中的 SharePoint 开发, 包"
ms.assetid: c3880bdd-f0a1-4d53-9a97-5767cb3f7b8e
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# 如何：使用 MSBuild 任务创建 SharePoint 解决方案包
  可以在开发计算机上使用命令行 MSBuild 任务来生成、清理和验证 SharePoint 包 \(.wsp\)。  通过在生成计算机上使用 Team Foundation Server，也可以使用这些命令来自动执行生成过程。  
  
## 生成 SharePoint 包  
  
#### 生成 SharePoint 包  
  
1.  在 Windows **开始** 菜单中，选择 **所有程序**，**附件**，**命令提示**。  
  
2.  更改为您的 SharePoint 项目所在的目录。  
  
3.  键入下面的命令以创建项目包。  用项目的名称替换*ProjectFileName*。  
  
    ```  
    msbuild /t:Package ProjectFileName  
    ```  
  
     例如，可以运行以下命令之一来打包名为 ListDefinition1 的 SharePoint 项目。  
  
    ```  
    msbuild /t:Package ListDefinition1.vbproj  
    msbuild /t:Package ListDefinition1.csproj  
    ```  
  
## 清理 SharePoint 包  
  
#### 清理 SharePoint 包  
  
1.  打开命令提示符窗口。  
  
2.  更改为您的 SharePoint 项目所在的目录。  
  
3.  键入下面的命令以清理项目包。  用项目的名称替换*ProjectFileName*。  
  
    ```  
    msbuild /t:CleanPackage ProjectFileName  
    ```  
  
     例如，可以运行以下命令之一来清理名为 ListDefinition1 的 SharePoint 项目。  
  
    ```  
    msbuild /t:CleanPackage ListDefinition1.vbproj  
    msbuild /t:CleanPackage ListDefinition1.csproj  
    ```  
  
## 验证 SharePoint 包  
  
#### 验证 SharePoint 包  
  
1.  打开命令提示符窗口。  
  
2.  更改为您的 SharePoint 项目所在的目录。  
  
3.  键入下面的命令以验证项目包。  用项目的名称替换*ProjectFileName*。  
  
    ```  
    msbuild /t:ValidatePackage ProjectFileName  
    ```  
  
     例如，可以运行以下命令之一来验证名为 ListDefinition1 的 SharePoint 项目。  
  
    ```  
    msbuild /t:ValidatePackage ListDefinition1.vbproj  
    msbuild /t:ValidatePackage ListDefinition1.csproj  
    ```  
  
## 设置 SharePoint 包中的属性  
  
#### 设置 SharePoint 包中的属性  
  
1.  打开命令提示符窗口。  
  
2.  更改为您的 SharePoint 项目所在的目录。  
  
3.  键入下面的命令以设置项目包中的属性。  用要设置的属性替换 *PropertyName*。  
  
    ```  
    msbuild /property:PropertyName=Value  
    ```  
  
     例如，可以运行下面的命令来设置警告等级。  
  
    ```  
    msbuild /property:WarningLevel = 2  
    ```  
  
## 请参阅  
 [创建 SharePoint 功能](../sharepoint/creating-sharepoint-features.md)   
 [如何：自定义 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [如何：在 SharePoint 功能中添加和移除项](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
  