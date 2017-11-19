---
title: "保留的项目项的属性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 61a477fa760a2ef9026b06facc8bc592706c5dd3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="persisting-the-property-of-a-project-item"></a>保留的项目项的属性
你可能想要保留添加到项目项，如源文件的作者的属性。 可以通过将属性存储在项目文件来执行此操作。  
  
 保存项目文件中的属性的第一步是获取作为项目的层次结构<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>接口。 您可以通过使用自动化或通过使用获得此接口<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>。 一旦获取接口，可用于确定当前选择的项目项。 项目项 ID 之后，你可以使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A>以添加属性。  
  
 在下面的过程中，保留 VsPkg.cs 属性`Author`值`Tom`项目文件中。  
  
### <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>若要获取与 DTE 对象的项目层次结构  
  
1.  将以下代码添加到你的 VSPackage 中：  
  
    ```csharp  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
    EnvDTE.Project project = dte.Solution.Projects.Item(1);  
  
    string uniqueName = project.UniqueName;  
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
    IVsHierarchy hierarchy;  
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    ```  
  
### <a name="to-persist-the-project-item-property-with-the-dte-object"></a>若要保存项目项属性与 DTE 对象  
  
1.  将以下代码添加到在前一过程的方法中给出的代码：  
  
    ```csharp  
    IVsBuildPropertyStorage buildPropertyStorage =   
        hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        uint itemId;  
        string fullPath = (string)project.ProjectItems.Item(  
            "VsPkg.cs").Properties.Item("FullPath").Value;  
        hierarchy.ParseCanonicalName(fullPath, out itemId);  
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");  
    }  
    ```  
  
### <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>若要获取使用 IVsMonitorSelection 的项目层次结构  
  
1.  将以下代码添加到你的 VSPackage 中：  
  
    ```csharp  
    IVsHierarchy hierarchy = null;  
    IntPtr hierarchyPtr = IntPtr.Zero;  
    IntPtr selectionContainer = IntPtr.Zero;  
    uint itemid;  
  
    // Retrieve shell interface in order to get current selection  
    IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection;  
    if (monitorSelection == null)  
        throw new InvalidOperationException();  
  
    try  
    {  
        // Get the current project hierarchy, project item, and selection container for the current selection  
        // If the selection spans multiple hierachies, hierarchyPtr is Zero  
        IVsMultiItemSelect multiItemSelect = null;  
        ErrorHandler.ThrowOnFailure(  
            monitorSelection.GetCurrentSelection(  
                out hierarchyPtr, out itemid,   
                out multiItemSelect, out selectionContainer));  
  
        // We only care if there is only one node selected in the tree  
        if (!(itemid == VSConstants.VSITEMID_NIL ||   
            hierarchyPtr == IntPtr.Zero ||  
            multiItemSelect != null ||  
            itemid == VSConstants.VSITEMID_SELECTION))  
        {  
            hierarchy = Marshal.GetObjectForIUnknown(hierarchyPtr)  
                as IVsHierarchy;  
        }  
    }  
    finally  
    {  
        if (hierarchyPtr != IntPtr.Zero)  
            Marshal.Release(hierarchyPtr);  
        if (selectionContainer != IntPtr.Zero)  
            Marshal.Release(selectionContainer);  
    }  
    ```  
  
2.  
  
### <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>若要保留选定的项目项属性，给定的项目层次结构  
  
1.  将以下代码添加到在前一过程的方法中给出的代码：  
  
    ```  
    IVsBuildPropertyStorage buildPropertyStorage =   
        hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");  
    }  
    ```  
  
### <a name="to-verify-that-the-property-is-persisted"></a>若要验证该属性持久化  
  
1.  启动[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]然后打开或创建的解决方案。  
  
2.  选择项目项中的 VsPkg.cs**解决方案资源管理器**。  
  
3.  使用断点或否则确定你的 VSPackage 已加载并且 SetItemAttribute 运行。  
  
    > [!NOTE]
    >  你可以自动上载 UI 上下文中 VSPackage <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionExists>。 有关详细信息，请参阅[加载 Vspackage](../extensibility/loading-vspackages.md)。  
  
4.  关闭[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]然后在记事本中打开项目文件。 你应该会看到\<作者 > 标记具有值 Tom，，如下所示：  
  
    ```  
    <Compile Include="VsPkg.cs">  
        <Author>Tom</Author>  
    </Compile>  
    ```  
  
## <a name="see-also"></a>另请参阅  
 [自定义工具](../extensibility/internals/custom-tools.md)