---
title: "生成的项目配置 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "项目 [Visual Studio SDK]，用于生成配置"
  - "生成的项目配置"
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# 生成的项目配置
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

由解决方案配置对话框中，给定的解决方案的解决方案配置的列表进行管理。  
  
 用户可以创建其他解决方案配置，每个都有其自己唯一的名称。 当用户创建新的解决方案配置时，IDE 默认为项目中或调试中的相应配置名称中，如果存在没有相应的名称。 用户可以更改所选内容，以满足特定要求，如有必要。 这一行为唯一的例外是当项目支持与新解决方案配置的名称匹配的配置。 例如，假定一个解决方案包含 Project1 和 Project2。 Project1 具有调试、 零售版和 MyConfig1 项目配置。 Project2 具有调试、 零售版和 MyConfig2 项目配置。  
  
 如果用户创建新的解决方案配置名为 MyConfig2，Project1 将绑定其调试配置到解决方案配置时，默认情况下。 Project2 也绑定其 MyConfig2 配置到解决方案配置时，默认情况下。  
  
> [!NOTE]
>  绑定是不区分大小写。  
  
 当用户选择 **多重选择** 项环境中配置下拉列表中，显示一个对话框，提供的可用配置的列表。  
  
 ![多重配置](~/extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs")  
多个配置  
  
 在此对话框中，用户可以选择一个或多个配置。 选择后，显示在属性页对话框中的属性值将反映所选配置的值的交集。  
  
 请参阅 [解决方案配置](../../extensibility/internals/solution-configuration.md) 与添加和重命名解决方案和项目的配置相关的信息。  
  
 项目依赖项和生成顺序是独立的解决方案配置: 也就是说，您只能设置为所有解决方案中项目的一个依赖关系树。 右键单击该解决方案或项目并选择其中任一 **项目依赖项** 或 **项目生成顺序** 选项打开 **项目依赖项** 对话框。 此外可以从打开 **项目** 菜单。  
  
 ![项目依赖项](~/extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies")  
项目依赖项  
  
 项目依赖项决定生成项目的顺序。 若要查看解决方案中的项目将生成，并使用依赖关系选项卡来修改生成顺序的准确顺序，请使用对话框中生成顺序选项卡。  
  
> [!NOTE]
>  已通过由指定的显式依赖关系由于环境添加在列表中的项目已选中其复选框，但显示为灰色 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> 或 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> 接口，并不能更改。 例如，添加项目引用从 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 到另一个项目的项目会自动添加只能通过删除该引用删除一个生成依赖项。 不能选择其复选框是很明显，并显示为灰色项目，因为这样做会在创建依赖关系循环 \(例如，Project1 将依赖于 Project2，并将依赖于 Project1 Project2\)，它将停止生成。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 生成过程包括典型的编译和链接使用单个生成命令调用的操作。 此外可以支持两个其他生成过程: 从之前的版本和最新的检查，以确定是否已更改配置中的一个输出项中删除所有输出项的清理操作。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> 对象返回相应 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> \(从返回 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>\) 来管理其生成过程。 若要报告的生成操作的状态，它发生时，所做配置调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>, 、 一个接口实现由下的环境和任何其他对象是否有兴趣生成状态事件。  
  
 生成后，可以使用配置设置来确定可以运行这些受调试器控制。 配置实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> 以支持调试。  
  
 在实现后项目依赖项，可以以编程方式操作通过自动化模型的依赖关系。 您调用 <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> 自动化模型中。 没有可用 VSIP API 级别接口允许直接操作的解决方案生成管理器配置和它们的属性。  
  
 此外，您可以提供项目依赖关系窗口中的一个网格。 有关更多信息，请参见[显示属性网格](../../extensibility/internals/properties-display-grid.md)。  
  
## 请参阅  
 [管理配置选项](../../extensibility/internals/managing-configuration-options.md)   
 [用于管理部署的项目配置](../../extensibility/internals/project-configuration-for-managing-deployment.md)   
 [输出的项目配置](../../extensibility/internals/project-configuration-for-output.md)