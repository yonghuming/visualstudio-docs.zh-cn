---
title: "项目持久性 | Microsoft Docs"
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
  - "持久性、 项目"
  - "项目 [Visual Studio SDK]，持久性"
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# 项目持久性
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

持久性是对项目的一个关键设计注意事项。  大多数项目使用表示文件的项目项; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 还数据的非基于文件的项目。  必须保存该项目和项目文件拥有的两个文件。  IDE 指示项目保存自身或项目项。  
  
 项目的模板传递到项目工厂。  模板应根据特定项目类型的要求支持所有项目项的初始化。  这些模板可以稍后保存为项目文件以及由 IDE 管理通过解决方案。  有关更多信息，请参见[通过使用项目工厂来创建项目实例](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)和 [解决方案](../../extensibility/internals/solutions.md)。  
  
 项目项可以基于文件或非基于文件:  
  
-   基于文件的项可以是本地或远程。  在 Web 在 c\# 项目中，例如，与文件的连接到远程系统仍存在，局部，而文件位于远程系统仍存在。  
  
-   不基于文件的项目可以将项目保存到数据库或储存库中。  
  
## 实现模型  
 在决定稍后的位置项目项，您必须选择适当实现模型。  例如，在使用本地文件的基于文件的模型，每个项目可以独立地保存。  在储存库模型，可以保存在一个事务的若干个项目。  有关更多信息，请参见 [项目类型的设计决策](../../extensibility/internals/project-type-design-decisions.md)。  
  
 若要确定文件的扩展名，项目实现 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> 接口，提供信息使对象客户端实现 **保存** 对话框是，填充的 **另存为类型** 下拉列表和管理初始文件扩展名。  
  
 IDE 对该项目的 `IPersistFileFormat` 接口指示该项目应保留其项目项根据需要。  因此，对象拥有其文件和布局的所有方面。  这包括对象的布局的名称。  
  
 在项目不是文件的情况下， `IPersistFileFormat` 仍是基于非文件的项目如何保持。  还必须保存项目文件，如 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 项目的 .vbp 文件或 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 项目的 .vcproj 文件，。  
  
 对于保存操作， IDE 检查运行文档表 \(RDT\)，并且该层次结构通过命令。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> 接口。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> 方法以确定是否修改项目。  如果项目使用， <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> 方法执行保存修改后的项目。  
  
 在 `IVsPersistHierarchyItem2` 接口的方法来确定项是可以重新加载，因此，如果该项目可以是，重新加载它。  此外， <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> 方法实现导致已更改的项被放弃，而不会保存。  
  
## 请参阅  
 [清单︰ 创建新的项目类型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [通过使用项目工厂来创建项目实例](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)