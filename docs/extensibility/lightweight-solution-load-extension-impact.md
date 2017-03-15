---
title: "轻量解决方案加载 (LSL) |Microsoft 文档"
ms.custom: 
ms.date: 01/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, lightweight solution load
- VSPackages, fast solution load
ms.assetid: 0a71d91e-dc71-4d6b-bbfe-9e4ecd9e5fd1
caps.latest.revision: 1
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
ms.sourcegitcommit: 221f4911981deec0330f76a82c0cc8a1b968e56e
ms.openlocfilehash: 28957abccc03001546038da10cf4ff7bbe21f63e
ms.lasthandoff: 02/22/2017

---
# <a name="lightweight-solution-load-lsl"></a>轻量解决方案加载 (LSL)

## <a name="background-information-on-lsl"></a>LSL 的背景信息

轻量解决方案加载是中 VS 2017 这将大大降低解决方案加载时，使您可以快速提高效率的新功能。 启用 LSL 后，Visual Studio 不会完全加载项目直到您开始使用它们。

LSL 可以影响 Visual Studio 扩展。 扩展其功能取决于要加载的项目可能不起作用或不遵循本文档中详细的指导原则的情况下无法正常工作。

对于 LSL 的详细背景，使用以下链接︰

* [种轻量型解决方案，负载博客](https://blogs.msdn.microsoft.com/visualstudio/2016/10/11/shorter-solution-load-time-in-visual-studio-15)
* 问题吗？ 以下地址与我们联系︰[lslsupport@microsoft.com](mailto:lslsupport@microsoft.com)

## <a name="enable-the-setting-to-load-projects-in-deferred-mode"></a>启用该设置将加载在"延迟"模式下的项目

1. 关闭当前打开的解决方案。
2. 转到**工具** > **选项** > **项目和解决方案** > **常规**设置页。
3. 检查**种轻量型解决方案，负载**框以启用该设置。

当具有上述设置开启打开解决方案时，IDE 将显示项目的常规视图，但未能加载项目。

## <a name="differences-between-deferred-load-and-regular-load-of-projects"></a>延迟的加载和正则加载的项目之间的差异

使用轻型解决方案加载，打开解决方案时未能加载项目。 对于这些"延迟项目"，将创建一个存根 （stub） 层次结构。 解决方案资源管理器中显示的预期的视图有图标和名称的项目中，某些或所有项目都以"延迟模式"没有用户界面指示。

与启用 LSL、 扩展插件不再可能会触发操作时已完全加载所需的项目。 调用方需要检查它们是否具有一个依赖项加载项目。 如果扩展需要从延迟的项目的信息，请扩展执行以下操作︰

1. 根据需要加载到项目。
2. 使用新**工作区 Api**从延迟的项目中获取信息，而不加载它。

新**工作区 Api**允许扩展来从延迟项目获取信息，如源文件及其所有指定的项目中的源代码文件所属的项目。 在某些情况下，只有一组有限的项目需要将加载。 合适的选择是操作的频率、 易用性的其他方法和整体用户体验之间的平衡。

所有项目和解决方案加载相关的事件仍然会触发在 LSL 模式下。 这将允许从 VS 获取预期的行为的组件，以及在加载项目的时间相同的方式的行为。 相关的项目加载期间打开的解决方案完成的工作就大大缩短不过了。

## <a name="ui-requirements-and-changes"></a>用户界面要求和更改

所有 UI 必须都将加载和延迟项目视为相等。 这意味着可以对已加载的项目执行任何操作必须是适用于延迟项目中，有一些例外。 为了帮助实现此目的的功能，没有到某个现有平台 Api，以及新的 Api 引入的更改。

### <a name="expectations-for-ui"></a>对用户界面的期望

1. 必须显示功能，是否项目是加载或延迟，具体取决于差异没有可视化。
2. 任何列表或通过该解决方案的加载项目的枚举必须包含延迟的项目。
3. 提供对已加载的项目的全部操作应可对照延迟项目。
4. 功能必须加载请求的项目时，才︰
  * 没有直接的用户交互的功能。 不会抢先会加载项目。
  * "查看更多结果"手势是通过用户。 为此 UI 准则，请参阅下文。
  * 只有完全加载的项目可以用于满足该操作。 使用 LSL 和打开的项目 Api，只要有可能，并发送功能请求要求缺少的功能时。

### <a name="changes-in-platform-apis-to-help-drive-ui"></a>平台 Api，可帮助促进用户界面中的更改

1. 提供了新的 Api，以提出解决方案，是否它已打开轻型解决方案负载模式和如何许多项目都处于延迟状态中。
2. 延迟的所有项目都加载解决方案中时，将为提供新的事件。
3. 新的 Api 可用于要求是否推迟一个项目。
4. 现有 Api 将更新以包括延迟的项目请求加载项目时。
5. 现有的 Api 会更新为明确的解决方案是完全加载后打开解决方案。

### <a name="how-to-add-see-more-results-for-a-feature"></a>如何添加功能"请参阅更多结果"。

对项目的内容执行查询的功能应考虑延迟项目的影响。 在某些情况下，功能可以从 LSL 和工作区 Api 获取他们的查询的结果，延迟的项目。 在其他情况下，一项功能的限制要求要加载的项目。 这两种情况应该提供新的"查看更多结果"手势，使用户可以完全加载项目和重新查询。 该笔势使功能可以向用户提供实际加载项目时获得最佳结果的方法时没有延迟的项目时，为最近似。

功能的常规算法应为︰

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

### <a name="when-the-query-is-performed-over-the-whole-solution"></a>当整个解决方案相比执行查询

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
    if (ErrorHandler.Succeeded(hr) && ((uint)deferredCount > 0))
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

IVsSolution7.IsSolutionLoadDeferred (out bool 延迟)

如果已在延迟模式下加载当前的解决方案，则返回 true。 请注意，即使延迟的所有项目也都是最终最初解决方案加载在延迟模式下，如果当前在会话中加载 （显式用户操作或强制操作），此属性仍将返回 true。

__VSPROPID7。VSPROPID_DeferredProjectCount

返回当前延迟模式下的项目数。 此属性将在范围 [0，VSPROPID_ProjectCount] 中具有一个值。

__VSHPROPID9。VSHPROPID_IsDeferred

如果项目层次结构处于延迟的加载状态，则返回 true。

值为 EPF_DEFERRED 和 EPF_NOTDEFERRED __VSENUMPROJFLAGS3

这些标志可以传递给[IVsSolution.GetProjectEnum()](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivssolution.getprojectenum.aspx)要循环访问延迟和非延迟项目。

### <a name="new-events"></a>新的事件

IVsSolutionEvents7.OnAfterLoadAllDeferredProjects()

在已加载延迟的所有项目后，将引发此事件。 此时，VSPROPID_DeferredProjectCount 等于 0。 请注意，此事件不引发作为解决方案负载的一部分，并且可能不会引发所有在会话中。 仅触发是否以及何时加载延迟的所有项目。

### <a name="changes-to-existing-api"></a>对现有 API 的更改

* 传递[__VSENUMPROJFLAGS](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vsenumprojflags.aspx)。到 EPF_LOADEDINSOLUTION [IVsSolution.GetProjectEnum()](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivssolution.getprojectenum.aspx)项目返回推迟。
* 传递[__VSENUMPROJFLAGS](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vsenumprojflags.aspx)。EPF_UNLOADEDINSOLUTION 不会返回延迟的项目。
* [KnownUIContexts.SolutionExistsAndFullyLoadedContext](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.knownuicontexts.solutionexistsandfullyloadedcontext.aspx)设置为打开的解决方案，则返回 true。 延迟的项目将被视为加载，因此，此上下文设置很多早于在非 LSL 模式下。
* [__VSPROPID](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vspropid.aspx)。VSPROPID_ProjectCount 返回加载和延迟项目的总和。

## <a name="helpful-code-snippets"></a>很有帮助的代码段

### <a name="check-if-a-solution-was-opened-in-deferred-load-mode"></a>检查是否在延迟的加载模式中打开解决方案

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

### <a name="check-if-a-project-is-deferred"></a>检查是否推迟一个项目

```csharp
/// <summary>
/// Checks to see if a project is deferred.
/// </summary>
/// <param name="projectsToLoad">A set of deferred and/or loaded projects to ensure are loaded.</param>
/// <returns>True if the project is deferred. False if it is any other state, such as loaded, unloaded, or virtual.</returns>
/// <remarks>Requires Microsoft.VisualStudio.Shell.15.0.dll</remarks>
public static bool IsInDeferredState(IVsHierarchy vsHierarchy)
{
    object deferred;
    int hr = vsHierarchy.GetProperty((int)VSConstants.VSITEMID.Root, (uint)__VSHPROPID9.VSHPROPID_IsDeferred, out deferred);

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

### <a name="load-a-set-of-projects"></a>加载一组项目

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

工作区中的新 Api 通过 IVsSolutionWorkspaceService 来帮助检索有关解决方案的详细的信息公开。

这些 Api 可以用于获取当前工作区、 该活动解决方案、 托管的命令行信息，以及工作区的索引服务。 这些 Api 可以进一步利用索引服务以获取详细的数据，例如，所有源文件在项目中，将源文件的所属的项目包含在当前解决方案中的所有项目在项目等所有 P2P 引用。

下面的代码段演示了工作区 Api 的用法。

### <a name="get-ivssolutionworkspaceservice-initially"></a>最初获取 IVsSolutionWorkspaceService

>**注意︰**请仅获取 IVsSolutionWorkspaceService LSL 方案以避免将加载工作区 API 程序包中。

```csharp
private readonly Lazy<IVsSolutionWorkspaceService> _solutionWorkspaceService;

[ImportingConstructor]
public DeferredProjectWorkspaceService(SVsServiceProvider serviceProvider)
{
    _solutionWorkspaceService = new Lazy<IVsSolutionWorkspaceService>(
        () => (IVsSolutionWorkspaceService)serviceProvider.GetService(typeof(SVsSolutionWorkspaceService)));
}
```

>**注意︰**下面的代码段假定 _solutionWorkspaceService 已延迟初始化。

### <a name="get-managed-command-line-info-for-deferred-projects-for-active-solution-configuration"></a>获得有关延迟项目类型提供的活动解决方案配置被管理的命令行信息

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

### <a name="get-the-active-solution-file-in-lsl"></a>获取在 LSL 活动解决方案文件

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

### <a name="get-the-owning-project-of-a-source-file"></a>获取源文件中的所属项目

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

### <a name="get-all-source-files-from-a-project"></a>从项目中获取的所有源代码文件

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

### <a name="get-the-p2p-references-in-a-project"></a>在项目中获取 P2P 引用

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

由于 LSL 的性质，它是有意用户看不到加载和延迟项目之间的差异。 这会使功能开发和测试困难。

您可以通过执行以下启用延迟的项目的用户界面中的可视化提示︰

1. 关闭 Visual Studio
2. Regedit.exe
3. 选择 HKLM
4. 文件&1;> 加载配置单元
5. `%localappdata%\microsoft\visualstudio\15.0_<instance ID>\privateregistry.bin`
6. 输入"visual Studio"作为密钥名称
7. 设置`HKLM\VisualStudio\Software\Microsoft\VisualStudio\15.0_<instanceID>\FeatureFlags\Solution\Loading\Deferred\Hint\Value=1`(DWORD)
8. 选择 HKLM\VisualStudio
9. 文件&1;> 卸载配置单元
10. 启动 Visual Studio

如有任何进一步的问题，请与联系[ lslsupport@microsoft.com ](mailto:lslsupport@microsoft.com)。







