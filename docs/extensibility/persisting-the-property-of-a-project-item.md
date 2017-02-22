---
title: "保存项目项的属性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "属性，将添加到项目项"
  - "项目项，添加属性"
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# 保存项目项的属性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可能想要保留的属性添加到项目项，如源代码文件的作者。 可以通过将该属性存储在项目文件来执行此操作。  
  
 若要保存项目文件中的属性的第一步是获取作为项目的层次结构 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 接口。 您可以通过使用自动化功能或通过使用获得此接口 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>。 一旦获得该接口，可用于确定当前选定的项目项。 项目项 ID 后，可以使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> 以添加属性。  
  
 在下面的过程中，您将保留 VsPkg.cs 属性 `Author` 值 `Tom` 项目文件中。  
  
### 若要获取 DTE 对象的项目层次结构  
  
1.  将以下代码添加到你的 VSPackage 中:  
  
    ```c#  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE)); EnvDTE.Project project = dte.Solution.Projects.Item(1); string uniqueName = project.UniqueName; IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution)); IVsHierarchy hierarchy; solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    ```  
  
### 若要保存项目项属性与 DTE 对象  
  
1.  将以下代码添加到在前面过程中的方法中给出的代码:  
  
    ```c#  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage; if (buildPropertyStorage != null) { uint itemId; string fullPath = (string)project.ProjectItems.Item( "VsPkg.cs").Properties.Item("FullPath").Value; hierarchy.ParseCanonicalName(fullPath, out itemId); buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom"); }  
    ```  
  
### 若要获取使用 IVsMonitorSelection 项目层次结构  
  
1.  将以下代码添加到你的 VSPackage 中:  
  
    ```c#  
    IVsHierarchy hierarchy = null; IntPtr hierarchyPtr = IntPtr.Zero; IntPtr selectionContainer = IntPtr.Zero; uint itemid; // Retrieve shell interface in order to get current selection IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection; if (monitorSelection == null) throw new InvalidOperationException(); try { // Get the current project hierarchy, project item, and selection container for the current selection // If the selection spans multiple hierachies, hierarchyPtr is Zero IVsMultiItemSelect multiItemSelect = null; ErrorHandler.ThrowOnFailure( monitorSelection.GetCurrentSelection( out hierarchyPtr, out itemid, out multiItemSelect, out selectionContainer)); // We only care if there is only one node selected in the tree if (!(itemid == VSConstants.VSITEMID_NIL || hierarchyPtr == IntPtr.Zero || multiItemSelect != null || itemid == VSConstants.VSITEMID_SELECTION)) { hierarchy = Marshal.GetObjectForIUnknown(hierarchyPtr) as IVsHierarchy; } } finally { if (hierarchyPtr != IntPtr.Zero) Marshal.Release(hierarchyPtr); if (selectionContainer != IntPtr.Zero) Marshal.Release(selectionContainer); }  
    ```  
  
2.  
  
### 若要保存所选的项目项的属性，给定的项目层次结构  
  
1.  将以下代码添加到在前面过程中的方法中给出的代码:  
  
    ```  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage; if (buildPropertyStorage != null) { buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom"); }  
    ```  
  
### 若要验证该属性保持不变  
  
1.  启动 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 然后打开或创建一个解决方案。  
  
2.  选择项目项中的 VsPkg.cs **解决方案资源管理器**。  
  
3.  使用断点或否则确定加载你的 VSPackage，并且该 SetItemAttribute 运行。  
  
    > [!NOTE]
    >  您可以自动加载 VSPackage 中 UI 上下文 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionExists>。 有关详细信息，请参阅[加载 Vspackage](../extensibility/loading-vspackages.md)。  
  
4.  关闭 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，然后在记事本中打开项目文件。 您应该看到与值 Tom \< 作者 \> 标记，如下所示:  
  
    ```  
    <Compile Include="VsPkg.cs"> <Author>Tom</Author> </Compile>  
    ```  
  
## 请参阅  
 [自定义工具](../extensibility/internals/custom-tools.md)