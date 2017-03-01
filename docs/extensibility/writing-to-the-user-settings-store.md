---
title: "写入用户设置存储 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
caps.latest.revision: 3
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 35ca397d57906a6316543325a08b118613fc2035
ms.lasthandoff: 02/22/2017

---
# <a name="writing-to-the-user-settings-store"></a>写入用户设置存储
用户设置是可写中一样**工具 / 选项**对话框、 属性窗口和某些其他对话框。 Visual Studio 扩展可能会使用它们来存储少量数据。 本演练演示如何将记事本到 Visual Studio 添加为外部工具，通过读取和写入用户设置存储。  
  
### <a name="backing-up-your-user-settings"></a>备份你的用户设置  
  
1.  您必须能重置外部工具设置，以便您可以调试并重复此过程。 若要执行此操作，必须保存原始设置，以便您可以根据需要恢复它们。  
  
2.  打开 Regedit.exe。  
  
3.  导航到 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External 工具\\。  
  
    > [!NOTE]
    >  请确保您要查找键，其中包含 \14.0Exp\ 和不 \14.0 处\\。 当您运行 Visual Studio 的实验实例时，您的用户设置将在注册表配置单元"14.0Exp"。  
  
4.  右键单击 \External Tools\ 子项，然后单击**导出**。 请确保**所选分支**处于选中状态。  
  
5.  保存生成的外部 Tools.reg 文件。  
  
6.  更高版本，当您想要重置外部工具设置，选择 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External 工具注册表项，然后单击**删除**上下文菜单上。  
  
7.  当**确认项删除**出现对话框，请单击**是**。  
  
8.  右键单击以前保存的外部 Tools.reg 文件，请单击**使用打开**，然后单击**注册表编辑器**。  
  
## <a name="writing-to-the-user-settings-store"></a>写入用户设置存储  
  
1.  创建一个名为 UserSettingsStoreExtension 的 VSIX 项目，然后添加名为 UserSettingsStoreCommand 的自定义命令。 有关如何创建自定义命令的详细信息，请参阅[使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  在 UserSettingsStoreCommand.cs，添加以下 using 语句︰  
  
    ```c#  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    ```  
  
3.  在 MenuItemCallback，删除方法的主体，并获取的用户设置存储，，如下所示︰  
  
    ```c#  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
    }  
    ```  
  
4.  现在，了解是否记事本已设置为外部工具。 您需要循环访问所有外部工具，以确定是否 ToolCmd 设置为"记事本"，如下所示︰  
  
    ```c#  
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
  
5.  如果未作为外部工具设置记事本，请按以下方式进行设置︰  
  
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
  
6.  测试代码。 请记住，它添加了记事本作为外部工具，所以您必须回滚注册表然后再运行第二次。  
  
7.  生成代码后，开始调试。  
  
8.  在**工具**菜单上，单击**调用 UserSettingsStoreCommand**。 这将添加到记事本**工具**菜单。  
  
9. 现在，您应看到记事本工具 / 选项菜单，并单击**记事本**应打开一个记事本实例。
