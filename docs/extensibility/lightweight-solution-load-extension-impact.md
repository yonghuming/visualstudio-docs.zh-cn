---
redirect_url: /visualstudio/extensibility/what-s-new-in-the-visual-studio-2017-sdk/
ms.openlocfilehash: 5706797ed88dce5b2f481b17d99e9501b960ddca
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2017
---
标题:"轻型解决方案负载 (LSL) |Microsoft 文档"ms.custom:""ms.date:"01/17/2017"ms.reviewer:""ms.suite:""ms.technology: 
  - "vs ide sdk"ms.tgt_pltfrm:""ms.topic:"文章"helpviewer_keywords: 
  - "加载 Vspackage，轻型解决方案"
  - "Vspackage，快速解决方案负载"ms.assetid: 0a71d91e-dc71-4d6b-bbfe-9e4ecd9e5fd1 caps.latest.revision: 1 的作者:"gregvanl"ms.author:"gregvanl"管理器： ghogen
---
# <a name="lightweight-solution-load-lsl"></a>轻量解决方案负载 (LSL)

## <a name="background-information-on-lsl"></a>LSL 背景信息

轻量解决方案加载是在 VS 2017 这将大大降低解决方案加载时间，使你能够快速提高工作效率的新功能。 启用 LSL 后，Visual Studio 不会完全加载项目之前在开始使用它们。

LSL 可能会影响 Visual Studio 扩展。 扩展其功能取决于要加载的项目可能不工作或工作不正常而无需遵循本文档详细说明的指导原则。

LSL 的更多背景，使用以下链接：

* [轻量解决方案负载博客](https://blogs.msdn.microsoft.com/visualstudio/2016/10/11/shorter-solution-load-time-in-visual-studio-15)
* 问题？ 以下地址与我们联系：[lslsupport@microsoft.com](mailto:lslsupport@microsoft.com)

## <a name="enable-the-setting-to-load-projects-in-deferred-mode"></a>启用该设置将加载在"延迟"模式下的项目

1. 关闭任何当前打开的解决方案。
2. 转到**工具** > **选项** > **项目和解决方案** > **常规**设置页。
3. 检查**轻型解决方案负载**框以启用该设置。

当与上述设置开启打开解决方案时，IDE 将显示项目的常规视图，但未能加载项目。

## <a name="differences-between-deferred-load-and-regular-load-of-projects"></a>延迟的加载和正则加载的项目之间的差异

用轻型解决方案负载，打开解决方案时未能加载项目。 对于这些"延迟项目"，创建存根 （stub） 层次结构。 解决方案资源管理器中显示图标和名称的项目的预期的视图没有 UI 指示某些或所有项目处于"延迟模式"。

与 LSL 启用、 扩展不再可能会触发操作时已完全加载所需的项目。 调用方需要检查是否已加载的项目具有依赖关系。 如果扩展需要从延迟项目的信息，该扩展执行以下操作：

1. 根据需要加载项目。
2. 使用新**工作区 Api**来获取从延迟项目的信息，而不加载它。

新**工作区 Api**允许扩展，以获取从延迟项目的信息，如所属项目的源文件和所有指定的项目中的源文件。 在某些情况下，仅一组有限的项目需要加载。 合适的选择是操作的频率、 的其他方法和总体用户体验的易用性之间取得平衡。

所有项目和解决方案负载相关的事件仍然会触发在 LSL 模式下。 这使组件以从 VS 获得预期的行为，并且它们在何时加载项目一样的方法中的行为。 项目加载相关但极大地减少了过程打开的解决方案中完成工作。

## <a name="ui-requirements-and-changes"></a>UI 要求和更改

所有 UI 必须都将加载和延迟项目视为相等。 这意味着可以在已加载的项目执行任何操作必须有一些例外适用于延迟项目。 为了帮助实现此目的的功能，没有为某个现有平台 Api 还引入了新的 Api 的更改。

### <a name="expectations-for-ui"></a>对 UI 的预期要求

1. 功能必须显示是否项目正在加载或延迟，具体取决于差异没有可视化。
2. 任何列表或通过在解决方案的已加载的项目的枚举必须包括延迟的项目。
3. 提供对加载的项目的全部操作应可对照的延迟的项目。
4. 功能必须加载请求项目时，才：
  * 没有与一项功能的用户直接交互。 不要主动加载项目。
  * "请参阅更多结果"笔势由用户发起。 为此 UI 原则，请参阅下文。
  * 可以使用仅完全加载的项目来满足该操作。 使用 LSL 和打开项目 Api 只要有可能，并发送功能请求要求功能时丢失。

### <a name="changes-in-platform-apis-to-help-drive-ui"></a>平台 Api 可帮助促进 UI 中的更改

1. 新的 Api 提供提出解决方案中轻型解决方案负载模式和多少项目处于延迟的状态已打开它。
2. 解决方案中加载延迟的所有项目后，将为提供新的事件。
3. 新的 Api 可用于要求项目是否所以事务将延迟。
4. 现有 Api 将更新以包括延迟的项目要求已加载的项目时。
5. 现有 Api 更新为快速的解决方案是完全加载后打开解决方案。

### <a name="how-to-add-see-more-results-for-a-feature"></a>如何将"请参阅更多结果"添加功能。

项目的内容进行查询的功能应考虑延迟项目的影响。 在某些情况下，功能可以从 LSL 和工作区 Api 获取其查询的结果，延迟的项目。 在其他情况下，功能的限制要求要加载的项目。 这两种情况应提供新的"请参阅更多结果"笔势，用户可完全加载项目和重新查询。 该笔势使功能可以向用户提供真正加载项目时获得完美的结果的方法时有延迟的项目时提供最佳近似值。

功能的常规算法应为：

### <a name="when-the-query-is-performed-over-a-single-project"></a>当在单个项目上执行查询

```csharp
// IsInDeferredState() and EnsureProjectIsLoadedHelper() in this sample can be found in the "Helpful code snippets" section of this document
public void Query(IVsHierarchy projectToQuery)
{
    // 1. Perform calculation/query
    DoQuery(projectToQuery);

    // 2. Present results to the user
    ShowResults();

    // 3. If the project was deferred, then present a "See More Results" UI element
    if (IsInDeferredState(projectToQuery))
    {
        ShowSeeMoreResults();
    }
}

public void OnClick_SeeMoreResults()
{
    // 1. Ask ask for the project to be loaded
    IVsHierarchy projectFromLastQuery = GetProjectFromLastQuery();
    IVsHierarchy loadedProject = EnsureProjectIsLoadedHelper(projectFromLastQuery);

    if (loadedProject != null)
    {
        // 2. Re-run the query on the loaded projects
        Query(loadedProject);
    }
    else
    {
        ShowErrorMessage();
    }
}
```

### <a name="when-the-query-is-performed-over-the-whole-solution"></a>当查询是在整个解决方案上执行

```csharp
// Requires Microsoft.VisualStudio.Shell.Interop.15.0.DesignTime.dll
public void Query()
{
    // 1. Perform calculation/query
    DoQuery();

    // 2. Present results to the user
    ShowResults();

    // 3. If there were deferred projects, then present a "See More Results from all projects" UI element
    var solution = // the solution
    object deferredCount = 0;
    int hr = ((IVsSolution)solution).GetProperty((int)__VSPROPID7.VSPROPID_DeferredProjectCount, out deferredCount);
    if (ErrorHandler.Succeeded(hr) && ((int)deferredCount > 0))
    {
        ShowSeeMoreResults();
    }
}

public void OnClick_SeeMoreResults()
{
    // 1. Force the solution to load, as requested by the user. This brings up a UI with a "Cancel" button (unless supppresed with __VSBSLFLAGS.VSBSLFLAGS_NotCancelable)
    var solution = // get IVsSolution4
    int hr = ((IVsSolution4)solution).EnsureSolutionIsLoaded((uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    if (ErrorHandler.Succeeded(hr))
    {
        // 2. Re-run the query
        Query();
    }
    else
    {
        ShowErrorMessage();
    }
}
```

## <a name="api-changes"></a>API 更改

### <a name="new-api"></a>新的 API

IVsSolution7.IsSolutionLoadDeferred （出 bool 延迟)

如果已在延迟模式下加载当前的解决方案，则返回 true。 请注意，如果即使最终是所需的所有延迟的项目最初解决方案加载在延迟模式下，当前在会话中加载 （由于显式的用户笔势或强制操作），此属性仍将返回 true。

__VSPROPID7。VSPROPID_DeferredProjectCount

返回当前在延迟模式下的项目数。 此属性将范围 [0，VSPROPID_ProjectCount] 中具有值。

__VSHPROPID9。VSHPROPID_IsDeferred

如果项目层次结构处于延迟的加载状态，则返回 true。

带有值 EPF_DEFERRED 和 EPF_NOTDEFERRED __VSENUMPROJFLAGS3

这些标志可以传递给[IVsSolution.GetProjectEnum()](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivssolution.getprojectenum.aspx)要循环访问非推迟的延迟和项目。

### <a name="new-events"></a>新事件

IVsSolutionEvents7.OnAfterLoadAllDeferredProjects()

加载延迟的所有项目后，将引发此事件。 此时，VSPROPID_DeferredProjectCount 等于 0。 请注意，此事件不是引发作为解决方案负载的一部分，而且可能不会引发根本在会话中。 它仅激发是否打开以及何时加载延迟的所有项目。

### <a name="changes-to-existing-api"></a>对现有 API 的更改

* 传递[__VSENUMPROJFLAGS](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vsenumprojflags.aspx)。到 EPF_LOADEDINSOLUTION [IVsSolution.GetProjectEnum()](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivssolution.getprojectenum.aspx)延迟返回的项目。
* 传递[__VSENUMPROJFLAGS](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vsenumprojflags.aspx)。EPF_UNLOADEDINSOLUTION 不返回延迟的项目。
* [KnownUIContexts.SolutionExistsAndFullyLoadedContext](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.knownuicontexts.solutionexistsandfullyloadedcontext.aspx)设置为 true 对打开的解决方案。 延迟的项目将被视为加载因此此上下文设置很多早于在非 LSL 模式下。
* [__VSPROPID](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vspropid.aspx)。VSPROPID_ProjectCount 返回加载和延迟项目的总和。

## <a name="helpful-code-snippets"></a>很有帮助的代码段

### <a name="check-if-a-solution-was-opened-in-deferred-load-mode"></a>检查是否在延迟的负载模式中打开解决方案

```csharp
/// <summary>
/// Checks if the solution was opened in LSL mode.
/// </summary>
/// <returns>True if the solution was opened in LSL mode, false otherwise.</returns> public static bool IsSolutionLoadDeferred()
{
    IVsSolution7 vsSolution = ServiceProvider.GlobalProvider.GetService(typeof(SVsSolution)) as IVsSolution7;
    Assumes.Present(vsSolution);

    return vsSolution.IsSolutionLoadDeferred();
}
```

### <a name="check-if-a-project-is-deferred"></a>检查是否延迟项目

```csharp
/// <summary>
/// Checks to see if a project is deferred.
/// </summary>
/// <param name="projectsToLoad">A set of deferred and/or loaded projects to ensure are loaded.</param>
/// <returns>True if the project is deferred. False if it is any other state, such as loaded, unloaded, or virtual.</returns>
/// <remarks>Requires Microsoft.VisualStudio.Shell.Interop.15.0.DesignTime.dll</remarks>
public static bool IsInDeferredState(IVsHierarchy vsHierarchy)
{
    object deferred;
    int hr = vsHierarchy.GetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID9.VSHPROPID_IsDeferred, out deferred);

    if (ErrorHandler.Succeeded(hr))
    {
        return (bool)deferred;
    }

    return false;
}
```

### <a name="load-a-project"></a>加载项目

```csharp
/// <summary>
/// Ensures a project is fully loaded.
/// </summary> /// <param name="projectToLoad">A deferred or loaded project to ensure is loaded.</param>
/// <remarks>Requires Microsoft.VisualStudio.Shell.15.0.dll and Microsoft.VisualStudio.Shell.Interop.dll</remarks>
public static IVsHierarchy EnsureProjectIsLoadedHelper(IVsHierarchy projectToLoad)
{
    int hr = VSConstants.S_OK;
    var solution = // get the solution

    // 1. Ask the solution to load the required project. To reduce wait time,
    //    we load only the project we need, not the entire solution.
    hr = projectToLoad.GetGuidProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_ProjectIDGuid, out projectGuid);
    hr = ErrorHandler.ThrowOnFailure(hr);
    hr = ((IVsSolution4)solution).EnsureProjectIsLoaded(projectGuid, (uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    hr = ErrorHandler.ThrowOnFailure(hr);

    // 2. After the project is loaded, grab the latest IVsHierarchy object.
    IVsHierarchy loadedProject = null;
    hr = ((IVsSolution)solution).GetProjectOfGuid(projectGuid, out loadedProject);
    hr = ErrorHandler.ThrowOnFailure(hr);

    return loadedProject;
}
```

### <a name="load-a-set-of-projects"></a>加载一组的项目

```csharp
/// <summary>
/// Ensures a collection of IVsHierarchys are loaded. To be used when deferred projects absolutely cannot be used.
/// </summary>
/// <param name="projectsToLoad">A set of deferred and/or loaded projects to ensure are loaded.</param>
/// <remarks>Requires Microsoft.VisualStudio.Shell.15.0.dll and Microsoft.VisualStudio.Shell.Interop.dll</remarks>
public static IReadOnlyCollection<IVsHierarchy> EnsureProjectsAreLoadedHelper(IReadOnlyCollection<IVsHierarchy> projectsToLoad)
{
    if (projectsToLoad == null || projectsToLoad.Count == 0)
        return projectsToLoad;

    int hr = VSConstants.S_OK;
    List<Guid> projectGuids = new List<Guid>(projectsToLoad.Count);
    List<IVsHierarchy> loadedProjects = new List<IVsHierarchy>(projectsToLoad.Count);
    var solution = // get the solution

    // 1. Collect projects to force load
    foreach (var project in projectsToLoad)
    {
        Guid projectGuid;
        hr = project.GetGuidProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_ProjectIDGuid, out projectGuid)
        hr = ErrorHandler.ThrowOnFailure(hr);
        projectGuids.Add(projectGuid);
    }

    // 2. Ask the solution to load the required projects. To reduce wait time,
    //    we load only the projects we need, not the entire solution.
    hr = ((IVsSolution4)solution).EnsureProjectsAreLoaded(projectCount, projectGuids.ToArray(), (uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    hr = ErrorHandler.ThrowOnFailure(hr);

    // 3. After the projects are loaded, grab the latest IVsHierarchy objects
    foreach (var projectGuid in projectGuids)
    {
        IVsHierarchy loadedProject = null;
        hr = ((IVsSolution)solution).GetProjectOfGuid(projectGuid, out loadedProject);
        hr = ErrorHandler.ThrowOnFailure(hr);
        loadedProjects.Add(loadedProject);
    }

    return loadedProjects;
}
```

### <a name="checks-if-the-solution-has-deferred-projects"></a>检查项目已推迟解决方案

```csharp
/// <summary>
/// Checks if the solution has deferred projects
/// </summary>
/// <returns>True if the solution has deferred projects, false otherwise.</returns>
public static bool SolutionHasDeferredProjects()
{
    IVsSolution vsSolution = ServiceProvider.GlobalProvider.GetService(typeof(SVsSolution)) as IVsSolution;
    Assumes.Present(vsSolution);
    object varHasDeferredProjects;
    if (ErrorHandler.Succeeded(vsSolution.GetProperty(
        (int)__VSPROPID7.VSPROPID_DeferredProjectCount, out varHasDeferredProjects)))
    {
        return (int)varHasDeferredProjects != 0;
    }

    return false;
}
```

## <a name="getting-detailed-information-with-workspace-apis"></a>获取与工作区中的 Api 的详细的信息

### <a name="how-to-get-detailed-info-on-a-lsl-solution"></a>如何获取有关 LSL 解决方案的详细的信息

新的工作区 Api 公开通过 IVsSolutionWorkspaceService 来帮助检索有关解决方案的详细的信息。

这些 Api 可以用于获取当前工作区、 活动的解决方案，托管的命令行信息，以及工作区中的索引服务。 这些 Api 可以进一步利用的索引服务可获取详细的数据，例如，所有源文件在项目中，所属项目的源文件，在当前解决方案中，包含的所有项目中项目等的所有 P2P 引用。

下面的代码段演示了工作区 Api 的用法。

### <a name="get-ivssolutionworkspaceservice-initially"></a>最初获取 IVsSolutionWorkspaceService

>**注意：**请仅获取 IVsSolutionWorkspaceService LSL 方案以避免加载工作区 API 包中。

```csharp
private readonly Lazy<IVsSolutionWorkspaceService> _solutionWorkspaceService;

[ImportingConstructor]
public DeferredProjectWorkspaceService(SVsServiceProvider serviceProvider)
{
    _solutionWorkspaceService = new Lazy<IVsSolutionWorkspaceService>(
        () => (IVsSolutionWorkspaceService)serviceProvider.GetService(typeof(SVsSolutionWorkspaceService)));
}
```

>**注意：**以下代码段假定 _solutionWorkspaceService 已延迟初始化。

### <a name="get-managed-command-line-info-for-deferred-projects-for-active-solution-configuration"></a>获取托管的命令行信息的延迟项目的活动解决方案配置

```csharp
/// <summary>
/// Get the managed command line info for active solution configuration
/// </summary>
/// <param name="cancellationToken"> the cancellation token</param>
/// <returns></returns>
public async Task<IReadOnlyDictionary<string, ManagedCommandLineInfo>> GetManagedCommandLineInfoForConfigurationAsyn(CancellationToken cancellationToken)
{
    var dte = ServiceProvider.GetGlobalService(typeof(EnvDTE.DTE)) as EnvDTE.DTE;
    var solutionConfig = (EnvDTE80.SolutionConfiguration2)dte.Solution.SolutionBuild.ActiveConfiguration;

    // Solution configuration is something like "Debug|Any CPU"
    return await _solutionWorkspaceService.Value.GetManagedCommandLineInfoAsync(
        $"{solutionConfig.Name}|{solutionConfig.PlatformName}", cancellationToken).ConfigureAwait(false);
}
```

### <a name="get-the-active-solution-file-in-lsl"></a>获取 LSL 中的活动解决方案文件

```csharp
/// <summary>
/// Get the active solution file.
/// </summary>
/// <returns>The solution file.</returns>
public string GetActiveSolutionFile()
{
    return _solutionWorkspaceService.Value.SolutionFile;
}
```

### <a name="get-the-owning-project-of-a-source-file"></a>获取源文件所属项目

```csharp
/// <summary>
/// Get the owning projects of a source file.
/// </summary>
/// <param name="filePath">the source file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetOwningProjectAsync(string filePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var result = await indexService.GetFileDependantsAsync(filePath, null, String.Empty, (int)FileReferenceInfoType.Source);
    return result.Select(f => f.Path);
}
```

### <a name="get-all-source-files-from-a-project"></a>从项目中获取所有源文件

```csharp
/// <summary>
/// Get all source files from a project.
/// </summary>
/// <param name="projectFilePath">the project file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetFileReferenceAsync(string projectFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var fileReferenceResult = await indexService.GetFileReferencesAsync(projectFilePath, referenceTypes: (int)FileReferenceInfoType.Source);
    return fileReferenceResult.Select(f => f.Path);
}
```

### <a name="get-the-p2p-references-in-a-project"></a>在项目中获取的 P2P 引用

```csharp
/// <summary>
/// Get outputs of project.
/// </summary>
/// <param name="projectFilePath">the project file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetFileReferenceAsync(string projectFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var fileReferenceResult = await indexService.GetFileReferencesAsync(projectFilePath, context: "Debug|AnyCPU", referenceTypes: (int)FileReferenceInfoType.Output);
    return fileReferenceResult.Select(f => f.Path);
}
```

### <a name="get-all-the-projects-in-a-solution"></a>在解决方案中获取所有项目

```csharp
/// <summary>
/// Get the projects in a solution.
/// </summary>
/// <param name="solutionFilePath">the solution file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetProjectsInSolutionAsync(string solutionFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();

    // Passing the configuration|Platform that projects apply to; passing null will return projects with all configurations.
    var result = await indexService.GetFileReferencesAsync(solutionFilePath, context: "Debug|AnyCPU", referenceTypes: (int)FileReferenceInfoType.ProjectReference);
    return result.Select(f => f.Path);
}
```

## <a name="troubleshooting"></a>疑难解答

由于 LSL 的性质，是有意用户看不到加载和延迟项目之间存在的差异。 这会使功能开发和测试困难。

可以通过执行以下启用延迟的项目的 UI 中的可视化提示：

1. 关闭 Visual Studio
2. Regedit.exe
3. 选择 HKLM
4. 文件 > 加载 Hive
5. `%localappdata%\microsoft\visualstudio\15.0_<instance ID>\privateregistry.bin`
6. 输入"visual Studio"作为项名称
7. 设置`HKLM\VisualStudio\Software\Microsoft\VisualStudio\15.0_<instanceID>\FeatureFlags\Solution\Loading\Deferred\Hint\Value=1`(DWORD)
8. 选择 HKLM\VisualStudio
9. 文件 > 卸载 Hive
10. 启动 Visual Studio

如有任何进一步的问题，请访问[ lslsupport@microsoft.com ](mailto:lslsupport@microsoft.com)。






