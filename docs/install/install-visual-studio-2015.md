---
title: "安装 Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-install"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
f1_keywords: 
  - "vs.about"
helpviewer_keywords: 
  - "Visual Studio, 安装"
  - "安装 Visual Studio"
  - "服务器安装 [Visual Studio]"
  - "安装 [Visual Studio]"
  - "安装 Visual Studio"
ms.assetid: da049020-cfda-40d7-8ff4-7492772b620f
caps.latest.revision: 177
caps.handback.revision: 150
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# 安装 Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此页包含帮助安装 Visual Studio 2015 的详细信息，这是一款由开发人员工作效率工具组成的集成套件。 此外，还介绍了可帮助你快速了解有关[功能](https://www.visualstudio.com/en-us/news/vs2015-vs.aspx)、[版本](http://go.microsoft.com/fwlink/?LinkID=242142)、[系统要求](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs)、[下载](http://go.microsoft.com/fwlink/?LinkId=517106)和更多信息的链接。  
  
> [!TIP]
>  若要查看 Visual Studio 早期版本的安装信息，请单击本页顶部的“其他版本”链接。  
  
## 快速链接  
 在我们深入了解详细信息之前，这里是最常用的链接列表。  
  
|功能|  
|--------|  
|若要了解有关 Visual Studio 2015 中的新增功能或更新的功能的详细信息，请参阅 [Visual Studio 2015 RTM](https://www.visualstudio.com/en-us/news/vs2015-vs.aspx) 和 [Visual Studio 2015 Update 1](https://www.visualstudio.com/news/vs2015-update1-vs) 的发行说明。|  
|若要查看 Visual Studio 2015 各个版本中的可用功能，请参阅我们的[比较 Visual Studio 产品](http://go.microsoft.com/fwlink/?LinkID=242142)页。|  
|若要查看 Visual Studio 2015 各个版本的系统要求，请参阅 [Visual Studio 2015 兼容性](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs)页。|  
|若要安装 Visual Studio 2015，请从 [Visual Studio 下载](http://go.microsoft.com/fwlink/?LinkId=517106)下载，或使用装箱产品中的安装媒体。|  
|若要查找你的产品密钥，请参阅[如何：定位 Visual Studio 产品密钥](../install/how-to-locate-the-visual-studio-product-key.md)主题。|  
|若要了解个人和企业客户的授权选项，请参阅 [Visual Studio 和 MSDN 授权](https://www.microsoft.com/download/details.aspx?id=13350)白皮书。|  
  
##  <a name="custom"></a> 默认安装与自定义安装  
 在安装 Visual Studio 2015 时，你可以包括或排除你每天都会使用的组件。 这意味着，默认安装比自定义安装所占用的空间更小，安装速度更快。 这还意味着在以前的版本中，默认安装的许多组件现在被视为必须在此版本中显式选择的自定义组件。  
  
 ![Visual Studio 2015 安装对话框](~/ide/media/vs2015_setup_screen.png "VS2015\_Setup\_screen")  
  
 自定义组件包括 Visual C\+\+、Visual F\#、SQL Server Data Tools、跨平台移动工具和 SDK，以及第三方 SDK 和扩展。 如果在初始安装过程中没有选择这些自定义组件，则可以在之后安装任何自定义组件。  
  
> [!NOTE]
>  自定义安装自动包含默认安装中的组件。  
  
 自定义组件的完整列表如下所示：  
  
-   **编程语言**  
  
    -   Visual C\+\+ 编译器、库和工具  
  
    -   Visual F\#  
  
    -   Visual Studio 的 Python 工具  
  
-   **Windows 和 Web 开发**  
  
    -   ClickOnce 发布工具  
  
    -   Microsoft SQL Server Data Tools  
  
    -   Microsoft Web 开发人员工具  
  
    -   Visual Studio 的 PowerShell 工具  
  
    -   Silverlight 开发工具包  
  
    -   通用 Windows 应用开发工具  
  
    -   Windows 10 工具和 SDK  
  
    -   Windows 8.1 和 Windows Phone 8.0\/8.1 工具  
  
    -   Windows 8.1 工具和 SDK  
  
-   **跨平台移动开发**  
  
    -   Xamarin \(C\#\/.NET\)  
  
    -   Apache Cordova \(HTML\/JavaScript\)  
  
    -   适用于 iOS\/Android 的 Visual C\+\+ 移动开发  
  
-   **常用工具和 SDK**  
  
    -   Android 本机开发工具包（R10E，32 位）  
  
    -   Android SDK  
  
    -   Android SDK 安装程序（API 级别 19 和 21）  
  
    -   Android SDK 安装程序（API 级别 22）  
  
    -   Apache Ant \(1.9.3\)  
  
    -   Java SE 开发工具包 \(7.0.550.13\)  
  
    -   Joyent Node.js  
  
-   **常用工具**  
  
    -   用于 Windows 的 Git  
  
    -   Visual Studio 的 GitHub 扩展  
  
    -   Visual Studio 扩展性工具  
  
##  <a name="installing"></a> 安装 Visual Studio  
 你必须具有管理员凭据才能安装 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 但是，在安装 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 之后，在使用时不需要凭据。  
  
 你的本地管理员帐户必须启用以下权限才能在 Visual Studio 中安装任意内容。  
  
|本地策略对象显示名称|用户权限|  
|----------------|----------|  
|备份文件和目录|SeBackupPrivilege|  
|调试程序|SeDebugPrivilege|  
|管理审核和安全日志|Sesecurityprivilege|  
  
 有关此本地管理员帐户要求的详细信息，请参阅知识库文章：[如果安装帐户没有某些用户权限，则 SQL Server 安装失败](https://support.microsoft.com/en-us/kb/2000257)。  
  
###  <a name="BKMK_Media"></a> 通过使用安装媒体进行安装  
  
-   若要在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 安装媒体上的根目录中安装 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，请运行所需版本的安装文件：  
  
    |版本|安装文件|  
    |--------|----------|  
    |Visual Studio Enterprise|vs\_enterprise.exe|  
    |Visual Studio Professional|vs\_professional.exe|  
    |Visual Studio 社区|vs\_community.exe|  
  
###  <a name="BKMK_Website"></a> 通过从产品网站下载来进行安装  
  
-   请访问 VisualStudio.com 网站上的 [Visual Studio 下载](http://go.microsoft.com/fwlink/?LinkId=517106)。  
  
###  <a name="BKMK_Offline"></a> 下载 Visual Studio 进行脱机安装  
 在多数情况下，你可以顺利地从下载站点安装 Visual Studio。 但是，在某些情况下，你可能希望在安装之前下载所有更新包（例如，在多台计算机或在脱机计算机上安装）。 下列步骤说明如何下载脱机安装所需的所有更新包。  
  
1.  从 MSDN 网站将更新可执行文件下载到你文件系统中的某个位置后，请在命令提示符处执行以下命令：`<executable name> /layout`。  
  
     此命令将下载用于安装的所有包。  
  
     通过使用 `/layout` 开关，你可以下载几乎所有核心安装包，而不仅仅是下载适用于下载计算机的安装包。 此方法可为你提供在任何地方运行此更新所需的所有文件，如果你想安装原来没有安装的组件，这种方法可能会很有用。  
  
2.  运行该命令后，系统会提示你指定下载位置。 输入位置，然后选择“下载”。  
  
3.  当包下载成功时，你应会看到一个 Visual Studio 屏幕，其中显示**安装成功\!已成功获取所有指定组件。**  
  
4.  在指定的文件位置中，查找可执行文件和包文件夹。 这是需要复制到共享位置或安装媒体上的所有内容。  
  
    > [!CAUTION]
    >  目前，Android SDK 不支持脱机安装体验。 如果在未连接到 Internet 的计算机上安装 Android SDK 安装程序项，则安装可能失败。  
  
5.  你现在可以从该文件位置或安装媒体运行安装。  
  
###  <a name="BKMK_Virtualized"></a> 在虚拟化环境中安装 Visual Studio  
 **有关 Hyper\-V 的视频问题**  
  
 如果你运行的 Windows Server 2008 R2 启用了 Hyper\-V 并包含加速图形适配器，则你可能会遇到系统速度下降的情况。  
  
 有关详细信息，请参阅 Microsoft 网站上的以下页面：[在基于 Windows Server 2008 或 Windows Server 2008 R2 的计算机启用了 Hyper\-V 角色并安装加速显示适配器时，视频性能可能会降低](http://go.microsoft.com/fwlink/?LinkID=231084)。  
  
 **有关 Hyper\-V 的模拟设备**  
  
 在不包含虚拟化的真实硬件上安装 Visual Studio 2015 时，你可以选择对使用 Hyper\-V 的 Windows 和 Android 设备启用模拟的功能。 安装到 Hyper\-V 中时，你将无法模拟 Windows 或 Android 设备。 这是因为仿真程序本身就是虚拟机，并且当前无法将 VM 托管在另一个 VM 内部。 解决方法是拥有能够直接在上面部署和调试应用程序的真正的 Windows 和 Android 设备。  
  
## 使用命令行参数  
 当你运行安装应用程序时，可以使用以下命令行参数（不区分大小写）。  
  
|参数|说明|  
|--------|--------|  
|**\/?**<br /><br /> **\/help**<br /><br /> **\/h**|显示命令行参数。|  
|**\/AddRemoveFeatures**|指定要在安装的产品中添加或移除的功能。|  
|**\/AdminFile** *AdminDeployment.xml*|使用你为管理安装指定的数据文件安装 Visual Studio。|  
|**\/CEIPConsent**|同意根据产品隐私策略收集信息以改进客户体验。|  
|**\/ChainingPackage** *BundleName*|指定此捆绑包链接到的捆绑包。 还可用于指定客户改善体验队列。|  
|**\/CreateAdminFile \<filename\>**|指定用于创建可与 \/AdminFile 一起使用的控制文件的位置|  
|**\/CustomInstallPath** *InstallationDirectory*|在你指定的目录中安装所有可重定目标的包。|  
|**\/ForceRestart**|安装完成后始终重新启动计算机。|  
|**\/full**|安装所有产品功能。|  
|**\/InstallSelectableItems \<item name 1\>\[;\<item name 2\>\]**|要在安装程序向导选择屏幕上检查的选择树项列表。|  
|**\/l**<br /><br /> **\/Log** *Filename*|指定日志文件的位置。|  
|**\/layout** *Directory*|将安装媒体上的文件复制到你指定的目录。|  
|**\/NoCacheOnlyMode**|阻止包缓存的预填充。|  
|**\/NoRefresh**|禁止检查此产品的较新版本是否存在必需或推荐的更新版本。|  
|**\/norestart**|在安装期间或安装完成后，阻止安装应用程序重新启动计算机。 请参阅 [Visual Studio 管理员指南](../install/visual-studio-administrator-guide.md) 的返回代码部分，了解要查找的返回代码。|  
|**\/noweb**|阻止从 Internet 中安装。|  
|**\/OverrideFeedUri \<path to feed file\>**|本地外部源的路径，它描述软件项|  
|**\/ProductKey**<br /><br /> *ProductKey*|设置不包含短划线且不超过 25 个字符的自定义产品密钥。|  
|**\/PromptRestart**|在重新启动计算机之前提示用户。|  
|**\/q**<br /><br /> **\/quiet**<br /><br /> **\/s**<br /><br /> **\/silent**|取消安装应用程序的用户界面 \(UI\)。 如果已安装 Visual Studio，并且你除了这个参数之外未指定任何参数，则在维护模式下运行安装应用程序。|  
|**\/qb**<br /><br /> **\/passive**|显示进度，但不等待用户输入。|  
|**\/repair**|修复 Visual Studio。|  
|**\/SuppressRefreshPrompt**|禁止在安装向导中显示更新可用对话框，因此安装向导将自动接受任意必需或推荐更新版本。|  
|**\/u**<br /><br /> **\/Uninstall**|卸载 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。|  
|**\/Uninstall \/Force**<br /><br /> **\/u \/force**|卸载 Visual Studio 以及与其他产品共享的所有功能。 **Warning:**  如果使用此参数，则在同一台计算机上安装的其他产品可能会停止正常工作。|  
  
 从命令行运行安装程序时，你将希望捕获和处理返回代码以获得更佳的命令行体验。  有关详细信息，请参阅 [Visual Studio 管理员指南](../install/visual-studio-administrator-guide.md)。  
  
##  <a name="troubleshooting"></a> 有关安装的疑难解答  
 使用这些资源来获取关于设置和安装问题的帮助：  
  
-   [Visual Studio Setup and Installation（Visual Studio 设置和安装）](http://go.microsoft.com/fwlink/?LinkID=151190)论坛。 查看 Visual Studio 社区中他人的问题和回答。 如果未找到所需的帮助，可自行提问。  
  
-   [Microsoft Support for Visual Studio（针对 Visual Studio 的 Microsoft 支持）](http://go.microsoft.com/fwlink/?LinkID=251019)网站。 阅读知识库 \(KB\) 文章并了解如何联系 Microsoft 支持，以获取有关 Visual Studio 安装问题的信息。  
  
-   对于 Visual Studio 2015 的发行版本，可以通过使用以下 Connect 站点来报告问题：[https:\/\/connect.microsoft.com\/visualstudio](https://connect.microsoft.com/visualstudio)。  
  
     报告问题时最好附安装日志。 你可以按照下列步骤，通过使用 Microsoft Visual Studio 和 .NET Framework 日志收集工具来准备日志进行问题报告。  
  
    1.  从 [http:\/\/aka.ms\/vscollect](http://aka.ms/vscollect) 下载安装诊断工具  
  
    2.  从提升的命令提示符处运行 collect.exe 程序。  
  
    3.  Collect.exe 程序完成后，从 Temp 目录提取 vslogs.cab 文件，并将其上载到问题报告。  
  
##  <a name="enterprise"></a> 企业网络部署  
 有关如何通过网络部署 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的信息，请参阅 [Visual Studio 管理员指南](../install/visual-studio-administrator-guide.md)。  
  
##  <a name="afterInstalling"></a> 安装 Visual Studio 之后  
 安装 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 后，我们建议你注册该产品的副本。  
  
###  <a name="register"></a> 注册 Visual Studio  
  
##### 要注册 Visual Studio  
  
1.  在菜单栏上，依次选择“帮助”和“关于”。  
  
     “关于”对话框显示产品标识号 \(PID\)。 需使用 PID 和 Windows 帐户凭据（如 Hotmail 或 Outlook.com 电子邮件地址和密码）来注册产品。  
  
2.  在菜单栏上，选择“帮助”和“注册产品”。  
  
###  <a name="helpContent"></a> 安装脱机帮助内容  
 安装 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 之后，为了可脱机使用，可以下载其他帮助内容。  
  
##### 安装或卸载帮助内容  
  
1.  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 菜单栏上，选择“帮助”和“添加和移除帮助内容”。  
  
2.  在“Microsoft 帮助查看器”的“管理内容”选项卡上，选择你的帮助内容对应的安装源。  
  
3.  如果要查找特定的帮助集合，在“搜索”文本框中输入名称或关键字，然后按 Enter。  
  
4.  在所需帮助集合的名称旁边，选择“添加”或“移除”链接。  
  
5.  选择“更新”按钮。  
  
 有关脱机帮助的详细信息，请参阅 [Microsoft 帮助查看器 2.2 帮助](../ide/microsoft-help-viewer.md)  
  
###  <a name="repair"></a> 修复 Visual Studio  
  
##### 要修复 Visual Studio  
  
1.  在“控制面板”上的“程序和功能”页中，选择要修复的产品版本，然后选择“更改”。  
  
2.  在安装向导中，选择“修复”，再选择“下一步”，然后按照其余说明进行操作。  
  
##### 在无提示或被动模式下修复 Visual Studio（即，从源中修复）  
  
1.  在安装了 Visual Studio 的计算机上，打开 Windows 命令提示符。  
  
2.  输入以下参数：  
  
     *DVDRoot* \\\<Installation File\> \<\/quiet&#124;\/passive\> \[\/norestart\]\/Repair  
  
###  <a name="optionalComponents"></a> 安装可选项  
  
##### 要安装可选项  
  
1.  在“控制面板”上的“程序和功能”页中，选择要将一个或多个组件添加到的产品版本，然后选择“更改”。  
  
2.  在安装向导中，选择“修改”，然后选择想要安装的组件。  
  
3.  选择“下一步”，然后按照其余说明进行操作。  
  
###  <a name="serviceReleases"></a> 检查是否有 Service Release 和产品更新  
 因为并非所有扩展都兼容，所以当你从 Visual Studio 早期版本进行升级的时候，它不会自动升级扩展。 必须从 [Visual Studio 库](http://go.microsoft.com/fwlink/?LinkId=178891) 或软件发行者处重新安装扩展。  
  
##### 自动检查是否有 Service Release  
  
1.  在菜单栏上，依次选择“工具”、“选项”。  
  
2.  在“选项”对话框中，展开“环境”，然后选择“扩展和更新”。 请确保已选中“自动检查更新”复选框，然后选择“确定”。  
  
##  <a name="uninstalling"></a> 卸载 Visual Studio  
 使用以下步骤以卸载Visual Studio 2015。  
  
#### 要卸载 Visual Studio  
  
1.  在“控制面板”上的“程序和功能”页中，选择要卸载的产品版本，然后选择“更改”。  
  
2.  在安装向导中，选择“卸载”，再选择“是”，然后在向导中按照其余说明进行操作。  
  
#### 在无提示或被动模式下卸载 Visual Studio（即，从源中卸载）  
  
1.  在安装了 Visual Studio 的计算机上，打开 Windows 命令提示符。  
  
2.  输入以下参数：  
  
     *DVDRoot* \\\<Installation File\> \<\/quiet&#124;\/passive\> \[\/norestart\]\/uninstall  
  
 如果你不能通过使用卸载实用程序卸载 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，则可以通过移除 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 以及相关组件来执行手动卸载。 有关详细信息，请参阅 Microsoft 知识库 \(KB\) 中的 [如何卸载 Visual Studio](https://support.microsoft.com/en-us/kb/2771441) 一文，或发表在 Microsoft 服务器与工具博客网站上的 [移除卸载后残留的 Visual Studio 组件](http://blogs.msdn.com/b/heaths/archive/2015/07/17/removing-visual-studio-components-left-behind-after-an-uninstall.aspx)。  
  
##  <a name="relatedTopics"></a> 相关主题  
  
|标题|说明|  
|--------|--------|  
|[并行安装 Visual Studio 版本](../Topic/Installing%20Visual%20Studio%20Versions%20Side-by-Side.md)|提供有关如何在同一台计算机上安装多个 Visual Studio 版本的信息。|  
|[Visual Studio 图像库](../designers/the-visual-studio-image-library.md)|提供有关如何安装可在 Visual Studio 应用程序中使用的图形的信息。|  
|[Visual Studio 管理员指南](../install/visual-studio-administrator-guide.md)|提供有关 Visual Studio 部署选项的信息。|  
|[安装 Visual Studio 的多个语言版本](../Topic/Installing%20Multiple%20Language%20Versions%20of%20Visual%20Studio.md)|提供有关如何安装不同 Visual Studio 版本的信息。|  
|[如何：定位 Visual Studio 产品密钥](../install/how-to-locate-the-visual-studio-product-key.md)|提供有关如何找到用于安装 Visual Studio 的产品密钥的信息。|  
|[入门](../ide/get-started-developing-with-visual-studio.md)|指向可帮助你有效地使用 Visual Studio 的文档的链接。|  
  
## 请参阅  
 [在 Visual Studio 中自定义开发设置](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)