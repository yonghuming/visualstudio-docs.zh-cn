---
title: "演练： 使用项模板创建的自定义操作项目项，第 2 部分 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
ms.assetid: 2d8165d3-4af9-4a5e-bdba-8b2a06b1dc8d
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b12a52101feebcfac08c7672834d9d7c65d41c55
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2"></a>演练：使用项模板创建自定义操作项目项（第 2 部分）
  定义自定义类型的 SharePoint 项目项并将其与 Visual Studio 中的项模板关联后，你可能还想要模板提供的向导。 可以使用向导收集从用户的信息，当用户使用你的模板添加到项目的项目项的新实例。 你收集的信息可以用于初始化项目项。  
  
 在本演练中，你将向自定义操作项目项中所示添加向导[演练： 使用项模板，第 1 部分创建自定义操作项目项](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)。 当用户将自定义操作项目项添加到 SharePoint 项目中时，向导可收集有关自定义操作 （如其位置和要导航到，当最终用户选择其 URL） 的信息并将此信息在新添加到 Elements.xml 文件项目项。  
  
 本演练演示了下列任务：  
  
-   创建自定义 SharePoint 项目项类型与项模板的向导。  
  
-   定义自定义向导 UI 类似于 Visual Studio 中的 SharePoint 项目项中的内置的向导。  
  
-   使用可替换参数来初始化此向导中收集的数据与 SharePoint 项目文件。  
  
-   调试和测试该向导。  
  
> [!NOTE]  
>  你可以下载包含已完成的项目、 代码和从以下位置在本演练中的其他文件的示例：[有关 SharePoint 工具扩展演练项目文件](http://go.microsoft.com/fwlink/?LinkId=191369)。  
  
## <a name="prerequisites"></a>先决条件  
 若要执行本演练，你必须首先创建 CustomActionProjectItem 解决方案通过完成[演练： 使用项模板，第 1 部分创建自定义操作项目项](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)。  
  
 你还需要以下组件来完成本演练的开发计算机上：  
  
-   受支持的 Windows、 SharePoint 和 Visual Studio 的版本。 有关详细信息，请参阅[有关开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio SDK。 本演练使用**VSIX 项目**SDK 创建 VSIX 包来部署项目项中的模板。 有关详细信息，请参阅[扩展 Visual Studio 中的 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
 以下概念的知识将会很有用，但不是要求必须完成本演练：  
  
-   用于 Visual Studio 中的项目和项模板的向导。 有关详细信息，请参阅[如何： 使用项目模板时使用向导](../extensibility/how-to-use-wizards-with-project-templates.md)和<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>接口。  
  
-   在 SharePoint 中的自定义操作。 有关详细信息，请参阅[自定义操作](http://go.microsoft.com/fwlink/?LinkId=177800)。  
  
## <a name="creating-the-wizard-project"></a>创建向导项目  
 若要完成本演练，必须将项目添加到你在中创建的 CustomActionProjectItem 解决方案[演练： 使用项模板，第 1 部分创建自定义操作项目项](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)。 将实现<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>接口，并在此项目中定义的向导 UI。  
  
#### <a name="to-create-the-wizard-project"></a>若要创建向导项目  
  
1.  在 Visual Studio 中，打开 CustomActionProjectItem 解决方案  
  
2.  在**解决方案资源管理器**，打开解决方案节点的快捷菜单，选择**添加**，然后选择**新项目**。  
  
3.  在**新项目**对话框框中，展开**Visual C#**或**Visual Basic**节点，然后选择**Windows**节点。  
  
4.  在顶部**新项目**对话框框中，请确保**.NET Framework 4.5**选择在列表中的.NET framework 的版本。  
  
5.  选择**WPF 用户控件库**项目模板，将项目**ItemTemplateWizard**，然后选择**确定**按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]将添加**ItemTemplateWizard**到解决方案的项目。  
  
6.  从项目中删除 UserControl1 项。  
  
## <a name="configuring-the-wizard-project"></a>配置向导项目  
 在创建该向导之前，必须添加 Windows Presentation Foundation (WPF) 窗口、 代码文件中和对项目的程序集引用。  
  
#### <a name="to-configure-the-wizard-project"></a>若要配置向导项目  
  
1.  在**解决方案资源管理器**，打开快捷菜单从**ItemTemplateWizard**项目节点，，然后选择**属性**。  
  
2.  在**项目设计器**，请确保目标框架设置为.NET Framework 4.5。  
  
     对于 Visual C# 项目，你可以将此值设置上**应用程序**选项卡。对于 Visual Basic 项目，你可以将此值设置上**编译**选项卡。有关详细信息，请参阅[如何：面向 .NET Framework 的某个版本](../ide/how-to-target-a-version-of-the-dotnet-framework.md)。  
  
3.  在**ItemTemplateWizard**项目中，添加**Window (WPF)**项目到项目中，并将其命名项**WizardWindow**。  
  
4.  添加两个分别名为 CustomActionWizard 和字符串的代码文件。  
  
5.  打开的快捷菜单**ItemTemplateWizard**项目，，然后选择**添加引用**。  
  
6.  在**引用管理器-ItemTemplateWizard**对话框中，在**程序集**节点，选择**扩展**节点。  
  
7.  选择下列程序集，旁边的复选框，然后选择**确定**按钮：  
  
    -   EnvDTE  
  
    -   Microsoft.visualstudio.shell.11.0 的引用  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
8.  在**解决方案资源管理器**中**引用**ItemTemplateWizard 项目文件夹，选择**EnvDTE**引用。  
  
9. 在**属性**窗口中，更改的值**嵌入互操作类型**属性**False**。  
  
## <a name="defining-the-default-location-and-id-strings-for-custom-actions"></a>为自定义操作中定义的默认位置和 ID 字符串  
 每个自定义操作，并且在位置中指定的 ID`GroupID`和`Location`属性`CustomAction`Elements.xml 文件中的元素。 在此步骤中，可定义一些 ItemTemplateWizard 项目中的这些属性的有效字符串。 完成本演练后，这些字符串是写入到的 Elements.xml 文件中的自定义操作项目项，当用户在向导中指定的位置和 ID。  
  
 为简单起见，此示例仅支持的子集的可用的默认位置和 Id。 完整列表，请参阅[默认自定义操作位置和 Id](http://go.microsoft.com/fwlink/?LinkId=181964)。  
  
#### <a name="to-define-the-default-location-and-id-strings"></a>若要定义的默认位置和 ID 字符串  
  
1.  打开。  
  
2.  在**ItemTemplateWizard**项目中，将替换为以下代码的字符串代码文件中的代码。  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/strings.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/strings.vb#6)]  
  
## <a name="creating-the-wizard-ui"></a>创建向导 UI  
 添加 XAML 定义用户界面的向导，并添加一些代码以在向导中将某些控件绑定到的 ID 字符串。 你创建向导类似于 Visual Studio 中的 SharePoint 项目的内置向导。  
  
#### <a name="to-create-the-wizard-ui"></a>若要创建向导 UI  
  
1.  在**ItemTemplateWizard**项目中，打开快捷菜单**WizardWindow.xaml**文件，然后依次**打开**以在设计器中打开窗口。  
  
2.  在 XAML 视图中，将当前的 XAML 替换下面的 XAML。 XAML 定义的用户界面可包含一个标题，用于指定自定义操作和在窗口底部的导航按钮的行为的控件。  
  
    > [!NOTE]  
    >  在添加此代码后，你的项目将出现一些编译错误。 在后续步骤中添加代码，这些错误将会消失。  
  
     [!code-xml[SPExtensibility.ProjectItem.CustomAction#9](../sharepoint/codesnippet/Xaml/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml#9)]  
  
    > [!NOTE]  
    >  在此 XAML 中创建的窗口派生自<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>基类。 当向 Visual Studio 添加自定义 WPF 对话框中时，我们建议从能够拥有与其他 Visual Studio 中的对话框的一致样式并能够避免出现的问题可能会使用模式对话框否则会发生此类派生对话框。 有关详细信息，请参阅[创建和管理模式对话框](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes)。  
  
3.  如果你要开发 Visual Basic 项目，删除`ItemTemplateWizard`命名空间从`WizardWindow`中的类名称`x:Class`属性`Window`元素。 此元素是在第一行中的 XAML。 完成后，第一行应类似于下面的代码：  
  
    ```  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  在 WizardWindow.xaml 文件代码隐藏文件中，将当前的代码替换下面的代码。  
  
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.cs#7)]  
  
## <a name="implementing-the-wizard"></a>实现向导  
 通过实现定义的向导的功能<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>接口。  
  
#### <a name="to-implement-the-wizard"></a>若要实现向导  
  
1.  在**ItemTemplateWizard**项目中，打开**CustomActionWizard**代码文件，然后将此文件中的当前代码替换为以下代码：  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/customactionwizard.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/customactionwizard.vb#8)]  
  
## <a name="checkpoint"></a>检查点  
 此时在本演练中，该向导的所有代码现在都是项目中。 生成项目，以确保它在编译时没有错误。  
  
#### <a name="to-build-your-project"></a>若要生成你的项目  
  
1.  在菜单栏上，依次选择 **“生成”**、 **“生成解决方案”**。  
  
## <a name="associating-the-wizard-with-the-item-template"></a>带有项模板关联向导  
 现在，已实现了向导，你必须将其与关联**自定义操作**项模板，通过完成三个主要步骤：  
  
1.  向导程序集具有强名称签名。  
  
2.  获取令牌向导程序集的公钥。  
  
3.  .Vstemplate 文件中添加对向导程序集的引用**自定义操作**项模板。  
  
#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>若要使用强名称对向导程序集签名  
  
1.  在**解决方案资源管理器**，打开快捷菜单从**ItemTemplateWizard**项目节点，，然后选择**属性**。  
  
2.  上**签名**选项卡上，选择**对程序集签名**复选框。  
  
3.  在**选择强名称密钥文件**列表中，选择**\<新建 … >**。  
  
4.  在**创建强名称密钥**对话框框中，输入一个名称，清除**保护我使用密码的密钥文件**复选框，然后依次**确定**按钮。  
  
5.  在菜单栏上，依次选择 **“生成”**、 **“生成解决方案”**。  
  
#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>若要获取的公钥令牌向导程序集  
  
1.  在 Visual Studio 命令提示符窗口中，运行以下命令，将*PathToWizardAssembly*替换为您在开发 ItemTemplateWizard 项目生成的 ItemTemplateWizard.dll 程序集的完整路径计算机。  
  
    ```  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     ItemTemplateWizard.dll 程序集的公钥令牌写入 Visual Studio 命令提示符窗口。  
  
2.  使 Visual Studio 命令提示符窗口保持打开。 你将需要公钥标记以完成下一步过程。  
  
#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>若要添加的.vstemplate 文件中的向导程序集的引用  
  
1.  在**解决方案资源管理器**，展开**ItemTemplate**项目节点，，然后打开 ItemTemplate.vstemplate 文件。  
  
2.  该文件的末尾添加以下`WizardExtension`之间的元素`</TemplateContent>`和`</VSTemplate>`标记。 替换*YourToken*值`PublicKeyToken`具有你在前面的过程中获得的公钥令牌属性。  
  
    ```  
    <WizardExtension>  
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>  
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     有关详细信息`WizardExtension`元素，请参阅[WizardExtension 元素 &#40;Visual Studio 模板 &#41;](/visualstudio/extensibility/wizardextension-element-visual-studio-templates).  
  
3.  保存并关闭文件。  
  
## <a name="adding-replaceable-parameters-to-the-elementsxml-file-in-the-item-template"></a>在项模板的 Elements.xml 文件中添加可替换参数  
 将多个可替换参数添加到 ItemTemplate 项目中的 Elements.xml 文件。 这些参数以进行初始化`PopulateReplacementDictionary`中的方法`CustomActionWizard`前面定义的类。 当用户将自定义操作项目项添加到项目时，Visual Studio 自动替换为新的项目项中的 Elements.xml 文件中的这些参数在向导中指定它们的值。  
  
 可替换参数是一个标记，用于开始和结束的美元符号 （$） 字符。 除了定义你自己的可替换参数，你可以使用内置 SharePoint 项目系统定义和初始化的参数。 有关详细信息，请参阅[可替换参数](../sharepoint/replaceable-parameters.md)。  
  
#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>若要向 Elements.xml 文件中添加可替换参数  
  
1.  在 ItemTemplate 项目中，用下列 XML 替换 Elements.xml 文件的内容。  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">  
      <CustomAction Id="$IdValue$"  
                    GroupId="$GroupIdValue$"  
                    Location="$LocationValue$"  
                    Sequence="1000"  
                    Title="$TitleValue$"  
                    Description="$DescriptionValue$" >  
        <UrlAction Url="$UrlValue$"/>  
      </CustomAction>  
    </Elements>  
    ```  
  
     新的 XML 更改的值`Id`， `GroupId`， `Location`， `Description`，和`Url`属性为可替换参数。  
  
2.  保存并关闭文件。  
  
## <a name="adding-the-wizard-to-the-vsix-package"></a>将向导添加到 VSIX 包  
 在 source.extension.vsixmanifest 文件在 VSIX 项目中，添加对向导项目的引用，以便与包含项目项的 VSIX 包部署。  
  
#### <a name="to-add-the-wizard-to-the-vsix-package"></a>将向导添加到 VSIX 包  
  
1.  在**解决方案资源管理器**，打开快捷菜单从**source.extension.vsixmanifest**在 CustomActionProjectItem 项目中，文件，然后选择**打开**以打开清单编辑器中的文件。  
  
2.  在清单编辑器中，选择**资产**选项卡，然后选择**新建**按钮。  
  
     **添加新资产**对话框随即出现。  
  
3.  在**类型**列表中，选择**Microsoft.VisualStudio.Assembly**。  
  
4.  在**源**列表中，选择**当前解决方案中的项目**。  
  
5.  在**项目**列表中，选择**ItemTemplateWizard**，然后选择**确定**按钮。  
  
6.  在菜单栏上，选择**生成**，**生成解决方案**，并确保解决方案在编译时没有错误。  
  
## <a name="testing-the-wizard"></a>测试向导  
 现在你就可以测试该向导。 首先，开始调试 Visual Studio 的实验实例中 CustomActionProjectItem 解决方案。 然后在 Visual Studio 的实验实例中的 SharePoint 项目中测试自定义操作项目项的向导。 最后，生成并运行 SharePoint 项目，以验证自定义操作按预期方式工作。  
  
#### <a name="to-start-to-debug-the-solution"></a>若要开始调试解决方案  
  
1.  使用管理凭据，重新启动 Visual Studio，然后打开 CustomActionProjectItem 解决方案。  
  
2.  在 ItemTemplateWizard 项目中，打开 CustomActionWizard 代码文件中，并将断点添加到代码中的第一行`RunStarted`方法。  
  
3.  在菜单栏上，选择**调试**，**异常**。  
  
4.  在**异常**对话框框中，请确保**引发**和**用户未处理**对应的复选框**公共语言运行时异常**已清除，然后选择**确定**按钮。  
  
5.  开始调试通过选择 F5 键，或在菜单栏上，选择**调试**，**启动调试**。  
  
     Visual Studio 将在 %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom 操作项目 Item\1.0 安装扩展，并启动 Visual Studio 的实验实例。 你将在 Visual Studio 的此实例中测试的项目项。  
  
#### <a name="to-test-the-wizard-in-visual-studio"></a>在 Visual Studio 中测试该向导  
  
1.  在实验实例中的 Visual Studio 中，在菜单栏上，选择**文件**，**新建**，**项目**。  
  
2.  展开**Visual C#**或**Visual Basic**节点 （具体取决于您的项模板支持的语言），展开**SharePoint**节点，然后选择**2010年**节点。  
  
3.  在项目模板列表中，选择**SharePoint 2010 项目**，命名该项目**CustomActionWizardTest**，然后选择**确定**按钮。  
  
4.  在**SharePoint 自定义向导**，输入你想要用于调试，站点的 URL，然后选择**完成**按钮。  
  
5.  在**解决方案资源管理器**，打开项目节点的快捷菜单，选择**添加**，然后选择**新项**。  
  
6.  在**添加新项-CustomItemWizardTest**对话框框中，展开**SharePoint**节点，然后展开**2010年**节点。  
  
7.  在项目项的列表中，选择**自定义操作**项，然后依次**添加**按钮。  
  
8.  验证在 Visual Studio 的其他实例中在代码停止在更早版本中设置的断点处`RunStarted`方法。  
  
9. 继续调试该项目，通过选择 F5 键，或在菜单栏中，选择**调试**，**继续**。  
  
     将出现 SharePoint 自定义向导。  
  
10. 下**位置**，选择**列表的编辑**选项按钮。  
  
11. 在**组 ID**列表中，选择**通信**。  
  
12. 在**标题**框中，输入**SharePoint 开发人员中心**。  
  
13. 在**说明**框中，输入**打开 SharePoint 开发人员中心网站**。  
  
14. 在**URL**框中，输入**http://msdn.microsoft.com/sharepoint/default.aspx**，然后选择**完成**按钮。  
  
     isual Studio 中添加一项名为**CustomAction1**到你的项目和 Elements.xml 文件在编辑器中打开。 确认 Elements.xml 文件包含你在向导中指定的值。  
  
#### <a name="to-test-the-custom-action-in-sharepoint"></a>若要在 SharePoint 中测试自定义操作  
  
1.  在 Visual Studio 的实验实例中，选择 F5 键或在菜单栏上，选择**调试**，**启动调试**。  
  
     自定义操作被打包并部署到指定的 SharePoint 站点**站点 URL**属性的项目中和 web 浏览器打开到此站点的默认页。  
  
    > [!NOTE]  
    >  如果**脚本调试已禁用**对话框出现时，选择**是**按钮。  
  
2.  在 SharePoint 站点列表区域中，选择**任务**链接。  
  
     **任务-所有任务**页将出现。  
  
3.  上**列表工具**选项卡的功能区中，选择**列表**选项卡上，然后在**设置**组中，选择**列表设置**。  
  
     **列表设置**页将出现。  
  
4.  下**通信**页面顶部附近标题下，选择**SharePoint 开发人员中心**链接，请验证浏览器打开网站 http://msdn.microsoft.com/sharepoint/default.aspx，，然后关闭浏览器。  
  
## <a name="cleaning-up-the-development-computer"></a>清理开发计算机  
 完成项目项的测试后，从 Visual Studio 的实验实例中删除项目项模板。  
  
#### <a name="to-clean-up-the-development-computer"></a>若要清理的开发计算机  
  
1.  在实验实例中的 Visual Studio 中，在菜单栏上，选择**工具**，**扩展和更新**。  
  
     此时，“扩展和更新”对话框打开。  
  
2.  在扩展的列表中，选择**自定义操作项目项**扩展，然后选择**卸载**按钮。  
  
3.  在显示的对话框中，选择**是**按钮以确认你要卸载扩展，然后选择**立即重新启动**按钮以完成卸载。  
  
4.  关闭 Visual Studio （实验实例和 CustomActionProjectItem 解决方案处于打开状态的 Visual Studio 的实例） 的两个实例。  
  
## <a name="see-also"></a>另请参阅  
 [演练： 使用项模板创建的自定义操作项目项，第 1 部分](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [定义自定义 SharePoint 项目项类型](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [为 SharePoint 项目项创建项模板和项目模板](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Visual Studio 模板架构参考](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [如何： 使用向导来处理项目模板](../extensibility/how-to-use-wizards-with-project-templates.md)   
 [默认自定义操作位置和 Id](http://go.microsoft.com/fwlink/?LinkId=181964)  
  
  