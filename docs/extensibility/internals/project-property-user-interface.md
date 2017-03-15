---
title: "项目属性用户界面 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: b344731061053abb208225a0480408ebbe682050
ms.lasthandoff: 02/22/2017

---
# <a name="project-property-user-interface"></a>项目属性用户界面
项目子类型可以在项目中使用的项**属性页**对话框中提供基本的项目中，隐藏或使只读控件和整页，根据提供的信息，或添加到项目的特定于子类型的页**属性页**对话框。  
  
## <a name="extending-the-project-property-dialog-box"></a>扩展项目属性对话框  
 项目子类型实现了自动化扩展程序和项目配置浏览对象。 这些扩展器实现<xref:EnvDTE.IFilterProperties>界面，从而使特定属性，隐藏或只读模式。</xref:EnvDTE.IFilterProperties> **属性页**对话框中的基本项目中，由基的项目中，实现遵循由自动化扩展程序执行的筛选。  
  
 扩展的过程**项目属性**如下所述对话框中︰  
  
-   基本项目可检索的项目子类型通过实现扩展程序<xref:EnvDTE80.IInternalExtenderProvider>接口。</xref:EnvDTE80.IInternalExtenderProvider> 浏览、 项目自动化和基的所有项目的项目配置浏览对象实现此接口。  
  
-   实现<xref:EnvDTE80.IInternalExtenderProvider>项目浏览对象和项目自动化对象委托给的<xref:EnvDTE80.IInternalExtenderProvider>项目子类型聚合函数的实现 (也就是说，它们`QueryInterface`为<xref:EnvDTE80.IInternalExtenderProvider>上<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>项目对象)。</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> </xref:EnvDTE80.IInternalExtenderProvider> </xref:EnvDTE80.IInternalExtenderProvider> </xref:EnvDTE80.IInternalExtenderProvider>  
  
-   基项目配置浏览对象还实现<xref:EnvDTE80.IInternalExtenderProvider>直接绑定中的项目子类型配置对象从自动化扩展程序。</xref:EnvDTE80.IInternalExtenderProvider> 其实现委托给<xref:EnvDTE80.IInternalExtenderProvider>项目子类型聚合器实现的接口。</xref:EnvDTE80.IInternalExtenderProvider>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>由项目配置浏览对象，返回实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>对象。</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy></xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>也由项目配置浏览对象，返回实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>对象。</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg></xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>  
  
-   项目子类型可以通过检索以下来确定在运行时的基本项目的各种可扩展对象为适当的 Catid<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>值︰</xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2></xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2></xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2></xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
 若要确定项目范围的 Catid，项目子类型检索的上述属性<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>从`VSITEMID``typedef`。</xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT> 项目子类型可能还想要控制哪些**属性页**对话框页显示的项目取决于配置和独立的配置。 某些项目子类型可能需要删除内置网页，并添加项目子类型的特定页面。 为了实现此目的，托管客户端项目调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>方法针对以下属性︰</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>  
  
-   `VSHPROPID_PropertyPagesCLSIDList`--以分号分隔的 Clsid 独立于配置的属性页的列表。  
  
-   `VSHPROPID_CfgPropertyPagesCLSIDList —`以分号分隔的 Clsid 依赖于配置的属性页的列表。  
  
 因为该项目的子类型聚合<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>对象，它会重写这些属性可以控制将哪个定义**属性页**显示的对话框。</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 项目子类型可以检索这些属性从内部的基本项目，然后添加或删除根据需要的 Clsid。  
  
 新添加的项目子类型的属性页是从基本项目实现传递的项目配置浏览对象。 此项目配置浏览对象支持自动化扩展程序。 AutomationExtenders 的详细信息，请参阅[中实现并使用自动化扩展程序](http://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356)。 由项目子类型调用实现的属性页<xref:EnvDTE.Project.Extender%2A>要扩展基本项目的配置浏览对象自己项目子类型配置浏览对象中检索。</xref:EnvDTE.Project.Extender%2A>  
  
## <a name="see-also"></a>另请参阅  
 <xref:EnvDTE.IFilterProperties></xref:EnvDTE.IFilterProperties>   
 [属性页对话框](http://msdn.microsoft.com/en-us/4a3d34ac-ed03-45e8-ae60-a0e1aad300e4)
