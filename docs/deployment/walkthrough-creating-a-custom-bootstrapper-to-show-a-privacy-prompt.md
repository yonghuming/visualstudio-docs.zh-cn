---
title: "演练： 创建自定义的引导程序，以显示隐私提示 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- dependencies [.NET Framework], custom bootstrapper package
- deploying applications [Visual Studio], custom prerequisites
- Windows Installer deployment, prerequisites
- prerequisites [.NET Framework], custom bootstrapper package
ms.assetid: 2f3edd6a-84d1-4864-a1ae-6a13c5732aae
caps.latest.revision: "10"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: f84abe8354f1affc566cc05d119edc4cbc030712
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt"></a>演练：创建自定义引导程序以显示隐私提示
你可以配置自动更新时使用较新的文件版本和程序集版本的程序集可用的 ClickOnce 应用程序。 若要确保你的客户同意此行为，可以向其显示隐私提示。 然后，他们可以选择是否用于授予对应用程序的自动更新权限。 如果应用程序不允许自动更新，它不安装。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练：  
  
-   Visual Studio 2010。  
  
## <a name="creating-an-update-consent-dialog-box"></a>创建一个更新同意对话框  
 若要显示隐私提示，请创建的应用程序询问读取器同意应用程序的自动更新。  
  
#### <a name="to-create-a-consent-dialog-box"></a>若要创建一个同意对话框  
  
1.  在 **“文件”** 菜单上，指向 **“新建”**，然后单击 **“项目”**。  
  
2.  在**新项目**对话框中，单击**Windows**，然后单击**WindowsFormsApplication**。  
  
3.  有关**名称**，类型**ConsentDialog**，然后单击**确定**。  
  
4.  在设计器中，单击表单。  
  
5.  在**属性**窗口中，更改**文本**属性**更新同意对话框**。  
  
6.  在**工具箱**，展开**所有 Windows 窗体**，并将其拖**标签**到窗体控件。  
  
7.  在设计器中，单击的标签控件。  
  
8.  在**属性**窗口中，更改**文本**下的属性**外观**所示：  
  
     在 Web 上找到最新的更新检查要安装的应用程序。 单击"我同意"，则会授权应用程序检查并自动从 Internet 安装更新。  
  
9. 在**工具箱**，拖动**复选框**控件添加到窗体的中间。  
  
10. 在**属性**窗口中，更改**文本**下的属性**布局**到**我同意**。  
  
11. 在**工具箱**，拖动**按钮**到左下方的窗体控件。  
  
12. 在**属性**窗口中，更改**文本**下的属性**布局**到**继续**。  
  
13. 在**属性**窗口中，更改**（名称）**下的属性**设计**到**ProceedButton**。  
  
14. 在**工具箱**，拖动**按钮**到窗体右下方的控件。  
  
15. 在**属性**窗口中，更改**文本**下的属性**布局**到**取消**。  
  
16. 在**属性**窗口中，更改**（名称）**下的属性**设计**到**CancelButton**。  
  
17. 在设计器中，双击**我同意**复选框以生成的 CheckedChanged 事件处理程序。  
  
18. 在 Form1 代码文件中，添加以下代码的 CheckedChanged 事件处理程序。  
  
     [!code-csharp[ConsentDialog#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.cs)]
     [!code-vb[ConsentDialog#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.vb)]  
  
19. 更新类构造函数，以禁用**继续**默认情况下的按钮。  
  
     [!code-csharp[ConsentDialog#6](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.cs)]
     [!code-vb[ConsentDialog#6](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.vb)]  
  
20. 在 Form1 代码文件中，添加以下代码以跟踪如果最终用户已同意联机更新的布尔变量。  
  
     [!code-csharp[ConsentDialog#3](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.cs)]
     [!code-vb[ConsentDialog#3](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.vb)]  
  
21. 在设计器中，双击**继续**按钮以生成 Click 事件处理程序。  
  
22. 在 Form1 代码文件中，将以下代码添加到 Click 事件处理程序**继续**按钮。  
  
     [!code-csharp[ConsentDialog#2](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.cs)]
     [!code-vb[ConsentDialog#2](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.vb)]  
  
23. 在设计器中，双击**取消**按钮以生成 Click 事件处理程序。  
  
24. 在 Form1 代码文件中，添加以下代码的 Click 事件处理程序**取消**按钮。  
  
     [!code-csharp[ConsentDialog#4](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.cs)]
     [!code-vb[ConsentDialog#4](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.vb)]  
  
25. 更新应用程序返回错误，如果最终用户不同意联机更新。  
  
     有关 Visual Basic 开发人员仅：  
  
    1.  在**解决方案资源管理器**，单击**ConsentDialog**。  
  
    2.  上**项目**菜单上，单击**添加模块**，然后单击**添加**。  
  
    3.  在 Module1.vb 代码文件中，添加以下代码。  
  
         [!code-vb[ConsentDialog#7](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_6.vb)]  
  
    4.  上**项目**菜单上，单击**ConsentDialog 属性**，然后单击**应用程序**选项卡。  
  
    5.  取消选中**启用应用程序框架**。  
  
    6.  在**启动对象**下拉列表菜单上，选择**Module1**。  
  
        > [!NOTE]
        >  禁用应用程序框架将禁用 Windows XP 视觉样式、 应用程序事件、 初始屏幕、 单实例应用程序，和的详细信息等功能。 有关详细信息，请参阅 [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)（应用程序页、项目设计器 (Visual Basic)。  
  
     有关 Visual C# 仅适用于开发人员：  
  
     打开 Program.cs 代码文件中，并添加下面的代码。  
  
     [!code-csharp[ConsentDialog#5](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_7.cs)]  
  
26. 上**生成**菜单上，单击**生成解决方案**。  
  
## <a name="creating-the-custom-bootstrapper-package"></a>创建自定义引导程序包  
 若要向最终用户显示隐私提示，可以创建更新同意对话框应用程序自定义引导程序包，并将其作为必备组件包含在所有 ClickOnce 应用程序。  
  
 此过程演示如何创建自定义引导程序包通过创建以下文档：  
  
-   Product.xml 清单文件来描述引导程序的内容。  
  
-   若要列出你的包，如字符串和软件许可条款的本地化特定方面 package.xml 清单文件。  
  
-   软件许可条款的文档。  
  
#### <a name="step-1-to-create-the-bootstrapper-directory"></a>步骤 1： 若要创建引导程序目录  
  
1.  创建一个名为目录**UpdateConsentDialog**在 %PROGRAMFILES%\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages。  
  
    > [!NOTE]
    >  你可能需要管理特权才能创建此文件夹。  
  
2.  在 UpdateConsentDialog 目录中，创建名为 en 的子目录。  
  
    > [!NOTE]
    >  创建一个新目录，每个区域设置。 例如，你可以添加为 fr 和 de 区域设置的子目录。 如有必要，这些目录将包含的法语和德语字符串和语言包。  
  
#### <a name="step-2-to-create-the-productxml-manifest-file"></a>步骤 2： 创建 product.xml 清单文件  
  
1.  创建名为文本文件`product.xml`。  
  
2.  在 product.xml 文件中，添加以下 XML 代码。 请确保你不会覆盖现有的 XML 代码。  
  
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
  
#### <a name="step-3-to-create-the-packagexml-manifest-file-and-the-software-license-terms"></a>步骤 3： 创建 package.xml 清单文件和软件许可条款  
  
1.  创建名为文本文件`package.xml`。  
  
2.  在 package.xml 文件中，添加下面的 XML 代码，以定义区域设置并包括软件许可条款。 请确保你不会覆盖现有的 XML 代码。  
  
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
  
4.  创建一个名为软件许可条款 eula.rtf 的文档。  
  
    > [!NOTE]
    >  软件许可条款应包括有关许可、 担保、 负债和当地的法律信息。 这些文件应是特定于区域设置，因此请确保该文件保存在支持 MBCS 或 UNICODE 字符的格式。 请查阅法律部门有关的内容的软件许可条款。  
  
5.  将文档保存到 UpdateConsentDialog 引导程序目录中的 en 子目录。  
  
6.  如有必要，请为每个区域设置的软件许可条款创建新的 package.xml 清单文件和新 eula.rtf 文档。 例如，如果你创建 fr 和 de 区域设置的子目录，则创建单独的 package.xml 清单文件和软件许可条款，并将它们保存到 fr 和 de 子目录。  
  
## <a name="setting-the-update-consent-application-as-a-prerequisite"></a>将更新同意应用程序设置作为必备组件  
 在 Visual Studio 中，你可以设置更新同意应用程序作为必备组件。  
  
#### <a name="to-set-the-update-consent-application-as-a-prerequisite"></a>更新同意应用程序设置作为必备组件  
  
1.  在**解决方案资源管理器**，单击你想要部署的应用程序的名称。  
  
2.  上**项目**菜单上，单击*ProjectName* **属性**。  
  
3.  单击**发布**页，，然后单击**先决条件**。  
  
4.  选择**更新同意对话框**。  
  
    > [!NOTE]
    >  你可能需要关闭并重新打开 Visual Studio 以查看更新的同意对话框的系统必备组件对话框中。  
  
5.  单击“确定”。  
  
## <a name="creating-and-testing-the-setup-program"></a>创建和测试安装程序  
 作为必备组件设置更新同意应用程序后，可以为你的应用程序中生成的安装程序和引导程序。  
  
#### <a name="to-create-and-test-the-setup-program-by-not-clicking-i-agree"></a>若要创建和测试安装程序通过不单击我同意  
  
1.  在**解决方案资源管理器**，单击你想要部署的应用程序的名称。  
  
2.  上**项目**菜单上，单击*ProjectName* **属性**。  
  
3.  单击**发布**页，，然后单击**立即发布**。  
  
4.  如果发布输出不会自动打开，导航到发布输出。  
  
5.  运行 Setup.exe 程序。  
  
     安装程序将显示更新的同意对话框软件许可协议。  
  
6.  阅读软件许可协议，，然后单击**接受**。  
  
     更新的同意对话框应用程序将出现并显示以下文本： 在 Web 上找到最新的更新检查要安装的应用程序。 通过单击我同意，你授权应用程序检查 Internet 上的自动更新。  
  
7.  关闭应用程序，或单击取消。  
  
     应用程序将显示错误： 安装系统的组件时发生错误*ApplicationName*。 之前已成功安装所有系统组件，安装程序无法继续。  
  
8.  单击详细信息，以显示以下错误消息： 组件更新同意对话框无法安装具有以下错误消息:"自动更新协议不被接受。" 无法安装以下组件:-更新同意对话框  
  
9. 单击 **“关闭”**。  
  
#### <a name="to-create-and-test-the-setup-program-by-clicking-i-agree"></a>若要创建和测试安装程序，通过单击我同意  
  
1.  在**解决方案资源管理器**，单击你想要部署的应用程序的名称。  
  
2.  上**项目**菜单上，单击*ProjectName* **属性**。  
  
3.  单击**发布**页，，然后单击**立即发布**。  
  
4.  如果发布输出不会自动打开，导航到发布输出。  
  
5.  运行 Setup.exe 程序。  
  
     安装程序将显示更新的同意对话框软件许可协议。  
  
6.  阅读软件许可协议，，然后单击**接受**。  
  
     更新的同意对话框应用程序将出现并显示以下文本： 在 Web 上找到最新的更新检查要安装的应用程序。 通过单击我同意，你授权应用程序检查 Internet 上的自动更新。  
  
7.  单击**我同意**，然后单击**继续**。  
  
     应用程序将开始安装。  
  
8.  如果出现安装应用程序对话框中，单击**安装**。  
  
## <a name="see-also"></a>另请参阅  
 [应用程序部署必备](../deployment/application-deployment-prerequisites.md)   
 [创建引导程序包](../deployment/creating-bootstrapper-packages.md)   
 [如何： 创建产品清单](../deployment/how-to-create-a-product-manifest.md)   
 [如何： 创建的包清单](../deployment/how-to-create-a-package-manifest.md)   
 [产品和包架构引用](../deployment/product-and-package-schema-reference.md)