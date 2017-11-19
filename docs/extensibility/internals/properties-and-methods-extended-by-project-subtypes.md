---
title: "通过项目子类型的属性和方法扩展 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fd4e46148950af925b7b41c4e3b5bd66fce5063c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>属性和扩展，由项目子类型的方法
项目子类型具有大量的能力，因为它被构造为基本项目的聚合器影响的项目的行为。 本部分总结了一些可以增强或修改的项目子类型的功能。  
  
## <a name="features-gained-by-aggregation"></a>聚合中获得的功能  
 下表总结了许多的聚合可让项目子类型，以在基的项目中重写的方法。  
  
|通过聚合中被重写的方法|项目子类型|  
|---------------------------------------|---------------------|  
|从<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|启用到的项目子类型<br /><br /> -更改标题和图标的项目节点。<br />-完全重写项目`Browse`对象。<br />-控制是否可以重命名项目。<br />控制排序顺序。<br />动态帮助控制用户上下文。|  
|从<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|使项目子类型以控制哪些上下文的服务提供给设计器和编辑器。|  
|从<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|启用到的项目子类型<br /><br /> -参与项目命令的命令路由。<br />添加、 删除或禁用项目环境命令和解决方案资源管理器活动命令。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|使项目子类型，来筛选用户所见的内容中**添加新项**对话框。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|启用到的项目子类型<br /><br /> -确定给定了一个文件扩展名的默认生成器。<br />-将人工可读生成器名称映射到 COM 对象。|  
  
## <a name="properties-used-by-project-subtypes"></a>使用项目子类型的属性  
 环境和基项目系统可以使用从属性<xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID>和<xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2>下表中的详细若要启用用于控制各种功能的项目系统的项目子类型的枚举。  
  
|VSHPROPID 属性|项目子类型|  
|------------------------|---------------------|  
|`AddItemTemplatesGuid`|允许项目子类型来控制的内容**添加项**对话框。 项目子类型可以提供新的模板目录规范、 添加新类型的项、 删除现有项和重新组织基项目中的项的子集**添加项**对话框。|  
|`PropertyPagesCLSIDList`|允许项目子类型以添加或删除独立于配置的属性页。|  
|`CfgPropertyPagesCLSIDList`|允许项目子类型以添加或删除依赖于配置的属性页。|  
|`ExtObjectCATID`|允许项目子类型可供自动化扩展程序的项目或项目项对象通过了解扩展程序 CATID。 例如，项目子类型可以提供自定义`Project.Extender("<subtype>")`对象。|  
|`BrowseObjectCATID`|允许项目子类型以提供有关自动化扩展程序`Browse`通过了解扩展程序 CATID 的对象。 例如，项目子类型可以额外将属性添加到<xref:EnvDTE.Project.Properties%2A>集合。|  
|`CfgBrowseObjectCATID`|允许为项目配置浏览对象提供自动化扩展程序的项目子类型。 例如，项目子类型可以额外将属性添加到<xref:EnvDTE.Configuration.Properties%2A>集合。|  
|`CfgExtObjectCATID`|允许配置对象提供自动化扩展程序的项目子类型。|  
|`DefaultPlatformName`|允许项目子类型来确定项目的配置对象的平台名称。|  
  
 该基项目提供了上述属性的默认实现。 基本项目获取这些通过调用`QueryInterface`为<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>外面项目子类型，从而允许项目子类型，以重写属性的实现。  
  
## <a name="see-also"></a>另请参阅  
 [项目子类型设计](../../extensibility/internals/project-subtypes-design.md)