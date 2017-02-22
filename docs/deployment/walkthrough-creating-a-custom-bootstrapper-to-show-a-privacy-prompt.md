---
title: "演练：创建自定义引导程序以显示隐私提示 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce 部署, 系统必备"
  - "依赖项 [.NET Framework], 自定义引导程序包"
  - "部署应用程序 [Visual Studio], 自定义系统必备"
  - "系统必备 [.NET Framework], 自定义引导程序包"
  - "Windows Installer 部署, 系统必备"
ms.assetid: 2f3edd6a-84d1-4864-a1ae-6a13c5732aae
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 演练：创建自定义引导程序以显示隐私提示
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可以配置 ClickOnce 应用程序以在发布了具有更新的文件版本和程序集版本的程序集时进行自动更新。  确保您的客户同意此行为，您可以为他们显示一个隐私提示。  然后，他们可以选择是否授权应用程序进行自动更新。  如果应用程序不允许自动更新，则不会安装更新。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## 系统必备  
 您需要以下组件来完成本演练：  
  
-   Visual Studio 2010。  
  
## 创建更新许可对话框  
 若要显示隐私提示，可创建一个应用程序以请求读者同意应用程序自动更新。  
  
#### 创建许可对话框  
  
1.  在**“文件”**菜单上指向**“新建”**，再单击**“项目”**。  
  
2.  在**“新建项目”**对话框中，单击**“Windows”**，再单击**“Windows 窗体应用程序”**。  
  
3.  对于**“名称”**，键入“ConsentDialog”，然后单击**“确定”**。  
  
4.  在设计器中单击窗体。  
  
5.  在**“属性”**窗口中，将**“Text”**属性更改为“Update Consent Dialog”。  
  
6.  在**“工具箱”**中展开**“所有 Windows 窗体”**，然后将一个**“Label”**控件拖到窗体中。  
  
7.  在设计器中单击 Label 控件。  
  
8.  在**“属性”**窗口中，将**“外观”**下的**“Text”**属性更改为以下内容：  
  
     将要安装的应用程序会在网站上查找最新更新。  如果单击“同意”，则表示您授权应用程序自动在 Internet 上查找和安装更新。  
  
9. 将一个**“Checkbox”**控件从**“工具箱”**中拖到窗体的中间。  
  
10. 在**“属性”**窗口中，将**“布局”**下的**“Text”**属性更改为“同意”。  
  
11. 将一个**“Button”**控件从**“工具箱”**中拖到窗体的左下角。  
  
12. 在**“属性”**窗口中，将**“布局”**下的**“Text”**属性更改为“继续”。  
  
13. 在**“属性”**窗口中，将**“设计”**下的**“\(Name\)”**属性更改为“ProceedButton”。  
  
14. 将一个**“Button”**控件从**“工具箱”**中拖到窗体的右下角。  
  
15. 在**“属性”**窗口中，将**“布局”**下的**“Text”**属性更改为“取消”。  
  
16. 在**“属性”**窗口中，将**“设计”**下的**“\(Name\)”**属性更改为“CancelButton”。  
  
17. 在设计器中，双击**“同意”**复选框以生成 CheckedChanged 事件处理程序。  
  
18. 在 Form1 代码文件中，为 CheckedChanged 事件处理程序添加以下代码。  
  
     [!code-cs[ConsentDialog#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.cs)]
     [!code-vb[ConsentDialog#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.vb)]  
  
19. 默认情况下，更新类构造函数以禁用**“继续”**按钮。  
  
     [!code-cs[ConsentDialog#6](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.cs)]
     [!code-vb[ConsentDialog#6](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.vb)]  
  
20. 在 Form1 代码文件中，为一个布尔变量添加以下代码以跟踪最终用户是否已同意联机更新。  
  
     [!code-cs[ConsentDialog#3](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.cs)]
     [!code-vb[ConsentDialog#3](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.vb)]  
  
21. 在设计器中，双击**“继续”**按钮以生成一个 Click 事件处理程序。  
  
22. 在 Form1 代码文件中，为**“继续”**按钮的 Click 事件处理程序添加以下代码。  
  
     [!code-cs[ConsentDialog#2](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.cs)]
     [!code-vb[ConsentDialog#2](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.vb)]  
  
23. 在设计器中，双击**“取消”**按钮以生成一个 Click 事件处理程序。  
  
24. 在 Form1 代码文件中，为**“取消”**按钮的 Click 事件处理程序添加以下代码。  
  
     [!code-cs[ConsentDialog#4](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.cs)]
     [!code-vb[ConsentDialog#4](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.vb)]  
  
25. 更新应用程序以便在最终用户不同意联机更新时返回一个错误。  
  
     以下内容仅适用于 Visual Basic 开发人员：  
  
    1.  在**“解决方案资源管理器”**中单击**“ConsentDialog”**。  
  
    2.  在**“项目”**菜单中单击**“添加模块”**，然后单击**“添加”**。  
  
    3.  在 Module1.vb 代码文件中，添加以下代码。  
  
         [!code-vb[ConsentDialog#7](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_6.vb)]  
  
    4.  在**“项目”**菜单上，单击**“ConsentDialog 属性”**，然后单击**“应用程序”**选项卡。  
  
    5.  取消选中**“启用应用程序框架”**。  
  
    6.  在**“启动对象”**下拉菜单中选择**“Module1”**。  
  
        > [!NOTE]
        >  如果禁用启用应用程序框架，则会禁用 Windows XP 视觉样式、应用程序事件、初始屏幕、单实例应用程序等功能。  有关更多信息，请参见[“项目设计器”, “应用程序”页 \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md)。  
  
     以下内容仅适用于 Visual C\# 开发人员：  
  
     打开 Program.cs 代码文件，并添加以下代码。  
  
     [!code-cs[ConsentDialog#5](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_7.cs)]  
  
26. 在**“生成”**菜单上，单击**“生成解决方案”**。  
  
## 创建自定义引导程序包  
 若要为最终用户显示隐私提示，可以为 Update Consent Dialog 应用程序创建一个自定义引导程序包，并将其作为系统必备组件包含在所有 ClickOnce 应用程序中。  
  
 此过程演示如何通过创建以下文档来创建自定义引导程序包：  
  
-   用于介绍引导程序的内容的 product.xml 清单文件。  
  
-   用于列出包的本地化特定内容（例如字符串和软件许可条款）的 package.xml 清单文件。  
  
-   有关软件许可条款的文档。  
  
#### 步骤 1：创建引导程序目录  
  
1.  在 %PROGRAMFILES%\\Microsoft SDKs\\Windows\\v7.0A\\Bootstrapper\\Packages 中创建一个名为 UpdateConsentDialog 的目录。  
  
    > [!NOTE]
    >  您可能需要具有管理特权才能创建此文件夹。  
  
2.  在 UpdateConsentDialog 目录下，创建一个名为 en 的子目录。  
  
    > [!NOTE]
    >  为每个区域设置创建一个新目录。  例如，可以为 fr 和 de 区域设置添加相应的子目录。  如果需要，这些目录将包含法语和德语字符串和语言包。  
  
#### 步骤 2：创建 product.xml 清单文件  
  
1.  创建一个名为 `product.xml` 的文本文件。  
  
2.  在 product.xml 文件中，添加以下 XML 代码。  确保不会覆盖现有的 XML 代码。  
  
    ```  
    <Product  
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
      ProductCode="Microsoft.Sample.EULA">  
      <!-- Defines the list of files to be copied on build. -->  
      <PackageFiles CopyAllPackageFiles="false">  
        <PackageFile Name="ConsentDialog.exe"/>  
      </PackageFiles>  
  
      <!-- Defines how to run the Setup package.-->  
      <Commands >  
        <Command PackageFile = "ConsentDialog.exe" Arguments=''>  
          <ExitCodes>  
            <ExitCode Value="0" Result="Success" />  
            <ExitCode Value="-1" Result="Fail" String="AU_Unaccepted" />  
            <DefaultExitCode Result="Fail"   
              FormatMessageFromSystem="true" String="GeneralFailure" />  
          </ExitCodes>  
        </Command>  
      </Commands>  
  
    </Product>  
    ```  
  
3.  将文件保存到 UpdateConsentDialog 引导程序目录。  
  
#### 步骤 3：创建 package.xml 清单文件和软件许可条款  
  
1.  创建一个名为 `package.xml` 的文本文件。  
  
2.  在 package.xml 文件中，添加以下 XML 代码以定义区域设置并包含软件许可条款。  确保不会覆盖现有的 XML 代码。  
  
    ```  
    <Package   
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
      Name="DisplayName"  
      Culture="Culture"  
      LicenseAgreement="eula.rtf">  
      <PackageFiles>  
        <PackageFile Name="eula.rtf"/>  
      </PackageFiles>  
  
      <!-- Defines a localizable string table for error messages. -->  
      <Strings>  
        <String Name="DisplayName">Update Consent Dialog</String>  
        <String Name="Culture">en</String>  
        <String Name="AU_Unaccepted">The automatic update agreement is not accepted.</String>  
        <String Name="GeneralFailure">A failure occurred attempting to launch the setup.</String>  
      </Strings>  
    </Package>  
    ```  
  
3.  将文件保存到 UpdateConsentDialog 引导程序目录中的 en 子目录。  
  
4.  创建一个用于软件许可条款的名为 eula.rtf 的文档。  
  
    > [!NOTE]
    >  软件许可条款应包含有关许可、担保、责任和当地法律的信息。  这些文件应会因区域设置而异，因此要确保以支持 MBCS 或 UNICODE 字符的格式保存文件。  请向您的法律部门咨询有关软件许可条款的内容。  
  
5.  将文档保存到 UpdateConsentDialog 引导程序目录中的 en 子目录。  
  
6.  如果需要，针对每一个区域设置创建一个新的 package.xml 清单文件和一个新的用于软件许可条款的 eula.rtf 文档。  例如，如果您已创建 fr 和 de 区域设置的子目录，则请创建单独的 package.xml 清单文件和软件许可条款并将其分别保存到 fr 和 de 子目录。  
  
## 将更新许可应用程序设置为系统必备组件。  
 在 Visual Studio 中，您可以将更新许可应用程序设置为系统必备组件。  
  
#### 将更新许可应用程序设置为系统必备组件  
  
1.  在**“解决方案资源管理器”**中，单击要部署的应用程序的名称。  
  
2.  在**“项目”**菜单上，单击“*项目名称***属性**”。  
  
3.  单击**“发布”**页，然后单击**“系统必备”**。  
  
4.  选择**“Update Consent Dialog”**。  
  
    > [!NOTE]
    >  您可能必须关闭并重新打开 Visual Studio 才能在“系统必备”对话框中看到“Update Consent Dialog”。  
  
5.  单击**“确定”**。  
  
## 创建和测试安装程序  
 将更新许可应用程序设置为系统必备组件之后，您可以生成应用程序的安装程序和引导程序。  
  
#### 创建和测试安装程序（在测试过程中不单击“同意”）  
  
1.  在**“解决方案资源管理器”**中，单击要部署的应用程序的名称。  
  
2.  在**“项目”**菜单上，单击“*项目名称***属性**”。  
  
3.  单击**“发布”**页，然后单击**“立即发布”**。  
  
4.  如果发布输出没有自动打开，请定位到发布输出。  
  
5.  运行 Setup.exe 程序。  
  
     安装程序显示 Update Consent Dialog 软件许可条款。  
  
6.  阅读软件许可协议，然后单击**“接受”**。  
  
     将出现 Update Consent Dialog 应用程序并显示以下文本：“将要安装的应用程序会在网站上查找最新更新。  如果单击‘同意’，则表示您授权应用程序自动在 Internet 上查找和安装更新。”  
  
7.  关闭应用程序或单击“取消”。  
  
     应用程序显示一个错误：“安装*应用程序名* 的系统组件时发生错误。  在成功安装所有系统组件之前，安装程序无法继续进行。”  
  
8.  单击“详细信息”以显示以下错误消息：“未能安装组件 Update Consent Dialog，并显示下列错误消息:‘未接受自动更新协议’。下列组件未能安装: Update Consent Dialog”  
  
9. 单击**“关闭”**。  
  
#### 创建和测试安装程序（在测试过程中单击“同意”）  
  
1.  在**“解决方案资源管理器”**中，单击要部署的应用程序的名称。  
  
2.  在**“项目”**菜单上，单击“*项目名称***属性**”。  
  
3.  单击**“发布”**页，然后单击**“立即发布”**。  
  
4.  如果发布输出没有自动打开，请定位到发布输出。  
  
5.  运行 Setup.exe 程序。  
  
     安装程序显示 Update Consent Dialog 软件许可条款。  
  
6.  阅读软件许可协议，然后单击**“接受”**。  
  
     将出现 Update Consent Dialog 应用程序并显示以下文本：“将要安装的应用程序会在网站上查找最新更新。  如果单击‘同意’，则表示您授权应用程序自动在 Internet 上查找和安装更新。”  
  
7.  单击**“同意”**，然后单击**“继续”**。  
  
     应用程序将开始安装。  
  
8.  如果出现“应用程序安装”对话框，请单击**“安装”**。  
  
## 请参阅  
 [应用程序部署必备](../deployment/application-deployment-prerequisites.md)   
 [创建引导程序包](../deployment/creating-bootstrapper-packages.md)   
 [如何：创建产品清单](../deployment/how-to-create-a-product-manifest.md)   
 [如何：创建程序包清单](../deployment/how-to-create-a-package-manifest.md)   
 [产品和包架构引用](../deployment/product-and-package-schema-reference.md)