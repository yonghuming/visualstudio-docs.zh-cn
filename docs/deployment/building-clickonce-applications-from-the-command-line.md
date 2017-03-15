---
title: "从命令行生成 ClickOnce 应用程序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce 部署, 从命令行"
  - "发布"
  - "发布, ClickOnce"
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 23
---
# 从命令行生成 ClickOnce 应用程序
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 中可以从命令行生成项目，即使这些项目是在集成开发环境 \(IDE\) 中创建的。  事实上，您可以在只安装了 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 的其他计算机上重新生成使用 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 创建的项目。  这使您可以使用自动化过程（例如，在中心生成实验室中或使用除生成项目本身的技术外的高级脚本技术）重现生成。  
  
## 使用 MSBuild 重现 ClickOnce 应用程序部署  
 当使用命令行调用 msbuild \/target:publish 时，它会通知 MSBuild 系统生成项目并在 publish 文件夹中创建 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序。  这与在 IDE 中选择**“发布”**命令是等效的。  
  
 此命令执行 msbuild.exe（位于 Visual Studio 命令提示环境中的路径上）。  
  
 “target”是 MSBuild 的一个指示器，指示如何处理该命令。  主要的目标有“build”目标和“publish”目标。  生成目标等效于在 IDE 中选择“生成”命令（或按 F5）。  通过键入 `msbuild` 可以只生成项目。  此命令之所以能工作，是因为生成目标是 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 生成的所有项目的默认目标。  这意味着不必明确指定生成目标。  因此，键入 `msbuild` 时执行的操作与键入 `msbuild /target:build` 时相同。  
  
 `/target:publish` 命令通知 MSBuild 调用发布目标。  发布目标取决于生成目标。  这意味着发布操作是生成操作的一个超集。  例如，如果更改了 Visual Basic 或 C\# 的一个源文件，则发布操作将自动重新生成相应的程序集。  
  
 有关使用 Mage.exe 命令行工具创建 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 清单来生成完整的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署的信息，请参见[演练：手动部署 ClickOnce 应用程序](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。  
  
## 使用 MSBuild 创建和生成基本的 ClickOnce 应用程序  
  
#### 创建和发布 ClickOnce 项目  
  
1.  在**“文件”**菜单上，单击**“新建项目”**。  此时将出现**“新建项目”**对话框。  
  
2.  选择**“Windows 应用程序”**，并将其命名为 `CmdLineDemo`。  
  
3.  在**“生成”**菜单中单击**“发布”**命令。  
  
     此步骤确保项目已正确配置为生成 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序部署。  
  
     出现“发布向导”。  
  
4.  在发布向导中单击**“完成”**。  
  
     Visual Studio 生成并显示名为 Publish.htm 的默认网页。  
  
5.  保存项目，并记下存储项目的文件夹位置。  
  
 上面的步骤创建一个已首次发布的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 项目。  现在您可以在 IDE 外重现该生成。  
  
#### 从命令行重现生成  
  
1.  退出 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]。  
  
2.  在 Windows 的**“开始”**菜单中单击**“所有程序”**，然后依次单击**“Microsoft Visual Studio”**、**“Visual Studio 工具”**和**“Visual Studio 命令提示”**。  这将打开处于当前用户的根文件夹中的命令提示。  
  
3.  在**“Visual Studio 命令提示”**中，将当前目录更改为上面刚刚生成的项目的位置。  例如，键入 `chdir My Documents\Visual Studio\Projects\CmdLineDemo`。  
  
4.  若要移除在“创建和发布 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 项目”中生成的现有文件，请键入 `rmdir /s publish`。  
  
     此步骤是可选的，但它确保所有新文件的生成均通过命令行生成完成。  
  
5.  键入 `msbuild /target:publish`。  
  
 上面的步骤将在项目的子文件夹**“Publish”**中生成完整的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序部署。  CmdLineDemo.application 为 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署清单。  文件夹 CmdLineDemo\_1.0.0.0 包含文件 CmdLineDemo.exe 和 CmdLineDemo.exe.manifest（[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序清单）。  Setup.exe 为引导程序，它在默认情况下配置为安装 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。  DotNetFX 文件夹包含 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 的可再发行组件。  这就是通过 Web、UNC 或 CD\/DVD 部署应用程序所需的所有文件。  
  
## 发布属性  
 当通过上面的过程发布应用程序时，发布向导在项目文件中插入以下属性。  这些属性直接影响 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序的生成方式。  
  
 在 CmdLineDemo.vbproj \/ CmdLineDemo.csproj 中：  
  
```  
<AssemblyOriginatorKeyFile>WindowsApplication3.snk</AssemblyOriginatorKeyFile>  
<GenerateManifests>true</GenerateManifests>  
<TargetZone>LocalIntranet</TargetZone>  
<PublisherName>Microsoft</PublisherName>  
<ProductName>CmdLineDemo</ProductName>  
<PublishUrl>http://localhost/CmdLineDemo</PublishUrl>  
<Install>true</Install>  
<ApplicationVersion>1.0.0.*</ApplicationVersion>  
<ApplicationRevision>1</ApplicationRevision>  
<UpdateEnabled>true</UpdateEnabled>  
<UpdateRequired>false</UpdateRequired>  
<UpdateMode>Foreground</UpdateMode>  
<UpdateInterval>7</UpdateInterval>  
<UpdateIntervalUnits>Days</UpdateIntervalUnits>  
<UpdateUrlEnabled>false</UpdateUrlEnabled>  
<IsWebBootstrapper>true</IsWebBootstrapper>  
<BootstrapperEnabled>true</BootstrapperEnabled>  
```  
  
 可通过命令行重写这些属性中的任何一个，而无需更改项目文件自身。  例如，下面的命令将生成不具有引导程序的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序部署：  
  
```  
msbuild /target:publish /property:BootstrapperEnabled=false  
```  
  
 发布属性在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中由**“项目设计器”**的**“发布”**、**“安全”**和**“签名”**属性页进行控制。  下面是对发布属性的说明，以及关于如何在应用程序设计器的各种属性页中设置每个属性的指示：  
  
-   `AssemblyOriginatorKeyFile` 确定用于对 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序清单进行签名的密钥文件。  同一密钥还可用于为程序集分配强名称。  此属性在**“项目设计器”**的**“签名”**页上设置。  
  
 下面的属性在**“安全”**页上设置：  
  
-   **“启用 ClickOnce 安全设置”**决定是否生成 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 清单。  默认情况下，最初创建项目时，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 清单生成是关闭的。  当第一次发布时，向导将自动打开此标志。  
  
-   **“TargetZone”**决定要发送到 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序清单中的信任级别。  可能的值有“Internet”、“LocalIntranet”和“Custom”。  “Internet”和“LocalIntranet”将使默认权限集发送到 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序清单中。  默认值为“LocalIntranet”，实际上意味着完全信任。  “Custom”指定只有在基本 app.manifest 文件中显式指定的权限才发送到 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序清单中。  app.manifest 文件是一个部分清单文件，只包含信任信息定义。  它是隐藏文件，在**“安全”**页上配置权限时会自动添加到项目中。  
  
 下面的属性在**“发布”**页上设置：  
  
-   `PublishUrl` 是 IDE 中应用程序要发布到的位置。  如果 `InstallUrl` 和 `UpdateUrl` 属性均未指定，则它将插入到 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序清单中。  
  
-   `ApplicationVersion` 指定 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序的版本。  这是一个四位版本号。  如果最后一位为“\*”，则用 `ApplicationRevision` 替换在生成时插入到清单中的值。  
  
-   `ApplicationRevision` 指定修订版本。  这是一个整数，每次在 IDE 中发布时都会递增。  注意，在命令行中执行的生成不会使其自动递增。  
  
-   `Install` 确定应用程序是安装的应用程序还是从 Web 运行的应用程序。  
  
-   `InstallUrl`（未显示）为用户从其安装应用程序的位置。  如果指定，此值在启用 `IsWebBootstrapper` 属性时写入 setup.exe 引导程序。  如果未指定 `UpdateUrl`，它也会插入到应用程序清单中。  
  
-   `SupportUrl`（未显示）为在安装的应用程序的**“添加\/删除程序”**对话框中链接的位置。  
  
 下面的属性在**“应用程序更新”**对话框（从**“发布”**页访问）中设置。  
  
-   `UpdateEnabled` 指示应用程序是否应检查更新。  
  
-   `UpdateMode` 指定前台更新或后台更新。  
  
-   `UpdateInterval` 指定应用程序检查更新的频率。  
  
-   `UpdateIntervalUnits` 指定 `UpdateInterval` 值的单位是小时、天还是星期。  
  
-   `UpdateUrl`（未显示）为应用程序将从其接收更新的位置。  如果指定，此值将插入到应用程序清单中。  
  
-   下面的属性在**“发布选项”**对话框（从**“发布”**页访问）中设置。  
  
-   `PublisherName` 指定在安装或运行应用程序时显示的提示中显示的发行者名称。  对于安装的应用程序，它还用于指定**“开始”**菜单上的文件夹名称。  
  
-   `ProductName` 指定在安装或运行应用程序时显示的提示中显示的产品名称。  对于安装的应用程序，它还用于指定**“开始”**菜单上的快捷方式名称。  
  
-   下面的属性在**“系统必备”**对话框（从**“发布”**页访问）中设置。  
  
-   `BootstrapperEnabled` 确定是否生成 setup.exe 引导程序。  
  
-   `IsWebBootstrapper` 确定 setup.exe 引导程序通过 Web 还是以基于磁盘的模式工作。  
  
## InstallURL、SupportUrl、PublishURL 和 UpdateURL  
 下表显示 ClickOnce 部署的四个 URL 选项。  
  
|URL 选项|说明|  
|------------|--------|  
|`PublishURL`|如果要将 ClickOnce 应用程序发布到网站，则是必需的。|  
|`InstallURL`|可选。  如果安装站点不同于 `PublishURL`，请设置此 URL 选项。  例如，您可以将 `PublishURL` 设置为 FTP 路径，并将 `InstallURL` 设置为 Web URL。|  
|`SupportURL`|可选。  如果支持站点不同于 `PublishURL`，请设置此 URL 选项。  例如，您可以将 `SupportURL` 设置为贵公司的客户支持网站。|  
|`UpdateURL`|可选。  如果更新位置不同于 `InstallURL`，请设置此 URL 选项。  例如，您可以将 `PublishURL` 设置为 FTP 路径，并将 `UpdateURL` 设置为 Web URL。|  
  
## 请参阅  
 <xref:Microsoft.Build.Tasks.GenerateBootstrapper>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>   
 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>   
 [ClickOnce 安全和部署](../deployment/clickonce-security-and-deployment.md)   
 [演练：手动部署 ClickOnce 应用程序](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)