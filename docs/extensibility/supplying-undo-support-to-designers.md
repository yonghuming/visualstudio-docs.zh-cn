---
title: "提供撤消支持添加到设计器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f9a33e8386dcdc2cbf79d057cc454a959b1c06b7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="supplying-undo-support-to-designers"></a>提供撤消支持添加到设计器
设计器中的，如编辑器，通常需要支持撤消操作，因此，修改代码元素时，用户可以反向他们最近的更改。  
  
 在 Visual Studio 中实现的大多数设计器有撤消支持自动提供的环境。  
  
 需要撤消功能提供支持的设计器实现：  
  
-   通过实现的抽象基类提供撤消管理<xref:System.ComponentModel.Design.UndoEngine>  
  
-   通过实现来提供持久性和 CodeDOM 支持<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>和<xref:System.ComponentModel.Design.IComponentChangeService>类。  
  
 有关详细信息写入设计器使用[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]，请参阅[扩展设计时支持](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)。  
  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]提供默认撤消基础结构的：  
  
-   提供撤消管理实现通过<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>和<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>类。  
  
-   提供持久性和默认值通过 CodeDOM 支持<xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>和<xref:System.ComponentModel.Design.IComponentChangeService>实现。  
  
## <a name="obtaining-undo-support-automatically"></a>自动获取撤消支持  
 在中创建任何设计器[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]自动和完整撤消支持如果，设计器：  
  
-   利用<xref:System.Windows.Forms.Control>基于其用户界面的类。  
  
-   为代码生成和持久性利用标准的基于 CodeDOM 的代码生成和分析系统。  
  
     有关使用 Visual Studio CodeDOM 支持的详细信息，请参阅[动态源代码生成和编译](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>何时使用显式的设计器撤消支持  
 如果它们使用图形用户界面，称为视图适配器，不是由设计器必须提供自己撤消管理<xref:System.Windows.Forms.Control>。  
  
 此示例可能会创建一种产品与基于 web 的图形设计界面而不是[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]基于图形界面。  
  
 在这种情况下，一个将需要注册使用此视图适配器[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]使用<xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>，并提供一个显式的撤消管理。  
  
 设计器需要提供 CodeDOM 和持久性支持如果它们不使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]中提供的代码生成模型<xref:System.CodeDom>命名空间。  
  
## <a name="undo-support-features-of-the-designer"></a>撤消设计器的支持的功能  
 环境 SDK 提供的接口提供所需的默认实现撤消可由不使用的设计器的支持<xref:System.Windows.Forms.Control>基于用于其用户界面或标准的 CodeDOM 和持久性模型的类。  
  
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>类派生自[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]<xref:System.ComponentModel.Design.UndoEngine>类使用的实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>类来管理撤消操作。  
  
 Visual Studio 提供到设计器撤消的以下功能：  
  
-   链接的撤消功能分布在多个设计器。  
  
-   与其父进行交互的设计器中的子单元可以通过实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>和<xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>上<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>。  
  
 环境 SDK 提供 CodeDOM 和持久性支持通过提供：  
  
-   <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>作为的实现<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
 A<xref:System.ComponentModel.Design.IComponentChangeService>由[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]' 设计宿主。  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>使用环境 SDK 功能提供撤消支持  
 若要获取撤消支持，实现设计器的对象必须：  
  
-   实例化和初始化的实例<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>使用一个有效的类<xref:System.IServiceProvider>实现。  
  
-   这<xref:System.IServiceProvider>类必须提供以下服务：  
  
    -   <xref:System.ComponentModel.Design.IDesignerHost>。  
  
    -   <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
         设计器使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]CodeDOM 序列化可以选择使用<xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>随附[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]作为其实现的<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>。  
  
         在这种情况下，<xref:System.IServiceProvider>类提供给<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>构造函数应返回此对象为的实现<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>类。  
  
    -   <xref:System.ComponentModel.Design.IComponentChangeService>  
  
         使用默认的设计器<xref:System.ComponentModel.Design.DesignSurface>由[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]设计宿主可以保证的默认实现<xref:System.ComponentModel.Design.IComponentChangeService>类。  
  
 设计器实现<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>基于的撤消机制自动跟踪更改，是否：  
  
-   属性更改都通过<xref:System.ComponentModel.TypeDescriptor>对象。  
  
-   <xref:System.ComponentModel.Design.IComponentChangeService>提交可撤消更改时，会手动生成事件。  
  
-   在设计器上的进行修改的上下文中创建<xref:System.ComponentModel.Design.DesignerTransaction>。  
  
-   设计器中选择显式创建撤消单元使用提供的实现的标准撤消单元<xref:System.ComponentModel.Design.UndoEngine.UndoUnit>或 Visual Studio 特定实现<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>，它派生自<xref:System.ComponentModel.Design.UndoEngine.UndoUnit>还提供了实现同时<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>和<xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>。  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [扩展设计时支持](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)