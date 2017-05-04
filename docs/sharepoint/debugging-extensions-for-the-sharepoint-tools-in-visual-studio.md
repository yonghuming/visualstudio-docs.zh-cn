---
title: "Debugging Extensions for the SharePoint Tools in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint development in Visual Studio, debugging extensions"
ms.assetid: 7cee8ce0-d07b-41f6-8ce1-b18e4be3b50c
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Debugging Extensions for the SharePoint Tools in Visual Studio
  您可以在 Visual Studio 的实验实例或常规实例中调试 SharePoint 工具扩展。  如果需要对扩展的行为进行疑难解答，您可以修改注册表值以显示其他错误信息并配置 Visual Studio 执行 SharePoint 命令的方式。  
  
## 在 Visual Studio 的实验实例中调试扩展  
 为了防止 Visual Studio 开发环境受到未经测试的扩展造成的意外损坏，Visual Studio SDK 提供了一个称为“实验实例”的替代 Visual Studio 实例，您可以使用该实例来安装和测试扩展。  您可以使用 Visual Studio 的常规实例开发新扩展，但在实验实例中调试和运行这些扩展。  有关详细信息，请参阅[实验实例](../extensibility/the-experimental-instance.md)。  
  
 如果使用 VSIX 项目来部署扩展，并且该 VSIX 项目是解决方案中的启动项目，则当您调试解决方案时，Visual Studio 将自动在实验实例中安装和运行该扩展。  启动项目是指在调试包含多个项目的解决方案时启动的项目。  有关使用 VSIX 项目来部署扩展的更多信息，请参见[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  有关启动项目的更多信息，请参见[如何：设置启动项目](http://msdn.microsoft.com/zh-cn/31465836-0911-48db-a5d9-e456b635e970)。  
  
 有关演示如何在 Visual Studio 的实验实例中调试各种类型的扩展的示例，请参见以下演练：  
  
-   [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
-   [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)  
  
-   [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)  
  
-   [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
-   [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)  
  
## 在 Visual Studio 的常规实例中调试扩展  
 如果要在 Visual Studio 的常规实例中调试扩展项目，请首先在常规实例中安装该扩展。  然后，将调试器附加到另一个 Visual Studio 进程。  完成之后，您可以移除扩展，以使其不再在开发计算机上加载。  
  
#### 安装扩展  
  
1.  关闭 Visual Studio 的所有实例。  
  
2.  在扩展项目的版本输出文件夹中，打开 .vsix 文件，可以通过双击它或通过打开其快捷菜单中选择“打开” :  
  
3.  在“Visual Studio Extension Installer”对话框中，选择要将扩展安装到的 Visual Studio 的版本，然后选择“安装”。  
  
     Visual Studio 会将扩展文件安装到 %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0\\Extensions\\*author name*\\*extension name*\\*version*中。  此路径中的最后三个文件夹是通过扩展的 extension.vsixmanifest 文件中的 `Author`、`Name` 和 `Version` 元素来构造的。  
  
4.  在 Visual Studio 安装完扩展之后，选择“关闭”。  
  
#### 调试扩展  
  
1.  利用管理员特权启动 Visual Studio，并打开扩展项目。  以下步骤将这个 Visual Studio 实例称为“第一个实例”。  
  
2.  利用管理员特权启动 Visual Studio 的另一个实例。  以下步骤将这个 Visual Studio 实例称为“第二个实例”。  
  
3.  切换到 Visual Studio 的第一个实例。  
  
4.  在菜单上选择“调试”，“附加到进程”。  
  
5.  在“可用进程”列表中，选择“devenv.exe”。  此项指的是 Visual Studio 的第二个实例；这是要在其中调试项目扩展的实例。  
  
6.  选择“完成”按钮。  
  
     Visual Studio 将以调试模式运行扩展项目。  
  
7.  切换到 Visual Studio 的第二个实例。  
  
8.  创建加载扩展的新 SharePoint 项目。  例如，如果要调试列表定义项目项的扩展，请创建**“列表定义”**项目。  
  
9. 执行测试扩展代码所需的任何步骤。  
  
10. 完成扩展调试后，关闭 Visual Studio 的第二个实例。  
  
#### 移除扩展  
  
1.  在 Visual Studio 菜单栏上，选择 “工具”，“扩展和更新”。  
  
     “扩展和更新”对话框将打开。  
  
2.  在扩展列表中，选择扩展的名称，然后选择“卸载”按钮。  
  
3.  在出现的对话框中，单击**“是”**以确认您要卸载该扩展。  
  
4.  选择 “立即重新启动” 按钮来完成卸载。  
  
## 调试 SharePoint 命令  
 若要调试作为 SharePoint 工具扩展的一部分的 SharePoint 命令，您必须将调试器附加到 vssphost4.exe 进程。  此进程是执行 SharePoint 命令的 64 位宿主进程。  有关 SharePoint 命令和 vssphost4.exe 的更多信息，请参见[Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)。  
  
#### 将调试器附加到 vssphost4.exe 进程  
  
1.  通过按照上述说明执行操作，可以在 Visual Studio 实验实例中或 Visual Studio 常规实例中开始调试扩展。  
  
2.  在正在运行调试器的 Visual Studio 实例中，在菜单上单击“调试” **“附加到进程”**。  
  
3.  在“可用进程”列表中，选择 vssphost.exe。  
  
    > [!NOTE]  
    >  如果列表中没有显示 vssphost.exe，则必须在正运行扩展的 Visual Studio 实例中开始 vssphost4.exe 进程。  通常，可以通过执行使 Visual Studio 连接到开发计算机上的 SharePoint 网站的操作来做到这一点。  例如，在展开位于**“服务器资源管理器”**窗口中的**“SharePoint 连接”**节点下的网站连接节点（此节点显示网站 URL）时，或在将某些 SharePoint 项目项（如**“列表实例”**或**“事件接收器”**项）添加到 SharePoint 项目中时，Visual Studio 会启动 vssphost4.exe。  
  
4.  选择“完成”按钮。  
  
5.  在正在调试的 Visual Studio 实例中，执行在执行命令时所需的步骤。  
  
## 修改注册表值以帮助调试 SharePoint 工具扩展  
 在 Visual Studio 中调试 SharePoint 工具的扩展时，可以修改注册表中的值以帮助对此扩展进行疑难解答。  这些值位于 HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\11.0\\SharePointTools 项下。  默认情况下，这些值不存在。  
  
 若要帮助对 SharePoint 工具的任何扩展进行疑难解答，可以创建并设置 EnableDiagnostics 值。  下表描述了此值。  
  
|值|描述|  
|-------|--------|  
|EnableDiagnostics|REG\_DWORD，指定是否在**“输出”**窗口中显示诊断消息。<br /><br /> 若要显示诊断消息，请将此值设置为 1。  若要停止显示消息，请将此值设置为 0 或删除此值。<br /><br /> 若要将消息从 SharePoint 工具扩展写入到**“输出”**窗口，请使用 SharePoint 项目服务。  有关详细信息，请参阅[Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)。|  
  
 如果扩展中包括某个 SharePoint 命令，则可以创建并设置其他值以帮助对该命令进行疑难解答。  下表描述了这些值。  
  
|值|描述|  
|-------|--------|  
|AttachDebuggerToHostProcess|用于指定是否显示对话框的 REG\_DWORD，利用此对话框可在 vssphost4.exe 启动时将调试器附加到其中。  如果 vssphost.exe 在启动后立即执行要调试的命令，并且在执行该命令前没有足够的时间来手动附加调试器，这将会很有用。  为了显示此对话框，vssphost4.exe 在启动时将调用 <xref:System.Diagnostics.Debugger.Break%2A> 方法。<br /><br /> 若要启用此行为，请将该值设置为 1。  若要禁用此行为，请将该值设置为 0 或删除该值。<br /><br /> 若将该值设置为 1，则可能还需要增大 HostProcessStartupTimeout 值，以使您在 Visual Studio 期待 vssphost4.exe 发出已成功启动信号前有足够的时间附加调试器。|  
|ChannelOperationTimeout|REG\_DWORD，指定 Visual Studio 等待 SharePoint 命令执行的时间（以秒为单位）。  如果命令未及时执行，则会引发 <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException>。<br /><br /> 默认值为 120 秒。|  
|HostProcessStartupTimeout|REG\_DWORD，指定 Visual Studio 等待 vssphost4.exe 发出成功启动信号的时间（以秒为单位）。  如果 vssphost4.exe 未及时发出成功启动信号，则会引发 <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException>。<br /><br /> 默认值为 60 秒。|  
|MaxReceivedMessageSize|REG\_DWORD，指定在 Visual Studio 和 vssphost4.exe 之间传递的 WCF 消息的最大允许大小（以字节为单位）。<br /><br /> 默认值为 1,048,576 字节 \(1 MB\)。|  
|MaxStringContentLength|REG\_DWORD，指定在 Visual Studio 和 vssphost4.exe 之间传递的字符串的最大允许大小（以字节为单位）。<br /><br /> 默认值为 1,048,576 字节 \(1 MB\)。|  
  
## 请参阅  
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  