---
title: "导致添加新项对话框 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "添加新项对话框，导致"
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# 导致添加新项对话框
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

项目子类型可以为 **添加新项目** 对话框提供项目完整新内容通过注册 **添加项目** 模板。 `Projects` 注册表子项下。  
  
## 注册添加新项目模板  
 本节中 **HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0\\Projects** 下位于注册表。  下面的注册表项假定假设项目子类型聚合的一个 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 项目。  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 项目的项下面列出。  
  
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
  
 `AddItemTemplates\TemplateDirs` 子项包含路径的注册表项使可用在 **添加新项目** 对话框放置项的内容。  
  
 该环境自动加载所有 `AddItemTemplates` 数据。 `Projects` 注册表子项下。  这可以包括数据对于基本项目实现以及数据用于特定项目类型的类型。  每个项目子类型是项类型 `GUID`确定的。  项目子类型可以指定应为特定调味的项目实例使用备用项设置 `Add Item` 模板通过支持从 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> 的 `VSHPROPID_ AddItemTemplatesGuid` 枚举 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> 实现返回项目子类型的 GUID 值。  如果 `VSHPROPID_AddItemTemplatesGuid` 未指定属性，使用基本项目 GUID。  
  
 通过实现在项目子类型聚合函数对象的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> 接口筛选在 **添加新项目** 对话框的项目。  例如，可以聚合 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 项目实现一个数据库项目中的项目子类型，可以通过实现筛选筛选从 **添加新项目** 对话框的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 特定项目，并且，然后，可以通过支持在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>的 `VSHPROPID_ AddItemTemplatesGuid` 添加数据库项目特定的项目。  有关筛选和添加项的更多信息。 **添加新项目** 对话框，请参见 [将项添加到添加新项对话框](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [通常用于扩展项目的对象的 Catid](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)