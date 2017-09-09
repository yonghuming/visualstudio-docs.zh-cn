---
title: Dynamically Adding Menu Items | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
caps.latest.revision: 37
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 0788c7cc5d659c1f0bbf1d4b0043b0c2f7181345
ms.contentlocale: zh-cn
ms.lasthandoff: 08/28/2017

---
# <a name="dynamically-adding-menu-items"></a>Dynamically Adding Menu Items
You can add menu items at run time by specifying the `DynamicItemStart` command flag on a placeholder button definition in the Visual Studio command-table (.vsct) file, then defining (in code) the number of menu items to display and handling the command(s). When the VSPackage is loaded, the placeholder is replaced with the dynamic menu items.  
  
 Visual Studio uses dynamic lists in the **Most Recently Used** (MRU) list, which displays the names of documents that have been opened recently, and the **Windows** list, which displays the names of windows that are currently open.   The `DynamicItemStart` flag on a command definition specifies that the command is a placeholder until the VSPackage is opened. When the VSPackage is opened, the placeholder is replaced with 0 or more commands that are created at run time and added to the dynamic list. You may not be able to see the position on the menu where the dynamic list appears until the VSPackage is opened.  To populate the dynamic list, Visual Studio asks the VSPackage to look for a command with an ID whose first characters are the same as the ID of the placeholder. When Visual Studio finds a matching command, it adds the name of the command  to the dynamic list. Then it increments the ID and looks for another matching command to add to the dynamic list until there are no more dynamic commands.  
  
 This walkthrough shows how to set the startup project in a Visual Studio solution with a command on the **Solution Explorer** toolbar. It uses a menu controller that has a dynamic dropdown list of the projects in the active solution. To keep this command from appearing when no solution is open or when the open solution has only one project, the VSPackage is loaded only when a solution has multiple projects.  
  
 For more information about .vsct files, see [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="creating-an-extension-with-a-menu-command"></a>Creating an Extension with a Menu Command  
  
1.  Create a VSIX project named `DynamicMenuItems`.  
  
2.  When the project opens, add a custom command item template and name it **DynamicMenu**. For more information, see [Creating an Extension with a Menu Command](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="setting-up-the-elements-in-the-vsct-file"></a>Setting up the elements in the .vsct file  
 To create a menu controller with dynamic menu items on a toolbar, you specify the following elements:  
  
-   Two command groups, one that contains the menu controller and another that contains the menu items in the dropdown  
  
-   One menu element of type `MenuController`  
  
-   Two buttons, one that acts as the placeholder for the menu items and another that supplies the icon and the tooltip on the toolbar.  
  
1.  In DynamicMenuPackage.vsct, define the command IDs. Go to the Symbols section and replace the IDSymbol elements in the **guidDynamicMenuPackageCmdSet** GuidSymbol block. You need to define IDSymbol elements for the two groups, the menu controller, the placeholder command, and the anchor command.  
  
    ```csharp  
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
  
2.  In the Groups section, delete the existing groups and add the two groups you just defined:  
  
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
  
     Add the MenuController. Set the DynamicVisibility command flag, since it is not always visible. The ButtonText is not displayed.  
  
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
  
3.  Add two buttons, one as a placeholder for the dynamic menu items and one as an anchor for the MenuController.  
  
     The parent of the placeholder button is the **MyMenuControllerGroup**. Add the DynamicItemStart, DynamicVisibility, and TextChanges command flags to the placeholder button. The ButtonText is not displayed.  
  
     The anchor button holds the icon and the tooltip text. The parent of the anchor button is also the **MyMenuControllerGroup**. You add the NoShowOnMenuController command flag to make sure the button doesn't actually appear in the menu controller dropdown, and the FixMenuController command flag to make it the permanent anchor.  
  
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
  
4.  Add an icon to the project (in the Resources folder), and then add the reference to it in the .vsct file. In this walkthrough, we use the Arrows icon that's included in the project template.  
  
5.  Add a VisibilityConstraints section outside the Commands section just before the Symbols section. (You may get a warning if you add it after Symbols.) This section makes sure that the menu controller appears only when a solution with multiple projects is loaded.  
  
    ```  
    <VisibilityConstraints>  
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->  
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>  
    </VisibilityConstraints>  
    ```  
  
## <a name="implementing-the-dynamic-menu-command"></a>Implementing the dynamic menu command  
 You create a dynamic menu command class that inherits from <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>. In this implementation, the constructor specifies a predicate to be used for matching commands. You must override the <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> method to use this predicate to set the <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> property, which identifies the command to be invoked.  
  
1.  Create a new C# class file named DynamicItemMenuCommand.cs, and add a class named **DynamicItemMenuCommand** that inherits from <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>:  
  
    ```csharp  
    class DynamicItemMenuCommand : OleMenuCommand  
    {  
  
    }  
  
    ```  
  
2.  Add the following using statements:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Add a private field to store the match predicate:  
  
    ```csharp  
    private Predicate<int> matches;  
  
    ```  
  
4.  Add a constructor that inherits from the <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> constructor and specifies a command handler and a <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> handler. Add a predicate for matching the command:  
  
    ```csharp  
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
  
5.  Override the <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> method so that it calls the matches predicate and sets the <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> property:  
  
    ```csharp  
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
  
## <a name="adding-the-command"></a>Adding the command  
 The DynamicMenu constructor is where you set up menu commands, including dynamic menus and menu items.  
  
1.  In DynamicMenuPackageGuids.cs, add the GUID of the command set and the command ID:  
  
    ```csharp  
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    public const uint cmdidMyCommand = 0x104;  
    ```  
  
2.  In the DynamicMenu.cs file, add the following using statements:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using System.ComponentModel.Design;  
    ```  
  
3.  In the DynamicMenu class, add a private field **dte2**.  
  
    ```csharp  
    private DTE2 dte2;  
    ```  
  
4.  Add a private rootItemId field:  
  
    ```csharp  
    private int rootItemId = 0;  
    ```  
  
5.  In the DynamicMenu constructor, add the menu command. In the next section we'll define the command handler, the `BeforeQueryStatus` event handler, and the match predicate.  
  
    ```csharp  
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
  
## <a name="implementing-the-handlers"></a>Implementing the handlers  
 To implement dynamic menu items on a menu controller, you must handle the command when a dynamic item is clicked. You must also implement the logic that sets the state of the menu item. Add the handlers to the DynamicMenu class.  
  
1.  To implement the **Set Startup Project** command, add the **OnInvokedDynamicItem** event handler. It looks for the project whose name is the same as the text of the command that has been invoked, and sets it as the startup project by setting its absolute path in the <xref:EnvDTE.SolutionBuild.StartupProjects%2A> property.  
  
    ```csharp  
    private void OnInvokedDynamicItem(object sender, EventArgs args)  
    {  
        DynamicItemMenuCommand invokedCommand = (DynamicItemMenuCommand)sender;  
        // If the command is already checked, we don't need to do anything  
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
  
2.  Add the `OnBeforeQueryStatusDynamicItem` event handler. This is the handler called before a `QueryStatus` event. It determines whether the menu item is a "real" item, that is, not the placeholder item, and whether the item is already checked (meaning that the project is already set as the startup project).  
  
    ```csharp  
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
  
## <a name="implementing-the-command-id-match-predicate"></a>Implementing the command ID match predicate  
  
1.  Now implement the match predicate. We need to determine two things: first, whether the command ID is valid (it is greater than or equal to the declared command ID), and second, whether it specifies a possible project (it is less than the number of projects in the solution).  
  
    ```csharp  
    private bool IsValidDynamicItem(int commandId)  
    {  
        // The match is valid if the command ID is >= the id of our root dynamic start item   
        // and the command ID minus the ID of our root dynamic start item  
        // is less than or equal to the number of projects in the solution.  
        return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);  
    }  
    ```  
  
## <a name="setting-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>Setting the VSPackage to load only when a solution has multiple projects  
 Because the **Set Startup Project** command doesn't make sense unless the active solution has more than one project, you can set your VSPackage to auto-load only in that case. You use <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> together with the UI context <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>. In the DynamicMenuPackage.cs file add the following attributes to the DynamicMenuPackage class:  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
[ProvideMenuResource("Menus.ctmenu", 1)]  
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]  
[Guid(DynamicMenuPackageGuids.PackageGuidString)]  
public sealed class DynamicMenuItemsPackage : Package  
{}  
```  
  
## <a name="testing-the-set-startup-project-command"></a>Testing the Set Startup Project command  
 Now you can test your code.  
  
1.  Build the project and start debugging. The experimental instance should appear.  
  
2.  In the experimental instance, open a solution that has more than one project.  
  
     You should see the arrow icon on the **Solution Explorer** toolbar. When you expand it, menu items that represent the different projects in the solution should appear.  
  
3.  When you check one of the projects, it becomes the startup project.  
  
4.  When you close the solution, or open a solution that has only one project, the toolbar icon should disappear.  
  
## <a name="see-also"></a>See Also  
 [Commands, Menus, and Toolbars](../extensibility/internals/commands-menus-and-toolbars.md)   
 [How VSPackages Add User Interface Elements](../extensibility/internals/how-vspackages-add-user-interface-elements.md)