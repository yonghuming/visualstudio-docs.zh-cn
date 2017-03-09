---
title: "演练：手动部署不需要重新签名并且保留署名信息的 ClickOnce 应用程序 | Microsoft Docs"
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
  - "品牌"
  - "ClickOnce 应用程序, 他方部署"
  - "ClickOnce 部署, 手动"
  - "ClickOnce 部署, SDK 工具"
  - "客户部署"
  - "清单 [ClickOnce]"
  - "手动 ClickOnce 部署"
  - "多个 ClickOnce 部署和品牌"
  - "保留的品牌信息"
ms.assetid: c21822fb-d4ee-42e4-b72d-41ee9786efe5
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 演练：手动部署不需要重新签名并且保留署名信息的 ClickOnce 应用程序
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在您创建 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序然后将其提供给客户来发布和部署时，客户通常必须更新部署清单并对其重新签名。虽然在大多数情况下这仍是首选方法，但是 .NET Framework 3.5 使您能够在无需重新生成新部署清单的情况下创建由客户部署的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署。  有关更多信息，请参见[在不重新签名的情况下为测试服务器和生产服务器部署 ClickOnce 应用程序](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md)。  
  
 当您创建一个 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序，然后将它提供给客户进行发布和部署时，该应用程序可以使用客户的署名，也可以保留您的署名。  例如，如果该应用程序是一个私有应用程序，您可能要保留您的署名。  如果该应用程序是一个针对每个客户高度自定义的应用程序，您可能要使用客户的署名。  当您将应用程序提供给某个组织进行部署时，.NET Framework 3.5 允许您保留您的署名、发行者信息和安全签名。  有关更多信息，请参见[创建供其他人部署的 ClickOnce 应用程序](../deployment/creating-clickonce-applications-for-others-to-deploy.md)。  
  
> [!NOTE]
>  在本演练中，您将通过使用命令行工具 Mage.exe 或图形工具 MageUI.exe 手动创建部署。  有关手动部署的更多信息，请参见[演练：手动部署 ClickOnce 应用程序](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。  
  
## 系统必备  
 若要执行本演练中的步骤，您需要：  
  
-   您准备部署的 Windows 窗体应用程序。  此应用程序将被称为 WindowsFormsApp1。  
  
-   Visual Studio 或 Windows SDK。  
  
### 使用 Mage.exe 部署具有多重部署和署名支持的 ClickOnce 应用程序  
  
1.  打开一个 Visual Studio 命令提示符或 [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] 命令提示符，并转到将要在其中存储 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 文件的目录。  
  
2.  创建一个目录，该目录以部署的当前版本命名。  如果这是首次部署应用程序，则可以选择 1.0.0.0。  
  
    > [!NOTE]
    >  部署的版本可能与应用程序文件的版本不同。  
  
3.  创建一个名为“bin”的子目录，将所有应用程序文件（包括可执行文件、程序集、资源和数据文件）全部复制到该目录中。  
  
4.  通过调用 Mage.exe 生成应用程序清单。  
  
    ```  
    mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"  
    ```  
  
5.  使用数字证书对应用程序清单进行签名。  
  
    ```  
    mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx  
    ```  
  
6.  通过调用 Mage.exe 生成部署清单。  默认情况下，Mage.exe 会将 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署标记为已安装的应用程序，以便它既可以联机运行又可以脱机运行。  若要使应用程序只在用户联机时可用，请使用值为 `f` 的 `-i` 参数。  由于此应用程序将利用多重部署功能，请排除 Mage.exe 的 `-providerUrl` 参数。  （在 3.5 版以前的 .NET Framework 版本中，对脱机应用程序排除 `-providerUrl` 将导致一个错误。）  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest   
    ```  
  
7.  不要对部署清单签名。  
  
8.  向将要在其网络上部署该应用程序的客户提供所有文件。  
  
9. 此时，客户必须使用他自己的自行生成的证书对部署清单签名。  例如，如果客户为 Adventure Works 公司工作，他可以使用 MakeCert.exe 工具生成一个自签名证书。  接着，使用 Pvk2pfx.exe 工具将 MakeCert.exe 创建的文件合并到可以传递给 Mage.exe 的 PFX 文件。  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
10. 接下来，客户使用此证书对部署清单签名。  
  
    ```  
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx  
    ```  
  
11. 客户为其用户部署该应用程序。  
  
### 使用 MageUI.exe 部署具有多重部署和署名支持的 ClickOnce 应用程序  
  
1.  打开一个 Visual Studio 命令提示符或 [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] 命令提示符，并导航到将要在其中存储 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 文件的目录。  
  
2.  创建一个名为“bin”的子目录，将所有应用程序文件（包括可执行文件、程序集、资源和数据文件）全部复制到该目录中。  
  
3.  创建一个子目录，该子目录以部署的当前版本命名。  如果这是首次部署应用程序，则可以选择 1.0.0.0。  
  
    > [!NOTE]
    >  部署的版本可能与应用程序文件的版本不同。  
  
4.  将 \\“bin”目录移到您在步骤 2 中创建的目录下。  
  
5.  启动图形工具 MageUI.exe。  
  
    ```  
    MageUI.exe  
    ```  
  
6.  从菜单中依次选择**“文件”**、**“新建”**和**“应用程序清单”**，创建一个新的应用程序清单。  
  
7.  在默认的**“名称”**选项卡中，输入此部署的名称和版本号。  并为**“发行者”**提供一个值，在部署应用程序时该值将作为“开始”菜单中该应用程序的快捷方式链接的文件夹名。  
  
8.  选择**“应用程序选项”**选项卡并单击**“将应用程序清单用于信任信息”**。  这将为此 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序启用第三方署名。  
  
9. 选择**“文件”**选项卡，然后单击“应用程序目录”文本框旁边的**“浏览”**按钮。  
  
10. 选择在步骤 2 中创建的包含应用程序文件的目录，然后在文件夹选择对话框中单击**“确定”**。  
  
11. 单击**“填充”**按钮，向文件列表中添加所有应用程序文件。  如果应用程序包含多个可执行文件，可以从**“文件类型”**下拉列表中选择**“入口点”**，将此部署的主可执行文件标记为启动应用程序。  （如果应用程序只包含一个可执行文件，MageUI.exe 将为您标记该文件）。  
  
12. 选择**“所需的权限”**选项卡，然后选择需要应用程序断言的信任级别。  默认级别为**“完全信任”**，此级别将适用于大多数应用程序。  
  
13. 从菜单中依次选择**“文件”**、**“保存”**，保存应用程序清单。  保存时，系统会提示您对应用程序清单进行签名。  
  
14. 如果已将证书作为文件存储在文件系统上，请使用**“作为证书文件签名”**选项，然后使用省略号（**“...”**）按钮从文件系统中选择证书。  
  
     \- 或 \-  
  
     如果证书保存在可通过您的计算机访问的证书存储区中，请选择**“使用存储的证书签名”**选项，再从提供的列表中选择证书。  
  
15. 从菜单中依次选择**“文件”**、**“新建”**和**“部署清单”**以创建部署清单，然后在**“名称”**选项卡上，提供名称和版本号（在此示例中为 1.0.0.0）。  
  
16. 切换到**“更新”**选项卡，指定此应用程序的更新频率。  如果应用程序使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署 API 自己检查更新，请清除标记为**“此应用程序应检查更新”**的复选框。  
  
17. 切换到**“应用程序引用”**选项卡。  通过单击**“选择清单”**按钮，然后选择在前面的步骤中创建的应用程序清单，可以预填充此选项卡中的所有值。  
  
18. 选择**“保存”**，将部署清单保存到磁盘。  保存时，系统会提示您对应用程序清单进行签名。  单击**“取消”**保存清单但不对它进行签名。  
  
19. 向客户提供所有应用程序文件。  
  
20. 此时，客户必须使用他自己的自行生成的证书对部署清单签名。  例如，如果客户为 Adventure Works 公司工作，他可以使用 MakeCert.exe 工具生成一个自签名证书。  接着，使用 Pvk2pfx.exe 工具将 MakeCert.exe 生成的文件合并到可以传递给 MageUI.exe 的 PFX 文件。  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
21. 生成证书后，客户此时可以通过在 MageUI.exe 中打开部署清单并保存它来对部署清单签名。  出现签名对话框后，客户选择**“作为证书文件签名”**选项，然后选择已经保存在磁盘上的 PFX 文件。  
  
22. 客户为其用户部署该应用程序。  
  
## 后续步骤  
  
## 请参阅  
 [Mage.exe（清单生成和编辑工具）](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [MageUI.exe（图形化客户端中的清单生成和编辑工具）](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)   
 [Makecert.exe（证书创建工具）](../Topic/Makecert.exe%20\(Certificate%20Creation%20Tool\).md)