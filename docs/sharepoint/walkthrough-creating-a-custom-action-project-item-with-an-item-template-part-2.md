---
title: "Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "project items [SharePoint development in Visual Studio], creating template wizards"
  - "SharePoint project items, creating template wizards"
  - "SharePoint development in Visual Studio, defining new project item types"
ms.assetid: 2d8165d3-4af9-4a5e-bdba-8b2a06b1dc8d
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2
  在定义 SharePoint 项目项的自定义类型并将其与 Visual Studio 中的项模板关联后，可能还需要提供模板向导。  当用户使用模板向项目中添加项目项的新实例时，您可以使用此向导收集用户的信息。  收集的信息可用于初始化项目项。  
  
 在本演练中，您将为[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)中演示的“自定义操作”项目项添加向导。  当用户添加自定义操作"项目项添加到 SharePoint 项目时，此向导将收集有关自定义操作的信息 \(例如其位置和将导航，如果最终用户选择它\) 时并将此信息添加到新项目项的 Elements.xml 文件。  
  
 本演练将演示以下任务：  
  
-   为与项模板关联的自定义 SharePoint 项目项类型创建向导。  
  
-   定义一个自定义向导 UI，它类似于 Visual Studio 中的 SharePoint 项目项的内置向导。  
  
-   通过可替换参数使用此向导中收集的数据来初始化 SharePoint 项目文件。  
  
-   调试并测试向导。  
  
> [!NOTE]  
>  您可以下载包含已完成项目、代码和其他文件从以下位置为本演练的示例：[SharePoint 工具扩展演练的项目文件](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## 系统必备  
 若要执行本演练，必须先通过完成[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)来创建 CustomActionProjectItem 解决方案。  
  
 还需要在开发计算机上安装以下组件才能完成本演练：  
  
-   Windows、SharePoint 和 Visual Studio 的支持的版本。  有关更多信息，请参见[开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio SDK。  本演练使用 SDK 中的**“VSIX 项目”**模板来创建 VSIX 包以部署项目项。  有关更多信息，请参见[Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
 了解以下概念很有用，但对于完成本演练并不是必需的：  
  
-   Visual Studio 中的项目和项模板的向导。  有关更多信息，请参见[如何：使用向导来处理项目模板](../Topic/How%20to:%20Use%20Wizards%20with%20Project%20Templates.md)和 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 接口。  
  
-   SharePoint 中的自定义操作。  有关更多信息，请参见 [Custom Action](http://go.microsoft.com/fwlink/?LinkId=177800)（自定义操作）。  
  
## 创建向导项目  
 若要完成本演练，您必须将项目添加到您在 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)创建的 CustomActionProjectItem 解决方案。  您将实现 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 接口并定义此项目中的向导 UI。  
  
#### 创建向导项目  
  
1.  在 Visual Studio 中，打开 CustomActionProjectItem 解决方案  
  
2.  在 **解决方案资源管理器**，请打开解决方案节点的快捷菜单上，选择 **添加**，然后选择 **新建项目**。  
  
    > [!NOTE]  
    >  在 Visual Basic 项目中，仅当在[“选项”对话框 \-\>“项目和解决方案”\-\>“常规”](http://msdn.microsoft.com/zh-cn/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)中选中**“总是显示解决方案”**复选框时，解决方案节点才会出现在**“解决方案资源管理器”**中。  
  
3.  在 **新建项目** 对话框中，展开 **visual C\#** 或 **Visual Basic** 节点，然后选择 **Windows** 节点。  
  
4.  在 **新建项目** 对话框顶部，确保 **.NET Framework 4.5** 在 .NET Framework 的版本列表中选择。  
  
5.  选择 **WPF 用户控件库** 项目模板，将项目命名为 **ItemTemplateWizard**，然后选择 **确定** 按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 将**“ItemTemplateWizard”**项目添加到解决方案中。  
  
6.  从项目中删除 UserControl1 项。  
  
## 配置向导项目  
 在创建向导之前，必须将 Windows presentation foundation \(WPF\) 窗口中，代码文件，并且，程序集引用添加到项目。  
  
#### 配置向导项目  
  
1.  在 **解决方案资源管理器**，则从 **ItemTemplateWizard** 项目节点的快捷菜单，然后选择 **属性**。  
  
2.  在 **项目设计器**，请确保目标框架设置为 .NET Framework 4.5。  
  
     对于 visual C\# 项目中，可以在 **应用程序** 选项的该值。  对于 Visual Basic 项目中，可以在 **编译** 选项的该值。  有关更多信息，请参见[如何：面向 .NET Framework 的某个版本](../Topic/How%20to:%20Target%20a%20Version%20of%20the%20.NET%20Framework.md)。  
  
3.  在 **ItemTemplateWizard** 项目中，添加一个 **Window \(WPF\)** 项添加到项目中，然后将项目命名为 **WizardWindow**。  
  
4.  添加一个名为 CustomActionWizard 和字符串的两个代码文件。  
  
5.  打开 **ItemTemplateWizard** 项目的快捷菜单，然后选择 **添加引用**。  
  
6.  在 **引用管理器\- ItemTemplateWizard** 对话框中，在 **程序集** 节点下，选择 **扩展** 节点。  
  
7.  以下程序集中旁边的复选框，然后选择 **确定** 按钮：  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.Shell.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
8.  在 **解决方案资源管理器**，在 ItemTemplateWizard 项目的 **引用** 文件夹，选择 **EnvDTE** 引用。  
  
    > [!NOTE]  
    >  在 Visual Basic 项目中，**“引用”**文件夹仅当在[“选项”对话框 \-\>“项目和解决方案”\-\>“常规”](http://msdn.microsoft.com/zh-cn/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)中选中**“总是显示解决方案”**复选框时显示。  
  
9. 在 **属性** 窗口中，更改 **嵌入互操作类型** 属性的值更改为 **假**。  
  
## 定义自定义操作的默认位置和 ID 字符串  
 每个自定义操作都具有一个位置和 ID，二者分别是在 Elements.xml 文件中的 `CustomAction` 元素的 `Location` 特性和 `GroupID` 特性中指定的。  在此步骤中，您将为 ItemTemplateWizard 项目中的这些特性定义一些有效字符串。  在完成本演练后，这些字符串写入 Elements.xml 文件在自定义操作"项目项，当用户在向导中指定位置和 ID。  
  
 为简单起见，此示例仅支持可用的默认位置和 ID 的一个子集。  有关完整列表，请参见 [Default Custom Action Locations and IDs](http://go.microsoft.com/fwlink/?LinkId=181964)（默认的自定义操作位置和 ID）。  
  
#### 定义默认的位置和 ID 字符串  
  
1.  打开。  
  
2.  在 **ItemTemplateWizard** 项目，用以下代码替换字符串中代码文件中的代码。  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/itemtemplatewizard/strings.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/vb/itemtemplatewizard/strings.vb#6)]  
  
## 创建向导 UI  
 添加 XAML 以定义向导的 UI，并添加一些代码以将向导中的一些控件绑定到 ID 字符串。  您创建的向导类似于 Visual Studio. 中的 SharePoint 项目的内置向导。  
  
#### 创建向导 UI  
  
1.  在 **ItemTemplateWizard** 项目中，打开 **WizardWindow.xaml** 文件的快捷菜单，然后选择 **打开** 在设计器中打开窗口。  
  
2.  在 XAML 视图中，用以下 XAML 替换当前 XAML。  XAML 定义一个 UI，该 UI 包含一个标题、用于指定自定义操作的行为的控件以及位于窗口底部的导航按钮。  
  
    > [!NOTE]  
    >  在添加此代码后，项目将会出现一些编译错误。  在添加后面的步骤中的代码之后，这些错误将消失。  
  
     [!code-xml[SPExtensibility.ProjectItem.CustomAction#9](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/itemtemplatewizard/wizardwindow.xaml#9)]  
  
    > [!NOTE]  
    >  此 XAML 创建的 windows <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> 从基类派生。  在添加自定义 WPF 对话框向 Visual Studio 时，我们建议您从该选件类派生自己的对话框具有一致的样式与可能发生与模式对话框的 Visual Studio 的其他对话框，并避免问题。  有关更多信息，请参见[创建和管理有模式对话框](../extensibility/creating-and-managing-modal-dialog-boxes.md)。  
  
3.  如果正在开发 Visual Basic 项目，请在 `Window` 元素的 `x:Class` 属性的 `WizardWindow` 类名称中移除 `ItemTemplateWizard` 命名空间。  此元素在 XAML 的第一行。  完成后，第一行应类似于以下代码：  
  
    ```  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  在 WizardWindow.xaml 文件的代码隐藏文件后，用以下代码替换当前代码。  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#7](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/itemtemplatewizard/wizardwindow.xaml.cs#7)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#7](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/vb/itemtemplatewizard/wizardwindow.xaml.vb#7)]  
  
## 实现向导  
 通过实现 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 接口来定义向导的功能。  
  
#### 实现向导  
  
1.  在 **ItemTemplateWizard** 项目中，打开 **CustomActionWizard** 代码文件，并用下面的代码替换此文件中的当前代码：  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#8](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/itemtemplatewizard/customactionwizard.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#8](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/vb/itemtemplatewizard/customactionwizard.vb#8)]  
  
## 检查点  
 演练进行到此时，向导的所有代码都位于项目中。  生成项目以确保编译项目时不会出错。  
  
#### 生成项目  
  
1.  在菜单栏上，依次选择 **Build**，**生成解决方案**。  
  
## 将向导与项模板关联  
 既然实现了向导，您必须将其与 **自定义操作** 项目模板通过完成以下三个主要步骤：  
  
1.  用强名称对向导程序集进行签名。  
  
2.  获取向导程序集的公钥标记。  
  
3.  在**“自定义操作”**项模板的 .vstemplate 文件中添加对向导程序集的引用。  
  
#### 用强名称对向导程序集进行签名  
  
1.  在 **解决方案资源管理器**，则从 **ItemTemplateWizard** 项目节点的快捷菜单，然后选择 **属性**。  
  
2.  在**“签名”**选项卡上，选中**“为程序集签名”**复选框。  
  
3.  在 **选择强名称密钥文件** 列表中，选择 **\<New...\>**。  
  
4.  在 **创建强名称密钥** 对话框中，输入名称，清除 **使用密码保护密钥文件** 复选框，然后选择 **确定** 按钮。  
  
5.  在菜单栏上，依次选择 **Build**，**生成解决方案**。  
  
#### 获取向导程序集的公钥标记  
  
1.  在 Visual Studio 命令提示符窗口中，运行以下命令，替换 *PathToWizardAssembly* 使用完整路径为 ItemTemplateWizard 项目生成的 ItemTemplateWizard.dll 程序集在开发计算机上。  
  
    ```  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     ItemTemplateWizard.dll 程序集的公钥标记会写入到 Visual Studio 命令提示符窗口中。  
  
2.  将 Visual Studio 命令提示符窗口保持打开状态。  您将需要公钥标记完成下一个过程。  
  
#### 在 .vstemplate 文件中添加对向导程序集的引用  
  
1.  在 **解决方案资源管理器**，展开 **ItemTemplate** 项目节点，然后打开 ItemTemplate.vstemplate 文件。  
  
2.  在该文件末尾附近的 `</TemplateContent>` 和 `</VSTemplate>` 标记之间添加以下 `WizardExtension` 元素。  用您在上一过程中获得的公钥标记替换 `PublicKeyToken` 属性的 *YourToken* 值。  
  
    ```  
    <WizardExtension>  
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>  
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     有关 `WizardExtension` 元素的更多信息，请参见 [WizardExtension 元素（Visual Studio 模板）](../extensibility/wizardextension-element-visual-studio-templates.md)。  
  
3.  保存并关闭文件。  
  
## 将可替换参数添加到项模板的 Elements.xml 文件中  
 将多个可替换参数添加到 ItemTemplate 项目中的 Elements.xml 文件中。  将在之前定义的 `CustomActionWizard` 类的 `PopulateReplacementDictionary` 方法中初始化这些参数。  当用户向某个项目添加“自定义操作”项目项时，Visual Studio 会自动将新项目项中的 Elements.xml 文件中的这些参数替换为在向导中指定的值。  
  
 一个可替换参数是以美元符号的标记 \($\) 字符开始和结束。  除了定义您的可替换参数外，还可以使用 SharePoint 项目系统定义和初始化的内置参数。  有关更多信息，请参见[可替换参数](../sharepoint/replaceable-parameters.md)。  
  
#### 向 Elements.xml 文件添加可替换参数  
  
1.  在 ItemTemplate 项目中，用以下 XML 替换 Elements.xml 文件的内容。  
  
    ```  
  
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
  
     新的 XML 会将 `Id`、`GroupId`、`Location`、`Description` 和 `Url` 特性的值更改为可替换参数。  
  
2.  保存并关闭文件。  
  
## 向 VSIX 包添加向导  
 在 VSIX 项目中的 source.extension.vsixmanifest 文件中，添加对向导项目，使其部署了与包含项目项的 VSIX 包。  
  
#### 向 VSIX 包添加向导  
  
1.  在 **解决方案资源管理器**，请打开快捷菜单在 CustomActionProjectItem 项目的 **source.extension.vsixmanifest** 文件，然后选择 **打开** 将在清单编辑器中打开该文件。  
  
2.  在清单编辑器中，选择 **资产** 选项卡，然后选择 **新建** 按钮。  
  
     **添加新资产** 出现对话框。  
  
3.  在 **类型** 列表中，选择 **Microsoft.VisualStudio.Assembly**。  
  
4.  在 **源** 列表中，选择 **当前解决方案中的项目**。  
  
5.  在 **项目** 列表中，选择 **ItemTemplateWizard**，然后选择 **确定** 按钮。  
  
6.  在菜单栏上，依次选择 **Build**，**生成解决方案**，然后确保解决方案已生成且未发生错误。  
  
## 测试向导  
 现在已经准备好对向导进行测试。  首先，调试在 Visual Studio 的实验实例的 CustomActionProjectItem 解决方案的开头。  然后测试自定义操作"项目项的向导在 Visual Studio 的实验实例的 SharePoint 项目。  最后，生成并运行 SharePoint 项目，以验证此自定义操作是否按预期工作。  
  
#### 开始调试解决方案  
  
1.  重新启动使用管理凭据的 Visual Studio，然后打开 CustomActionProjectItem 解决方案。  
  
2.  在 ItemTemplateWizard 项目中，打开 CustomActionWizard 代码文件，然后将断点添加到第一个代码行中 `RunStarted` 方法的。  
  
3.  在菜单栏上，依次选择 **调试**，**异常**。  
  
4.  在 **异常** 对话框中，确保清除 **公共语言运行时异常** 的 **引发** 和 **用户未处理的** 复选框，然后选择 **确定** 按钮。  
  
5.  开始调试通过选择 F5 键或，在菜单栏上，选择 **调试**，**启动调试**。  
  
     Visual Studio 将扩展安装到 %UserProfile% \\ AppData \\ local \\ Microsoft \\ VisualStudio \\ 11.0Exp \\ extensions \\ Contoso \\ custom action project item \\ 1.0 中启动 Visual Studio 的实验实例。  在此 Visual Studio 实例中测试项目项。  
  
#### 在 Visual Studio 中测试向导  
  
1.  在 Visual Studio 的实验实例中，在菜单栏上，依次选择 **文件**，**新建**，**项目**。  
  
2.  外接 **visual C\#** 或 **Visual Basic** 节点 \(具体取决于项目模板支持的语言\)，再展开 **SharePoint** 节点，然后选择 **2010** 节点。  
  
3.  在项目模板列表中，选择 **SharePoint 2010 项目**，将项目命名为 **CustomActionWizardTest**，然后选择 **确定** 按钮。  
  
4.  在 **SharePoint 自定义向导**，输入要用于调试的网站的 URL，然后选择 **完成** 按钮。  
  
5.  在 **解决方案资源管理器**，请打开项目节点的快捷菜单上，选择 **添加**，然后选择 **新建项**。  
  
6.  在 **添加新项目\- CustomItemWizardTest** 对话框中，展开 **SharePoint** 节点，然后展开 **2010** 节点。  
  
7.  在项目项的列表中，选择 **自定义操作** 项目，然后选择 **添加** 按钮。  
  
8.  验证另一个 Visual Studio 实例中的代码是否会在您之前在 `RunStarted` 方法中设置的断点处停止。  
  
9. 继续选择 F5 键调试该项目，在菜单栏上，选择 **调试**，**继续**。  
  
     这将显示“SharePoint 自定义向导”。  
  
10. 在 **位置**下，选择 **列表编辑器** 选项按钮。  
  
11. 在 **组 ID** 列表中，选择 **通信**。  
  
12. 在 **标题** 框中，输入 **SharePoint 开发中心**。  
  
13. 在 **说明** 框中，输入 **打开 SharePoint 开发人员中心\) 网站**。  
  
14. 在 **URL** 框中，输入 **http:\/\/msdn.microsoft.com\/sharepoint\/default.aspx**，然后选择 **完成** 按钮。  
  
     isual studio 将添加一个名为"项目的 **CustomAction1** 的一个项目并在编辑器中打开 Elements.xml 文件。  验证 Elements.xml 是否包含您在向导中指定的值。  
  
#### 测试 SharePoint 中的自定义操作  
  
1.  在 Visual Studio 的实验实例中，选择 F5 键或，在菜单栏上，选择 **调试**，**启动调试**。  
  
     该项的 **网站 URL** 属性进行打包并部署到 SharePoint。站点指定的自定义操作，这样，浏览器将打开此网站的默认页。  
  
    > [!NOTE]  
    >  如果 **脚本调试被禁用** 出现对话框，请选择 **是** 按钮。  
  
2.  在列表中 SharePoint 网站的区域，选择 **任务** 链接。  
  
     **任务–所有任务** 页。  
  
3.  在功能区的 **列表工具** 选项卡中，选择 **列表** 选项，然后，在 **设置** 组中，选择 **列表设置**。  
  
     **列表设置** 页。  
  
4.  在归为在页的顶部附近的 **通信** 下，选择 **SharePoint 开发中心** 链接，验证浏览器中打开网站 http:\/\/msdn.microsoft.com\/sharepoint\/default.aspx，然后关闭浏览器。  
  
## 清理开发计算机  
 测试完项目项之后，从 Visual Studio 的实验实例中移除项目项模板。  
  
#### 清理开发计算机  
  
1.  在 Visual Studio 的实验实例中，在菜单栏上，依次选择 **工具**，**扩展和更新**。  
  
     **扩展和更新** 对话框打开。  
  
2.  在扩展列表中，选择 **自定义操作"项目项** 扩展，然后选择 **卸载** 按钮。  
  
3.  在出现的对话框中，选择 **是** 按钮以确认您要卸载该扩展，然后选择 **立即重新启动** 按钮来卸载。  
  
4.  关闭 Visual Studio 的实验实例 \(和 CustomActionProjectItem 解决方案处于打开状态的实例\) 两个实例 Visual Studio。  
  
## 请参阅  
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)   
 [如何：使用向导来处理项目模板](../Topic/How%20to:%20Use%20Wizards%20with%20Project%20Templates.md)   
 [默认自定义操作位置和 ID](http://go.microsoft.com/fwlink/?LinkId=181964)  
  
  