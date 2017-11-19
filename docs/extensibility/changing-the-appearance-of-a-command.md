---
title: "更改命令的外观 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7ffb8aed183b50958c8835b2a1e79b808ac20174
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="changing-the-appearance-of-a-command"></a>更改外观的命令
通过更改命令的外观，你可以对你的用户提供反馈。 例如，您可能希望命令不可用时查找不同。 你可以使命令可用或不可用，隐藏或显示它们，或选中或取消它们选中的菜单上。  
  
 若要更改命令的外观，请执行以下操作之一：  
  
-   在命令文件中的表的命令定义中指定相应的标志。  
  
-   使用<xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>服务。  
  
-   实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>接口，并修改原始命令对象。  
  
 以下步骤显示如何查找和使用托管包框架 (MPF) 更新命令的外观。  
  
### <a name="to-change-the-appearance-of-a-menu-command"></a>若要更改菜单命令的外观  
  
1.  按照中的说明[更改菜单命令的文本](../extensibility/changing-the-text-of-a-menu-command.md)要创建菜单项名为`New Text`。  
  
2.  在 ChangeMenuText.cs 文件中，添加以下 using 语句：  
  
    ```csharp  
    using System.Security.Permissions;  
    ```  
  
3.  在 ChangeMenuTextPackageGuids.cs 文件中，添加以下行：  
  
    ```csharp  
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    ```  
  
4.  在 ChangeMenuText.cs 文件中，将替换为以下 ShowMessageBox 方法中的代码：  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var command = sender as OleMenuCommand;  
        if (command.Text == "New Text")  
            ChangeMyCommand(command.CommandID.ID, false);}  
    }  
    ```  
  
5.  获取你想要从更新命令<xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>对象，然后在命令对象上设置适当的属性。 例如，以下方法使指定的命令从 VSPackage 命令设置可用或不可用。 下面的代码使名为菜单项`New Text`后单击它不可用。  
  
    ```csharp  
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
  
6.  生成项目并启动调试。 应显示 Visual Studio 的实验实例。  
  
7.  上**工具**菜单上，单击**调用 ChangeMenuText**命令。 此时该命令名是**调用 ChangeMenuText**，因此命令处理程序不会调用 ChangeMyCommand()。  
  
8.  上**工具**菜单现在应看到**新文本**。 单击**新文本**。 该命令应现在灰显。  
  
## <a name="see-also"></a>另请参阅  
 [命令、 菜单和工具栏](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Vspackage 如何添加用户界面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [扩展菜单和命令](../extensibility/extending-menus-and-commands.md)   
 [Visual Studio 命令表格 (.Vsct) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)