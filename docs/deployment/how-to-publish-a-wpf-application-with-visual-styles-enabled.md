---
title: "如何：发布启用了视觉样式的 WPF 应用程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
caps.latest.revision: 3
caps.handback.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
---
# 如何：发布启用了视觉样式的 WPF 应用程序
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

视觉样式启用公共控件更改基于用户选择的主题外观。  默认情况下，视觉样式对 Windows Presentation Foundation \(WPF\) 应用程序禁用，因此，您必须进行手动启用。  但是，启用 WPF 应用程序的视觉样式然后发布解决方案导致错误。  本主题介绍如何解决此错误和发布 WPF 应用程序启用视觉样式的进程。  有关视觉样式的更多信息，请参见[Visual Styles Overview](http://msdn.microsoft.com/zh-cn/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e)。  有关错误消息的更多信息，请参见[ClickOnce 部署中的特定错误的疑难解答](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)。  
  
 若要解决该错误和发布解决方案，必须执行以下任务：  
  
-   [发布解决方案不使用视觉样式](#BKMK_publishsolwovs)。  
  
-   [创建清单文件。](#BKMK_CreateManifest)。  
  
-   [嵌入清单文件发布到发布解决方案的可执行文件](#BKMK_embedmanifest)。  
  
-   [对应用程序清单和部署清单进行签名。](#BKMK_signappdeplyman)。  
  
 然后您可以将发布的文件移动到您希望最终用户来安装应用程序的位置。  
  
##  <a name="BKMK_publishsolwovs"></a> 发布解决方案不使用视觉样式  
  
1.  确保您的项目没有启用视觉样式。  首先，检查以下 XML 的项目清单文件。  然后，如果 XML 存在，则用注释标记括住 XML。  
  
     默认情况下，视觉样式不会启用。  
  
    ```  
    <dependency>    <dependentAssembly>      <assemblyIdentity          type="win32"          name="Microsoft.Windows.Common-Controls"          version="6.0.0.0"          processorArchitecture="*"          publicKeyToken="6595b64144ccf1df"          language="*"        />    </dependentAssembly>  </dependency>  
    ```  
  
     以下过程显示如何打开与您的项目相关的清单文件。  
  
    ###### 若要打开在 Visual Basic 项目中的清单文件  
  
    1.  在菜单栏上，选择“项目”、*ProjectNameProjectName*“属性”，其中 *ProjectName* 是 WPF 项目的名称。  
  
         此时将显示 WPF 项目的属性页。  
  
    2.  在**“应用程序”**选项卡中，选择**“查看 Windows 设置”**。  
  
         应用程序清单文件将在**“代码编辑器”**中打开。  
  
    ###### 若要打开在 C\# 项目中的清单文件  
  
    1.  在菜单栏上，选择“项目”、*ProjectNameProjectName*“属性”，其中 *ProjectName* 是 WPF 项目的名称。  
  
         此时将显示 WPF 项目的属性页。  
  
    2.  在**“应用程序”**选项，请记下显示在清单字段的名称。  这是与您的项目相关联的清单名称。  
  
        > [!NOTE]
        >  如果 **“嵌入带默认设置的清单”** 或 **“创建不带清单的应用程序** 在清单字段显示，视觉样式未启用。  如果在清单字段显示清单文件的名称，请执行本过程中的下一步。  
  
    3.  在**“解决方案资源管理器”**中选择**“显示所有文件”**（）。  
  
         此按钮显示所有项目项，包括已被排除的合通常是隐藏的。  清单文件作为项目项出现。  
  
2.  生成并发布您的解决方案。  有关如何发布解决方案的更多信息，请参见[如何：使用发布向导发布 ClickOnce 应用程序](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)。  
  
##  <a name="BKMK_CreateManifest"></a> 创建清单文件。  
  
1.  将以下 XML 粘贴到记事本文件中。  
  
     此 XML 描述包含控件支持视觉样式的程序集。  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?><asmv1:assembly manifestVersion="1.0"                xmlns="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"                xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  <dependency>    <dependentAssembly>      <assemblyIdentity        type="win32"        name="Microsoft.Windows.Common-Controls"        version="6.0.0.0"        processorArchitecture="*"        publicKeyToken="6595b64144ccf1df"        language="*"        />    </dependentAssembly>  </dependency></asmv1:assembly>  
    ```  
  
2.  在记事本中，单击**“文件”**，然后单击**“另存为”**。  
  
3.  在**“另存为”**对话框中的**“保存类型”**下拉列表中，选择**“所有文件”**。  
  
4.  在**“文件名”**框中，为该文件命名，并在文件名末尾追加 .manifest。  例如：themes.manifest。  
  
5.  选择**“浏览文件夹”**按钮以选择任意文件夹，然后单击**“保存”**。  
  
    > [!NOTE]
    >  其余过程假定此文件的名称为 themes.manifest 和该文件被保存到您的计算机的 C:\\temp 目录中。  
  
##  <a name="BKMK_embedmanifest"></a> 嵌入清单文件发布到发布解决方案的可执行文件  
  
1.  打开**“Visual Studio 命令提示”**。  
  
     有关如何打开**“Visual Studio 命令提示”**的更多信息，请参见[命令提示符](../Topic/Developer%20Command%20Prompt%20for%20Visual%20Studio.md)。  
  
    > [!NOTE]
    >  其余步骤针对您的解决方案做出以下假设：  
    >   
    >  -   该解决方案的名称是 MyWPFProject。  
    > -   解决方案位于以下目录中：`%UserProfile%\Documents\Visual Studio 2010\Projects\`。  
    >   
    >      解决方案发布在以下目录中：`%UserProfile%\Documents\Visual Studio 2010\Projects\publish`。  
    > -   发布的应用程序文件的最新版本位于以下目录：`%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`  
    >   
    >  没必要使用以上描述的名称或目录位置。  以上描述的名称和位置仅用于说明发布解决方案的步骤。  
  
2.  在命令提示处，请更改路径到包含发布应用程序文件的最新版本的内容的目录。  下面的示例说明了这一步骤。  
  
    ```  
    cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"  
    ```  
  
3.  在命令提示处，运行下列命令以嵌入该清单文件到应用程序的可执行文件。  
  
    ```  
    mt –manifest c:\temp\themes.manifest –outputresource:MyWPFApp.exe.deploy  
    ```  
  
##  <a name="BKMK_signappdeplyman"></a> 对应用程序清单和部署清单进行签名。  
  
1.  在命令提示处，运行下列命令以将当前目录中的可执行文件中的`.deploy` 扩展移除。  
  
    ```  
    ren MyWPFApp.exe.deploy MyWPFApp.exe  
    ```  
  
    > [!NOTE]
    >  此示例假定只有一个文件具有 `.deploy` 文件扩展名。  确保此目录中的具有 `.deploy` 文件扩展名的所有文件被重命名。  
  
2.  在命令提示符处，运行以下命令以登陆应用程序清单。  
  
    ```  
    mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
    ```  
  
    > [!NOTE]
    >  此示例假定您使用项目的 `.pfx` 文件在清单中签名。  如果不清单签名，则可以忽略此示例中使用的 `–cf` 参数。  如果在用需要密码的证书清单签名，请指定 `–password` 选项\(`For example: mage –u MyWPFApp.exe.manifest –cf ..\..\..\MyWPFApp_TemporaryKey.pfx – password Password`\)。  
  
3.  在命令提示处，运行下列命令以添加 `.deploy` 扩展到此文件的上一步中重命名的文件名。  
  
    ```  
    ren MyWPFApp.exe MyWPFApp.exe.deploy  
    ```  
  
    > [!NOTE]
    >  此示例假定只有一个文件具有 `.deploy` 文件扩展名。  确保此目录中的先前具有 `.deploy` 文件扩展名的所有文件被重命名。  
  
4.  在命令提示符下，运行以下命令以登陆部署清单。  
  
    ```  
    mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
    ```  
  
    > [!NOTE]
    >  此示例假定您使用项目的 `.pfx` 文件在清单中签名。  如果不清单签名，则可以忽略此示例中使用的 `–cf` 参数。  如果在用需要密码的证书清单签名，请指定 `–password` 选项，如此例所示：`For example: mage –u MyWPFApp.exe.manifest –cf ..\..\..\MyWPFApp_TemporaryKey.pfx – password Password`。  
  
 在执行这些步骤之后，您可以将发布的文件移动到您希望最终用户安装这种应用程序的位置。  如果您打算经常更新解决方案，您可以将这些命令移动到一个脚本中，并且每次发布新版本时运行该脚本。  
  
## 请参阅  
 [ClickOnce 部署中的特定错误的疑难解答](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)   
 [Visual Styles Overview](http://msdn.microsoft.com/zh-cn/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e)   
 [Enabling Visual Styles](VS|Controls|~\controls\userex\cookbook.htm)   
 [命令提示符](../Topic/Developer%20Command%20Prompt%20for%20Visual%20Studio.md)