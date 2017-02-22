---
title: "通用 Windows 项目管理 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# 通用 Windows 项目管理
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

通用 Windows 应用程序是面向 Windows 8.1 和 Windows Phone 8.1，从而允许开发人员在这两个平台上使用的代码和其他资产的应用程序。 共享的代码和资源都保存在共享项目中，而特定于平台的代码和资源保留在单独的项目，一个用于 Windows，另一个用于 Windows Phone。 有关通用 Windows 应用程序的详细信息，请参阅 [通用 Windows 应用程序](http://msdn.microsoft.com/library/windows/apps/dn609832.aspx)。 管理项目的 visual Studio 扩展应注意通用 Windows 应用程序项目具有不同于单一平台的应用程序的结构。 本演练演示如何导航共享的项目和管理的共享的项。  
  
## 系统必备  
 启动 Visual Studio 2015 中，您并不安装 Visual Studio SDK 从下载中心获得。 它将包括作为 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
### 导航共享的项目  
  
1.  创建一个名为 C\# VSIX 项目 **TestUniversalProject**。 \(**文件，新建、 项目** 然后 **C\# 中，可扩展性，Visual Studio 程序包**\)。 添加 **自定义命令** 项目项模板 \(在解决方案资源管理器，右键单击项目节点并选择 **添加 \/ 新项**, ，然后转到 **扩展性**\)。 命名该文件 **TestUniversalProject**。  
  
2.  添加对 Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll 和 Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll 引用 \(在 **扩展** 部分\)。  
  
3.  打开 TestUniversalProject.cs 并添加以下 `using` 语句︰  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.PlatformUI;  
    using Microsoft.Internal.VisualStudio.PlatformUI;   
    using System.Collections.Generic;   
    using System.IO;  
    using System.Windows.Forms;  
    ```  
  
4.  在 TestUniversalProject 类中添加一个指向的私有字段 **输出** 窗口。  
  
    ```c#  
    public sealed class TestUniversalProject   
    {  
        IVsOutputWindowPane output;  
    . . .  
    }  
    ```  
  
5.  设置对 TestUniversalProject 构造函数内的输出窗格的引用︰  
  
    ```c#  
    private TestUniversalProject(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException("package");  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
            EventHandler eventHandler = this.ShowMessageBox;  
            MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
        // get a reference to the Output window  
                    output = (IVsOutputWindowPane)ServiceProvider.GetService(typeof(SVsGeneralOutputWindowPane));  
    }  
    ```  
  
6.  移除从现有代码 `ShowMessageBox` 方法︰  
  
    ```c#  
    private void ShowMessageBox(object sender, EventArgs e)   
    {  
    }  
    ```  
  
7.  获取 DTE 对象，我们将使用在本演练中有多种不同的用途。 此外，请确保单击菜单按钮时加载的解决方案。  
  
    ```c#  
    private void ShowMessageBox(object sender, EventArgs e)  
    {   
        var dte = (EnvDTE.DTE)this.ServiceProvider.GetService(typeof(EnvDTE.DTE));  
        if (dte.Solution != null)   
        {  
            . . .  
        }  
        else   
        {  
            MessageBox.Show("No solution is open");  
            return;   
        }  
    }  
    ```  
  
8.  查找共享的项目。 共享的项目是一个纯粹的容器;它不生成或生成输出。 下面的方法查找第一个共享的项目解决方案中寻找 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 具有共享的项目功能的对象。  
  
    ```c#  
    private IVsHierarchy FindSharedProject()  
    {  
        var sln = (IVsSolution)this.ServiceProvider.GetService(typeof(SVsSolution));  
        Guid empty = Guid.Empty;  
        IEnumHierarchies enumHiers;  
  
        //get all the projects in the solution  
        ErrorHandler.ThrowOnFailure(sln.GetProjectEnum((uint)__VSENUMPROJFLAGS.EPF_LOADEDINSOLUTION, ref empty, out enumHiers));  
        foreach (IVsHierarchy hier in ComUtilities.EnumerableFrom(enumHiers))  
        {  
            if (PackageUtilities.IsCapabilityMatch(hier, "SharedAssetsProject"))  
            {  
                return hier;  
            }  
        }  
        return null;  
    }  
    ```  
  
9. 在 `ShowMessageBox` 方法中，输出标题 \(中显示的项目名称 **解决方案资源管理器**\) 的共享项目。  
  
    ```c#  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));  
  
        if (dte.Solution != null)  
        {  
            var sharedHier = this.FindSharedProject();  
            if (sharedHier != null)  
            {  
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,  
                     (int)__VSHPROPID.VSHPROPID_Caption);  
                output.OutputStringThreadSafe(string.Format("Found shared project: {0}\n", sharedCaption));  
            }  
            else  
            {  
                MessageBox.Show("Solution has no shared project");  
                return;  
            }  
                }  
        else  
        {  
            MessageBox.Show("No solution is open");  
            return;  
        }  
    }  
    ```  
  
10. 获取活动平台项目。 平台项目都包含特定于平台的代码和资源的项目。 下面的方法使用新字段 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7> 若要获取活动平台项目。  
  
    ```c#  
    private IVsHierarchy GetActiveProjectContext(IVsHierarchy hierarchy)  
    {  
        IVsHierarchy activeProjectContext;  
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,  
             (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, out activeProjectContext))  
        {  
            return activeProjectContext;  
        }  
        else  
        {  
            return null;  
        }  
    }  
    ```  
  
11. 在 `ShowMessageBox` 方法中，输出活动平台项目的标题。  
  
    ```c#  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));  
  
        if (dte.Solution != null)  
        {  
            var sharedHier = this.FindSharedProject();  
            if (sharedHier != null)  
            {  
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,  
                     (int)__VSHPROPID.VSHPROPID_Caption);  
                output.OutputStringThreadSafe(string.Format("Shared project: {0}\n", sharedCaption));  
  
                var activePlatformHier = this.GetActiveProjectContext(sharedHier);  
                if (activePlatformHier != null)  
                {  
                    string activeCaption = HierarchyUtilities.GetHierarchyProperty<string>(activePlatformHier,  
                         (uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_Caption);  
                    output.OutputStringThreadSafe(string.Format("Active platform project: {0}\n", activeCaption));  
                }  
                else  
                {  
                MessageBox.Show("Shared project has no active platform project");  
                }  
            }  
            else  
            {  
                MessageBox.Show("Solution has no shared project");  
                return;  
            }  
        }  
        else  
            {  
                MessageBox.Show("No solution is open");  
                return;  
            }  
        }  
  
    ```  
  
12. 循环访问平台项目。 下面的方法获取从共享的项目导入的所有 （平台） 项目。  
  
    ```c#  
    private IEnumerable<IVsHierarchy> EnumImportingProjects(IVsHierarchy hierarchy)  
    {  
        IVsSharedAssetsProject sharedAssetsProject;  
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,  
            (int)__VSHPROPID7.VSHPROPID_SharedAssetsProject, out sharedAssetsProject)  
            && sharedAssetsProject != null)  
        {  
            foreach (IVsHierarchy importingProject in sharedAssetsProject.EnumImportingProjects())  
            {  
                yield return importingProject;  
            }  
        }  
    }  
    ```  
  
    > [!IMPORTANT]
    >  如果用户已经在实验实例中打开一个 c \+ \+ 通用 Windows 应用程序项目，上面的代码将引发异常。 这是一个已知的问题。 若要避免此异常，请替换 `foreach` 上面阻止替换为以下︰  
  
    ```c#  
    var importingProjects = sharedAssetsProject.EnumImportingProjects();  
    for (int i = 0; i < importingProjects.Count; ++i)  
    {  
        yield return importingProjects[i];  
    }   
    ```  
  
13. 在 `ShowMessageBox` 方法中，输出每个平台项目的标题。 输出活动平台项目的标题的行后面插入以下代码。 此列表中显示已加载的平台项目。  
  
    ```c#  
    output.OutputStringThreadSafe("Platform projects:\n");  
  
    IEnumerable<IVsHierarchy> projects = this.EnumImportingProjects(sharedHier);  
  
    bool isActiveProjectSet = false;  
    foreach (IVsHierarchy platformHier in projects)  
    {  
        string platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,  
            (int)__VSHPROPID.VSHPROPID_Caption);  
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));  
    }  
    ```  
  
14. 将活动平台项目更改。 下面的方法设置活动项目使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>。  
  
    ```c#  
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)  
    {  
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);  
    }  
    ```  
  
15. 在 `ShowMessageBox` 方法中，更改活动平台项目。 插入此代码 `foreach` 块。  
  
    ```c#  
    bool isActiveProjectSet = false;  
    string platformCaption = null;  
    foreach (IVsHierarchy platformHier in projects)  
    {  
        platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,  
             (int)__VSHPROPID.VSHPROPID_Caption);  
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));  
  
        // if this project is neither the shared project nor the current active platform project,   
        // set it to be the active project  
        if (!isActiveProjectSet && platformHier != activePlatformHier)  
        {  
            this.SetActiveProjectContext(sharedHier, platformHier);  
            activePlatformHier = platformHier;  
            isActiveProjectSet = true;  
        }  
    }  
    output.OutputStringThreadSafe("set active project: " + platformCaption +'\n');  
    ```  
  
16. 现在试一试。 按 F5 以启动该实验实例。 在实验实例中创建一个 C\# 通用中心应用程序项目 \(在 **新项目** 对话框中， **Visual C\# \/ Windows \/ Windows 8 \/ 通用 \/ 中心应用**\)。 在加载解决方案后，请转到 **工具** 菜单，然后单击 **调用 TestUniversalProject**, ，然后签入文本 **输出** 窗格。 您应看到类似于以下内容︰  
  
    ```  
    Found shared project: HubApp.Shared  
    The active platform project: HubApp.Windows  
    Platform projects:  
     * HubApp.Windows  
     * HubApp.WindowsPhone  
    set active project: HubApp.WindowsPhone  
    ```  
  
### 管理平台项目中的共享的项  
  
1.  在平台项目中找到共享的项目。 共享项目中的项显示在平台项目中为共享项目。 看不到它们在 **解决方案资源管理器**, ，但您也可以逐步项目层次结构，以找到它们。 以下方法将指导层次结构，并收集所有共享的项。 （可选），它将输出每个项的标题。 由新属性标识的共享的项 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7>。  
  
    ```c#  
    private void InspectHierarchyItems(IVsHierarchy hier, uint itemid, int level, List<uint> itemIds, bool getSharedItems, bool printItems)  
    {  
        string caption = HierarchyUtilities.GetHierarchyProperty<string>(hier, itemid, (int)__VSHPROPID.VSHPROPID_Caption);  
        if (printItems)  
            output.OutputStringThreadSafe(string.Format("{0}{1}\n", new string('\t', level), caption));  
  
        // if getSharedItems is true, inspect only shared items; if it's false, inspect only unshared items  
        bool isSharedItem;  
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID7.VSHPROPID_IsSharedItem, out isSharedItem)  
            && (isSharedItem == getSharedItems))  
        {  
            itemIds.Add(itemid);  
        }  
  
        uint child;  
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID.VSHPROPID_FirstChild, Unbox.AsUInt32, out child)  
            && child != (uint)VSConstants.VSITEMID.Nil)  
        {  
            this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);  
  
            while (HierarchyUtilities.TryGetHierarchyProperty(hier, child, (int)__VSHPROPID.VSHPROPID_NextSibling, Unbox.AsUInt32, out child)  
                && child != (uint)VSConstants.VSITEMID.Nil)  
            {  
                this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);  
            }  
                    }  
    }  
    ```  
  
2.  在 `ShowMessageBox` 方法中，添加以下代码来遍历平台项目层次结构项。 插入放 `foreach` 块。  
  
    ```c#  
    output.OutputStringThreadSafe("Walk the active platform project:\n");  
    var sharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ```  
  
3.  读取共享的项目。 共享的项将显示在平台项目为隐藏链接的文件，并能够读取作为普通链接的文件的所有属性。 下面的代码读取第一个共享项目的完整路径。  
  
    ```c#  
    var sharedItemId = sharedItemIds[0];  
    string fullPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));  
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));  
    ```  
  
4.  现在试一试。 按 F5 以启动该实验实例。 在实验实例中创建一个 C\# 通用中心应用程序项目 \(在 **新项目** 对话框中， **Visual C\# \/ Windows \/ Windows 8 \/ 通用 \/ 中心应用程序**\) 转到 **工具** 菜单，然后单击 **调用 TestUniversalProject**, ，，然后签入文本 **输出** 窗格。 您应看到类似于以下内容︰  
  
    ```  
    Found shared project: HubApp.Shared  
    The active platform project: HubApp.Windows  
    Platform projects:  
     * HubApp.Windows  
     * HubApp.WindowsPhone  
    set active project: HubApp.WindowsPhone  
    Walk the active platform project:  
        HubApp.WindowsPhone  
            <HubApp.Shared>  
                App.xaml  
                    App.xaml.cs  
                Assets  
                    DarkGray.png  
                    LightGray.png  
                    MediumGray.png  
                Common  
                    NavigationHelper.cs  
                    ObservableDictionary.cs  
                    RelayCommand.cs  
                    SuspensionManager.cs  
                DataModel  
                    SampleData.json  
                    SampleDataSource.cs  
                HubApp.Shared.projitems  
                Strings  
                    en-US  
                        Resources.resw  
            Assets  
                HubBackground.theme-dark.png  
                HubBackground.theme-light.png  
                Logo.scale-240.png  
                SmallLogo.scale-240.png  
                SplashScreen.scale-240.png  
                Square71x71Logo.scale-240.png  
                StoreLogo.scale-240.png  
                WideLogo.scale-240.png  
            HubPage.xaml  
                HubPage.xaml.cs  
            ItemPage.xaml  
                ItemPage.xaml.cs  
            Package.appxmanifest  
            Properties  
                AssemblyInfo.cs  
            References  
                .NET for Windows Store apps  
                HubApp.Shared  
                Windows Phone 8.1  
            SectionPage.xaml  
                SectionPage.xaml.cs  
    ```  
  
### 检测平台项目和共享的项目中的更改  
  
1.  可以使用层次结构和项目事件以检测更改在共享项目中，就像可以平台的项目。 但是，共享项目中的项目项是不可见，这意味着共享的项目项发生更改时，某些事件不会发生激发。  
  
     请考虑重命名项目中的文件时的事件序列︰  
  
    1.  该文件名更改磁盘上。  
  
    2.  项目文件将更新以包括该文件的新名称。  
  
     层次结构中的事件 \(例如， <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>\) 通常可跟踪所做的更改显示在 UI 中，如下所示 **解决方案资源管理器**。 层次结构中的事件，请考虑组成文件删除操作，然后文件添加的文件重命名操作。 但是，当更改不可见的项层次结构事件系统激发 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> 事件但不是 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> 事件。 因此，如果您重命名的平台项目中的文件，您获取这两项 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>, ，但如果您重命名共享项目的文件中，您获得仅 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>。  
  
     若要在项目项中进行修订，可以处理 DTE 项目项事件 \(在中找到的 <xref:EnvDTE.ProjectItemsEventsClass>\)。 但是，如果您正处理大量的事件，您可以获得更好的性能处理中的事件 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>。 在本演练中我们将显示仅限于的层次结构事件和 DTE 事件。 在此过程中对共享的项目和平台项目添加事件侦听器。 然后，重命名共享项目中的一个文件，并在平台项目中的另一个文件后，您可以看到为每个重命名操作激发的事件。  
  
     在此过程中对共享的项目和平台项目添加事件侦听器。 然后，重命名共享项目中的一个文件，并在平台项目中的另一个文件后，您可以看到为每个重命名操作激发的事件。  
  
2.  添加事件侦听器。 将新的类文件添加到项目，并调用它 HierarchyEventListener.cs。  
  
3.  打开 HierarchyEventListener.cs 文件并添加以下 using 语句︰  
  
    ```c#  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio;  
    using System.IO;  
  
    ```  
  
4.  具有 `HierarchyEventListener` 类实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>:  
  
    ```c#  
    class HierarchyEventListener : IVsHierarchyEvents  
    { }  
  
    ```  
  
5.  实现的成员 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>, ，如下面的代码。  
  
    ```c#  
    class HierarchyEventListener : IVsHierarchyEvents  
    {  
        private IVsHierarchy hierarchy;  
        IVsOutputWindowPane output;   
  
        internal HierarchyEventListener(IVsHierarchy hierarchy, IVsOutputWindowPane outputWindow) {  
             this.hierarchy = hierarchy;  
             this.output = outputWindow;  
        }  
  
        int IVsHierarchyEvents.OnInvalidateIcon(IntPtr hIcon) {  
            return VSConstants.S_OK;  
        }  
  
        int IVsHierarchyEvents.OnInvalidateItems(uint itemIDParent) {  
            return VSConstants.S_OK;  
        }  
  
        int IVsHierarchyEvents.OnItemAdded(uint itemIDParent, uint itemIDSiblingPrev, uint itemIDAdded) {  
            output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemAdded: " + itemIDAdded + "\n");  
            return VSConstants.S_OK;  
        }  
  
        int IVsHierarchyEvents.OnItemDeleted(uint itemID) {  
            output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemDeleted: " + itemID + "\n");  
            return VSConstants.S_OK;  
        }  
  
        int IVsHierarchyEvents.OnItemsAppended(uint itemIDParent) {  
            output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemsAppended\n");  
            return VSConstants.S_OK;  
        }  
  
        int IVsHierarchyEvents.OnPropertyChanged(uint itemID, int propID, uint flags) {  
            output.OutputStringThreadSafe("IVsHierarchyEvents.OnPropertyChanged: item ID " + itemID + "\n");  
            return VSConstants.S_OK;  
        }  
    }  
  
    ```  
  
6.  在同一个类中添加另一个事件的事件处理程序 DTE <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>, ，每当重命名项目项时出现这种情况。  
  
    ```c#  
    public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)  
    {  
        output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",  
             oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));  
    }  
    ```  
  
7.  注册的层次结构事件。 您需要注册单独跟踪每个项目。 添加下面的代码 `ShowMessageBox`, ，一个用于共享的项目中，而另一个用于平台项目之一。  
  
    ```c#  
    // hook up the event listener for hierarchy events on the shared project  
    HierarchyEventListener listener1 = new HierarchyEventListener(sharedHier, output);  
    uint cookie1;  
    sharedHier.AdviseHierarchyEvents(listener1, out cookie1);  
  
    // hook up the event listener for hierarchy events on the   
    active project  
    HierarchyEventListener listener2 = new HierarchyEventListener(activePlatformHier, output);  
    uint cookie2;  
    activePlatformHier.AdviseHierarchyEvents(listener2, out cookie2);  
    ```  
  
8.  DTE 项目项事件注册 <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>。 可以将挂接到第二个侦听器后，请添加以下代码。  
  
    ```c#  
    // hook up DTE events for project items  
    Events2 dteEvents = (Events2)dte.Events;  
    dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;  
  
    ```  
  
9. 修改共享的项。 不能修改平台项目; 中的共享的项相反，必须在这些项目的实际所有者的共享项目中修改它们。 可以使用共享项目中获取相应的项 ID <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>, ，向其提供共享的项的完整路径。 然后可以修改共享的项。 于平台的项目传播更改。  
  
    > [!IMPORTANT]
    >  您应找出项目项共享的项目之前对其进行修改。  
  
     下面的方法修改的项目项文件的名称。  
  
    ```c#  
    private void ModifyFileNameInProject(IVsHierarchy project, string path)  
    {    
        int found;  
        uint projectItemID;  
        VSDOCUMENTPRIORITY[] priority = new VSDOCUMENTPRIORITY[1];  
        if (ErrorHandler.Succeeded(((IVsProject)project).IsDocumentInProject(path, out found, priority, out projectItemID))  
            && found != 0)  
        {  
            var name = DateTime.Now.Ticks.ToString() + Path.GetExtension(path);  
            project.SetProperty(projectItemID, (int)__VSHPROPID.VSHPROPID_EditLabel, name);  
            output.OutputStringThreadSafe(string.Format("Renamed {0} to {1}\n", path,name));  
        }  
    }  
    ```  
  
10. 调用此方法，别忘了中的其他代码 `ShowMessageBox` 若要修改的文件的名称中共享的项目中的项。 获取共享的项目中的项的完整路径的代码后面插入此操作。  
  
    ```c#  
    // change the file name of an item in a shared project  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));   
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));  
    this.ModifyFileNameInProject(sharedHier, fullPath);  
    ```  
  
11. 生成并运行该项目。 在实验实例中创建 C\# 通用 hub 应用程序，请转到 **工具** 菜单，然后单击 **调用 TestUniversalProject**, ，并检查常规输出窗格中的文本。 在共享中的第一项的名称应更改项目 （我们希望它是 App.xaml 文件），并且您应该会看到 <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> 触发事件。 在这种情况下，由于重命名 App.xaml 导致 App.xaml.cs 以及重命名，您应该看到以下四个事件 （对于每个平台项目的两个）。 （DTE 事件不跟踪共享的项目中的项。） 您应看到两个 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> 事件 （一个是用于每个平台项目中），但不对 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> 事件。  
  
12. 现在，尝试重命名在平台项目中，文件，可以看到获取激发的事件中的差异。 添加下面的代码 `ShowMessageBox` 后，调用 `ModifyFileName`。  
  
    ```c#  
    // change the file name of an item in a platform project  
    var unsharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, unsharedItemIds, false, false);  
  
    var unsharedItemId = unsharedItemIds[0];  
    string unsharedPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(unsharedItemId, out unsharedPath));  
    output.OutputStringThreadSafe(string.Format("Platform project item ID = {0}, full path = {1}\n", unsharedItemId, unsharedPath));  
  
    this.ModifyFileNameInProject(activePlatformHier, unsharedPath);  
    ```  
  
13. 生成并运行该项目。 在实验实例中创建一个 C\# 通用项目，请转到 **工具** 菜单，然后单击 **调用 TestUniversalProject**, ，并检查常规输出窗格中的文本。 平台项目中的文件重命名后，您应该会同时看到 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> 事件和一个 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> 事件。 更改以来，文件会导致其他文件被更改，并且因为对平台项目中的项的更改不会传播任何地方，没有仅每个以上事件之一。