---
title: "项目子类型 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 84d2700e1dfb5d66fb2df6376db9e0ce5352ad4e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="project-subtypes"></a>项目子类型
项目子类型允许你自定义或 flavor 的项目系统的行为[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 自定义包括在项目文件中，添加或筛选中的项目中保存的其他数据**添加新项**对话框中，控制如何调试和部署，程序集和扩展项目**属性页**对话框。 Vspackage 实现项目子类型使用 COM 聚合。  
  
> [!NOTE]
>  Visual c + + 项目系统不支持项目子类型。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]本身使用项目子类型来实现 SQL Server 和智能设备项目。  
  
## <a name="in-this-section"></a>本节内容  
 [项目子类型设计](../../extensibility/internals/project-subtypes-design.md)  
 描述项目子类型的概念。  
  
 [项目子类型的初始化序列](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)  
 通过以编程方式项目子类型初始化顺序进行了说明[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]环境。  
  
 [项目子类型扩展的属性和方法](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)  
 提供的功能和最常使用项目子类型扩展的方法的详细的说明。  
  
 [保留 MSBuild 项目文件中的数据](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)  
 介绍如何来持久保存项目文件中的数据以及如何使用<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>以维护跨项目子类型聚合级别的项目文件中的数据。  
  
 [项目属性用户界面](../../extensibility/internals/project-property-user-interface.md)  
 描述如何项目子类型可以修改项目**属性页**对话框。  
  
 [扩展基项目的对象模型](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)  
 提供有关项目子类型如何使用自动化扩展程序来扩展自动化对象模型的信息。  
  
 [构成“添加新项”对话框](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)  
 描述如何将项添加到**添加新项**对话框。  
  
 [将数据保存在项目文件中](../../extensibility/saving-data-in-project-files.md)  
 说明如何保存和检索项目文件中的特定子类型的数据通过使用托管包框架 (MPF) 项目子类型。  
  
 [处理专用部署](../../extensibility/internals/handling-specialized-deployment.md)  
 说明如何项目子类型可以提供专用的部署行为，通过实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>接口。  
  
 [添加和删除属性页](../../extensibility/adding-and-removing-property-pages.md)  
 介绍如何添加和删除项目设计器中的属性页。  
  
## <a name="related-sections"></a>相关章节  
 [项目类型](../../extensibility/internals/project-types.md)  
 提供的详细说明的主题链接[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]项目。