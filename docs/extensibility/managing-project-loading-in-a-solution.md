---
title: "管理解决方案中的项目加载 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b28db42e17e95ea7c354f5ba4d7b0c231c2d2fe5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="managing-project-loading-in-a-solution"></a>在解决方案中的管理项目加载
Visual Studio 解决方案可以包含大量的项目。 默认 Visual Studio 行为是在打开解决方案时，时间加载解决方案中的所有项目，而不是允许用户访问任何项目，直到所有它们完成加载。 当项目加载过程将持续超过 2 分钟时，将显示进度栏，显示加载的项目数量以及项目总数。 用户可以在具有多个项目的解决方案中使用时，卸载项目，但此过程也有些缺点： 已卸载的项目不属于重新生成解决方案命令中，生成和关闭 IntelliSense 类型的描述和的成员项目不会显示。  
  
 开发人员可以减少解决方案加载时间和管理项目通过创建解决方案负载管理器中加载行为。 解决方案负载管理器可以将不同的项目加载特定项目或项目类型的优先级设置，请确保在开始后台生成之前加载了项目、 延迟后台加载直到其他后台任务都完成时，并执行其他项目负载管理任务。  
  
## <a name="project-loading-priorities"></a>加载优先级的项目  
 Visual Studio 定义四个不同的项目加载优先顺序：  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>（默认值）： 当打开解决方案时，项目会以异步方式加载。 如果已打开解决方案后，将已卸载的项目上设置此优先级，则将在下一个空闲点加载项目。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>： 当打开解决方案时，将项目加载在后台，允许用户访问的项目，因为它们是加载而无需等待，直到加载的所有项目。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>： 项目加载时访问它们。 当用户展开解决方案资源管理器中的项目节点或属于项目的文件时解决方案打开，因为它是在打开的文档列表中 （保留在该解决方案用户选项文件），打开时访问项目另一个项目它是正在加载该项目具有依赖关系。 此类型的项目不在开始生成过程; 之前自动加载解决方案负载管理器负责确保加载所需的所有项目。 此外应在整个解决方案文件中开始查找/替换之前加载这些项目。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>： 项目将不能加载，除非用户显式请求它。 显式卸载项目时，这种情况。  
  
## <a name="creating-a-solution-load-manager"></a>创建解决方案负载管理器  
 开发人员可以创建解决方案负载 manager 通过实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager>并告知 Visual Studio 解决方案负载管理器处于活动状态。  
  
#### <a name="activating-a-solution-load-manager"></a>激活解决方案负载管理器  
 Visual Studio 允许只有一个解决方案负载管理器在给定时间，因此当你想要激活解决方案负载时，你必须告知 Visual Studio 管理器。 如果第二个解决方案负载管理器激活更高版本上，解决方案负载管理器将断开连接。  
  
 你必须获取<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>服务并将设置<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>属性：  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### <a name="implementing-ivssolutionloadmanager"></a>实现 IVsSolutionLoadManager  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A>在打开解决方案的过程中调用方法。 若要实现此方法，你可以使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport>服务将你想要管理的项目的类型的负载优先级设置。 例如，下面的代码设置 C# 项目类型以在后台加载：  
  
```csharp  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}");  
pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A>正在关闭 Visual Studio 或其他包已活动解决方案负载管理器作为更改通过调用时调用方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A>与<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>属性。  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>为不同类型的解决方案的策略加载管理器  
 你可以以不同的方式，具体取决于它们为了管理的解决方案的类型来实现解决方案负载管理器。  
  
 如果解决方案负载管理器旨在管理一般情况下加载的解决方案，它可实现 VSPackage 的一部分。 通过添加情况下，包应设置为自动上载<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>值为 VSPackage 上<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>。 然后可以在中激活解决方案负载管理器<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>方法。  
  
> [!NOTE]
>  有关自动加载的包的详细信息，请参阅[加载 Vspackage](../extensibility/loading-vspackages.md)。  
  
 因为 Visual Studio 能够识别仅的最后一个解决方案负载管理器将激活，常规解决方案负载管理器应该始终首先检测是否存在现有的负载管理器在激活本身之前。 如果解决方案服务上调用 GetProperty()<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>返回`null`，没有任何活动解决方案负载管理器。 如果它不返回 null，请检查对象是否与你的解决方案负载管理器相同。  
  
 如果解决方案负载管理器旨在管理只有几种解决方案，VSPackage 可以解决方案加载事件订阅 (通过调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>)，并使用事件处理程序<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>激活解决方案负载管理器。  
  
 如果解决方案负载管理器旨在管理仅特定解决方案，则可以作为的解决方案文件的一部分保留激活信息。 若要执行此操作，调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>预解决方案部分。  
  
 特定解决方案负载经理应停用本身中<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A>事件处理程序，为了不与其他解决方案负载管理器发生冲突。  
  
 如果你需要解决方案负载管理器，若要保存全局项目负载优先顺序 （例如，在选项页上设置的属性），则可以激活中的解决方案负载管理器仅<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>事件处理程序中，保留在解决方案属性中，设置然后停用解决方案负载管理器。  
  
## <a name="handling-solution-load-events"></a>处理解决方案加载事件  
 若要订阅解决方案加载事件，调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>激活解决方案负载管理器。 如果你实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>，你可以对与不同的项目加载优先级相关的事件作出响应。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>： 此激发之前打开解决方案。 可用于更改项目加载解决方案中项目的优先级。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>： 此触发后的解决方案是完全加载，但在后台之前加载的项目将重新开始计算。 例如，用户可能已访问其负载优先级是 LoadIfNeeded，一个项目或解决方案负载管理器可能已更改项目负载优先级，为 BackgroundLoad，将启动该项目的背景负载。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>： 此后触发最初完全加载解决方案，无论存在解决方案负载管理器。 后台负载或需加载时该解决方案将成为完全加载后，它也会激发。 同时，<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid>重新激活。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>： 此前加载的一个项目 （或项目） 激发。 若要确保加载项目之前完成其他后台进程，设置`pfShouldDelayLoadToNextIdle`到**true**。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>： 这一批的项目将被加载时激发。 如果`fIsBackgroundIdleBatch`为 true，项目要加载在后台中; 如果`fIsBackgroundIdleBatch`为 false，项目是要加载以同步方式由于用户请求，例如用户如果展开解决方案资源管理器中的挂起项目。 你可以实现这完成否则将需要在中，进行的昂贵工作<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>： 此加载项目一批之后激发。  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>检测和管理解决方案和项目加载  
 若要检测的项目和解决方案的加载状态，调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A>使用以下值：  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>:`var`返回`true`解决方案和所有项目将加载，否则如果`false`。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>:`var`返回`true`如果项目一批当前正在加载在后台，否则`false`。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>:`var`返回`true`如果项目一批当前正在加载同步由于用户命令或其他显式负载，否则`false`。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>:`var`返回`true`解决方案当前正在关闭，否则如果`false`。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>:`var`返回`true`如果目前打开解决方案，否则`false`。  
  
 此外可以通过调用以下方法之一来确保 （无论项目负载优先顺序是什么） 加载项目和解决方案：  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>： 调用此方法强制加载完毕，该方法返回的解决方案中的项目。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>： 调用此方法强制中的项目`guidProject`加载完毕，该方法返回。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>： 调用此方法强制中的项目`guidProjectID`加载完毕，该方法返回。  
  
> [!NOTE]
>  . 默认情况下仅有需求的项目加载和后台负载优先级已加载，但如果<xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS>标志中传递给方法，将标记为显式加载那些除外加载的所有项目。