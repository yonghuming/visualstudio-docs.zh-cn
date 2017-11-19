---
title: "提供 Vspackage 的自动化 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4d81a96b7eea9f19352ae8a1deeeeb73ba5dc089
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="providing-automation-for-vspackages"></a>提供 Vspackage 的自动化
有两种主要方法，提供你的 Vspackage 的自动化： 通过实现特定于 VSPackage 的对象和通过实现标准的自动化对象。 通常情况下，这些一起用于扩展自动化模型的环境。  
  
## <a name="vspackage-specific-objects"></a>特定于 VSPackage 的对象  
 自动化模型中的某些地方要求你提供对你的 VSPackage 是唯一的自动化对象。 例如，新项目需要你的 VSPackage 提供的不同对象。 这些对象的名称在注册表中输入，并通过对环境的调用获得`DTE`对象。  
  
 自动化使用者使用提供通过标准的对象的对象属性的对象时，也可以获取特定于 VSPackage 的对象。 例如，标准`Window`对象具有`Object`属性，通常称为`Windows.Object`属性。 当使用者调用`Window.Object`上一个窗口，在你的 VSPackage 中实现，你可能传回自己设计的一个特定的自动化对象。  
  
#### <a name="projects"></a>项目  
 Vspackage 可以扩展通过其自己的 VSPackage 特定对象的新项目类型的自动化模型。 从对象提供新的自动化对象，你的 VSPackage 区分唯一项目的主要目的<xref:Microsoft.VisualStudio.VCProjectEngine.VCProject>或<xref:VSLangProj80.VSProject2>对象。 此差异是很方便的如果你想要提供一种方法来挑选出或循环你类型的其他项目类型，脱离项目应显示并排显示在解决方案中。 有关详细信息，请参阅[公开项目对象](../../extensibility/internals/exposing-project-objects.md)。  
  
#### <a name="events"></a>事件  
 环境的事件体系结构提供了为你要追加您自己的 VSPackage 特定对象的另一个位置。 例如，通过创建您自己的唯一事件对象，你可以扩展项目的环境的事件模型。 你可能想要提供您自己的事件的新项添加到你自己的项目类型时。 有关详细信息，请参阅[公开事件](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)。  
  
#### <a name="window-objects"></a>窗口对象  
 Windows 可以返回特定于 VSPackage 的自动化将对象传递回调用时的环境。 实现派生自对象<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>，<xref:EnvDTE.IExtensibleObject>或`IDispatch`，将重新传送属性，扩展在其中就位的窗口对象。 例如，可以使用此方法提供自动化放置在一个窗口框架的控件。 此对象，它可能会延长的任何其他对象的语义是由您负责进行设计。 有关详细信息，请参阅[如何： 为 Windows 提供自动化](../../extensibility/internals/how-to-provide-automation-for-windows.md)。  
  
#### <a name="options-pages-on-the-tools-menu"></a>在工具菜单上的选项页  
 你可以创建扩展的工具，通过实现页并将信息添加到注册表，以创建你自己的选项的选项自动化模型的页。 然后，可以通过如任何其他选项页的环境对象模型调用您的网页。 如果要添加到 Vspackage 通过环境的功能的设计要求选项页，则应添加的自动化支持。 有关详细信息，请参阅[选项页的自动化支持](../../extensibility/internals/automation-support-for-options-pages.md)。  
  
## <a name="standard-automation-objects"></a>标准自动化对象  
 若要扩展项目的自动化，你还实现标准的自动化对象 (派生自`IDispatch`) 的其他项目对象旁边独立和实施标准方法和属性。 标准的对象的示例包括如插入到解决方案层次结构中的项目对象`Projects`， `Project`， `ProjectItem`，和`ProjectItems`。 每个新的项目类型应实现这些对象 （和可能的具体语义取决于你的项目的其他计算机）。  
  
 在某种意义上，这些对象提供 VSPackage 特定项目对象的相对优势。 标准自动化对象允许你的项目，如支持相同的对象的任何其他项目的通用方式使用。 因此外, 接程序，针对常规编写`Project`和`ProjectItem`对象客户端可对任何类型的项目。 有关详细信息，请参阅[项目建模](../../extensibility/internals/project-modeling.md)。