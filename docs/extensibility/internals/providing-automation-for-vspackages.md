---
title: "提供有关 Vspackage 自动化 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
caps.latest.revision: 15
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
ms.openlocfilehash: ca3700d1e26ccd4be1054463e9426b364ba17301
ms.lasthandoff: 02/22/2017

---
# <a name="providing-automation-for-vspackages"></a>提供有关 Vspackage 的自动化
有两种主要方法，以实现您 Vspackage 的自动化︰ 通过实现特定于 VSPackage 的对象以及通过实现标准自动化对象。 通常情况下，这些一起用于扩展环境的自动化模型。  
  
## <a name="vspackage-specific-objects"></a>VSPackage 特定对象  
 自动化模型中的某些地方要求您提供对你的 VSPackage 是唯一的自动化对象。 例如，新的项目要求你的 VSPackage 提供的不同对象。 这些对象的名称输入到注册表中，并通过对环境的调用获得`DTE`对象。  
  
 当自动化客户可以使用通过标准的对象的对象属性提供的对象时，也可以获得 VSPackage 特定的对象。 例如，标准`Window`对象具有`Object`属性时，通常称为`Windows.Object`属性。 当使用者调用`Window.Object`上一个窗口，在你的 VSPackage 中实现，您传递回您自己的设计一个特定的自动化对象。  
  
#### <a name="projects"></a>项目  
 Vspackage 可以扩展用于通过自己 VSPackage 特定对象的新项目类型的自动化模型。 从对象提供新的自动化对象，你的 VSPackage 区分唯一项目的主要用途<xref:Microsoft.VisualStudio.VCProjectEngine.VCProject>或<xref:VSLangProj80.VSProject2>对象。</xref:VSLangProj80.VSProject2> </xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> 此差异是很方便的如果想要提供一种方法来挑选出或循环访问您的类型的其他项目类型，除了项目应显示通过并行解决方案中。 有关详细信息，请参阅[公开项目对象](../../extensibility/internals/exposing-project-objects.md)。  
  
#### <a name="events"></a>事件  
 环境的事件体系结构提供了为您要将您自己 VSPackage 特定对象追加另一个位置。 例如，通过创建您自己唯一的事件的对象，可以扩展项目的环境的事件模型。 您可能想要提供您自己的事件在一个新项添加到您自己的项目类型时。 有关详细信息，请参阅[公开事件](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)。  
  
#### <a name="window-objects"></a>窗口对象  
 Windows 可以传递回 VSPackage 特定自动化对象返回给调用时环境。 实现一个对象，派生自<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>，<xref:EnvDTE.IExtensibleObject>或`IDispatch`，将重新传送属性，扩展在其中确定位置的窗口对象。</xref:EnvDTE.IExtensibleObject> </xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> 例如，可以使用此方法以实现自动化放置在一个窗口框架的控件。 此对象以及可能会延长的任何其他对象的语义是由您负责进行设计。 有关详细信息，请参阅[如何︰ 为 Windows 提供自动化](../../extensibility/internals/how-to-provide-automation-for-windows.md)。  
  
#### <a name="options-pages-on-the-tools-menu"></a>在工具菜单上的选项页  
 您可以创建页来扩展的工具，通过实现页面和将信息添加到注册表，以创建您自己的选项的选项自动化模型。 然后，可以通过环境对象模型，像任何其他选项页一样调用您的页面。 如果要添加到 Vspackage 通过环境的功能的设计需要选项页，则应添加的自动化支持。 有关详细信息，请参阅[选项页的自动化支持](../../extensibility/internals/automation-support-for-options-pages.md)。  
  
## <a name="standard-automation-objects"></a>标准自动化对象  
 若要扩展项目的自动化，您还实现标准自动化对象 (派生自`IDispatch`)，代表其他项目对象旁边以及实现标准的方法和属性。 标准的对象的示例包括如插入到解决方案层次结构的项目对象`Projects`， `Project`， `ProjectItem`，和`ProjectItems`。 每个新的项目类型应实现这些对象 （和可能是您的项目的其他的具体取决于语义）。  
  
 在某种意义上，这些对象提供的相反的 VSPackage 特定项目对象的优点。 标准的自动化对象允许您的项目以使用支持的相同对象的其他任何项目一样的通用方式。 因此外, 接程序，针对常规编写`Project`和`ProjectItem`对象可以正常针对任何类型的项目。 有关详细信息，请参阅[项目建模](../../extensibility/internals/project-modeling.md)。
