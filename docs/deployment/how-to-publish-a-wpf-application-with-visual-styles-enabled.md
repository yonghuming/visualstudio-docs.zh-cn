---
title: "如何： 发布启用了视觉样式的 WPF 应用程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: acef07cd95395312d1456401bd58142264d89794
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-publish-a-wpf-application-with-visual-styles-enabled"></a>如何：发布启用了视觉样式的 WPF 应用程序
视觉样式启用公共控件，若要更改根据用户所选择的主题的外观。 默认情况下，视觉样式不会启用 Windows Presentation Foundation (WPF) 应用程序，因此你必须手动启用它们。 但是，启用一个 WPF 应用程序的可视样式，然后发布该解决方案将导致错误。 本主题介绍如何解决此错误以及发布启用了视觉样式的 WPF 应用程序的过程。 关于视觉样式的详细信息，请参阅[视觉样式概览](http://msdn.microsoft.com/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e)。 有关错误消息的详细信息，请参阅[疑难解答 ClickOnce 部署中的特定错误](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)。  
  
 若要解决该错误并发布解决方案，你必须执行以下任务：  
  
-   [发布解决方案，而无需启用视觉样式](#BKMK_publishsolwovs)。  
  
-   [创建清单文件](#BKMK_CreateManifest)。  
  
-   [清单文件嵌入到已发布解决方案的可执行文件](#BKMK_embedmanifest)。  
  
-   [应用程序和部署清单签名](#BKMK_signappdeplyman)。  
  
 然后，你可以将已发布的文件移动到要从中安装应用程序的最终用户的位置。  
  
##  <a name="BKMK_publishsolwovs"></a>发布解决方案，而无需启用视觉样式  
  
1.  确保你的项目不具有启用视觉样式。 下面的 XML，首先，检查你的项目的清单文件。 然后，如果存在 XML，则请将带注释标记的 XML。  
  
     默认情况下，不启用视觉样式。  
  
    ```  
    <dependency>    <dependentAssembly>      <assemblyIdentity          type="win32"          name="Microsoft.Windows.Common-Controls"          version="6.0.0.0"          processorArchitecture="*"          publicKeyToken="6595b64144ccf1df"          language="*"        />    </dependentAssembly>  </dependency>  
    ```  
  
     下面的过程演示如何打开与你的项目关联的清单文件。  
  
    ###### <a name="to-open-the-manifest-file-in-a-visual-basic-project"></a>若要在 Visual Basic 项目中打开清单文件  
  
    1.  在菜单栏上，选择**项目**， *ProjectName***属性**，其中*ProjectName*是 WPF 项目的名称。  
  
         显示你的 WPF 项目的属性页。  
  
    2.  上**应用程序**选项卡上，选择**查看 Windows 设置**。  
  
         在中打开应用程序清单文件**代码编辑器**。  
  
    ###### <a name="to-open-the-manifest-file-in-a-c-project"></a>若要在 C# 项目中打开清单文件  
  
    1.  在菜单栏上，选择**项目**， *ProjectName***属性**，其中*ProjectName*是 WPF 项目的名称。  
  
         显示你的 WPF 项目的属性页。  
  
    2.  上**应用程序**选项卡上，记下显示在清单字段的名称。 这是与你的项目相关联的清单名称。  
  
        > [!NOTE]
        >  如果**使用默认设置嵌入清单**或**创建应用程序而无需清单**出现在清单的字段中，不启用了可视样式。 如果清单文件的名称出现在清单字段，则继续执行此过程的下一步。  
  
    3.  在**解决方案资源管理器**，选择**显示所有文件**（)。  
  
         此按钮会显示所有项目项，其中包括已排除以及通常处于隐藏状态。 该清单文件将显示作为项目项。  
  
2.  生成并发布你的解决方案。 有关如何发布解决方案的详细信息，请参阅[如何： 发布 ClickOnce 应用程序使用发布向导](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)。  
  
##  <a name="BKMK_CreateManifest"></a>创建清单文件  
  
1.  将下面的 XML 粘贴到记事本文件。  
  
     此 XML 描述包含支持视觉样式的控件的程序集。  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?><asmv1:assembly manifestVersion="1.0"                xmlns="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"                xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  <dependency>    <dependentAssembly>      <assemblyIdentity        type="win32"        name="Microsoft.Windows.Common-Controls"        version="6.0.0.0"        processorArchitecture="*"        publicKeyToken="6595b64144ccf1df"        language="*"        />    </dependentAssembly>  </dependency></asmv1:assembly>  
    ```  
  
2.  在记事本中，单击**文件**，然后单击**另存为**。  
  
3.  在**另存为**对话框中，在**另存为类型**下拉列表中，选择**所有文件**。  
  
4.  在**文件名**框中，命名该文件，追加**.manifest**到的文件名称的末尾。 例如： **themes.manifest**。  
  
5.  选择**浏览文件夹**按钮，选择任意文件夹，然后单击**保存**。  
  
    > [!NOTE]
    >  剩余步骤假定此文件的名称是**themes.manifest**和文件保存到 C:\temp 目录在你的计算机上。  
  
##  <a name="BKMK_embedmanifest"></a>清单文件嵌入到已发布解决方案的可执行文件  
  
1.  打开**Visual Studio 命令提示**。  
  
     有关如何打开详细信息**Visual Studio 命令提示符**，请参阅[命令提示](/dotnet/framework/tools/developer-command-prompt-for-vs)。  
  
    > [!NOTE]
    >  其余步骤作出下列假设有关你的解决方案：  
    >   
    >  -   解决方案的名称是**MyWPFProject**。  
    > -   解决方案位于以下目录： `%UserProfile%\Documents\Visual Studio 2010\Projects\`。  
    >   
    >      解决方案发布到以下目录： `%UserProfile%\Documents\Visual Studio 2010\Projects\publish`。  
    > -   发布的应用程序文件的最新版本位于以下目录：`%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`  
    >   
    >  无需使用的名称或上面所述的目录位置。 名称和位置上面所述仅用于说明发布你的解决方案所需的步骤。  
  
2.  在命令提示符下，将更改为包含已发布的应用程序文件的最新版本的目录的路径。 下面的示例演示此步骤。  
  
    ```  
    cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"  
    ```  
  
3.  在命令提示符下运行以下命令以将清单文件嵌入到应用程序的可执行文件。  
  
    ```  
    mt -manifest c:\temp\themes.manifest -outputresource:MyWPFApp.exe.deploy  
    ```  
  
##  <a name="BKMK_signappdeplyman"></a>应用程序和部署清单签名  
  
1.  在命令提示符处，运行以下命令以删除`.deploy`从当前目录中的可执行文件的扩展。  
  
    ```  
    ren MyWPFApp.exe.deploy MyWPFApp.exe  
    ```  
  
    > [!NOTE]
    >  此示例假定该只有一个文件具有`.deploy`文件扩展名。 请确保您重命名此目录中具有的所有文件`.deploy`文件扩展名。  
  
2.  在命令提示符下运行以下命令以对应用程序清单进行签名。  
  
    ```  
    mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
    ```  
  
    > [!NOTE]
    >  此示例假定你对清单签名使用`.pfx`项目文件。 如果不签名的清单，则可以省略`-cf`此示例中使用的参数。 如果你使用签名的清单需要密码的证书，指定`-password`选项 (`For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password`)。  
  
3.  在命令提示符处，运行以下命令以添加`.deploy`扩展到你在此过程的上一步中重命名文件的名称。  
  
    ```  
    ren MyWPFApp.exe MyWPFApp.exe.deploy  
    ```  
  
    > [!NOTE]
    >  此示例假定该只有一个文件具有`.deploy`文件扩展名。 请确保您重命名以前此目录中的所有文件`.deploy`文件扩展名。  
  
4.  在命令提示符下运行以下命令以对部署清单进行签名。  
  
    ```  
    mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
    ```  
  
    > [!NOTE]
    >  此示例假定你对清单签名使用`.pfx`项目文件。 如果不签名的清单，则可以省略`-cf`此示例中使用的参数。 如果你使用签名的清单需要密码的证书，指定`-password`选项，如此示例所示：`For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password`。  
  
 执行这些步骤之后，你可以将已发布的文件移动到要从中安装应用程序的最终用户的位置。 如果你想要经常更新解决方案，可以将这些命令移到一个脚本，并运行该脚本每次发布新版本。  
  
## <a name="see-also"></a>另请参阅  
 [ClickOnce 部署中的特定错误的疑难解答](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)   
 [视觉样式概述](http://msdn.microsoft.com/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e)   
 [启用视觉样式](https://msdn.microsoft.com/library/bb773175.aspx)   
 [命令提示](/dotnet/framework/tools/developer-command-prompt-for-vs)