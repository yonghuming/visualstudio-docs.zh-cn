---
title: "源控制集成概述 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d3facc06885ef927448eb506ff2f4aa5c04ce85f
ms.lasthandoff: 02/22/2017

---
# <a name="source-control-integration-overview"></a>源代码管理集成概述
本部分将进行比较的两种方法将集成到 Visual Studio 源代码管理;源代码管理插件并提供了一个源代码控制解决方案并突出显示新的源控制功能的 VSPackage。 Visual Studio 允许个源代码管理 Vspackage 和源代码管理插件之间进行手动切换，以及自动基于解决方案的切换。  
  
## <a name="source-control-integration"></a>源代码管理集成  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]支持两种类型的源代码管理集成选项。 在所有版本的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，您仍可以集成基于源控制插件 API （以前也称为 MSSCCI API），这在使用 Visual Studio 源控制用户界面 (UI) 的同时提供基本的源控件功能的插件。 源代码管理 VSPackage，另一方面，提供了新的深度集成[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]路径适用于要求复杂程度和在其源控件模型中的自治的高程度的源代码管理集成。  
  
 ![源控件概述](~/extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")  
  
## <a name="source-control-plug-in"></a>源代码管理插件  
 所有版本的 Visual Studio 都支持集成路径作为源控制插件 API 规范 1.2 版。 源控制插件实施者将写入一个 DLL，它实现进行源代码管理集成和注册的源控制插件 API 函数中所述[创建源代码管理插件](../../extensibility/internals/creating-a-source-control-plug-in.md)。 在这种方法，集成开发环境 (IDE) 使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]UI 对话框，如签入签出、 工具/选项属性页、 工具栏和源控件标志符号。 严格遵守源控制插件 API 将确保方便地集成到 Visual Studio 和用户提供完美的体验。 这意味着源代码管理插件必须实现的大多数功能和详细的 API 中的回调。  
  
 若要实现了源代码管理插件使用源控制插件 API，请按照下列步骤︰  
  
1.  创建一个实现中指定的函数的 DLL[源代码管理插件](../../extensibility/source-control-plug-ins.md)。  
  
2.  通过使相应的注册表项注册此 DLL (中所述[如何︰ 安装源代码管理插件](../../extensibility/internals/how-to-install-a-source-control-plug-in.md))。  
  
3.  创建帮助器 UI 和显示当出现提示时源控件适配器包 （处理通过源代码管理插件的源代码管理功能的 Visual Studio 组件）  
  
 在源代码管理命令响应，Visual Studio IDE 提供的基本操作的标准 UI，然后将信息传递到源代码管理插件通过源控制插件 API 中定义的函数。 对于高级选项，源代码管理插件不能对调用能够提供其自己的 UI，例如，浏览受源代码管理项目。 这意味着，用户可能会出现两种可能具有不同样式的用户界面处理与源代码管理时︰ Visual Studio 会向用户界面和源代码管理插件显示用户界面。 这是最明显高级的源代码管理操作。  
  
### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>实现了源代码管理插件的缺点  
  
-   高级功能，用户可能会看到两种不同样式的接口，从而导致可能的混淆。  
  
-   源代码管理插件仅限于权限隐含的源控制插件 API 的源代码管理模型。  
  
-   源控制插件 API 可能过于严格的某些源代码管理方案。  
  
### <a name="advantages-to-implementing-a-source-control-plug-in"></a>实现了源代码管理插件的优点  
  
-   Visual Studio 提供所有基本源代码管理操作的所有用户的界面，以便不需要实现潜在的复杂的用户界面的源代码管理插件。  
  
-   由于严格的 API，源代码管理插件可以轻松地进行交互与外部源控件程序，以提供更广泛的功能;Visual Studio 并不关心过得多的源代码控制功能如何完成，仅，而且它根据源控制插件 API 来完成。  
  
-   它是可以轻松地实现了源代码管理插件比源控件 VSPackage。  
  
## <a name="source-control-vspackage"></a>源控件 VSPackage  
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]允许使用源代码管理功能的完全控制和全面更换提供 Visual Studio 源代码管理用户界面的深入集成到 Visual Studio。 源代码管理 VSPackage 注册 Visual Studio，并提供源代码管理功能。 尽管可以使用 Visual Studio 注册多个源控件 VSPackages 迁移，但只有一个可以处于活动状态一次。 处于活动状态时，源代码管理 VSPackage Visual Studio 中具有完全控制的源代码管理功能和外观。 所有其他源代码管理可能在系统中注册的 Vspackage 处于非活动状态，并将不显示任何用户界面。  
  
 实现源代码管理 VSPackage 需要一种"全有或执行任何操作"的策略。 源代码管理 VSPackage 的创建者须花大量的精力实现很多源控制接口及新用户界面元素 （对话框、 菜单和工具栏） 以涵盖整个源控件功能。 请参阅[创建源控件 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)的更多详细信息。  
  
### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>实现源控件 VSPackage 的缺点  
  
-   VSPackage 必须实现大量复杂的接口，以便与 Visual Studio 成功集成。  
  
-   VSPackage 必须提供所需的源控件，则所有用户界面Visual Studio 将提供此区域中的提供任何帮助。  
  
-   源代码管理 VSPackage 非常绑定到 Visual Studio，并不能执行操作的独立程序，因此不能与源代码管理程序的外部版本一样轻松地共享功能。  
  
### <a name="advantages-to-implementing-a-source-control-vspackage"></a>源控件 VSPackage 优点  
  
-   因为 VSPackage 具有完全控制的源控件 UI 和功能，用户会看到与源代码管理的无缝的界面。  
  
-   VSPackage 不局限于特定的源控件模型。  
  
## <a name="see-also"></a>另请参阅  
 [源代码管理](../../extensibility/internals/source-control.md)   
 [创建了源代码管理插件](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [创建源控件 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)   
 [在源代码管理中的新增功能](../../extensibility/internals/what-s-new-in-source-control.md)
