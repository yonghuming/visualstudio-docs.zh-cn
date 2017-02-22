---
title: "动态添加菜单项 | Microsoft Docs"
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
  - "DYNAMICITEMSTART"
  - "动态添加的菜单项"
  - "添加动态项的菜单"
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
caps.latest.revision: 37
caps.handback.revision: 37
ms.author: "gregvanl"
manager: "ghogen"
---
# 动态添加菜单项
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可以通过指定在运行时添加菜单项 `DynamicItemStart` 然后 （在代码中） 中定义的菜单项来显示和处理命令的命令根据在 Visual Studio 命令表 \(.vsct\) 文件中，占位符按钮定义的标志。 加载 VSPackage 时，该占位符将替换动态菜单项。  
  
 Visual Studio 将使用中的动态列表 **最近使用过** \(的 MRU\) 列表中，后者会显示最近打开的文档的名称，与 **Windows** 列表中，后者会显示当前打开的窗口的名称。`DynamicItemStart` 标志命令定义上的指定该命令是一个占位符，只有先打开 VSPackage。 当打开 VSPackage 时，占位符将被替换 0 或更多命令，会在运行时创建并添加到动态列表。 您不能以查看 VSPackage 打开之前，动态列表的显示位置菜单上的位置。 若要填充的动态列表，Visual Studio 会要求 VSPackage 要查找命令并将其第一个字符是占位符的 ID 相同的 ID。 当 Visual Studio 找到匹配的命令时，它将该命令的名称添加到动态列表。 然后它会增加 ID 并查找另一个匹配的命令将添加到动态列表，直到没有更多动态命令。  
  
 本演练演示如何设置命令的命令的 Visual Studio 解决方案中的启动项目 **解决方案资源管理器** 工具栏。 它使用活动解决方案中有一个项目的动态下拉列表菜单控制器。 若要防止此命令显示时，没有解决方法是打开的或者时打开的解决方案具有只有一个项目，仅当解决方案包含多个项目时将加载 VSPackage。  
  
 有关.vsct 文件的详细信息，请参阅 [Visual Studio 命令表 \(。Vsct\) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。  
  
## 使用菜单命令创建扩展  
  
1.  创建一个名为的 VSIX 项目 `DynamicMenuItems`。  
  
2.  当项目打开时，将添加到自定义命令的项模板并将其命名 **DynamicMenu**。 有关更多信息，请参见[使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
## 设置.vsct 文件中的元素  
 若要创建的工具栏上的动态菜单项的菜单控制器，您可以指定以下元素︰  
  
-   两个命令组，包含菜单控制器的一个，另一个包含下拉列表中的菜单项  
  
-   类型的一个菜单元素 `MenuController`  
  
-   两个按钮，一个充当占位符的菜单项，另一个，用于提供该图标，并在工具栏上的工具提示。  
  
1.  在 DynamicMenuPackage.vsct，来定义的命令 Id。 转到符号部分并替换 IDSymbol 元素中的 **guidDynamicMenuPackageCmdSet** GuidSymbol 块。 您需要定义两个组、 菜单控制器、 占位符命令和定位点命令 IDSymbol 元素。  
  
    ```c#  
    <GuidSymbol name="guidDynamicMenuPackageCmdSet" value="{ your GUID here }">  
        <IDSymbol name="MyToolbarItemGroup" value="0x1020" />  
        <IDSymbol name="MyMenuControllerGroup" value="0x1025" />  
        <IDSymbol name="MyMenuController" value ="0x1030"/>  
        <IDSymbol name="cmdidMyAnchorCommand" value="0x0103" />  
        <!-- NOTE: The following command expands at run time to some number of ids.  
         Try not to place command ids after it (e.g. 0x0105, 0x0106).  
         If you must add a command id after it, make the gap very large (e.g. 0x200) -->  
        <IDSymbol name="cmdidMyDynamicStartCommand" value="0x0104" />  
    </GuidSymbol>    
    ```  
  
2.  在组部分中，删除现有组并添加您刚定义的两个组︰  
  
    ```  
    <Groups>  
        <!-- The group that adds the MenuController on the Solution Explorer toolbar.   
             The 0x4000 priority adds this group after the group that contains the  
             Preview Selected Items button, which is normally at the far right of the toolbar. -->  
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" priority="0x4000" >  
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN" />  
        </Group>  
        <!-- The group for the items on the MenuController drop-down. It is added to the MenuController submenu. -->  
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" priority="0x4000" >  
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" />  
        </Group>  
    </Groups>  
    ```  
  
     添加 MenuController。 设置 DynamicVisibility 的命令标志，因为它不是始终可见。 不显示 ButtonText。  
  
    ```  
    <Menus>  
        <!-- The MenuController to display on the Solution Explorer toolbar.  
             Place it in the ToolbarItemGroup.-->  
        <Menu guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" priority="0x1000" type="MenuController">  
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" />  
            <CommandFlag>DynamicVisibility</CommandFlag>  
            <Strings>  
               <ButtonText></ButtonText>  
           </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
3.  为 MenuController 添加两个按钮，一个作为动态菜单项的占位符，一个为定位点。  
  
     占位符按钮的父级是 **MyMenuControllerGroup**。 将 DynamicItemStart、 DynamicVisibility 和 TextChanges 命令标志添加到占位符按钮。 不显示 ButtonText。  
  
     定位点按钮保存图标和工具提示文本。 父元素的定位点按钮也是 **MyMenuControllerGroup**。 添加 NoShowOnMenuController 的命令标志，以确保按钮不会实际出现在菜单上的控制器下拉列表中和 FixMenuController 的命令标志，以使其永久定位点。  
  
    ```  
    <!-- The placeholder for the dynamic items that expand to N items at runtime. -->  
    <Buttons>  
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyDynamicStartCommand" priority="0x1000" >  
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />  
          <CommandFlag>DynamicItemStart</CommandFlag>  
          <CommandFlag>DynamicVisibility</CommandFlag>  
          <CommandFlag>TextChanges</CommandFlag>  
          <!-- This text does not appear. -->  
          <Strings>  
            <ButtonText>Project</ButtonText>  
          </Strings>  
        </Button>  
  
        <!-- The anchor item to supply the icon/tooltip for the MenuController -->  
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyAnchorCommand" priority="0x0000" >  
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />  
          <!-- This is the icon that appears on the Solution Explorer toolbar. -->  
          <Icon guid="guidImages" id="bmpPicArrows"/>  
          <!-- Do not show on the menu controller's drop down list-->  
          <CommandFlag>NoShowOnMenuController</CommandFlag>  
          <!-- Become the permanent anchor item for the menu controller -->  
          <CommandFlag>FixMenuController</CommandFlag>  
          <!-- The text that appears in the tooltip.-->  
          <Strings>  
            <ButtonText>Set Startup Project</ButtonText>  
          </Strings>  
        </Button>  
    </Buttons>  
    ```  
  
4.  将图标添加到项目 （在资源文件夹中），然后再在.vsct 文件中添加对它的引用。 在本演练中，我们将使用包含在项目模板的箭头图标。  
  
5.  添加一个 VisibilityConstraints 部分外紧前面的符号部分的命令部分。 （如果将其添加后符号可能会收到一条警告。） 本部分可确保菜单控制器将仅在加载具有多个项目的解决方案时出现。  
  
    ```  
    <VisibilityConstraints>  
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->  
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>  
    </VisibilityConstraints>  
    ```  
  
## 实现动态菜单命令  
 创建动态菜单命令类，该类继承 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>。 在此实现中，构造函数指定要用于匹配命令的谓词。 必须重写 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> 方法可使用此谓词来设置 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> 属性，它标识要调用的命令。  
  
1.  创建一个新 C\# 类文件命名为 DynamicItemMenuCommand.cs，并添加一个名为类 **DynamicItemMenuCommand** ，该类继承自 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>:  
  
    ```c#  
    class DynamicItemMenuCommand : OleMenuCommand  
    {  
  
    }  
  
    ```  
  
2.  添加以下 using 语句︰  
  
    ```c#  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using System.ComponentModel.Design;  
    ```  
  
3.  添加一个私有字段来存储匹配谓词︰  
  
    ```c#  
    private Predicate<int> matches;  
  
    ```  
  
4.  添加继承自一个构造函数 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 构造函数，并指定命令处理程序和一个 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> 处理程序。 添加一个谓词匹配的命令︰  
  
    ```c#  
    public DynamicItemMenuCommand(CommandID rootId, Predicate<int> matches, EventHandler invokeHandler, EventHandler beforeQueryStatusHandler)  
        : base(invokeHandler, null /*changeHandler*/, beforeQueryStatusHandler, rootId)  
    {  
        if (matches == null)  
        {  
            throw new ArgumentNullException("matches");  
        }  
  
        this.matches = matches;  
    }  
    ```  
  
5.  重写 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> 方法，以便它调用匹配项，谓词和集 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> 属性︰  
  
    ```c#  
    public override bool DynamicItemMatch(int cmdId)  
    {  
        // Call the supplied predicate to test whether the given cmdId is a match.  
        // If it is, store the command id in MatchedCommandid   
        // for use by any BeforeQueryStatus handlers, and then return that it is a match.  
        // Otherwise clear any previously stored matched cmdId and return that it is not a match.  
        if (this.matches(cmdId))  
        {  
            this.MatchedCommandId = cmdId;  
            return true;  
        }  
  
        this.MatchedCommandId = 0;  
        return false;  
    }  
    ```  
  
## 添加命令  
 DynamicMenu 构造函数是在其中设置菜单命令，其中包括动态菜单和菜单项。  
  
1.  在 DynamicMenuPackageGuids.cs，将添加该命令集的 GUID 和命令 ID:  
  
    ```c#  
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    public const uint cmdidMyCommand = 0x104;  
    ```  
  
2.  在 DynamicMenu.cs 文件中，添加以下 using 语句︰  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    using System.ComponentModel.Design;  
    ```  
  
3.  在 DynamicMenu 类中，添加一个私有字段 **dte2**。  
  
    ```c#  
    private DTE2 dte2;  
    ```  
  
4.  添加私有 rootItemId 字段︰  
  
    ```c#  
    private int rootItemId = 0;  
    ```  
  
5.  在 DynamicMenu 构造函数中，添加菜单命令。 在下一节中，我们将定义命令处理程序中， `BeforeQueryStatus` 事件处理程序，并匹配谓词。  
  
    ```c#  
    private DynamicMenu(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            // Add the DynamicItemMenuCommand for the expansion of the root item into N items at run time.   
            CommandID dynamicItemRootId = new CommandID(new Guid(DynamicMenuPackageGuids.guidDynamicMenuPackageCmdSet), (int)DynamicMenuPackageGuids.cmdidMyCommand);  
            DynamicItemMenuCommand dynamicMenuCommand = new DynamicItemMenuCommand(dynamicItemRootId,  
                IsValidDynamicItem,  
                OnInvokedDynamicItem,  
                OnBeforeQueryStatusDynamicItem);  
                commandService.AddCommand(dynamicMenuCommand);  
                }  
  
        dte2 = (DTE2)this.ServiceProvider.GetService(typeof(DTE));  
    }  
    ```  
  
## 实现这些处理程序  
 若要在菜单控制器上实现动态菜单项，必须单击动态项时处理该命令。 您还必须实现设置菜单项的状态的逻辑。 将处理程序添加到 DynamicMenu 类。  
  
1.  若要实现 **设置启动项目** 命令中，添加 **OnInvokedDynamicItem** 事件处理程序。 它会查找其名称是以文本形式的已调用并将其设置为启动项目，通过设置其绝对路径中的命令相同的项目 <xref:EnvDTE.SolutionBuild.StartupProjects%2A> 属性。  
  
    ```c#  
    private void OnInvokedDynamicItem(object sender, EventArgs args)  
    {  
        DynamicItemMenuCommand invokedCommand = (DynamicItemMenuCommand)sender;  
        // If the command is already checked, we don’t need to do anything  
        if (invokedCommand.Checked)  
            return;  
  
        // Find the project that corresponds to the command text and set it as the startup project  
        var projects = dte2.Solution.Projects;  
        foreach (Project proj in projects)  
        {  
            if (invokedCommand.Text.Equals(proj.Name))  
            {  
                dte2.Solution.SolutionBuild.StartupProjects = proj.FullName;  
                return;  
            }  
        }  
    }  
    ```  
  
2.  添加 `OnBeforeQueryStatusDynamicItem` 事件处理程序。 这是处理程序之前调用 `QueryStatus` 事件。 它确定菜单项是否为"真正"的项，即不占位符项，以及是否该项目已选中 （即该项目已设置为启动项目）。  
  
    ```c#  
    private void OnBeforeQueryStatusDynamicItem(object sender, EventArgs args)  
    {  
        DynamicItemMenuCommand matchedCommand = (DynamicItemMenuCommand)sender;  
        matchedCommand.Enabled = true;  
        matchedCommand.Visible = true;  
  
        // Find out whether the command ID is 0, which is the ID of the root item.  
        // If it is the root item, it matches the constructed DynamicItemMenuCommand,  
         // and IsValidDynamicItem won't be called.  
        bool isRootItem = (matchedCommand.MatchedCommandId == 0);  
  
        // The index is set to 1 rather than 0 because the Solution.Projects collection is 1-based.  
        int indexForDisplay = (isRootItem ? 1 : (matchedCommand.MatchedCommandId - (int) DynamicMenuPackageGuids.cmdidMyCommand) + 1);  
  
        matchedCommand.Text = dte2.Solution.Projects.Item(indexForDisplay).Name;  
  
        Array startupProjects = (Array)dte2.Solution.SolutionBuild.StartupProjects;  
        string startupProject = System.IO.Path.GetFileNameWithoutExtension((string)startupProjects.GetValue(0));  
  
        // Check the command if it isn't checked already selected  
        matchedCommand.Checked = (matchedCommand.Text == startupProject);  
  
        // Clear the ID because we are done with this item.  
        matchedCommand.MatchedCommandId = 0;  
    }  
    ```  
  
## 实现的命令 ID 匹配谓词  
  
1.  现在，实现匹配谓词。 我们需要确定两件事情︰ 第一次，命令 ID 是否有效 （它是大于或等于声明的命令 ID），第二，它是否指定可能的项目 （它是小于的解决方案中的项目数）。  
  
    ```c#  
    private bool IsValidDynamicItem(int commandId)  
    {  
        // The match is valid if the command ID is >= the id of our root dynamic start item   
        // and the command ID minus the ID of our root dynamic start item  
        // is less than or equal to the number of projects in the solution.  
        return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);  
    }  
    ```  
  
## 设置要只在一个解决方案包含多个项目时加载 VSPackage  
 因为 **设置启动项目** 命令没有任何意义，除非该活动解决方案具有多个项目，您可以设置你的 VSPackage，若要仅在这种情况下自动加载。 您使用 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> 以及 UI 上下文 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>。 在 DynamicMenuPackage.cs 文件到 DynamicMenuPackage 类中添加以下属性︰  
  
```c#  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
[ProvideMenuResource("Menus.ctmenu", 1)]  
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]  
[Guid(DynamicMenuPackageGuids.PackageGuidString)]  
public sealed class DynamicMenuItemsPackage : Package  
{}  
```  
  
## 测试设置启动项目命令  
 现在，你可以测试您的代码。  
  
1.  生成项目并启动调试。 应显示的实验实例。  
  
2.  在实验实例中，打开具有多个项目的解决方案。  
  
     您应看到针对箭头图标 **解决方案资源管理器** 工具栏。 在将其展开时，会显示表示解决方案中的不同项目的菜单项。  
  
3.  当您检查其中一个项目时，它将成为启动项目。  
  
4.  当您关闭解决方案，或打开具有只有一个项目的解决方案时，应消失工具栏图标。  
  
## 请参阅  
 [命令、 菜单和工具栏](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Vspackage 如何添加用户界面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)