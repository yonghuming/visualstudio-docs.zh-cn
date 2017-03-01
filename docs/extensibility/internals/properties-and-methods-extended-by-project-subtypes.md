---
title: "属性和方法扩展项目的子类型 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
caps.latest.revision: 17
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 38bb86636edeaeda4485b7ebe6c8a6349450343c
ms.lasthandoff: 02/22/2017

---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>属性和扩展项目的子类型的方法
项目子类型包含大量的电源来影响项目的行为，因为它被构造为基的项目的聚合函数。 本部分总结了一些功能可以增强或修改的项目子类型。  
  
## <a name="features-gained-by-aggregation"></a>通过聚合获得的功能  
 下表总结了很多聚合使项目子类型在基础项目中重写的方法。  
  
|重写由聚合方法|项目子类型|  
|---------------------------------------|---------------------|  
|从<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>::</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|启用对项目子类型<br /><br /> -更改标题和图标的项目节点。<br />-完全重写项目`Browse`对象。<br />-控制是否可以重命名项目。<br />控制排序顺序。<br />控制动态帮助的用户上下文。|  
|从<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>::</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|使项目子类型以控制哪些上下文的服务提供给设计器和编辑器。|  
|从<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>::</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|启用对项目子类型<br /><br /> -参与项目命令在命令路由。<br />添加、 删除或禁用项目环境命令和解决方案资源管理器活动命令。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2></xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|使项目子类型，来筛选用户可以看到在**添加新项**对话框。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory></xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|启用对项目子类型<br /><br /> -确定提供的文件扩展名的默认值生成器。<br />-将人工可读的生成器名称映射到 COM 对象。|  
  
## <a name="properties-used-by-project-subtypes"></a>所使用的项目子类型属性  
 环境和基项目系统可以使用从属性<xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID>和<xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2>下表中的详细若要启用用于控制各种功能的项目系统的项目子类型的枚举。</xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> </xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID>  
  
|VSHPROPID 属性|项目子类型|  
|------------------------|---------------------|  
|`AddItemTemplatesGuid`|允许的项目子类型，来控制的内容**添加项**对话框。 项目子类型可以提供模板目录的新规范、 添加新项的类型、 删除现有项和重新组织的基本项目中的项子集**添加项**对话框。|  
|`PropertyPagesCLSIDList`|允许添加或删除独立于配置的属性页的项目子类型。|  
|`CfgPropertyPagesCLSIDList`|允许添加或删除依赖于配置的属性页的项目子类型。|  
|`ExtObjectCATID`|允许的项目子类型，以提供自动化扩展程序项目或项目项对象通过了解扩展程序 CATID。 例如，项目子类型可以提供自定义`Project.Extender("<subtype>")`对象。|  
|`BrowseObjectCATID`|允许的项目子类型，以提供有关自动化扩展程序`Browse`通过了解扩展程序 CATID 的对象。 例如，项目子类型可以为其添加额外属性<xref:EnvDTE.Project.Properties%2A>集合。</xref:EnvDTE.Project.Properties%2A>|  
|`CfgBrowseObjectCATID`|允许为项目配置浏览对象提供自动化扩展程序的项目子类型。 例如，项目子类型可以为其添加额外属性<xref:EnvDTE.Configuration.Properties%2A>集合。</xref:EnvDTE.Configuration.Properties%2A>|  
|`CfgExtObjectCATID`|允许为配置对象提供自动化扩展程序的项目子类型。|  
|`DefaultPlatformName`|允许确定项目的配置对象的平台名称的项目子类型。|  
  
 基本项目提供了上述属性的默认实现。 基本项目获得这些通过调用`QueryInterface`为<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>最外面的项目的子类型，从而重写的属性实现的项目子类型。</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
## <a name="see-also"></a>另请参阅  
 [项目的子类型设计](../../extensibility/internals/project-subtypes-design.md)
