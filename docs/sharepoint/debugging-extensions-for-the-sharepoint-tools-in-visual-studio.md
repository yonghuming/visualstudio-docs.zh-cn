---
title: "调试 Visual Studio 中的 SharePoint 工具扩展 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, debugging extensions
ms.assetid: 7cee8ce0-d07b-41f6-8ce1-b18e4be3b50c
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 98bb43322d4a222d63bafac22d78e433a3000530
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-extensions-for-the-sharepoint-tools-in-visual-studio"></a>在 Visual Studio 中调试 SharePoint 工具扩展
  你可以调试在实验实例或 Visual Studio 的正则实例中的 SharePoint 工具扩展。 如果您需要解决的扩展的行为，你还可以修改注册表值以显示其他错误信息并配置 Visual Studio 执行 SharePoint 命令的方式。  
  
## <a name="debugging-extensions-in-the-experimental-instance-of-visual-studio"></a>调试 Visual Studio 的实验实例中的扩展  
 若要通过未经测试的扩展保护从意外损坏你 Visual Studio 开发环境，Visual Studio SDK 提供一个备用的 Visual Studio 实例，称为*实验实例*，可以使用若要安装和测试扩展。 通过使用 Visual Studio 中，正则实例开发新的扩展，但调试并在实验实例中运行。 有关详细信息，请参阅[实验实例](/visualstudio/extensibility/the-experimental-instance)。  
  
 如果使用 VSIX 项目来部署你的扩展，并将 VSIX 项目中你的解决方案的启动项目，Visual Studio 将自动安装和调试你的解决方案时，在实验实例中运行扩展。 启动项目是启动时调试包含多个项目的解决方案的项目。 有关使用 VSIX 项目来部署你的扩展的详细信息，请参阅[部署 Visual Studio 中的 SharePoint 工具扩展](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  

 有关演示如何调试不同类型的 Visual Studio 的实验实例中的扩展的示例，请参阅下面的演练：  
  
-   [演练：扩展 SharePoint 项目项类型](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
-   [演练：使用项模板创建自定义操作项目项（第 1 部分）](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)  
  
-   [演练：为 SharePoint 项目创建自定义部署步骤](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)  
  
-   [演练：扩展服务器资源管理器以显示 Web 部件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
-   [演练：在服务器资源管理器扩展中调入 SharePoint 客户端对象模型](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)  
  
## <a name="debugging-extensions-in-the-regular-instance-of-visual-studio"></a>调试 Visual Studio 的正则实例中的扩展  
 如果你想要调试你的 Visual Studio 常规实例中的扩展项目，首先常规实例中安装扩展。 然后，将调试器附加到第二个 Visual Studio 进程。 完成后，你可以删除该扩展，使它不再在开发计算机上加载。  
  
#### <a name="to-install-the-extension"></a>安装扩展  
  
1.  关闭 Visual Studio 的所有实例。  
  
2.  在扩展项目的生成输出文件夹，打开.vsix 文件通过双击它或通过打开其快捷菜单，然后选择**打开**:  
  
3.  在**Visual Studio Extension Installer**对话框框中，选择你想要安装的扩展，然后选择的 Visual Studio 的版本**安装**按钮。  
  
     Visual Studio 将扩展文件安装到 %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions\\*作者姓名*\\*扩展名*\\*版本*。 在此路径的最后三个文件夹都从构造`Author`， `Name`，和`Version`扩展 extension.vsixmanifest 文件中的元素。  
  
4.  Visual Studio 安装扩展后，请选择**关闭**按钮。  
  
#### <a name="to-debug-the-extension"></a>若要调试扩展  
  
1.  使用管理员权限启动 Visual Studio 并打开扩展项目。 以下步骤，请参阅与此实例作为 Visual Studio*首先实例*。  
  
2.  使用管理员权限启动 Visual Studio 的另一个实例。 以下步骤，请参阅与此实例作为 Visual Studio*第二个实例*。  
  
3.  切换到 Visual Studio 的第一个实例。  
  
4.  在菜单栏上，选择**调试**，**附加到进程**。  
  
5.  在**可用进程**列表中，选择 devenv.exe。 此项是指 Visual Studio; 第二个实例这是你想要调试你的项目扩展中的实例。  
  
6.  选择**附加**按钮。  
  
     Visual Studio 在调试模式下运行扩展项目。  
  
7.  切换到 Visual Studio 的第二个实例。  
  
8.  创建一个新的 SharePoint 项目加载你的扩展。 例如，如果你正在调试的列表定义项目项扩展，则创建**列表定义**项目。  
  
9. 执行所需测试扩展代码的任何步骤。  
  
10. 当完成调试扩展后，关闭 Visual Studio 的第二个实例。  
  
#### <a name="to-remove-the-extension"></a>若要删除扩展  
  
1.  在 Visual Studio 中，在菜单栏上，选择**工具**，**扩展和更新**。  
  
     此时，“扩展和更新”对话框打开。  
  
2.  在扩展的列表中，选择扩展的名称，然后选择**卸载**按钮。  
  
3.  在显示的对话框中，选择**是**按钮，以确认你想要卸载扩展。  
  
4.  选择**立即重新启动**按钮以完成卸载。  
  
## <a name="debugging-sharepoint-commands"></a>调试 SharePoint 命令  
 如果你想要调试的是 SharePoint 工具扩展的一部分的 SharePoint 命令，必须将调试器附加到 vssphost4.exe 进程。 这是执行 SharePoint 命令的 64 位主机进程。 有关 SharePoint 命令和 vssphost4.exe 的详细信息，请参阅[调入 SharePoint 对象模型](../sharepoint/calling-into-the-sharepoint-object-models.md)。  
  
#### <a name="to-attach-the-debugger-to-the-vssphost4exe-process"></a>若要将调试器附加到 vssphost4.exe 进程  
  
1.  开始调试你的 Visual Studio 实验实例或 Visual Studio 的正则实例中的扩展按照上面的说明。  
  
2.  在菜单栏在其中运行调试程序时，Visual Studio 实例中，选择**调试**，**附加到进程**。  
  
3.  在**可用进程**列表中，选择 vssphost.exe。  
  
    > [!NOTE]  
    >  如果 vssphost.exe 不出现在列表中，你必须在其中运行扩展的 Visual Studio 的实例来启动 vssphost4.exe 过程。 通常情况下，你执行此操作执行的操作导致 Visual Studio 以连接到开发计算机上的 SharePoint 站点。 例如，Visual Studio 将启动 vssphost4.exe 下展开站点连接节点 （节点显示站点 URL） 时**SharePoint 连接**中的节点**服务器资源管理器**窗口中，或当你添加某些 SharePoint 项目项，如**列表实例**或**事件接收器**项，向 SharePoint 项目。  
  
4.  选择**附加**按钮。  
  
5.  在 Visual Studio 正在调试的情况下，执行所需执行命令的步骤。  
  
## <a name="modifying-registry-values-to-help-debug-sharepoint-tools-extensions"></a>修改注册表值，以帮助调试 SharePoint 工具扩展  
 调试的 Visual Studio 中的 SharePoint 工具扩展时，你可以修改注册表来帮助你解决扩展中的值。 值已存在 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools 项下。 默认情况下不存在这些值。  
  
 为了帮助排查任何扩展 SharePoint 工具，可以创建和设置 EnableDiagnostics 值。 下表描述了此值。  
  
|值|描述|  
|-----------|-----------------|  
|EnableDiagnostics|指定是否显示诊断消息的 REG_DWORD**输出**窗口。<br /><br /> 若要显示的诊断消息，请将此值设置为 1。 若要停止显示消息，将此值设置为 0，或删除此值。<br /><br /> 若要将消息写入到**输出**窗口从 SharePoint 工具扩展时，请使用 SharePoint 项目服务。 有关详细信息，请参阅[使用 SharePoint 项目服务](../sharepoint/using-the-sharepoint-project-service.md)。|  
  
 如果你的扩展包括 SharePoint 命令，你可以创建和设置其他值，以帮助解决该命令。 下表描述这些值。  
  
|值|描述|  
|-----------|-----------------|  
|AttachDebuggerToHostProcess|指定是否显示一个对话框，使您能够将调试器附加到 vssphost4.exe，一旦它开始意外的 REG_DWORD。 如果你想要调试的命令执行通过 vssphost.exe 开始后立即这很有用，并且没有足够的时间来手动将调试器附加之前执行此命令。 若要显示的对话框中，vssphost4.exe 调用<xref:System.Diagnostics.Debugger.Break%2A>方法启动时。<br /><br /> 若要启用此行为，请将此值设置为 1。 若要禁用此行为，将此值设置为 0，或删除此值。<br /><br /> 如果此值设置为 1 时，你可能还需要增加 HostProcessStartupTimeout 值以便自己给足够的时间来在 Visual Studio 期望 vssphost4.exe 以指示它已成功启动之前附加调试器。|  
|ChannelOperationTimeout|指定的时间，以秒为单位，Visual Studio 等待 SharePoint 命令以执行意外的 REG_DWORD。 如果该命令不会执行时间，<xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException>引发。<br /><br /> 默认值为 120 秒。|  
|HostProcessStartupTimeout|已成功启动指定的时间，以秒为单位，Visual Studio 等待 vssphost4.exe 发出信号，它的 REG_DWORD。 如果 vssphost4.exe 时间，不指示成功启动<xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException>引发。<br /><br /> 默认值为 60 秒。|  
|MaxReceivedMessageSize|指定允许的最大大小，以字节为单位，Visual Studio 和 vssphost4.exe 之间传递的 WCF 消息的意外的 REG_DWORD。<br /><br /> 默认值为 1048576 字节 (1 MB)。|  
|MaxStringContentLength|指定允许的最大大小，以字节为单位，Visual Studio 和 vssphost4.exe 之间传递的字符串的意外的 REG_DWORD。<br /><br /> 默认值为 1048576 字节 (1 MB)。|  
  
## <a name="see-also"></a>另请参阅  
 [扩展 Visual Studio 中的 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [在 Visual Studio 中部署 SharePoint 工具扩展](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  