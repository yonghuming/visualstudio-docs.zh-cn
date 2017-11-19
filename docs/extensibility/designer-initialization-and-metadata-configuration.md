---
title: "设计器的初始化和元数据配置 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 12ed4c42335590b7e48d0f6f0fed716a7f149bd0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="designer-initialization-and-metadata-configuration"></a>设计器的初始化和元数据配置
与设计器或设计器组件关联的元数据和筛选器属性的操作提供用于应用程序定义将哪些工具由特定的设计器，用于处理不同的机制<xref:System.Type>对象 （如数据结构类或图形实体），设计器不可用时，以及如何配置 Visual Studio IDE 以支持设计器 (该实例**工具箱**类别或选项卡上的可用)。  
  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]提供多种机制，以便设计器的或设计器组件的初始化的控件和 VSPackage 通过其元数据的操作。  
  
## <a name="initializing-metadata-and-configuration-information"></a>初始化元数据和配置信息  
 因为它们是按需加载的不可能已通过加载 Vspackage[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]之前的设计器实例化的环境。 因此，Vspackage 不能使用标准机制，来配置设计器或设计器组件上创建，这是处理<xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated>事件。 相反，VSPackage 实现的实例<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>接口，并将其本身以提供自定义项，称为设计曲面扩展注册。  
  
### <a name="customizing-initialization"></a>自定义初始化  
 自定义设计器、 组件或设计器图面，包括：  
  
1.  修改设计器元数据和有效地更改如何某一特定<xref:System.Type>访问或转换。  
  
     这通常是通过<xref:System.Drawing.Design.UITypeEditor>或<xref:System.ComponentModel.TypeConverter>机制。  
  
     例如，当<xref:System.Windows.Forms>的基于设计器进行了初始化，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]环境修改<xref:System.Drawing.Design.UITypeEditor>为<xref:System.Web.UI.WebControls.Image>与设计器使用，以使用资源管理器获取位图，而不是文件系统的对象。  
  
2.  将与集成环境，例如，通过订阅事件，或获取项目的配置信息。 你可以获取项目的配置信息和订阅事件，通过获取<xref:System.ComponentModel.Design.ITypeResolutionService>接口。  
  
3.  通过激活适当的用户环境修改**工具箱**类别或通过限制应用的实例由设计器的适用性<xref:System.ComponentModel.ToolboxItemFilterAttribute>到设计器的类。  
  
### <a name="designer-initialization-by-a-vspackage"></a>设计器的初始化由 VSPackage  
 VSPackage 应处理由设计器的初始化：  
  
1.  创建一个对象，实现<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>类。  
  
    > [!NOTE]
    >  <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>类应永远不会在与相同的对象中实现<xref:Microsoft.VisualStudio.Shell.Package>类。  
  
2.  注册类实现<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>作为通过应用的实例为 VSPackage 的设计器扩展提供支持<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>，<xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute>和<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>到提供的 VSPackage 的实现类<xref:Microsoft.VisualStudio.Shell.Package>.  
  
 每当创建任何设计器或设计器组件时，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]环境：  
  
1.  访问每个已注册的设计曲面扩展提供程序。  
  
2.  实例化和初始化每个设计曲面扩展提供程序实例的<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>对象  
  
3.  调用每个设计曲面扩展提供程序的<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A>方法或<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A>（根据需要） 的方法。  
  
 在实现时<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>对象作为成员的 VSPackage，务必了解，：  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]环境不提供任何控制哪些元数据或其他配置设置的特定`DesignSurfaceExtension`提供程序的修改。 可以为两个或多个`DesignSurfaceExtension`包含正在权威所最终修改冲突方式修改相同的设计器功能的提供程序。 它是不确定上次应用的修改。  
  
2.  可以显式限制的实现<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>到特定设计器中，通过应用的实例的对象<xref:System.ComponentModel.ToolboxItemFilterAttribute>到该实现。 有关详细信息**工具箱**项筛选，请参阅<xref:System.ComponentModel.ToolboxItemFilterAttribute>和<xref:System.ComponentModel.ToolboxItemFilterType>。  
  
## <a name="additional-metadata-provisioning"></a>其他元数据设置  
 VSPackage 可以更改在设计时设计器或设计器以外的其他组件的配置。  
  
 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>类可用于以编程方式，或者应用到 VSPackage 提供的设计器。  
  
 实例<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>类用于修改在设计图面上创建的组件的元数据。 例如，一个可以替换默认属性浏览器使用<xref:System.Windows.Forms.CommonDialog>对象，使用自定义属性浏览器。  
  
 修改由的实例提供<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>应用于的 VSPackage 的实现<xref:Microsoft.VisualStudio.Shell.Package>可以具有两个作用域之一：  
  
-   全局-为给定的组件的所有新实例  
  
-   本地-相关仅对当前的 VSPackage 提供的设计图面上创建的组件的实例。  
  
 `IsGlobal`属性<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>实例应用于的 VSPackage 的实现<xref:Microsoft.VisualStudio.Shell.Package>确定此作用域。  
  
 将特性应用于的实现<xref:Microsoft.VisualStudio.Shell.Package>与<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A>属性<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>对象设置为`true`，如以下更改浏览器的整个[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]环境：  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
 如果全局标志设置为`false`，则元数据更改是本地的当前设计器当前 VSPackage 支持：  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
> [!NOTE]
>  目前，设计图面仅支持创建组件，并且因此仅组件可以本地元数据。 在上面的示例中，我们已尝试修改一个属性，例如`Color`对象的属性。 如果`false`传入的全局标志，`CustomBrowser`将永远不会显示，因为设计器永远不会实际创建的实例`Color`。 将全局标志设置为`false`用于组件，如控件、 计时器和对话框。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>   
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>   
 <xref:System.ComponentModel.ToolboxItemFilterType>   
 [扩展设计时支持](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)