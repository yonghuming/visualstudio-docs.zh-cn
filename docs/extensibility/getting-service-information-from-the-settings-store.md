---
title: "从设置存储中获取服务信息 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# 从设置存储中获取服务信息
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

若要查看所有可用的服务或确定是否安装了特定服务，您可以使用设置存储。 您必须知道服务类的类型。  
  
### 若要列出可用服务  
  
1.  创建一个名为 FindServicesExtension 的 VSIX 项目，然后添加名为 FindServicesCommand 的自定义命令。 有关如何创建自定义命令的详细信息，请参阅 [使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  在 FindServicesCommand.cs，添加以下 using 语句:  
  
    ```vb  
    using System.Collections.Generic; using Microsoft.VisualStudio.Settings; using Microsoft.VisualStudio.Shell.Settings; using System.Windows.Forms;  
    ```  
  
3.  获取配置设置存储区，然后查找名为 Services 子集合。 此集合包含所有可用的服务。 在 MenuItemCommand 方法中，移除现有代码并将其替换为以下:  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e) { SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration); string message = "Available services:\n"; IEnumerable<string> collection = configurationSettingsStore.GetSubCollectionNames("Services"); int n = 0; foreach (string service in collection) { message += configurationSettingsStore.GetString("Services\\" + service, "Name", "Unknown") + "\n"; } MessageBox.Show(message); }  
    ```  
  
4.  生成项目并启动调试。 将显示的实验实例。  
  
5.  在实验实例中，在 **工具** 菜单上，单击 **调用 FindServicesCommand**。  
  
     您应看到一个消息框，其中列出所有服务。  
  
     若要验证这些设置，可以使用注册表编辑器。  
  
## 查找特定的服务  
 您还可以使用 <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> 方法，以确定是否安装了特定服务。 您必须知道服务类的类型。  
  
1.  在前面的过程中创建的项目的 MenuItemCallback，搜索的配置设置存储 `Services` 集合中具有子集合名为该服务的 guid。 在这种情况下，我们将寻找帮助服务。  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e) { SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration); string helpServiceGUID = typeof(SVsHelpService).GUID.ToString("B").ToUpper(); bool hasHelpService = configurationSettingsStore.CollectionExists("Services\\" + helpServiceGUID); string message = "Help Service Available: " + hasHelpService; MessageBox.Show(message); }  
    ```  
  
2.  生成项目并启动调试。  
  
3.  在实验实例中，在 **工具** 菜单上，单击 **调用 FindServicesCommand**。  
  
     您应该看到消息，消息文本 **帮助服务可用:**  跟 **True** 或 **False**。 若要验证此设置，可以使用注册表编辑器，如前面的步骤中所示。