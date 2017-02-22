---
title: "项目子类型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "项目 [Visual Studio SDK]，子类型"
  - "项目子类型 [Visual Studio SDK]"
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# 项目子类型
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

项目子类型，您可以自定义或色彩的项目系统的行为 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 自定义项包括在项目文件中，添加或筛选中的项目中保存的其他数据 **添加新项** 对话框中，控制如何调试和部署后，程序集和扩展项目 **属性页** 对话框。 Vspackage 实现使用 COM 聚合的项目子类型。  
  
> [!NOTE]
>  Visual c \+ \+ 项目系统不支持项目子类型。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 使用项目子类型实现 SQL Server 和智能设备项目本身。  
  
## 本节内容  
 [项目的子类型设计](../../extensibility/internals/project-subtypes-design.md)  
 描述项目子类型的概念。  
  
 [项目子类型的初始化序列](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)  
 介绍通过编程项目子类型初始化序列 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 环境。  
  
 [属性和扩展项目的子类型的方法](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)  
 提供功能和最常使用项目子类型扩展的方法的详细的的说明。  
  
 [MSBuild 项目文件中保存数据](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)  
 描述如何将数据保持在项目文件以及如何使用 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 跨项目子类型聚合级别维护项目文件中的数据。  
  
 [项目属性用户界面](../../extensibility/internals/project-property-user-interface.md)  
 描述项目子类型可以如何修改项目 **属性页** 对话框。  
  
 [扩展的对象模型的基本项目](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)  
 提供有关项目子类型如何使用自动化扩展程序来扩展自动化对象模型的信息。  
  
 [导致添加新项对话框](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)  
 描述如何将项添加到 **添加新项** 对话框。  
  
 [将数据保存在项目文件中](../../extensibility/saving-data-in-project-files.md)  
 说明如何将保存并通过使用管理包框架 \(MPF\) 检索子类型特有的项目文件中的数据项目子类型。  
  
 [处理专用部署](../../extensibility/internals/handling-specialized-deployment.md)  
 说明如何项目子类型可以提供专门的部署行为，通过实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> 接口。  
  
 [添加和删除属性页](../../extensibility/adding-and-removing-property-pages.md)  
 介绍如何添加和删除项目设计器中的属性页。  
  
## 相关章节  
 [项目类型](../../extensibility/internals/project-types.md)  
 提供指向主题详细介绍 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 项目。