---
title: "使用设置存储 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f1d62e3ccc47a2b74629cd1468b023c787a1289e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="using-the-settings-store"></a>使用设置存储
有两种类型的设置存储：  
  
-   配置设置是只读的 Visual Studio 和 VSPackage 的设置。 Visual Studio 将合并到此存储的所有已知的.pkgdef 文件中的设置。  
  
-   用户设置，如在页面上显示的可写设置**选项**对话框、 属性页和某些其他对话框。 Visual Studio 扩展可能会使用它们的本地存储的少量数据。  
  
 本演练演示如何从配置设置存储读取数据。 请参阅[写入用户设置存储](../extensibility/writing-to-the-user-settings-store.md)有关如何将写入到的用户设置存储中的说明。  
  
## <a name="creating-the-example-project"></a>创建示例项目  
 本部分演示如何创建一个简单的扩展名项目演示一个菜单命令。  
  
1.  每个 Visual Studio 扩展开头 VSIX 部署项目将包含扩展资产。 创建[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]名为 VSIX 项目`SettingsStoreExtension`。 你可以查找中的 VSIX 项目模板**新项目**下的对话框**Visual C# / 可扩展性**。  
  
2.  现在，添加名为的自定义命令项模板**SettingsStoreCommand**。 在**添加新项**对话框中，转到**Visual C# / 可扩展性**和选择**自定义命令**。 在**名称**在窗口底部字段中，命令文件名称更改为**SettingsStoreCommand.cs**。 有关如何创建自定义命令的详细信息，请参阅[使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
## <a name="using-the-configuration-settings-store"></a>使用配置设置存储区  
 本部分演示如何检测并显示配置设置。  
  
1.  在 SettingsStorageCommand.cs 文件中，添加以下 using 语句：  
  
    ```  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
2.  在`MenuItemCallback`方法的正文中移除并添加以下行获取配置设置存储区：  
  
    ```  
    SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
    SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager>高于托管帮助器类<xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager>服务。  
  
3.  现在，了解是否安装了 Windows Phone 工具。 代码应如下所示：  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
        bool arePhoneToolsInstalled = configurationSettingsStore.CollectionExists(@"InstalledProducts\Microsoft Windows Phone Developer Tools");  
        string message = "Microsoft Windows Phone Developer Tools: " + arePhoneToolsInstalled;  
        MessageBox.Show(message);  
    }  
    ```  
  
4.  测试代码。 生成项目并启动调试。  
  
5.  在实验实例中，在**工具**菜单上，单击**调用 SettingsStoreCommand**。  
  
     你应该会看到消息框，显示**Microsoft Windows Phone 开发人员工具：**跟**True**或**False**。  
  
 Visual Studio 将在系统注册表中设置存储。  
  
#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>若要使用注册表编辑器来验证配置设置  
  
1.  打开 Regedit.exe。  
  
2.  导航到 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts\\。  
  
    > [!NOTE]
    >  请确保你要在包含 \14.0Exp_Config\ 且不 \14.0_Config 密钥\\。 当你运行 Visual Studio 的实验实例时，配置设置位于注册表配置单元"14.0Exp_Config"。  
  
3.  展开 \Installed Products\ 节点。 如果前面的步骤中的消息是**Microsoft Windows Phone 开发人员工具安装： True**，然后 \Installed Products\ 应包含 Microsoft Windows Phone 开发人员工具节点。 如果消息已**Microsoft Windows Phone 开发人员工具安装： False**，然后 \Installed Products\ 不应包含 Microsoft Windows Phone 开发人员工具节点。