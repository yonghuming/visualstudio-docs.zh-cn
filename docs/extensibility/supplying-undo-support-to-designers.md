---
title: "提供撤消支持添加到设计器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 95e6873d0a3b254fa8f34144253a44c0a8cab60d
ms.lasthandoff: 02/22/2017

---
# <a name="supplying-undo-support-to-designers"></a>向设计器提供撤消支持
设计器中的，如编辑器中，通常需要支持撤消操作，以便修改代码元素时，用户可以撤消他们最近的更改。  
  
 在 Visual Studio 中实现的大多数设计器都有撤消支持自动环境所提供的。  
  
 需要撤消功能提供支持的设计器实现︰  
  
-   通过实现的抽象基类提供撤消管理<xref:System.ComponentModel.Design.UndoEngine></xref:System.ComponentModel.Design.UndoEngine>  
  
-   通过实现来提供持久性和 CodeDOM 支持<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>和<xref:System.ComponentModel.Design.IComponentChangeService>类。</xref:System.ComponentModel.Design.IComponentChangeService> </xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
 有关编写使用设计器的详细信息[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]，请参阅[扩展设计时支持](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)。  
  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]提供默认撤消基础结构的︰  
  
-   提供撤消通过实施管理<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>和<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>类。</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>  
  
-   提供持久性和 CodeDOM 支持通过默认情况下<xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>和<xref:System.ComponentModel.Design.IComponentChangeService>实现。</xref:System.ComponentModel.Design.IComponentChangeService> </xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>  
  
## <a name="obtaining-undo-support-automatically"></a>自动获取撤消支持  
 在中创建任何设计器[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]已自动和完整撤消支持 if、 设计器︰  
  
-   利用<xref:System.Windows.Forms.Control>基于其用户界面的类。</xref:System.Windows.Forms.Control>  
  
-   为代码生成和持久性采用标准的基于 CodeDOM 的代码生成和分析系统。  
  
     使用 Visual Studio CodeDOM 支持的详细信息，请参阅[动态源代码生成和编译](http://msdn.microsoft.com/Library/d077a3e8-bd81-4bdf-b6a3-323857ea30fb)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>何时使用显式的设计器撤消支持  
 如果他们使用图形用户界面，称为视图适配器，而非由<xref:System.Windows.Forms.Control>。</xref:System.Windows.Forms.Control>提供，设计人员必须提供它们自己的撤消管理  
  
 此示例，可能创建一种产品与基于 web 的图形设计界面而不是[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]基于图形界面。  
  
 在这种情况下，一个需要注册使用此视图适配器[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]使用<xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>，并提供显式撤消管理。</xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>  
  
 设计器需要提供 CodeDOM 和持久性支持，如果它们不使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]中提供的代码生成模型<xref:System.CodeDom>命名空间。</xref:System.CodeDom>  
  
## <a name="undo-support-features-of-the-designer"></a>撤消支持功能的设计器  
 环境 SDK 提供了提供所需的接口的默认实现撤消支持，未使用的设计可以使用这些<xref:System.Windows.Forms.Control>基于其用户界面或标准的 CodeDOM 和持久性模型的类。</xref:System.Windows.Forms.Control>  
  
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>类派生自[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]<xref:System.ComponentModel.Design.UndoEngine>类通过实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>类来管理撤消操作。</xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> </xref:System.ComponentModel.Design.UndoEngine> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>  
  
 Visual Studio 提供了以下功能，到设计器还原︰  
  
-   跨多个设计器的链接的撤消功能。  
  
-   子单位的设计器中可以实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>和<xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit><xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>。</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit></xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit></xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>其某个父级与交互  
  
 环境 SDK 提供了通过提供支持的 CodeDOM 和持久性︰  
  
-   <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>作为的实现<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService></xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService></xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>  
  
 一个<xref:System.ComponentModel.Design.IComponentChangeService>提供[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]' 设计宿主。</xref:System.ComponentModel.Design.IComponentChangeService>  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>使用环境 SDK 功能来提供撤消支持  
 若要获取撤消支持，实现设计器的对象必须︰  
  
-   实例化和初始化的实例<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>类具有有效<xref:System.IServiceProvider>实现。</xref:System.IServiceProvider> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>  
  
-   这<xref:System.IServiceProvider>类必须提供以下服务︰</xref:System.IServiceProvider>  
  
    -   <xref:System.ComponentModel.Design.IDesignerHost>.</xref:System.ComponentModel.Design.IDesignerHost>  
  
    -   <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService></xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
         设计器使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]CodeDOM 序列化可能会选择使用<xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>附带[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]作为其实现<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>。</xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> </xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>  
  
         在此情况下，<xref:System.IServiceProvider>类提供给<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>构造函数应返回此对象作为<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>类</xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>的实现</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine></xref:System.IServiceProvider>  
  
    -   <xref:System.ComponentModel.Design.IComponentChangeService></xref:System.ComponentModel.Design.IComponentChangeService>  
  
         使用默认的设计器<xref:System.ComponentModel.Design.DesignSurface>提供[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]保证设计宿主都具有<xref:System.ComponentModel.Design.IComponentChangeService>类</xref:System.ComponentModel.Design.IComponentChangeService>的默认实现</xref:System.ComponentModel.Design.DesignSurface>  
  
 设计器实现<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>基于的撤消机制自动跟踪更改，如果︰</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>  
  
-   属性更改都通过<xref:System.ComponentModel.TypeDescriptor>对象。</xref:System.ComponentModel.TypeDescriptor>  
  
-   <xref:System.ComponentModel.Design.IComponentChangeService>提交可撤消的更改时，手动将生成事件。</xref:System.ComponentModel.Design.IComponentChangeService>  
  
-   在一种<xref:System.ComponentModel.Design.DesignerTransaction>。</xref:System.ComponentModel.Design.DesignerTransaction>的上下文中创建的设计器上的修改  
  
-   设计器选择显式创建撤消单元使用提供的<xref:System.ComponentModel.Design.UndoEngine.UndoUnit>或 Visual Studio-特定于实现的<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit><xref:System.ComponentModel.Design.UndoEngine.UndoUnit>并且还提供了这两个<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>和<xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>。</xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit></xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>实现</xref:System.ComponentModel.Design.UndoEngine.UndoUnit>其派生</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit></xref:System.ComponentModel.Design.UndoEngine.UndoUnit>实现的标准的撤消单元  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.ComponentModel.Design.UndoEngine></xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine></xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [扩展设计时支持](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
