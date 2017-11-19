---
title: "项目生成的配置 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f89736c448570157711c15d2d86091d91e1f30d6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="project-configuration-for-building"></a>生成的项目配置
由解决方案配置对话框中，给定的解决方案的解决方案配置的列表进行管理。  
  
 用户可以创建其他解决方案配置，每个都有其自己的唯一名称。 当用户创建新的解决方案配置时，IDE 将默认的项目或调试中的相应配置名称为如果没有相应的名称存在。 用户可以更改所选内容，以满足特定要求，如有必要。 此行为的唯一例外是当项目支持与新的解决方案配置的名称匹配的配置时。 例如，假定一个解决方案包含 Project1 和 Project2。 Project1 具有调试、 零售版和 MyConfig1 项目配置。 Project2 具有调试、 零售版和 MyConfig2 项目配置。  
  
 如果用户创建新的解决方案配置名为 MyConfig2，Project1 绑定到的解决方案配置具有默认情况下其调试配置。 Project2 还会将解决方案配置到的其 MyConfig2 配置默认绑定。  
  
> [!NOTE]
>  绑定是不区分大小写。  
  
 当用户选择**多重选择**项环境在配置下拉列表中，显示一个对话框，提供的可用配置的列表。  
  
 ![多个配置](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs")  
多个配置  
  
 在此对话框中，用户可以选择一个或多个配置。 选择后，属性页对话框中显示的属性值将反映所选的配置的值的交集。  
  
 请参阅[解决方案配置](../../extensibility/internals/solution-configuration.md)有关添加和重命名为解决方案和项目的配置与相关的信息。  
  
 项目依赖项和生成顺序是独立的解决方案配置： 即，你可以仅将设置所有解决方案中项目的一个依赖关系树。 右键单击解决方案或项目并选择**项目依赖项**或**项目生成顺序**选项将打开**项目依赖项**对话框。 此外可以从打开**项目**菜单。  
  
 ![项目依赖项](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies")  
项目依赖项  
  
 项目依赖项确定在其中生成项目的顺序。 若要查看解决方案中的项目将生成，并使用依赖关系选项卡来修改生成顺序的确切顺序，请使用对话框中生成顺序选项卡。  
  
> [!NOTE]
>  已通过显式指定的依赖关系由于环境添加项目列表中的，具有其复选框处于选中状态，但它们显示为灰色<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency>或<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency>接口，并不能更改。 例如，添加项目引用从[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]到另一个项目的项目会自动添加只能删除通过删除该引用的生成依赖项。 不能选择的项目的复选框是很明显，并显示为灰色，因为这样会在创建依赖关系循环 （例如，Project1 将依赖于 Project2，和将依赖于 Project1 Project2），这将停止生成。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]生成过程中，包括典型编译和链接使用单个生成命令调用的操作。 此外可以支持两个其他生成进程： 从之前的版本和最新的检查，以确定是否已更改配置中的输出项中删除所有输出项的清理操作。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>对象返回相应<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>(从返回<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>) 来管理它们生成的进程。 若要报告生成操作的状态，正在进行中时，配置进行了调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>、 一个接口实现由下的环境和任何其他对象是否有兴趣生成状态事件。  
  
 生成后，配置设置可以用于确定可以运行这些受控制的调试器。 配置实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>以支持调试。  
  
 在实施项目依赖项之后, 可以以编程方式操作通过自动化模型的依赖关系。 你调用<xref:EnvDTE.SolutionBuild.BuildDependencies%2A>自动化模型中。 没有可用 VSIP API 级别接口允许解决方案生成管理器配置及其属性的直接操作。  
  
 此外，你可以提供的网格项目依赖关系窗口中。 有关详细信息，请参阅[属性显示网格](../../extensibility/internals/properties-display-grid.md)。  
  
## <a name="see-also"></a>另请参阅  
 [管理配置选项](../../extensibility/internals/managing-configuration-options.md)   
 [用于管理部署的项目配置](../../extensibility/internals/project-configuration-for-managing-deployment.md)   
 [用于输出的项目配置](../../extensibility/internals/project-configuration-for-output.md)