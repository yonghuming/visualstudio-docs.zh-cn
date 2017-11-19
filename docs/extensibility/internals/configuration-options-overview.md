---
title: "配置选项概述 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f91f6c3668b7cc1ce881dd0b98d1bd5dddebf530
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="configuration-options-overview"></a>配置选项概述
中的项目[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]可以支持多个可以生成、 调试、 运行，和/或已部署的配置。 配置是描述与属性、 通常编译器开关和文件位置的已命名集的生成类型。 默认情况下，新的解决方案包含两个配置，调试和发布。 使用其默认设置，或修改以满足你的特定解决方案和/或项目要求，可以应用这些配置。 某些包可以生成两种方式： 为 ActiveX 编辑器或作为就地组件。 项目不需要支持多个配置，但是。 如果没有可用的只有一个配置，则将该配置映射到所有的解决方案配置。  
  
 配置通常由两部分组成 — 配置名称 （如调试或发布） 和平台设置。 配置的平台名称标识的配置目标，例如 API 将设置的环境或操作系统平台。 用户的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]无法创建平台; 他们必须从选项中选择 VSPackage 允许的项目。 当用户安装 VSPackage，在包开发过程中创建的传递平台可以图面所需的任何平台名称基于由包创建者设置的任何条件。 然后，用户可以选择从时实例化的属性页可用于通过 VSPackage 的平台列表。  
  
 平台名称是可选的因为并非所有项目都支持的平台的概念。 配置缺少平台名称，将在 UI 中显示字符串"n/A"。  
  
 每个解决方案具有自己的配置，可以一次 active 只有一个集。 解决方案配置是一套不能超过一个配置时，从每个项目。 "不能超过"的要求取决于要排除项目从解决方案配置的选项。 用户可以创建其自己的自定义解决方案配置。  
  
 下表说明了一个项目的典型配置设置。 行标记为配置名称和平台名称的列。  
  
|配置名称|平台-Win32|平台-Win64|  
|------------------------|----------------------|----------------------|  
|调试|\<调试 Win32 设置 >|\<调试 Win64 设置 >|  
|发布|\<释放 Win32 设置 >|\<释放 Win64 设置 >|  
|MyConfig|不可用|\<MyConfig Win64 设置 >|  
  
> [!NOTE]
>  无法创建"MyConfig"解决方案配置时，除非您的目标的项目不支持 Win32 排除"Win32"平台。  
  
 更改活动解决方案配置该解决方案中选择生成、 运行、 调试或部署时，项目配置的集。 例如，如果将活动解决方案配置从版本更改为调试，在该解决方案中的所有项目中自动都生成解决方案的调试配置中所示的项目的配置。 项目的配置通常也是命名的调试除非用户所做的手动更改环境的配置管理器中。  
  
 存储的每个项目的解决方案配置属性包括项目名称、 项目配置名称、 标志以指示生成或部署，和平台名称。 有关详细信息，请参阅[解决方案配置](../../extensibility/internals/solution-configuration.md)。  
  
 用户可以查看和设置在层次结构 （解决方案资源管理器） 中选择解决方案并打开属性页解决方案配置参数。 同样，你可以查看和通过在解决方案资源管理器中选择项目并打开该项目的属性页来设置项目配置参数。  
  
 用户还可以生成一个项目，如有必要将发布配置设置和所有 rest 使用的调试配置设置。 有关详细信息，请参阅[构建的项目配置](../../extensibility/internals/project-configuration-for-building.md)。  
  
 下图显示了支持解决方案和项目配置的接口的实现方式：  
  
 ![配置界面图](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces")  
配置接口  
  
 与上图中相关的一些注释：  
  
-   `IDispatch`标记为可选配置对象中。 具体而言，它是可选具有浏览对象上的配置接口。  
  
-   `IVsDebuggableProjectCfg`标记为可选中所配置的对象，但需要调试支持。  
  
-   `IVsProjectCfg2`标记为可选中所配置的对象，但所需的分组支持的输出。  
  
-   `Config Provider`对象被标记为一个可选对象，但选项是实现它的位置。 在项目对象或上一个单独的对象，你可以实现的对象。  
  
-   `IVsCfgProvider2`需要为平台支持和配置编辑。 `IVsCfgProvider`足以如果你不会实现该功能。  
  
-   这些对象在关系图中显示为单独的对象可以组合到同一个类，在实际应用中的某些基于你的特定设计要求。 在本部分的其他主题中，但是，对象和与这些对象关联的接口将讨论根据关系图中给出的方案。  
  
-   单独实现某些对象。 例如，项目和解决方案构建出现在单独的线程和要管理的生成生活分开描述生成的配置的对象的对象上。  
  
 在配置对象接口和上图中的配置提供程序对象接口上的进一步信息，请参阅[项目配置对象](../../extensibility/internals/project-configuration-object.md)。 此外，[构建的项目配置](../../extensibility/internals/project-configuration-for-building.md)配置生成器和生成依赖对象的接口，提供了详细信息和[管理部署的项目配置](../../extensibility/internals/project-configuration-for-managing-deployment.md)进一步描述附加到的配置 deployer 和部署依赖项对象的接口。 最后，[输出的项目配置](../../extensibility/internals/project-configuration-for-output.md)说明输出组与输出对象接口，以及查看和设置配置相关属性的属性页中的使用。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>   
 [生成的项目配置](../../extensibility/internals/project-configuration-for-building.md)   
 [解决方案配置](../../extensibility/internals/solution-configuration.md)