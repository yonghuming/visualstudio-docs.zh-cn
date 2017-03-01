---
title: "配置选项概述 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
caps.latest.revision: 10
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
ms.openlocfilehash: 2c188af385d75fed49f6e9aca6703365c3b63ca5
ms.lasthandoff: 02/22/2017

---
# <a name="configuration-options-overview"></a>配置选项概述
中的项目[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]可以支持多个可以生成、 调试、 运行，和/或已部署的配置。 配置是描述与属性、 通常编译器开关和文件位置的已命名集的生成类型。 默认情况下，新的解决方案包含两个配置调试和发布。 可以使用其默认设置，或修改以满足您的特定解决方案和/或项目要求应用这些配置。 某些程序包可以生成以下两种方式︰ 作为一个 ActiveX 编辑器也可以作为就地组件。 项目不需要支持多个配置，但是。 如果没有可用的只有一个配置，该配置映射到的所有解决方案配置。  
  
 配置通常由两部分组成 — 配置名称 （如调试或发布） 和平台设置。 配置的平台名称标识的配置目标，例如 API 将设置的环境或操作系统平台。 用户[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]不能创建一个平台; 它们必须从选项中选择 VSPackage 允许的项目。 当用户安装 VSPackage，交付平台在包开发过程中创建可以呈现所需的任何平台名称基于由包创建者设置任何条件。 然后，用户可以选择从可通过 VSPackage 实例化的属性页时的平台列表中。  
  
 平台名称是可选的因为并非所有的项目支持的平台的概念。 当一个配置没有平台名称时，将在 UI 中显示字符串"n/A"。  
  
 每个解决方案都具有其自己的配置，其中只有一个可以处于活动状态一次集。 解决方案配置是一套不能超过一个配置时，从每个项目。 "不能超过"的要求是由于从解决方案配置中排除某个项目的选项。 用户可以创建其自己的自定义解决方案配置。  
  
 下表说明了一个项目的典型配置设置。 行标记为配置名称和平台名称的列。  
  
|配置名称|平台 — Win32|平台 — Win64|  
|------------------------|----------------------|----------------------|  
|调试|\<调试 Win32 设置&1;>|\<调试 Win64 设置&1;>|  
|发布|\<版本 Win32 设置&1;>|\<版本 Win64 设置&1;>|  
|MyConfig|不可用|\<MyConfig Win64 设置&1;>|  
  
> [!NOTE]
>  无法创建排除"Win32"平台，除非您的目标的项目不支持 Win32"MyConfig"解决方案配置。  
  
 更改活动解决方案配置该解决方案中选择的一套生成、 运行、 调试或部署的项目配置。 例如，如果将活动解决方案配置从版本更改为调试，使用解决方案的调试配置中所示的项目的配置自动生成该解决方案中的所有项目。 项目的配置通常也是命名的调试除非用户已进行手动更改了环境的配置管理器中。  
  
 项目名称、 项目配置名称、 标志，用于指示生成或部署时，和平台名称，包括存储为每个项目的解决方案配置属性。 有关详细信息，请参阅[解决方案配置](../../extensibility/internals/solution-configuration.md)。  
  
 用户可以查看和设置通过在层次结构 （解决方案资源管理器） 中选择该解决方案并打开属性页解决方案配置参数。 同样，您可以查看和设置项目配置参数，通过在解决方案资源管理器中选择一个项目并打开该项目的属性页。  
  
 用户还可以生成一个项目使用 Release 配置设置和其余所有如有必要 Debug 配置设置。 有关详细信息，请参阅[构建的项目配置](../../extensibility/internals/project-configuration-for-building.md)。  
  
 下图显示如何实现这些接口支持解决方案和项目配置︰  
  
 ![配置界面图](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces")  
配置接口  
  
 与上一个关系图相关的一些注释︰  
  
-   `IDispatch`标记为可选配置对象中。 具体而言，它是一个可选具有浏览对象上的配置接口。  
  
-   `IVsDebuggableProjectCfg`标记为可选配置对象中，但所必需的调试支持。  
  
-   `IVsProjectCfg2`标记参数是可选的配置对象，但所需的输出分组的支持。  
  
-   `Config Provider`对象标记为一个可选对象，但是的选项来实现它的位置。 在项目对象或上一个单独的对象，你可以实现该对象。  
  
-   `IVsCfgProvider2`平台支持和配置编辑的需要。 `IVsCfgProvider`已足够，如果您没有实现该功能。  
  
-   如在实际应用中，可以将单独的对象合并到同一个类图中显示这些对象中的部分根据特定的设计要求。 在本部分其他主题中，但是，对象和与这些对象关联的接口将讨论根据关系图中给出的方案。  
  
-   某些对象是单独实现的。 例如，项目和解决方案构建在单独的线程以及发生要描述生成的配置对象分开管理的生成生活的对象。  
  
 上的配置对象接口和上图中的配置提供程序对象接口的详细信息，请参阅[项目配置对象](../../extensibility/internals/project-configuration-object.md)。 此外，[构建的项目配置](../../extensibility/internals/project-configuration-for-building.md)配置生成器，生成依赖项对象的接口，提供了详细信息和[管理部署的项目配置](../../extensibility/internals/project-configuration-for-managing-deployment.md)进一步描述附加到的配置部署者和部署的依赖项对象的接口。 最后，[输出的项目配置](../../extensibility/internals/project-configuration-for-output.md)描述这些输出组和输出对象的接口，以及如何使用属性页可以查看和设置配置相关的属性。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2></xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>   
 [生成的项目配置](../../extensibility/internals/project-configuration-for-building.md)   
 [解决方案配置](../../extensibility/internals/solution-configuration.md)
