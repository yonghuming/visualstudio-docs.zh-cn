---
title: "项目属性用户界面 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 36d8f6afebf09d4efd176ba204dcc6f485a56124
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="project-property-user-interface"></a>项目属性用户界面
项目子类型可以在项目中使用的项**属性页**对话框中提供基本的项目中，隐藏或记只读控件和整个页面，因为提供，或将项目子类型特定页添加到**属性页**对话框。  
  
## <a name="extending-the-project-property-dialog-box"></a>扩展项目属性对话框  
 项目子类型实现自动化扩展程序和项目配置浏览对象。 这些扩展程序实现<xref:EnvDTE.IFilterProperties>界面，从而使特定属性，隐藏或只读的。 **属性页**对话框中的基本项目，基本的项目中，由实现遵循由自动化扩展程序执行筛选。  
  
 扩展的过程**项目属性**下面列出了对话框中：  
  
-   基本项目可检索项目子类型通过实现 extender<xref:EnvDTE80.IInternalExtenderProvider>接口。 浏览、 项目自动化和项目配置浏览对象的所有基本项目实现此接口。  
  
-   实现<xref:EnvDTE80.IInternalExtenderProvider>为项目浏览对象和项目自动化对象委托给<xref:EnvDTE80.IInternalExtenderProvider>实现项目子类型聚合器 (即，它们`QueryInterface`为<xref:EnvDTE80.IInternalExtenderProvider>上<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>项目对象）。  
  
-   基本项目配置浏览对象还实现<xref:EnvDTE80.IInternalExtenderProvider>来直接连接在自动化扩展程序从项目子类型配置对象中。 其实现委托给<xref:EnvDTE80.IInternalExtenderProvider>由项目子类型聚合器实现的接口。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>由项目配置浏览对象，返回实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>对象。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>由项目配置的浏览对象返回还实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>对象。  
  
-   项目子类型可以通过检索以下确定对各种的可扩展对象的基本项目在运行时适当 Catid<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>值：  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
 若要确定为项目作用域 Catid，项目子类型检索的上述属性<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>从`VSITEMID``typedef`。 项目子类型可能还想要控制哪些**属性页**对话框页显示的项目取决于配置和独立的配置。 某些项目子类型可能需要删除内置页，并添加项目子类型特定页。 若要启用此选项，在托管客户端项目调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>针对以下属性的方法：  
  
-   `VSHPROPID_PropertyPagesCLSIDList`-独立于配置的属性页中的 Clsid 的以分号分隔列表。  
  
-   `VSHPROPID_CfgPropertyPagesCLSIDList —`以分号分隔的 Clsid 依赖于配置的属性页的列表。  
  
 因为项目子类型聚合<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>对象，它会重写这些属性可以控制将哪个定义**属性页**显示的对话框。 项目子类型可以从内部的基本项目中检索这些属性，然后添加或删除根据需要的 Clsid。  
  
 新添加的项目子类型的属性页的基本项目实现从系统会向项目配置浏览对象。 此项目配置浏览对象支持自动化扩展程序。 AutomationExtenders 的详细信息，请参阅[实现和使用自动化扩展程序](http://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356)。 由项目子类型调用实现的属性页<xref:EnvDTE.Project.Extender%2A>检索扩展的基本项目的配置浏览对象自己项目子类型配置浏览对象。  
  
## <a name="see-also"></a>另请参阅  
 <xref:EnvDTE.IFilterProperties>   
 [属性页对话框中](http://msdn.microsoft.com/en-us/4a3d34ac-ed03-45e8-ae60-a0e1aad300e4)