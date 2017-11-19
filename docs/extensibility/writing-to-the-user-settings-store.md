---
title: "写入用户设置存储 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
caps.latest.revision: "3"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7a824f0934a260a4e825a5618e5d3b91a500be7b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="writing-to-the-user-settings-store"></a>写入到用户设置存储区
用户设置均等中的可写设置**工具 / 选项**对话框、 属性窗口和某些其他对话框。 Visual Studio 扩展可以使用这些存储少量数据。 本演练演示如何将记事本到 Visual Studio 添加为外部工具，通过读取和写入用户设置存储。  
  
### <a name="backing-up-your-user-settings"></a>备份你的用户设置  
  
1.  你必须能够重置的外部工具设置，以便您可以调试并重复此过程。 若要执行此操作，必须保存原始设置，以便你可以根据需要还原这些。  
  
2.  打开 Regedit.exe。  
  
3.  导航到 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External 工具\\。  
  
    > [!NOTE]
    >  请确保你要在包含 \14.0Exp\ 且不 \14.0 密钥\\。 当你运行 Visual Studio 的实验实例时，你的用户设置是在注册表配置单元"14.0Exp"。  
  
4.  右键单击该 \External Tools\ 子项，并依次**导出**。 请确保**所选分支**选择。  
  
5.  保存生成的外部 Tools.reg 文件。  
  
6.  更高版本，当你想要重置的外部工具设置，选择 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External Tools\ 注册表项，然后单击**删除**上下文菜单上。  
  
7.  当**确认键删除**显示对话框，请单击**是**。  
  
8.  右键单击你前面保存的外部 Tools.reg 文件，单击**使用打开**，然后单击**注册表编辑器**。  
  
## <a name="writing-to-the-user-settings-store"></a>写入到用户设置存储区  
  
1.  创建一个名为 UserSettingsStoreExtension 的 VSIX 项目，然后添加名为 UserSettingsStoreCommand 自定义命令。 有关如何创建自定义命令的详细信息，请参阅[使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  在 UserSettingsStoreCommand.cs，添加以下 using 语句：  
  
    ```csharp  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    ```  
  
3.  在 MenuItemCallback，删除方法的正文，并使的用户非常设置存储，，如下所示：  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
    }  
    ```  
  
4.  现在，了解是否记事本已设置为外部工具。 你需要循环访问所有外部工具来确定是否 ToolCmd 设置为"记事本"，如下所示：  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
  
        // Find out whether Notepad is already an External Tool.  
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");  
        bool hasNotepad = false;  
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;  
        for (int i = 0; i < toolCount; i++)  
        {  
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)  
            {  
                hasNotepad = true;  
                break;  
            }  
        }  
    }  
  
    ```  
  
5.  如果记事本未被设为外部工具，请按以下方式进行设置：  
  
    ```vb  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
  
        // Find out whether Notepad is already installed.  
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");  
        bool hasNotepad = false;  
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;  
        for (int i = 0; i < toolCount; i++)  
        {  
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)  
            {  
                hasNotepad = true;  
                break;  
            }  
        }  
  
        string message = (hasNotepad) ? "Notepad already installed" : "Installing Notepad";  
         if (!hasNotepad)  
        {  
            userSettingsStore.SetString("External Tools", "ToolTitle" + toolCount, "&Notepad");  
            userSettingsStore.SetString("External Tools", "ToolCmd" + toolCount, "C:\\Windows\\notepad.exe");  
            userSettingsStore.SetString("External Tools", "ToolArg" + toolCount, "");  
            userSettingsStore.SetString("External Tools", "ToolDir" + toolCount, "$(ProjectDir)");  
            userSettingsStore.SetString("External Tools", "ToolSourceKey" + toolCount, "");  
            userSettingsStore.SetUInt32("External Tools", "ToolOpt" + toolCount, 0x00000011);  
  
            userSettingsStore.SetInt32("External Tools", "ToolNumKeys", toolCount + 1);  
        }  
    }  
    ```  
  
6.  测试代码。 请记住，添加记事本作为外部工具，所以你必须回滚注册表之前第二次运行它。  
  
7.  生成代码并开始调试。  
  
8.  上**工具**菜单上，单击**调用 UserSettingsStoreCommand**。 这将添加到记事本**工具**菜单。  
  
9. 现在，你应看到记事本工具 / 选项菜单，然后单击**记事本**应打开记事本的实例。