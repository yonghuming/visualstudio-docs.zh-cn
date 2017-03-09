---
title: "演练：手动部署 ClickOnce 应用程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
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
  - "ClickOnce 部署, 手动"
  - "ClickOnce 部署, SDK 工具"
  - "部署应用程序 [ClickOnce], 手动 ClickOnce 部署"
  - "Mage.exe, 手动 ClickOnce 部署"
  - "MageUI.exe, 手动 ClickOnce 部署"
  - "清单 [ClickOnce]"
  - "手动 ClickOnce 部署"
ms.assetid: ccee6551-a1b9-4ca2-8845-9c1cf4ac2560
caps.latest.revision: 49
caps.handback.revision: 47
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 演练：手动部署 ClickOnce 应用程序
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果您无法使用 Visual Studio 来部署 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序，或者是需要使用高级部署功能（如受信任的应用程序部署），则应使用 Mage.exe 命令行工具来创建 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 清单。  此演练说明如何使用清单生成和编辑工具的命令行版本 \(Mage.exe\) 或图形版本 \(MageUI.exe\) 来创建 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署。  
  
## 系统必备  
 在本演练中，生成部署之前，您需要选择一些系统必备组件和选项。  
  
-   安装 Mage.exe 和 MageUI.exe。  
  
     Mage.exe 和 MageUI.exe 是 [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] 的一部分。  您必须已安装 [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)]，或者拥有 Visual Studio 随附的 [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] 版本。  有关更多信息，请参见 MSDN 上的 [Windows SDK](http://go.microsoft.com/fwlink/?LinkId=158044)。  
  
-   提供要部署的应用程序。  
  
     本演练假设您有一个已准备好要部署的 Windows 应用程序。  此应用程序将称为“AppToDeploy”。  
  
-   确定部署的分发方式。  
  
     分发选项包括：Web、文件共享或 CD。  有关更多信息，请参见 [ClickOnce 安全和部署](../deployment/clickonce-security-and-deployment.md)。  
  
-   确定应用程序是否需要提升的信任级别。  
  
     如果应用程序需要完全信任（例如，对用户系统的完全访问权限），可以使用 Mage.exe 的 `-TrustLevel` 选项进行此设置。  如果要为应用程序定义自定义的权限集，可以使用文本编辑器或 MageUI.exe 从其他清单复制 Internet 或 Intranet 权限部分，根据需要对其进行修改，然后将其添加到应用程序清单中。  有关更多信息，请参见[受信任的应用程序部署概述](../deployment/trusted-application-deployment-overview.md)。  
  
-   获取 Authenticode 证书。  
  
     应使用 Authenticode 证书为部署签名。  可使用 Visual Studio、MageUI.exe 或 MakeCert.exe 和 Pvk2Pfx.exe 工具生成测试证书，也可以从证书颁发机构 \(CA\) 获取证书。  如果选择使用“受信任的应用程序部署”，还必须将证书一次性安装到所有客户端计算机上。  有关更多信息，请参见[受信任的应用程序部署概述](../deployment/trusted-application-deployment-overview.md)。  
  
-   确保应用程序的清单不具有 UAC 信息。  
  
     您需要确定应用程序包含的清单是否具有用户帐户控制 \(UAC\) 信息，如 `<dependentAssembly>` 元素。  若要检查应用程序清单，可使用 Windows Sysinternals [Sigcheck](http://go.microsoft.com/fwlink/?LinkId=158035) 实用工具。  
  
     如果应用程序包含的清单具有 UAC 详细信息，则必须重新生成不带 UAC 信息的清单。  对于 Visual Studio 中的 C\# 项目，请打开项目属性，选择“应用程序”选项卡。  在**“清单”**下拉列表中，选择**“创建不带清单的应用程序”**。  对于 Visual Studio 中的 Visual Basic 项目，请打开项目属性，选择“应用程序”选项卡，然后单击**“查看 UAC 设置”**。  在打开的清单文件中，删除那个 `<asmv1:assembly>` 元素内的所有元素。  
  
-   确定应用程序在客户端计算机上是否有系统必备组件要求。  
  
     对于从 Visual Studio 中部署的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序，可在部署中包含系统必备组件的安装引导程序 \(setup.exe\)。  本演练创建 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署所需的两个清单。  系统必备组件引导程序可使用 [GenerateBootstrapper 任务](../msbuild/generatebootstrapper-task.md)来创建。  
  
### 使用 Mage.exe 命令行工具部署应用程序  
  
1.  创建用于存储 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署文件的目录。  
  
2.  在刚创建的部署目录中，创建一个版本子目录。  如果这是首次部署应用程序，请将该版本子目录命名为 1.0.0.0。  
  
    > [!NOTE]
    >  部署的版本可以与应用程序的版本不同。  
  
3.  将所有应用程序文件（包括可执行文件、程序集、资源和数据文件）全部复制到该版本子目录中。  如有必要，可以创建包含其他文件的其他子目录。  
  
4.  打开 [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] 或 Visual Studio 命令提示，切换到该版本子目录。  
  
5.  调用 Mage.exe，创建应用程序清单。  以下语句为编译为在 Intel x86 处理器上运行的代码创建应用程序清单。  
  
    ```  
    mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .   
    ```  
  
    > [!NOTE]
    >  请确保在 `-FromDirectory` 选项后包括点 \(.\)，用于指示当前目录。  如果不包括句点，则必须指定应用程序文件的路径。  
  
6.  使用 Authenticode 证书为应用程序清单签名。  用证书文件的路径替换 *mycert.pfx*。  用您证书文件的密码替换*密码*。  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd  
    ```  
  
7.  切换到部署目录的根目录。  
  
8.  通过调用 Mage.exe 生成部署清单。  默认情况下，Mage.exe 会将 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署标记为已安装的应用程序，以便它既可以联机运行又可以脱机运行。  若要使应用程序仅当用户联机时可用，请使用值为 `false` 的 `-Install` 选项。  如果使用默认值，且用户将通过网站或文件共享来安装您的应用程序，请确保 `-ProviderUrl` 选项的值指向应用程序清单在 Web 服务器或共享上的位置。  
  
    ```  
    mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application  
    ```  
  
9. 使用 Authenticode 证书为部署清单签名。  
  
    ```  
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd  
    ```  
  
10. 将部署目录中的所有文件都复制到部署目标或媒体。  这可以是网站或 FTP 站点上的文件夹、文件共享或 CD\-ROM。  
  
11. 为用户提供安装应用程序所需的 URL、UNC 或物理媒体。  如果提供 URL 或 UNC，则必须为用户提供完整的部署清单路径。  例如，如果 AppToDeploy 将会部署到 http:\/\/webserver01\/ 中的 AppToDeploy 目录，则完整的 URL 路径应为 http:\/\/webserver01\/AppToDeploy\/AppToDeploy.application。  
  
### 使用 MageUI.exe 图形工具部署应用程序  
  
1.  创建用于存储 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署文件的目录。  
  
2.  在刚创建的部署目录中，创建一个版本子目录。  如果这是首次部署应用程序，请将该版本子目录命名为 1.0.0.0。  
  
    > [!NOTE]
    >  部署的版本可能与应用程序的版本不同。  
  
3.  将所有应用程序文件（包括可执行文件、程序集、资源和数据文件）全部复制到该版本子目录中。  如有必要，可以创建包含其他文件的其他子目录。  
  
4.  启动图形工具 MageUI.exe。  
  
    ```  
    MageUI.exe  
    ```  
  
5.  从菜单中依次选择**“文件”**、**“新建”**和**“应用程序清单”**，创建一个新的应用程序清单。  
  
6.  在默认的**“名称”**选项卡中，键入此部署的名称和版本号。  此外，指定生成应用程序时针对的**“处理器”**，如 x86。  
  
7.  选择**“文件”**选项卡，然后单击**“应用程序目录”**文本框旁边的省略号（**“...”**）按钮。  随即将显示“浏览文件夹”对话框。  
  
8.  选择包含应用程序文件的版本子目录，然后单击**“确定”**。  
  
9. 如果将从 Internet Information Services \(IIS\) 进行部署，请选中**“填充时为没有 .deploy 扩展名的任何文件添加该扩展名”**复选框。  
  
10. 单击**“填充”**按钮，向文件列表中添加所有应用程序文件。  如果应用程序包含多个可执行文件，可以从**“文件类型”**下拉列表中选择**“入口点”**，将此部署的主可执行文件标记为启动应用程序。  如果应用程序只包含一个可执行文件，MageUI.exe 将为您标记该文件。  
  
11. 选择**“需要权限”**选项卡，然后选择需要让应用程序断言的信任级别。  默认级别为**“完全信任”**，这适用于大多数应用程序。  
  
12. 从菜单中选择**文件**，然后选择**另存为**。  将出现“签名选项”对话框，提示您为应用程序清单签名。  
  
13. 如果已将证书作为文件存储在文件系统上，请使用**“使用证书文件签名”**选项，然后使用省略号（**“...”**）按钮从文件系统中选择证书。  然后，键入证书密码。  
  
     \- 或 \-  
  
     如果证书保存在可从计算机上访问的证书存储区中，请选择**“使用存储的证书签名”**选项，然后从提供的列表中选择证书。  
  
14. 单击**“确定”**，为应用程序清单签名。  将出现“另存为”对话框。  
  
15. 在“另存为”对话框中，指定版本目录，然后单击**“保存”**。  
  
16. 从菜单中依次选择**“文件”**、**“新建”**和**“部署清单”**，创建部署清单。  
  
17. 在**“名称”**选项卡上，为此部署指定名称和版本号（在本示例中为 1.0.0.0）。  此外，指定生成应用程序时针对的**“处理器”**，如 x86。  
  
18. 选择**“说明”**选项卡，为**“发布者”**和**“产品”**指定值。  其中**“产品”**是应用程序安装在客户端计算机上供脱机使用时，Windows“开始”菜单上给出的应用程序名称。  
  
19. 选择**“部署选项”**选项卡，在**“启动位置”**文本框中，指定应用程序清单在 Web 服务器或共享上的位置。  例如，\\\\myServer\\myShare\\AppToDeploy.application。  
  
20. 如果在上一步添加了 .deploy 扩展名，则在此还应选择**使用 .deploy 文件扩展名**。  
  
21. 选择**“更新选项”**选项卡，指定此应用程序的更新频率。  如果应用程序通过 <xref:System.Deployment.Application.UpdateCheckInfo> 自行检查更新，请清除**“此应用程序应检查更新”**复选框。  
  
22. 选择**“应用程序引用”**选项卡，然后单击**“选择清单”**按钮。  将出现一个“打开”对话框。  
  
23. 选择之前创建的应用程序清单，然后单击**“打开”**。  
  
24. 从菜单中选择**文件**，然后选择**另存为**。  将出现“签名选项”对话框，提示您为部署清单签名。  
  
25. 如果已将证书作为文件存储在文件系统上，请使用**“使用证书文件签名”**选项，然后使用省略号（**“...”**）按钮从文件系统中选择证书。  然后，键入证书密码。  
  
     \- 或 \-  
  
     如果证书保存在可从计算机上访问的证书存储区中，请选择**“使用存储的证书签名”**选项，然后从提供的列表中选择证书。  
  
26. 单击**“确定”**，为部署清单签名。  将出现“另存为”对话框。  
  
27. 在**“另存为”**对话框中，上移一级目录，转至部署的根位置，然后单击**“保存”**。  
  
28. 将部署目录中的所有文件都复制到部署目标或媒体。  这可以是网站或 FTP 站点上的文件夹、文件共享或 CD\-ROM。  
  
29. 为用户提供安装应用程序所需的 URL、UNC 或物理媒体。  如果提供 URL 或 UNC，则必须为用户提供完整的部署清单路径。  例如，如果 AppToDeploy 将会部署到 http:\/\/webserver01\/ 中的 AppToDeploy 目录，则完整的 URL 路径应为 http:\/\/webserver01\/AppToDeploy\/AppToDeploy.application。  
  
## 后续步骤  
 在需要部署应用程序的新版本时，请新建一个以新版本命名的目录（例如，1.0.0.1），然后将新应用程序文件复制到新目录中。  随后，您需要按照前面的步骤，创建新应用程序清单并为其签名，更新部署清单并为其签名。  请注意，应在 Mage.exe `-New` 调用和 `–Update` 调用中指定同一较高版本，因为 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 仅更新较高的版本，以最左面的整数为最高有效位。  如果您使用 MageUI.exe，则可以按以下方法更新部署清单：打开清单，选择**“应用程序引用”**选项卡，单击**“选择清单”**按钮，然后选择更新后的应用程序清单。  
  
## 请参阅  
 [Mage.exe（清单生成和编辑工具）](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [MageUI.exe（图形化客户端中的清单生成和编辑工具）](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)   
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)   
 [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)   
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)