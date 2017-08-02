---
title: "从 Visual Studio 部署 Windows 应用商店应用程序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: ef3a0f36-bfc9-4ca0-aa61-18261f619bff
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# 从 Visual Studio 部署 Windows 应用商店应用程序
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![仅适用于 Windows](~/debugger/media/windows_only_content.png "windows\_only\_content")  
  
 Visual Studio 部署功能可在目标设备上生成和注册随 Visual Studio 创建的 Windows 应用商店应用。 应用的实际注册方法取决于目标设备是本地还是远程：  
  
-   如果目标是本地 Visual Studio 计算机，Visual Studio 将从其生成文件夹注册应用。  
  
-   如果目标是远程设备，Visual Studio 会将所需的文件复制到远程计算机并在该设备上注册应用。  
  
 从 Visual Studio 调试应用时，部署是自动的，调试方法是使用“启动调试”选项（键盘：F5）或“启动但不调试”选项（键盘：CTRL \+ F5）。 你也可以手动部署应用。 手动部署在以下情况中非常有用：  
  
-   本地或远程计算机上的随机测试。  
  
-   部署将启动你要调试的另一个应用的应用。  
  
-   部署由另一个应用或方法启动时将进行调试的应用。  
  
##  <a name="BKMK_In_this_topic"></a> 主题内容  
 在本主题中，你将了解：  
  
 [如何部署 Windows 应用商店应用](#BKMK_How_to_deploy_a_Windows_Store_app)  
  
 [如何指定远程设备](#BKMK_How_to_specify_a_remote_device)  
  
 [部署选项](#BKMK_Deployment_options)  
  
##  <a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> 如何部署 Windows 应用商店应用  
 手动部署应用是一个非常简单的过程：  
  
1.  如果你要部署到远程设备，请在应用的启动项目的属性项目页中指定设备的名称或 IP 地址。 （执行此操作的步骤在本主题靠后的位置列出\)。  
  
2.  在调试器的“Visual Studio”工具栏上，从**“启动调试”**按钮旁的下拉列表选择部署目标。  
  
     ![在本地计算机上运行](../debugger/media/vsrun_f5_local.png "VSRUN\_F5\_Local")  
  
3.  在**“生成”**菜单上，选择**“部署”**  
  
##  <a name="BKMK_How_to_specify_a_remote_device"></a> 如何指定远程设备  
 **先决条件**  
  
 将应用部署到远程设备：  
  
-   必须在远程设备上安装开发人员许可证。  
  
-   远程设备上必须已安装 Visual Studio 远程工具并且远程调试监视器必须正在运行。  
  
     部署使用远程调试器网络渠道将应用文件发送到远程设备。  
  
#### 指定远程设备  
  
1.  在启动项目的“调试”属性页上，指定远程部署目标的名称或 IP 地址。  
  
2.  要打开“调试”属性页，请在解决方案资源管理器中选择项目，然后从快捷菜单中选择**“属性”**。  
  
3.  然后，在属性页窗口上选择**“调试”**节点。  
  
4.  你可以键入远程设备的名称或 IP 地址，也可以从**“选择远程调试器连接”**对话框选择该设备。  
  
     ![“选择远程调试器连接”对话框](~/debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN\_SelectRemoteDebuggerDlg")  
  
     **“选择远程调试器连接”**对话框显示本地子网上的设备以及通过以太网电缆直接连接到 Visual Studio 计算机的任何设备。  
  
 **在 JavaScript 或 Visual C\+\+ 项目页中指定远程设备**  
  
 ![用于远程调试的 C&#43;&#43; 项目属性](~/debugger/media/vsrun_cpp_projprop_remote.png "VSRUN\_CPP\_ProjProp\_Remote")  
  
1.  从**“要启动的调试器”**列表中选择**“远程调试器”**。  
  
2.  在**“计算机名称”**框中输入远程设备的网络名称。 或者，你可以选择框中的下拉箭头，以从“选择远程调试器连接”对话框中选择该设备。  
  
 **在 Visual C\# 和 Visual Basic 项目页中指定远程设备**  
  
 ![用于远程调试的托管项目属性](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN\_Managed\_ProjProp\_Remote")  
  
1.  从**“目标设备”**列表中选择**“远程计算机”**。  
  
2.  在**“远程计算机”**框中输入远程设备的网络名称，或单击**“查找”**，从**“选择远程调试器连接”**对话框中选择该设备。  
  
##  <a name="BKMK_Deployment_options"></a> 部署选项  
 你可以在启动项目的“调试”属性页上设置以下部署选项。  
  
 **允许网络环回**  
 为安全起见，不允许以标准方式安装的 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 应用对装有它的设备进行网络调用。 默认情况下，Visual Studio 部署功能为所部署的应用程序创建此规则的例外。 通过此例外，在一台计算机上即可测试通信过程。 向 [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] 提交应用之前，应在没有例外的情况下测试应用。  
  
 若要从应用中移除网络环回例外，请执行以下操作：  
  
-   在 C\# 和 VB 调试属性页上，清除**“允许网络环回”**复选框。  
  
-   在 JavaScript 和调试属性页上，将**“允许网络环回”**值设置为**“否”**。  
  
 **不启动，但在启动时调试代码（C\# 和 VB）\/启动应用程序（JavaScript 和 C\+\+）时调试我的代码**  
 配置部署以在应用启动时自动启动调试会话：  
  
-   在 C\# 和 VB 调试属性页上，选中**“不启动，但在启动时调试代码”**复选框。  
  
-   在 JavaScript 和调试属性页上，将**“启动应用程序”**值设置为**“是”**。  
  
## 请参阅  
 [从 Visual Studio 运行应用程序](../debugger/run-store-apps-from-visual-studio.md)