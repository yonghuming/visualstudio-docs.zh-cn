---
title: "更改命令的外观 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "更改外观的命令"
  - "菜单命令、 更改外观"
  - "菜单、 更改命令外观"
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# 更改命令的外观
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

通过更改命令的外观，可以向用户提供反馈。 例如，您可能希望命令不可用时看起来不同。 您可以使命令可用或不可用、 隐藏或显示它们，或检查或取消选中那些在菜单上。  
  
 若要更改命令的外观，请执行以下操作之一︰  
  
-   在命令文件中的表的命令定义中指定适当的标志。  
  
-   使用 <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> 服务。  
  
-   实现 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 接口，并修改原始命令对象。  
  
 下列步骤显示如何查找和使用管理包框架 \(MPF\) 更新命令的外观。  
  
### 若要更改菜单命令的外观  
  
1.  按照中的说明 [更改菜单命令的文本](../extensibility/changing-the-text-of-a-menu-command.md) 创建菜单项名为 `New Text`。  
  
2.  在 ChangeMenuText.cs 文件中，添加以下 using 语句︰  
  
    ```c#  
    using System.Security.Permissions;  
    ```  
  
3.  在 ChangeMenuTextPackageGuids.cs 文件中，添加以下行︰  
  
    ```c#  
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    ```  
  
4.  在 ChangeMenuText.cs 文件中，替换为以下替换 ShowMessageBox 方法中的代码︰  
  
    ```c#  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var command = sender as OleMenuCommand;  
        if (command.Text == "New Text")  
            ChangeMyCommand(command.CommandID.ID, false);}  
    }  
    ```  
  
5.  获取你想要从更新的命令 <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> 对象，然后在 command 对象上设置适当的属性。 例如，下面的方法将指定的命令从 VSPackage 命令设置可用或不可用。 下面的代码使名为菜单项 `New Text` 后单击它不可用。  
  
    ```c#  
    public bool ChangeMyCommand(int cmdID, bool enableCmd)  
    {  
        bool cmdUpdated = false;  
        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService))  
            as OleMenuCommandService;  
        var newCmdID = new CommandID(new Guid(ChangeMenuTextPackageGuids.guidChangeMenuTextPackageCmdSet), cmdID);  
        MenuCommand mc = mcs.FindCommand(newCmdID);  
        if (mc != null)  
        {  
            mc.Enabled = enableCmd;  
            cmdUpdated = true;  
        }  
        return cmdUpdated;    }  
    }  
    ```  
  
6.  生成项目并启动调试。 Visual Studio 的实验实例应显示。  
  
7.  在 **工具** 菜单上，单击 **调用 ChangeMenuText** 命令。 此时该命令名是 **调用 ChangeMenuText**, ，因此命令处理程序不会调用 ChangeMyCommand\(\)。  
  
8.  在 **工具** 菜单现在应该看到 **新文本**。 单击 **新文本**。 现在，该命令应灰显。  
  
## 请参阅  
 [命令、 菜单和工具栏](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Vspackage 如何添加用户界面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [扩展的菜单和命令](../extensibility/extending-menus-and-commands.md)   
 [Visual Studio 命令表 \(。Vsct\) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)