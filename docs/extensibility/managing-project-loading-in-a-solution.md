---
title: "在解决方案中的管理项目加载 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "管理项目加载的解决方案"
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# 在解决方案中的管理项目加载
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio 解决方案可以包含大量的项目。 默认 Visual Studio 行为是在打开解决方案时，不会加载解决方案中的所有项目而不是允许用户访问的任何项目，直到所有这些已完成加载。 当项目加载的过程将持续时间超过两分钟时，将显示一个进度栏，显示加载的项目数量以及项目总数。 用户可以在具有多个项目的解决方案中工作时卸载项目，但此过程也存在一些弊端: 已卸载的项目未生成作为重新生成解决方案命令的一部分，并且不显示 IntelliSense 类型的说明和已关闭的项目的成员。  
  
 开发人员可以减少解决方案加载时间，并管理项目加载将由管理器中创建解决方案加载行为。 解决方案负载管理器可以将不同的项目加载为特定项目或项目类型的优先级设置，请确保在开始后台生成之前加载了项目、 延迟后台加载其他后台任务都完成时，直到以及执行其他项目负载管理任务。  
  
## 加载优先级的项目  
 Visual Studio 定义四个不同的项目加载优先级别:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority> \(默认值\): 当打开解决方案时，会以异步方式加载项目。 如果已打开该解决方案后，将在已卸载的项目上设置此优先级，则将在下一个空闲点加载项目。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: 当打开解决方案时，将项目加载在后台，这样就允许用户访问的项目，因为它们是加载而无需等待直到加载了所有项目。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: 进行访问时加载项目。 当用户展开解决方案资源管理器中的项目节点时解决方案打开，因为它是在打开的文档列表中 \(保持不变的解决方案用户选项文件中\)，打开属于项目文件时访问某个项目或另一个项目时加载该项目具有依赖项。 此类型的项目不会自动加载之前启动的生成过程;解决方案负载管理器负责确保加载了所有所需的项目。 此外应在整个解决方案中的文件开始查找\/替换前加载这些项目。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: 项目将不能加载，除非用户明确请求。 显式卸载项目时，这是这种情况。  
  
## 管理器中创建解决方案加载  
 开发人员可以创建解决方案加载管理器通过实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> 并告知 Visual Studio 解决方案负载管理器处于活动状态。  
  
#### 激活解决方案负载管理器  
 Visual Studio 允许只有一个解决方案负载管理器在给定时间，因此当您想要激活您的解决方案的负载时，你必须告知 Visual Studio 管理器。 如果在以后激活第二个解决方案负载管理器，则将断开解决方案负载管理器。  
  
 你必须获取 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> 服务并设置 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> 属性:  
  
```c#  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution; object objLoadMgr = this;   //the class that implements IVsSolutionManager pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### 实现 IVsSolutionLoadManager  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A> 打开解决方案的过程中调用方法。 若要实现此方法，您可以使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport> 服务来设置你想要管理的项目的类型的负载优先级。 例如，下面的代码设置 C\# 项目类型在后台中加载:  
  
```c#  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}"); pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> 正在关闭 Visual Studio 或在不同的包已占用作为活动解决方案负载管理器通过调用时调用方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> 与 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> 属性。  
  
#### 针对不同的解决方案负载管理器的策略  
 您可以以不同的方式，具体取决于它们旨在管理的解决方案的类型实现解决方案负载经理。  
  
 如果解决方案负载管理器用于管理在一般情况下加载的解决方案，则它可以实现作为 VSPackage 的一部分。 通过添加，应将包设置为自动加载 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> 上值为 VSPackage <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>。 然后可以在中激活解决方案负载管理器 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 方法。  
  
> [!NOTE]
>  有关自动加载包的详细信息，请参阅 [加载 Vspackage](../extensibility/loading-vspackages.md)。  
  
 因为 Visual Studio 能够识别只有的最后一个解决方案负载经理将激活，通用解决方案负载经理应该始终首先检测是否存在现有的负载管理器才能激活自己。 如果解决方案服务上调用 GetProperty\(\) <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> 返回 `null`, ，没有活动解决方案负载管理器。 如果它不返回 null，则检查对象是否与解决方案负载管理器相同。  
  
 如果解决方案负载管理器用于管理只有几个类型的解决方案，解决方案加载事件可以订阅 VSPackage \(通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>\)，并使用事件处理程序 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> 激活解决方案负载管理器。  
  
 如果解决方案负载管理器用于管理特定的解决方案，可作为解决方案文件的一部分保持激活信息。 若要执行此操作，调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> 预解决方案部分。  
  
 具体的解决方案负载经理应停用本身中 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> 事件处理程序，为了不与其他解决方案负载管理器发生冲突。  
  
 如果您需要解决方案负载管理器，若要保存全局项目负载优先顺序 \(例如，在选项页上设置的属性\)，您可以激活解决方案负载管理器中的仅 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> 事件处理程序保留在解决方案属性设置，然后停用解决方案负载管理器。  
  
## 处理解决方案加载事件  
 若要订阅解决方案加载事件，请调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> 时激活解决方案负载管理器。 如果实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, ，您可以对与不同的项目加载优先级相关的事件作出响应。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: 这是之前打开解决方案时激发事件。 可用于更改项目加载解决方案中项目的优先级。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: 此后的解决方案是完全加载，但后台加载的项目开始之前再次激发。 例如，用户可能已经访问了其负载优先级是 LoadIfNeeded，一个项目或解决方案负载管理器可能已更改项目负载优先级，为 BackgroundLoad，将启动该项目的后台加载。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: 此后激发一种解决方案最初完全加载，无论存在解决方案负载管理器。 后台加载或需加载时该解决方案将成为完全加载后，它也会激发。 在同一时间 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> 就会重新激活。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: 此项目 \(或项目\) 加载前激发。 若要确保加载项目之前完成其他后台进程，设置 `pfShouldDelayLoadToNextIdle` 到 **true**。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: 此项目的批处理是要从中加载时激发。 如果 `fIsBackgroundIdleBatch` 为 true 的项目是加载在后台中; 如果 `fIsBackgroundIdleBatch` 为 false 的项目是要加载以同步方式由于用户请求，例如用户如果展开解决方案资源管理器中的挂起项目。 您可以实现此接口可以完成否则将需要在中完成的昂贵工作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterOpenProject%2A>。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: 此加载一批的项目之后激发。  
  
## 检测和管理解决方案和项目加载  
 若要检测的项目和解决方案的加载状态，请调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> 具有以下值:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` 返回 `true` 解决方案和所有项目加载的否则 `false`。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` 返回 `true` 如果一批的项目当前正在加载在后台，否则 `false`。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` 返回 `true` 如果一批的项目当前正在加载以同步方式因用户命令或其他显式加载，而否则 `false`。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` 返回 `true` 解决方案当前正在关闭，否则如果 `false`。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` 返回 `true` 如果当前正在打开解决方案，否则 `false`。  
  
 此外可以通过调用以下方法之一来确保项目和解决方案加载了 \(无论什么项目负载优先顺序\):  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: 调用此方法强制加载完毕，该方法将返回解决方案中的项目。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: 调用此方法强制中的所有项目 `guidProject` 加载完毕，则此方法返回。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: 调用此方法强制中的项目 `guidProjectID` 加载完毕，则此方法返回。  
  
> [!NOTE]
>  . 默认情况下有此要求的项目加载和背景负载优先级都会被加载，但如果 <xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS> 标志在传入到方法，所有项目将都加载将标记为显式加载的除外。