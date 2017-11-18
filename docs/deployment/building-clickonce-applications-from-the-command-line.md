---
title: "生成 ClickOnce 应用程序从命令行 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, from command line
- publishing
- publishing, ClickOnce
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
caps.latest.revision: "23"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 86dba79e6e8b7e3f3b2837e494cfeddd2692d0cf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="building-clickonce-applications-from-the-command-line"></a>从命令行生成 ClickOnce 应用程序
在[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]，你可以生成从命令行的项目，即使它们在集成的开发环境 (IDE) 中创建。 事实上，你可以重新生成与创建的项目[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]只有的另一台计算机上[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]安装。 这样您就可以重现使用自动化的过程生成，例如，在中心生成实验室或使用高级脚本编写超出范围的生成项目本身的技巧。  
  
## <a name="using-msbuild-to-reproduce-clickonce-application-deployments"></a>使用 MSBuild 重现 ClickOnce 应用程序部署  
 在命令行的 msbuild /target:publish 调用时，它会通知 MSBuild 系统以生成项目并创建[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序的发布文件夹中。 这相当于选择**发布**命令在 IDE 中。  
  
 此命令执行 msbuild.exe，这将在 Visual Studio 命令提示符环境中的路径上。  
  
 "目标"是如何处理命令到 MSBuild 指示器。 密钥的目标是"build"目标和"发布"目标。 Build 目标相当于选择生成命令 （或按 F5），在 IDE 中。 如果你只想要生成你的项目，你可以通过键入实现， `msbuild`。 此命令有效，因为 build 目标是所生成的所有项目的默认目标[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]。 这意味着你不显式需要指定 build 目标。 因此，键入`msbuild`是相同的操作键入`msbuild /target:build`。  
  
 `/target:publish`命令指示 MSBuild 来调用发布目标。 发布目标取决于 build 目标。 这意味着发布操作是生成操作的超集。 例如，如果你对 Visual Basic 或 C# 源文件之一做出更改，相应的程序集将自动重新生成发布操作。  
  
 有关生成完整信息[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]使用 Mage.exe 命令行工具创建的部署你[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]清单，请参阅[演练： 手动部署 ClickOnce 应用程序](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。  
  
## <a name="creating-and-building-a-basic-clickonce-application-using-msbuild"></a>创建和构建基本的 ClickOnce 应用程序使用 MSBuild  
  
#### <a name="to-create-and-publish-a-clickonce-project"></a>创建和发布 ClickOnce 项目  
  
1.  单击**新项目**从**文件**菜单。 此时将出现 “新建项目” 对话框。  
  
2.  选择**Windows 应用程序**并将其命名`CmdLineDemo`。  
  
3.  从**生成**菜单上，单击**发布**命令。  
  
     此步骤可确保该项目是否已正确配置以生成[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序部署。  
  
     出现“发布向导”。  
  
4.  在发布向导中，单击**完成**。  
  
     Visual Studio 生成并显示调用 Publish.htm 默认 Web 页。  
  
5.  保存你的项目，并记下在其中存储的文件夹位置。  
  
 上面的步骤创建[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]已首次发布的项目。 现在您可以重新生成在 IDE 外部生成。  
  
#### <a name="to-reproduce-the-build-from-the-command-line"></a>若要重现从命令行生成  
  
1.  退出 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]。  
  
2.  从 Windows**启动**菜单上，单击**所有程序**，然后**Microsoft Visual Studio**，然后**Visual Studio Tools**，然后**Visual Studio 命令提示**。 这应在当前用户的根文件夹中打开命令提示符。  
  
3.  在**Visual Studio 命令提示符**，当前将目录更改为你刚才上面生成项目的位置。 例如，键入`chdir My Documents\Visual Studio\Projects\CmdLineDemo`。  
  
4.  若要删除的现有文件而生成中"创建和发布[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]项目中，"类型`rmdir /s publish`。  
  
     此步骤是可选的但可确保，新的文件所有由生成命令行生成。  
  
5.  键入 `msbuild /target:publish`。  
  
 上述步骤将生成完整[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]的子文件夹中的名为 P 的项目的应用程序部署**ublish**。 CmdLineDemo.application 是[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署清单。 文件夹 CmdLineDemo_1.0.0.0 包含 CmdLineDemo.exe CmdLineDemo.exe.manifest，文件[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序清单。 Setup.exe 是引导程序，后者的默认设置配置为安装[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。 DotNetFX 文件夹包含的可再发行文件[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。 这是通过 Web 或通过 UNC 或 CD/DVD 部署你的应用程序所需的文件的整个集。  
  
## <a name="publishing-properties"></a>发布属性  
 在上面的过程中发布应用程序时，以下属性到你的项目文件由插入发布向导。 这些属性直接影响如何[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]生成应用程序。  
  
 在 CmdLineDemo.vbproj / CmdLineDemo.csproj:  
  
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
  
 你可以重写任何这些属性在命令行而无需更改项目文件本身。 例如，以下将生成[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]不具有引导程序的应用程序部署：  
  
```  
msbuild /target:publish /property:BootstrapperEnabled=false  
```  
  
 发布属性进行控制[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]从**发布**，**安全**，和**签名**属性页**项目设计器**. 下面是发布的属性以及相对值的每个应用程序设计器的各种属性页中的设置方式的说明：  
  
-   `AssemblyOriginatorKeyFile`确定用于对进行签名的密钥文件你[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序清单。 这个相同密钥还可能用于你的程序集分配强名称。 此属性上设置**签名**页**项目设计器**。  
  
 下面的属性上设置**安全**页：  
  
-   **启用 ClickOnce 安全设置**确定是否[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]在生成清单。 最初创建项目，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]清单生成默认处于关闭状态。 向导将自动打开上首次发布时此标志。  
  
-   **TargetZone**确定发送到的信任级别你[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序清单。 可能的值为"Internet"、"LocalIntranet"和"自定义"。 Internet 和 LocalIntranet 将导致的默认权限集发送到你[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序清单。 LocalIntranet 是默认设置，以及它基本上意味着完全信任。 自定义指定基的应用程序清单文件中显式指定权限要发出到[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序清单。 应用程序清单文件是包含只信任信息定义部分清单文件。 它是一个隐藏的文件，在上配置权限时，自动添加到你的项目**安全**页。  
  
 下面的属性上设置**发布**页：  
  
-   `PublishUrl`是其中应用程序将发布到在 IDE 中的位置。 插入到[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序清单如果既没有`InstallUrl`或`UpdateUrl`指定属性。  
  
-   `ApplicationVersion`指定的版本[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序。 这是四位数字的版本号。 如果最后一个数字为"*"，则`ApplicationRevision`替换为在生成时插入到清单中的值。  
  
-   `ApplicationRevision`指定的修订版本。 这是一个整数，它每次在 IDE 中发布的时都会递增。 请注意，不自动递增为生成在命令行执行。  
  
-   `Install`确定应用程序是否已安装应用程序或运行从 Web 应用程序。  
  
-   `InstallUrl`（未显示） 是用户将在其中安装应用程序的位置。 如果指定，此值刻录到 setup.exe 引导程序中，如果`IsWebBootstrapper`启用属性。 它也会插入到应用程序清单如果`UpdateUrl`未指定。  
  
-   `SupportUrl`（未显示） 中链接的位置**添加/删除程序**已安装应用程序的对话框。  
  
 在中设置以下属性**应用程序更新**对话框中，从访问**发布**页。  
  
-   `UpdateEnabled`指示应用程序是否应检查更新。  
  
-   `UpdateMode`指定前景更新或后台更新。  
  
-   `UpdateInterval`指定应用程序检查更新的频率。  
  
-   `UpdateIntervalUnits`指定是否`UpdateInterval`值是以小时、 天或周为单位。  
  
-   `UpdateUrl`（未显示） 是应用程序将从其接收更新的位置。 如果指定，则此值插入应用程序清单。  
  
-   在中设置以下属性**发布选项**对话框中，从访问**发布**页。  
  
-   `PublisherName`指定在安装或运行应用程序时显示的提示中显示发布服务器的名称。 对于已安装的应用程序，它还用于在指定的文件夹名称**启动**菜单。  
  
-   `ProductName`指定在安装或运行应用程序时显示的提示中显示的产品的名称。 对于已安装的应用程序，它还用于在指定的快捷名称**启动**菜单。  
  
-   在中设置以下属性**先决条件**对话框中，从访问**发布**页。  
  
-   `BootstrapperEnabled`确定是否生成的 setup.exe 引导。  
  
-   `IsWebBootstrapper`确定 setup.exe 引导程序是否可以通过 Web 或基于磁盘的方式。  
  
## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL、 SupportUrl、 PublishURL 和 UpdateURL  
 下表显示 ClickOnce 部署的四个 URL 选项。  
  
|URL 选项|描述|  
|----------------|-----------------|  
|`PublishURL`|所需发布 ClickOnce 应用程序到网站。|  
|`InstallURL`|可选。 设置此 URL 选项，则不同于安装站点时`PublishURL`。 例如，你可以设置`PublishURL`到一个 FTP 路径和一组`InstallURL`到 Web URL。|  
|`SupportURL`|可选。 如果支持站点位于不同设置此 URL 选项`PublishURL`。 例如，你可以设置`SupportURL`公司的客户技术支持网站。|  
|`UpdateURL`|可选。 设置此 URL 选项，则更新位置不同于时`InstallURL`。 例如，你可以设置`PublishURL`到一个 FTP 路径和一组`UpdateURL`到 Web URL。|  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.Build.Tasks.GenerateBootstrapper>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>   
 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>   
 [ClickOnce 安全和部署](../deployment/clickonce-security-and-deployment.md)   
 [演练：手动部署 ClickOnce 应用程序](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)