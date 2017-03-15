---
title: "设计器的初始化和元数据配置 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
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
ms.openlocfilehash: c0865b62cc2683a8197b5eb6cbc0599d6c063534
ms.lasthandoff: 02/22/2017

---
# <a name="designer-initialization-and-metadata-configuration"></a>设计器的初始化和元数据配置
使用设计器或设计器组件相关联的元数据和筛选器属性的操作提供了一种应用程序定义将哪些工具由特定的设计器，用于处理不同的机制<xref:System.Type>对象 （如数据结构、 类或图形的实体），设计器不可用，何时以及如何在 Visual Studio IDE 配置为支持设计器 (其实例**工具箱**类别或选项卡上的可用)。</xref:System.Type>  
  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]提供了多种机制，以便设计器的或设计器组件的初始化的控件和 VSPackage 由其元数据的操作。  
  
## <a name="initializing-metadata-and-configuration-information"></a>初始化元数据和配置信息  
 因为它们是按需加载，不可能具有由加载 Vspackage[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]之前的设计器的实例化的环境。 因此，Vspackage 无法使用的标准机制，在创建过程中，用来处理上配置设计器或设计器组件<xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated>事件。</xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> 相反，VSPackage 实现的实例<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>接口，并将其本身以提供自定义项，称为设计图面扩展注册。</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
### <a name="customizing-initialization"></a>自定义初始化  
 自定义设计器、 组件或设计器图面，包括︰  
  
1.  修改设计器元数据和有效地更改如何某一特定<xref:System.Type>是访问或转换。</xref:System.Type>  
  
     这通常是通过<xref:System.Drawing.Design.UITypeEditor>或<xref:System.ComponentModel.TypeConverter>机制。</xref:System.ComponentModel.TypeConverter> </xref:System.Drawing.Design.UITypeEditor>  
  
     例如，当<xref:System.Windows.Forms>的基于设计器进行了初始化，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]环境修改<xref:System.Drawing.Design.UITypeEditor>为<xref:System.Web.UI.WebControls.Image>使用设计器使用资源管理器来获取位图，而不是文件系统对象。</xref:System.Web.UI.WebControls.Image> </xref:System.Drawing.Design.UITypeEditor> </xref:System.Windows.Forms>  
  
2.  将与集成环境，例如，通过订阅事件或获得项目配置信息。 您可以获取项目配置信息，然后通过获取订阅事件<xref:System.ComponentModel.Design.ITypeResolutionService>接口。</xref:System.ComponentModel.Design.ITypeResolutionService>  
  
3.  通过激活相应的用户环境修改**工具箱**类别或通过设计器的适用性限制通过应用的一个实例<xref:System.ComponentModel.ToolboxItemFilterAttribute>类与设计器。</xref:System.ComponentModel.ToolboxItemFilterAttribute>  
  
### <a name="designer-initialization-by-a-vspackage"></a>设计器初始化 VSPackage  
 VSPackage 应处理由设计器的初始化︰  
  
1.  创建实现<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>类</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>的对象  
  
    > [!NOTE]
    >  <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>永远不应在与<xref:Microsoft.VisualStudio.Shell.Package>类</xref:Microsoft.VisualStudio.Shell.Package>相同的对象上实现类</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
2.  注册<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>为提供对通过应用的实例<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>，<xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute>并<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>为类提供的<xref:Microsoft.VisualStudio.Shell.Package>。</xref:Microsoft.VisualStudio.Shell.Package> VSPackage 的实现</xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute></xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute></xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>的 VSPackage 的设计器扩展支持</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>实现的类  
  
 每当创建任何设计器或设计器组件时，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]环境︰  
  
1.  访问每个已注册的设计图面扩展提供程序。  
  
2.  实例化和初始化每个设计表面的扩展提供程序的<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>对象</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>的实例  
  
3.  调用每个设计表面的扩展提供<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A>方法或<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A>方法 （根据需要）。</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A>  
  
 在实现时<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>对象作为 VSPackage 的成员务必了解，︰</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]环境不提供任何控制哪些元数据或其他配置设置一个特殊`DesignSurfaceExtension`提供程序的修改。 可以为两个或多个`DesignSurfaceExtension`与被明确的最后修改冲突的方式修改相同的设计器功能的提供程序。 则是不确定上次应用的修改。  
  
2.  可以明确限制的实现<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>对象传递给特定设计器中，通过将应用的实例<xref:System.ComponentModel.ToolboxItemFilterAttribute>实施过程的。</xref:System.ComponentModel.ToolboxItemFilterAttribute> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> 有关详细信息**工具箱**项筛选，请参阅<xref:System.ComponentModel.ToolboxItemFilterAttribute>和<xref:System.ComponentModel.ToolboxItemFilterType>。</xref:System.ComponentModel.ToolboxItemFilterType> </xref:System.ComponentModel.ToolboxItemFilterAttribute>  
  
## <a name="additional-metadata-provisioning"></a>其他元数据设置  
 VSPackage 可以更改在设计时设计器或设计器以外的其他组件的配置。  
  
 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>类可用于以编程方式，或应用于提供一个设计器的 VSPackage。</xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>  
  
 一个实例<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>类用于修改在设计图面上创建的组件的元数据。</xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> 例如，一个可替换使用默认属性浏览器<xref:System.Windows.Forms.CommonDialog>对象，其中的自定义属性浏览器。</xref:System.Windows.Forms.CommonDialog>  
  
 提供的实例修改<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>应用于的 VSPackage 的实现<xref:Microsoft.VisualStudio.Shell.Package>可以具有两个作用域之一︰</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>  
  
-   全局-为给定组件的所有新实例  
  
-   本地-指仅在由当前的 VSPackage 的设计图面上创建该组件的实例。  
  
 `IsGlobal`属性<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>应用于的 VSPackage 实现的实例<xref:Microsoft.VisualStudio.Shell.Package>确定此作用域。</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>  
  
 将属性应用到的实现<xref:Microsoft.VisualStudio.Shell.Package>与<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A>属性<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>对象设置为`true`，如以下更改整个浏览器[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]环境︰</xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> </xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> </xref:Microsoft.VisualStudio.Shell.Package>  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
 如果全局标志已设置为`false`，则当前设计器支持当前的 VSPackage 的本地元数据更改︰  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
> [!NOTE]
>  在存在时，设计图面只支持创建组件，并因此只需要组件可以使本地元数据。 在上面的示例中，我们已尝试修改一个属性，如`Color`对象的属性。 如果`false`全局标志，为传入的`CustomBrowser`因为设计器永远不会实际创建的实例将永远不会出现`Color`。 将全局标志设置为`false`对于组件，如控件、 计时器和对话框很有用。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension></xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>   
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute></xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>   
 <xref:System.ComponentModel.ToolboxItemFilterType></xref:System.ComponentModel.ToolboxItemFilterType>   
 [扩展设计时支持](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
