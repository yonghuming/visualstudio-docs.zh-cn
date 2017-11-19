---
title: "项目持久性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7bb782b79c00576a431c8f4453ddf020606aaf5a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="project-persistence"></a>项目持久性
持久性是你的项目的关键设计注意事项。 大多数项目使用代表文件; 的项目项[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]还支持其数据是不基于文件的项目。 必须保留这两个拥有的项目和项目文件的文件。 IDE 指示要保存自身或项目项的项目。  
  
 项目的模板传递给项目工厂。 模板应支持根据特定项目类型的要求的所有项目项的初始化。 可以稍后保存项目文件为这些模板，并为其管理的解决方案通过 IDE。 有关详细信息，请参阅[创建项目实例通过使用项目工厂](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)和[解决方案](../../extensibility/internals/solutions.md)。  
  
 项目项可以基于文件的或非基于文件的：  
  
-   基于文件的项可以是本地或远程。 在 C# 中的 Web 项目，例如，连接保存到远程系统上的文件会保留本地，而文件本身将保留在远程系统。  
  
-   非基于文件的项可以将项保存到数据库或存储库。  
  
## <a name="commit-models"></a>提交模型  
 决定项目项所在的位置之后, 你必须选择适当的提交模型。 例如，在基于文件的模型中使用本地文件，每个项目可以保存自主。 在存储库模型中，你可以保存在一个事务中的多个项。 有关详细信息，请参阅[项目类型的设计决策](../../extensibility/internals/project-type-design-decisions.md)。  
  
 若要确定文件扩展名，项目实现<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>接口，从而提供启用对象的客户端实现的信息**另存为**对话框中-即，以填充**另存为类型**下拉列表和管理的初始文件扩展名。  
  
 IDE 调用`IPersistFileFormat`接口上以指示该项目应保留其项目的项目项视。 因此，该对象拥有其文件和格式的所有方面。 这包括的对象的格式的名称。  
  
 项不是文件，这种情况中`IPersistFileFormat`仍是如何非基于文件的项将保留。 项目文件，如.vbp 文件[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]项目或.vcproj 文件[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]项目中，还必须存在。  
  
 对于保存操作，IDE 会检查正在运行的 document 表 (RDT) 和层次结构将命令传递给<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>接口。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A>实现方法是为了确定是否已修改的项。 如果项具有，<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A>实现方法是为了保存已修改的项。  
  
 上的方法`IVsPersistHierarchyItem2`使用接口来确定是否可以重新加载项，如果可以将项，重新加载它。 此外，<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A>方法可实现来导致已更改的项，要放弃未保存。  
  
## <a name="see-also"></a>另请参阅  
 [清单： 创建新项目类型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [使用项目工厂创建项目实例](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)