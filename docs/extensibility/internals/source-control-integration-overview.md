---
title: "源控制集成概述 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ed0ffd44e248cb1f420cb7be308a46c914fffee2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="source-control-integration-overview"></a>源代码管理集成概述
本部分比较的两种方法将集成到 Visual Studio 源代码管理;源代码管理插件和 VSPackage 提供源代码管理解决方案，并突出显示新的源控件功能。 Visual Studio 允许的源控件 Vspackage 和源控件插件之间进行手动切换，以及自动基于解决方案的切换。  
  
## <a name="source-control-integration"></a>源代码管理集成  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]支持两种类型的源代码管理集成选项。 在所有版本的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，你仍可以集成基于源控件插件 API （以前也称为 MSSCCI API），它使用 Visual Studio 源控制用户接口 （同时提供基本源代码管理功能的插件UI)。 源代码管理 VSPackage，另一方面，提供新的深度集成[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]路径适用于要求高的复杂程度和自主性在其源控件模型中的源代码管理集成。  
  
 ![源控件概述](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")  
  
## <a name="source-control-plug-in"></a>源代码管理插件  
 所有版本的 Visual Studio 都支持集成路径作为源控件插件 API 规范版本 1.2。 源控件插件实施者写入中所述实现源代码管理集成和注册的源控制插件 API 函数的 DLL[创建源代码管理插件](../../extensibility/internals/creating-a-source-control-plug-in.md)。 在此方法时，集成开发环境 (IDE) 使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]对话框框中，如签入，签出、 工具/选项属性页、 工具栏和源控件标志符号的 UI。 严格遵守源控制插件 API 将确保方便地集成到 Visual Studio 和用户提供可靠的体验。 这意味着源代码管理插件必须实现的大多数函数和详细的 API 中的回调。  
  
 若要实现源代码管理插件使用源控件插件 API，请按照下列步骤：  
  
1.  创建实现中指定的函数的 DLL[源代码管理插件](../../extensibility/source-control-plug-ins.md)。  
  
2.  通过进行相应的注册表项注册 DLL (中所述[如何： 安装源代码管理插件](../../extensibility/internals/how-to-install-a-source-control-plug-in.md))。  
  
3.  创建一个帮助程序 UI 和显示当出现提示时源控件适配器包 （处理源控件插件通过源代码管理功能的 Visual Studio 组件）  
  
 在源代码管理命令的响应，Visual Studio IDE 提供的基本操作的标准 UI，然后将信息传递到源代码管理插件通过源控件插件 API 中定义的函数。 有关高级选项，源代码管理插件不能调用上提供其自己的 UI，例如，浏览受源代码管理项目。 这意味着用户可能看到其中两种可能具有不同样式的 UI 中，在处理与源代码管理： Visual Studio 会显示 UI 和源代码管理插件显示 UI。 这是最为明显与高级的源代码管理操作。  
  
### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>实现源代码管理插件的缺点  
  
-   有关高级功能，用户可能会看到两种不同样式的接口，从而导致可能的混淆。  
  
-   源代码管理插件仅限于源控制插件 API 通过隐式的源代码管理模型。  
  
-   源控件插件 API 可能过于严格为某些源的控件方案。  
  
### <a name="advantages-to-implementing-a-source-control-plug-in"></a>实现源代码管理插件的优点  
  
-   Visual Studio 提供所有基本源代码管理操作的所有用户界面，以便不需要实现潜在的复杂的用户界面源代码管理插件。  
  
-   由于严格的 API，源代码管理插件随时可以与外部源控件程序来提供更广泛的功能; 交互Visual Studio 不关心太得多如何源代码管理功能实现，仅，它根据源控制插件 API 来实现。  
  
-   很容易地实现了源代码管理插件比源控件 VSPackage。  
  
## <a name="source-control-vspackage"></a>源控件 VSPackage  
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]允许深度集成到 Visual Studio 使用的源代码管理功能的完全控制和 Visual Studio 提供的源控制用户界面的完全替换。 源代码管理 VSPackage 注册 Visual Studio，并提供源控件功能。 尽管可以使用 Visual Studio 注册 Vspackage 的多个源代码管理，其中只有一可以处于活动状态一次。 处于活动状态时，源代码管理 VSPackage Visual Studio 中具有完全控制的源代码管理功能和外观。 所有其他源控件可能会在系统中注册的 Vspackage 处于非活动状态，并将不显示任何 UI。  
  
 实现源代码管理 VSPackage 需要使用"所有或执行任何操作"的策略。 源控件 VSPackage 的创建者必须投入大量的精力实现大量的源控制接口和新的 UI 元素 （对话框、 菜单和工具栏） 以涵盖整个源控件的功能。 请参阅[创建源控件 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)有关详细信息。  
  
### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>实现源控件 VSPackage 的缺点  
  
-   VSPackage 必须实现大量复杂的接口，以便与 Visual Studio 成功集成。  
  
-   VSPackage 必须提供所需的源控件，则所有用户界面Visual Studio 将提供此区域中的提供任何帮助。  
  
-   源代码管理 VSPackage 联系密切到 Visual Studio 和不能执行操作独立程序，因此不能与源代码管理程序的外部版本一样轻松共享功能。  
  
### <a name="advantages-to-implementing-a-source-control-vspackage"></a>实现源控件 VSPackage 的优点  
  
-   由于 VSPackage 具有完全控制的源控件 UI 和功能，则用户会看到与源代码管理的无缝接口。  
  
-   VSPackage 不局限于特定的源控件模型中。  
  
## <a name="see-also"></a>另请参阅  
 [源代码管理](../../extensibility/internals/source-control.md)   
 [创建源代码管理插件](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [创建源控件 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)   
 [源代码管理中的新增功能](../../extensibility/internals/what-s-new-in-source-control.md)