---
title: "演练： 手动部署 ClickOnce 应用程序 |Microsoft 文档"
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
- Mage.exe, manual ClickOnce deployments
- MageUI.exe, manual ClickOnce deployments
- deploying applications [ClickOnce], manual ClickOnce deployments
- ClickOnce deployment, manually
- ClickOnce deployment, SDK tools
- manual ClickOnce deployments
- manifests [ClickOnce]
ms.assetid: ccee6551-a1b9-4ca2-8845-9c1cf4ac2560
caps.latest.revision: "49"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 10f99d620060245fd7dac4e2420216a23d068a83
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="walkthrough-manually-deploying-a-clickonce-application"></a>演练：手动部署 ClickOnce 应用程序
如果你不能使用 Visual Studio 部署你[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序，或你需要使用高级的部署功能，如受信任的应用程序部署，你应使用 Mage.exe 命令行工具来创建你[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]清单。 本演练介绍如何创建[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]通过使用命令行版本 (Mage.exe) 或清单生成和编辑工具的图形版本 (MageUI.exe) 部署。  
  
## <a name="prerequisites"></a>先决条件  
 本演练具有一些先决条件和需要生成部署之前选择的选项。  
  
-   安装 Mage.exe 和 MageUI.exe。  
  
     Mage.exe 和 MageUI.exe 是的一部分[!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]。 您必须具有[!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)]安装的版本或[!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)]Visual Studio 所含的。 有关详细信息，请参阅[Windows SDK](http://go.microsoft.com/fwlink/?LinkId=158044) MSDN 上。  
  
-   提供要部署应用程序。  
  
     本演练假定你就可以部署一个 Windows 应用程序。 此应用程序称为 AppToDeploy。  
  
-   确定如何将分布式部署。  
  
     分发选项包括： Web、 文件共享或 CD。 有关详细信息，请参阅 [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md)。  
  
-   确定应用程序是否需要提升的信任级别。  
  
     如果你的应用程序需要完全信任 — 例如，完全访问权限用户的系统-你可以使用`-TrustLevel`Mage.exe 若要设置此选项。 如果你想要定义你的应用程序设置的自定义权限，你可以从另一个清单复制 Internet 或 intranet 的权限部分、 修改它以满足你的需求，并将其添加到应用程序清单使用文本编辑器或 MageUI.exe。 有关详细信息，请参阅 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)。  
  
-   获取一个验证码证书。  
  
     你应注册你的部署使用验证码证书。 你可以通过使用 Visual Studio、 MageUI.exe 中，或 MakeCert.exe 和 Pvk2Pfx.exe 工具生成测试证书，或可以从证书颁发机构 (CA) 获取证书。 如果你选择使用受信任的应用程序部署，您还必须执行的一次性安装到所有客户端计算机上的证书。 有关详细信息，请参阅 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)。  
  
    > [!NOTE]
    >  你可以注册你的部署使用可以从证书颁发机构获取的 CNG 证书。  
  
-   请确保应用程序没有使用 UAC 信息对清单。  
  
     你需要确定你的应用程序是否包含与用户帐户控制 (UAC) 信息清单，如`<dependentAssembly>`元素。 若要检查应用程序清单，你可以使用 Windows Sysinternals [Sigcheck](http://go.microsoft.com/fwlink/?LinkId=158035)实用程序。  
  
     如果你的应用程序包含具有 UAC 详细信息清单，你必须重新生成不带 UAC 信息。 对于 C# 项目在 Visual Studio 中，打开项目属性并选择应用程序选项卡。在**清单**下拉列表中，选择**创建不带清单的应用程序**。 对于 Visual Studio 中 Visual Basic 项目，打开项目属性，选择应用程序选项卡，然后单击**视图 UAC 设置**。 在打开清单文件中，删除单个中的所有元素`<asmv1:assembly>`元素。  
  
-   确定应用程序是否需要客户端计算机上的系统必备组件。  
  
     [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]从 Visual Studio 部署的应用程序可以包括与部署的系统必备组件安装引导程序 (setup.exe)。 本演练将创建所需的两个清单[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署。 你可以通过创建系统必备组件引导[GenerateBootstrapper 任务](../msbuild/generatebootstrapper-task.md)。  
  
### <a name="to-deploy-an-application-with-the-mageexe-command-line-tool"></a>部署应用程序使用 Mage.exe 命令行工具  
  
1.  创建一个目录将在其中存储你[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署文件。  
  
2.  在部署目录中你刚刚创建，创建一个版本子目录。 如果这是首次部署应用程序，该版本子目录命名**1.0.0.0**。  
  
    > [!NOTE]
    >  你的部署的版本可以不同于你的应用程序的版本。  
  
3.  将所有应用程序文件复制到的版本的子目录，包括可执行文件、 程序集、 资源和数据文件。 如有必要，你可以创建其他包含其他文件的子目录。  
  
4.  打开[!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)]或 Visual Studio 命令提示并将更改为版本子目录。  
  
5.  通过调用 Mage.exe 创建应用程序清单。 下面的语句创建代码编译为在 Intel x86 处理器上运行应用程序的清单。  
  
    ```  
    mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .   
    ```  
  
    > [!NOTE]
    >  请务必包括句点 （.） 后`-FromDirectory`选项，它指示当前目录。 如果不包括该点，必须到你的应用程序文件指定的路径。  
  
6.  使用验证码证书的应用程序清单进行签名。 替换*mycert.pfx*替换为您的证书文件的路径。 替换*passwd*替换为您的证书文件的密码。  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd  
    ```  
  
     若要登录的 CNG 证书与应用程序清单，使用以下命令。 替换*cngCert.pfx*替换为您的证书文件的路径。  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile cngCert.pfx  
    ```  
  
7.  将更改为部署目录的根目录。  
  
8.  生成部署清单，mage.exe 的调用。 默认情况下，Mage.exe 会将标记你[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]作为安装应用程序，以便它可以同时在线运行和脱机状态的部署。 若要使应用程序可用，仅当用户处于联机状态时，使用`-Install`选项中包含的值`false`。 如果你使用默认值，并且用户从网站或文件共享安装你的应用程序，请确保值`-ProviderUrl`应用程序的位置的选项指向清单在 Web 服务器或共享上。  
  
    ```  
    mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application  
    ```  
  
9. 使用验证码或 CNG 证书的部署清单进行签名。  
  
    ```  
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd  
    ```  
  
     或  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile cngCert.pfx  
    ```  
  
10. 将在部署目录中的所有文件复制到部署目标地址或媒体中。 这可能是网站或 FTP 站点、 文件共享或 CD-ROM 上的任一的文件夹。  
  
11. 为用户提供 URL、 UNC 或安装你的应用程序所需的物理介质。 如果你提供 URL 或 UNC，则必须为你的用户的完整路径向部署清单。 例如，如果 AppToDeploy 部署到 http://webserver01/ AppToDeploy 目录中，完整的 URL 路径将为 http://webserver01/AppToDeploy/AppToDeploy.application。  
  
### <a name="to-deploy-an-application-with-the-mageuiexe-graphical-tool"></a>若要部署的应用程序 MageUI.exe 图形工具  
  
1.  创建一个目录将在其中存储你[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署文件。  
  
2.  在部署目录中你刚刚创建，创建一个版本子目录。 如果这是首次部署应用程序，该版本子目录命名**1.0.0.0**。  
  
    > [!NOTE]
    >  你的版本是部署的可能不同于你的应用程序的版本。  
  
3.  将所有应用程序文件复制到的版本的子目录，包括可执行文件、 程序集、 资源和数据文件。 如有必要，你可以创建其他包含其他文件的子目录。  
  
4.  启动 MageUI.exe 图形工具。  
  
    ```  
    MageUI.exe  
    ```  
  
5.  通过选择创建一个新的应用程序清单**文件**，**新建**，**应用程序清单**从菜单。  
  
6.  默认值上**名称**选项卡上，键入此部署的名称和版本数。 此外指定**处理器**，如 x86 生成应用程序。  
  
7.  选择**文件**选项卡，然后单击省略号 (**...**) 按钮旁边**应用程序目录**文本框。 浏览文件夹对话框。  
  
8.  选择包含你的应用程序文件，该版本子目录，然后单击**确定**。  
  
9. 如果你将部署从 Internet 信息服务 (IIS) 中，选择**时填充将.deploy 扩展名添加到不具有任何文件**复选框。  
  
10. 单击**填充**按钮以将所有应用程序文件添加到文件列表。 如果你的应用程序包含多个可执行文件，通过选择标记为启动应用此部署的主要可执行文件**入口点**从**文件类型**下拉列表。 （如果你的应用程序包含一个可执行文件，MageUI.exe 将将其标记为你。）  
  
11. 选择**所需权限**选项卡上，然后选择需要你的应用程序要断言的信任级别。 默认值是**FullTrust**，它将是适用于大多数应用程序。  
  
12. 选择**文件**，**另存为**从菜单。 签名选项对话框显示提示您对应用程序清单进行签名。  
  
13. 如果必须将证书作为文件系统上的文件存储，使用**使用证书文件签名**选项，然后从文件系统的证书选择使用的省略号 (**...**) 按钮。 然后键入您证书的密码。  
  
     - 或 -  
  
     如果你的证书保存在证书存储区可从你的计算机访问，请选择**使用存储的证书进行签名**选项，然后从提供的列表中选择的证书。  
  
14. 单击**确定**应用程序清单进行签名。 将出现另存为对话框。  
  
15. 在另存为对话框中，指定的版本目录中，，然后单击**保存**。  
  
16. 选择**文件**，**新建**，**部署清单**从菜单以创建部署清单。  
  
17. 上**名称**选项卡上，指定此部署的名称和版本编号 (**1.0.0.0**在此示例中)。 此外指定**处理器**，如 x86 生成应用程序。  
  
18. 选择**说明**选项卡，并为指定值**发布服务器**和**产品 * * * t**。 (**产品**是在脱机使用的客户端计算机上安装你的应用程序时提供到 Windows 开始菜单上的应用程序的名称。)  
  
19. 选择**部署选项**选项卡上，然后在**启动位置**文本框中，指定 Web 服务器或共享上的应用程序清单的位置。 例如， \\\myServer\myShare\AppToDeploy.application。  
  
20. 如果你在上一步中添加.deploy 扩展名，则还要选择**使用.deploy 文件扩展名**此处。  
  
21. 选择**更新选项**选项卡，然后指定此应用程序的更新频率。 如果你的应用程序使用<xref:System.Deployment.Application.UpdateCheckInfo>若要检查更新自身，清除**此应用程序应检查更新**复选框。  
  
22. 选择**应用程序引用**选项卡，然后单击**选择清单**按钮。 将显示打开的对话框。  
  
23. 选择前面创建的应用程序清单，然后单击**打开**。  
  
24. 选择**文件**，**另存为**从菜单。 签名选项对话框将显示提示您为部署清单签名。  
  
25. 如果必须将证书作为文件系统上的文件存储，使用**使用证书文件签名**选项，然后从文件系统的证书选择使用的省略号 (**...**) 按钮。 然后键入您证书的密码。  
  
     - 或 -  
  
     如果你的证书保存在证书存储区可从你的计算机访问，请选择**使用存储的证书进行签名**选项，然后从提供的列表中选择的证书。  
  
26. 单击**确定**部署清单进行签名。 将出现另存为对话框。  
  
27. 在**另存为**对话框中，你的部署，然后单击根上移一个目录**保存**。  
  
28. 将在部署目录中的所有文件复制到部署目标地址或媒体中。 这可能是网站或 FTP 站点、 文件共享或 CD-ROM 上的任一的文件夹。  
  
29. 为用户提供 URL、 UNC 或安装你的应用程序所需的物理介质。 如果你提供 URL 或 UNC，则必须为你的用户部署清单的完整路径。 例如，如果 AppToDeploy 部署到 http://webserver01/ AppToDeploy 目录中，完整的 URL 路径将为 http://webserver01/AppToDeploy/AppToDeploy.application。  
  
## <a name="next-steps"></a>后续步骤  
 当你需要部署应用程序的新版本时，创建一个名为的新版本的新目录-例如，1.0.0.1—and 将新的应用程序文件复制到新的目录。 接下来，你需要按照前面的步骤以创建和注册一个新的应用程序清单，并更新以及部署清单进行签名。 请注意，在这两个在 Mage.exe 中指定相同的更高版本`-New`和`-Update`调用，作为[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]仅使用最重要的最左边的整数中更新更高版本。 如果你使用 MageUI.exe，你可以更新部署清单通过打开它，选择**应用程序引用**选项卡上，单击**选择清单**按钮，，然后选择已更新应用程序清单。  
  
## <a name="see-also"></a>另请参阅  
 [Mage.exe（清单生成和编辑工具）](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe（图形化客户端中的清单生成和编辑工具）](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)   
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)   
 [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)   
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)