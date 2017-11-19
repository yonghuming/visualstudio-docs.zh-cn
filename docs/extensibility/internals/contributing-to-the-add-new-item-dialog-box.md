---
title: "导致添加新项对话框 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 13f4d254027fe168018fe597f772518bd8ac6b94
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="contributing-to-the-add-new-item-dialog-box"></a>导致添加新项对话框
项目子类型可以提供完整的项的新目录**添加新项**通过注册的对话框**添加项**下的模板`Projects`注册表子项。  
  
## <a name="registering-add-new-item-templates"></a>注册添加新项模板  
 本部分位于**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects**注册表中。 下面的注册表项假定[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]项目按假设项目子类型聚合。 项[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]项目如下所示。  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}]  
@="#2143"  
"DefaultProjectExtension"="vbproj"  
"PossibleProjectExtensions"="vbproj;vbp"  
"ProjectTemplatesDir"="visualStudioInstallPath\\Vb\\.\\VBProjects"  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}\AddItemTemplates\TemplateDirs\{12345678-1234-1234-1122334455667788}\/1]  
@="#100"  
"TemplatesDir"="projectSubTypeTemplatesDir\\VBProjectItems"  
```  
  
 `AddItemTemplates\TemplateDirs`子项包含替换为项目成为中可用的目录的路径的注册表条目**添加新项**位于对话框。  
  
 环境自动加载的所有`AddItemTemplates`下的数据`Projects`注册表子项。 这可能包括基本项目实现的数据以及特定项目子类型类型的数据。 每个项目子类型由一种项目类型`GUID`。 项目子类型可以指定一种替代设置的`Add Item`模板应用于通过支持的特定风格化的项目实例`VSHPROPID_ AddItemTemplatesGuid`来自枚举<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>中<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>实现以返回 GUID项目子类型的值。 如果`VSHPROPID_AddItemTemplatesGuid`未指定属性，使用 GUID 基本项目。  
  
 你可以筛选中的项**添加新项**对话框中，通过实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>项目子类型聚合器对象上的接口。 例如，通过进行聚合来实现的数据库项目的项目子类型才能[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]项目中，可以筛选[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]特定项从**添加新项**可通过实现筛选，然后在对话框中打开，则可以添加通过支持数据库项目的特定项`VSHPROPID_ AddItemTemplatesGuid`中<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>。 有关详细信息筛选和将项添加到**添加新项**对话框中，请参阅[将项添加到添加新项对话框](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [通常用于扩展项目的对象的 CATID](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)