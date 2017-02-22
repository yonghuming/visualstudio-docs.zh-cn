---
title: "使用设置存储 | Microsoft Docs"
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
  - "设置存储使用"
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
caps.latest.revision: 28
caps.handback.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
---
# 使用设置存储
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

有两种类型的设置存储:  
  
-   配置设置是只读的 Visual Studio 和 VSPackage 的设置。 Visual Studio 将所有已知的.pkgdef 文件中设置合并到此存储区。  
  
-   用户设置，包括可写设置，例如那些在页上显示 **选项** 对话框、 属性页和某些其他对话框。 Visual Studio 扩展可能会使用这些本地存储少量数据。  
  
 本演练演示如何从配置设置存储区中读取数据。 请参阅 [写入用户设置存储](../extensibility/writing-to-the-user-settings-store.md) 有关如何将写入到用户设置存储的说明。  
  
## 创建示例项目  
 本部分演示如何创建一个简单的扩展项目演示的菜单命令。  
  
1.  每个 Visual Studio 的扩展从一个 VSIX 部署项目，它将包含的扩展资产开始。 创建 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX 项目名为 `SettingsStoreExtension`。 您可以找到中的 VSIX 项目模板 **新项目** 下的对话框 **Visual C\# \/ 可扩展性**。  
  
2.  现在，添加一个名为的自定义命令项模板 **SettingsStoreCommand**。 在 **添加新项** 对话框中，转到 **Visual C\# \/ 可扩展性** ，然后选择 **自定义命令**。 在 **名称** 在窗口的底部字段中，命令文件名称更改为 **SettingsStoreCommand.cs**。 有关如何创建自定义命令的详细信息，请参阅 [使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
## 使用配置设置存储  
 本部分说明如何检测和显示配置设置。  
  
1.  在 SettingsStorageCommand.cs 文件中，添加以下 using 语句:  
  
    ```  
    using System.Collections.Generic; using Microsoft.VisualStudio.Settings; using Microsoft.VisualStudio.Shell.Settings; using System.Windows.Forms;  
    ```  
  
2.  在 `MenuItemCallback`, ，该方法的正文中删除并添加这些行获得配置设置存储:  
  
    ```  
    SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> 高于托管帮助器类 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> 服务。  
  
3.  现在，了解是否安装了 Windows Phone 工具。 该代码应如下所示:  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e) { SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration); bool arePhoneToolsInstalled = configurationSettingsStore.CollectionExists(@"InstalledProducts\Microsoft Windows Phone Developer Tools"); string message = "Microsoft Windows Phone Developer Tools: " + arePhoneToolsInstalled; MessageBox.Show(message); }  
    ```  
  
4.  测试代码。 生成项目并启动调试。  
  
5.  在实验实例中，在 **工具** 菜单上，单击 **调用 SettingsStoreCommand**。  
  
     您应该看到消息框中，显示 **Microsoft Windows Phone 开发人员工具:**  跟 **True** 或 **False**。  
  
 Visual Studio 会保留在系统注册表中的设置存储。  
  
#### 若要使用注册表编辑器来验证配置设置  
  
1.  打开 Regedit.exe。  
  
2.  导航到 HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\14.0Exp\_Config\\InstalledProducts\\。  
  
    > [!NOTE]
    >  请确保您要查找键，其中包含 \\14.0Exp\_Config\\ 和不 \\14.0\_Config\\ 处。 当运行 Visual Studio 的实验实例时，配置设置是在注册表配置单元"14.0Exp\_Config"。  
  
3.  展开 \\Installed Products\\ 节点。 如果前面的步骤中的消息是 **Microsoft Windows Phone 开发人员安装工具: True**, ，则 \\Installed Products\\ 应包含 Microsoft Windows Phone 开发人员工具节点。 如果消息已 **Microsoft Windows Phone 开发人员安装工具: False**, ，则 \\Installed Products\\ 不应包含 Microsoft Windows Phone 开发人员工具节点。