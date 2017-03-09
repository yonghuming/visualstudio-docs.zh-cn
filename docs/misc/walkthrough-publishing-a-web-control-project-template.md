---
title: "演练：发布 Web 控件项目模板 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "模板, Web 控件"
  - "Web 控件模板"
ms.assetid: b56490f8-38bd-4220-a17e-5ebb30d3ac78
caps.latest.revision: 22
caps.handback.revision: 22
manager: "douge"
---
# 演练：发布 Web 控件项目模板
可以创建 Web 控件项目模板，该模板可用作其他 Web 控件项目的基础。 也可将该模板作为 VSIX 扩展来分发。  
  
 若要分发 VSIX 扩展，建议你将其添加到 Visual Studio 库网站，因为开发人员可以使用“扩展管理器”从中浏览新扩展和已更新的扩展。 要分发扩展，还可以将扩展置于不同的服务器上或者刻录到 CD 或其他媒体。  
  
 本演练为两个相关演练之一，介绍如何创建 Web 控件项目模板，然后分发该模板。 另一个演练，即[演练: 发布 Visual Studio 扩展](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)，介绍如何创建和分发 Web 控件。  
  
 本演练包含以下各节：  
  
-   在 VSIX 扩展中创建 Web 控件项目模板  
  
-   将模板发布到 Visual Studio 库  
  
-   安装 Visual Studio 库中的模板  
  
-   测试安装的模板  
  
-   向模板添加“调试操作向导”  
  
## 系统必备  
 要完成本演练，必须了解 Web 控件，知道如何创建项目、设置项目属性和使用 Visual Studio 实验实例。 计算机上须安装有 Visual Studio 和 Visual Studio SDK。 在开始此演练之前，必须完成[演练: 发布 Visual Studio 扩展](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)。  
  
## 在 VSIX 扩展中创建 Web 控件项目模板  
 要创建 Web 控件项目模板，首先要创建 Web 控件项目。 本演练从你在[演练: 发布 Visual Studio 扩展](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)中创建的 ColorTextControl Web 控件项目开始。  
  
 将项目模板发布到 Visual Studio 库之前，请使用“模板导出为 VSIX”向导，将模板导出为 VSIX 扩展并为其提供一个图标（用于帮助在“扩展管理器”中识别它）和一个图像（用于阐释其用途）。  
  
#### 准备用于分发的 Web 控件项目  
  
1.  在 Visual Studio 中，打开 MyWebControls 项目。  
  
2.  使用“扩展管理器”从“Visual Studio 库”网站下载“导出模板向导”。  
  
     安装此向导后，若项目处于打开状态，则“将模板导出为 VSIX”将出现在“文件”菜单上。  
  
3.  在“文件”菜单上，单击“将模板导出为 VSIX”。  
  
     ![File menu Export Project as VSIX](../misc/media/pcwc_exportasvsix.png "PCWC\_ExportAsVsix")  
  
4.  在“选择模板类型”页上，选择“项目模板”，然后选择 MyWebControls.csproj。 单击“下一步”。  
  
     ![选择项目模板](../misc/media/pcwc_choosetemplate.png "PCWC\_ChooseTemplate")  
  
5.  在“选择模板选项”页上，将“模板名”设为`Extensibility Color Text Web Toolbox Control`，将“模板说明”设为`Color text web control project that produces a VSIX extension.`  
  
6.  在“图标图像”框旁，单击“浏览”。 在“文件名”框中，键入 `*.*`。 找到 Color.bmp 并单击“打开”。  
  
7.  在“预览图像”框旁，单击“浏览”。 在“文件名”框中，键入 `*.*`。 找到 ScreenShot.bmp 并单击“打开”。 单击“下一步”。  
  
     ![选择模板选项](../misc/media/pcwc_selecttemplateoptions2.png "PCWC\_SelectTemplateOptions2")  
  
8.  在“选择 VSIX 选项”页上，将“产品名称”更改为 `Extensibility Color Text Web Control Template`。  
  
9. 如果需要，可以更改“公司名称”、“版本”、“许可证”和“入门指南 URL”。  
  
10. 取消勾选“自动将模板导入 Visual Studio”选项。 单击“完成”。  
  
     ![取消选中自动导入模板](../misc/media/pcwc_.png "PCWC\_")  
  
     在 Windows 资源管理器的 ..\\My Documents\\Visual Studio *\<version\>*\\My Exported Templates\\ 文件夹中，列有 Extensibility Color Text Web Control Template.vsix。  
  
## 将模板发布到 Visual Studio 库  
 现在已准备好将项目模板发布到 Visual Studio 库。  
  
#### 将模板发布到 Visual Studio 库  
  
1.  在 Web 浏览器中，打开 [Visual Studio 库](http://go.microsoft.com/fwlink/?LinkId=194329)网站。  
  
2.  在右上角，单击“登录”。  
  
3.  使用您的 Microsoft 帐户登录。 如果没有 Microsoft 帐户，可以在此处创建一个。  
  
4.  单击“上载”。  
  
5.  在“步骤 1: 扩展类型”中，选择“项目或项模板”，然后单击“下一步”。  
  
6.  在“步骤 2: 上载”中，单击“浏览”。 在 \\My Exported Templates\\ 文件夹中，选择“Extensibility Color Text Web Control Template.vsix”。 单击“下一步”。  
  
7.  在“步骤 3: 基本信息”中，将显示来自“将模板导出为 VSIX 向导”的信息。  
  
8.  将“类别”设为 `ASP.NET`，将“标记”设为`toolbox, web control, templates`。  
  
9. 读取并同意“贡献协议”，然后在框中键入显示的文本。  
  
10. 单击“创建贡献”，然后单击“发布”。  
  
11. 在 Visual Studio 库中搜索可扩展性彩色文本 Web 控件模板。 将显示该模板的列表。  
  
     ![新 Web 控件模板列表](../misc/media/pcwc_templatelisting.png "PCWC\_TemplateListing")  
  
## 安装 Visual Studio 库中的模板  
 发布 Web 控件项目模板后，请在 Visual Studio 中进行安装和测试。  
  
#### 在 Visual Studio 中安装 Web 控件项目模板  
  
1.  在 Visual Studio 的“工具”菜单中，单击“扩展管理器”。  
  
2.  单击“联机库”，然后搜索“可扩展性彩色文本 Web 控件模板”。 将显示该模板的列表。  
  
3.  单击**“下载”**。 下载该扩展后，单击“安装”。  
  
## 测试安装的模板  
 现在，可以使用“可扩展性彩色文本 Web 控件项目模板”来创建自定义 Web 控件。 不需要一个个手动创建。 本节说明如何使用模板来创建 BlueColorTextControl Web 控件。  
  
#### 创建基于此模板的 Web 控件  
  
1.  在**“文件”**菜单上指向**“新建”**，然后单击**“项目”**。  
  
2.  在左窗格中，单击“联机模板”，展开“模板”，然后单击“ASP.NET”。 在中心窗格中，单击“扩展性彩色文本 Web 控件模板”。  
  
     ![Select the extensibility color text web template](../Image/PCWC_NewProjectTemplate.png "PCWC\_NewProjectTemplate")  
  
3.  将“名称”设为 `MoreWebControls`。 单击“确定”。  
  
4.  在“解决方案资源管理器”中，将 ColorTextControl.cs 重命名为 BlueColorTextControl.cs。  
  
5.  双击 BlueColorTextControl.cs 以在编辑器中将其打开。  
  
6.  在 `ToolboxData` 属性中，将两个 `ColorTextControl` 替换为 `BlueColorTextControl`。  
  
     这些值指定在设计时将控件从“工具箱”拖至网页的时候，为控件生成的开始和结束标记。  它们必须与控件类的名称匹配，该名称也是将出现在“工具箱”中的控件的名称。  
  
     控件类源代码的开头现在应类似于下面的代码。  
  
    ```  
    namespace MoreWebControls { [DefaultProperty("Text")] [ToolboxData("<{0}:BlueColorTextControl runat=server> </{0}:BlueColorTextControl>")] [ProvideToolboxControl("MoreWebControls", false)] public class BlueColorTextControl : WebControl {  
  
    ```  
  
7.  在 `get` 方法中，将 `color:green` 更改为 `color:blue`。  
  
    ```  
    get { String s = (String)ViewState["Text"]; return "<span style='color:blue'>" + s + "</span>"; }  
    ```  
  
     这将使 span 标记（使其变为蓝色）中的文本换行。  
  
8.  生成 MoreWebControls 项目。  
  
## 测试新的 Web 控件  
 现在，可以测试新 Web 控件在“工具箱”中是否可用。 但是，即使 MoreWebControls 项目处于打开状态，按 F5 也不会启动用于测试该控件的 Visual Studio 的实验实例。 这是因为该项目是基于扩展性彩色文本 Web 控件模板的，该模板尚不能设置调试操作。 （下一节介绍如何向模板添加设置调试操作的向导。） 现在，若要测试该控件，可采取以下步骤。  
  
#### 测试新的 Web 控件  
  
1.  若要打开 Visual Studio 的实验实例，请启动实验实例。  
  
    1.  在 [!INCLUDE[win7](../debugger/includes/win7_md.md)] 中，使用“开始”菜单 \(“Start\/All Programs\/Microsoft Visual Studio \<version\> SDK\/Tools\/Start Experimental Instance of Microsoft Visual Studio \<version\>”。  
  
    2.  在 [!INCLUDE[win81](../debugger/includes/win81_md.md)] 的“开始”屏幕中，键入**启动 Microsoft Visual Studio \<version\> 的实验实例**。  
  
2.  创建 Web 应用程序项目。  
  
3.  在项目中，打开 default.aspx。 请确保显示“源”视图。  
  
4.  在“工具箱”的“MoreWebControls”类别中，应显示有“BlueColorTextControl”。  
  
     ![MoreWebControls BlueColorTextControl](../Image/PCWC_Toolbox2.png "PCWC\_Toolbox2")  
  
5.  将 BlueColorTextControl 拖到网页 `body` 标记中的某个位置。  
  
6.  在 `ColorTextControl` 标记中，添加 `Text` 属性，并将其值设置为 `Think Blue!`。 所得标记应与如下标记类似。  
  
    ```  
    <cc1:BlueColorTextControl ID="BlueColorTextControl1" Text="Think Blue!" runat="server" />  
  
    ```  
  
7.  按 F5 以启动 ASP.NET 开发服务器。  
  
     BlueColorTextControl 的显示应与下图类似。  
  
     ![BlueColorTextControl 呈现深蓝色](../misc/media/pcwc_thinkblue.png "PCWC\_ThinkBlue")  
  
8.  关闭 ASP.NET 开发服务器。  
  
9. 关闭 Visual Studio 的实验实例。  
  
## 向模板添加“调试操作向导”  
 如上节所述，在 MoreWebControls 项目处于打开状态时按 F5，不会打开 Visual Studio 的实验实例。 而是显示消息：“不能直接启动输出类型为类库的项目”。 项目不知道实验实例的位置时，将发生这种情况。 但是，你可以启用一个模板，用于确定目标计算机上实验实例的位置并设置适当的调试操作。 之后，计算机上基于该模板的所有项目均将按预期响应 F5。  
  
 Visual Studio SDK 中所含的每个可扩展性项目模板均包含一个向导，该向导在安装过程中运行、在目标计算机上找到实验实例并设置调试操作。 可以创建自己的向导用于执行此操作，并且可以将其包含在你所分发的每个模板中。  
  
 若要将调试操作向导添加到可扩展性彩色文本 Web 控件模板，必须删除该模板的第一个版本，向它添加向导，然后重新创建它。  
  
#### 删除模板的第一个版本  
  
1.  在 Visual Studio 库网站左上角，单击“我的贡献”。 将显示“扩展性彩色文本 Web 控件模板”列表。  
  
2.  若要从 Visual Studio 库中永久删除你的项目模板，单击“删除”。  
  
3.  在 Visual Studio 的“工具”菜单中，单击“扩展管理器”。  
  
4.  选择“扩展性彩色文本 Web 控件模板”，然后单击“卸载”。  
  
5.  关闭“扩展管理器”。  
  
6.  关闭 MoreWebControls 解决方案。  
  
7.  关闭 Visual Studio。  
  
8.  删除 MoreWebControls 解决方案文件夹。  
  
9. 若要完成卸载过程，请重新启动 Visual Studio。  
  
 调试操作向导必须具有 `Microsoft.VisualStudio.TemplateWizard.IWizard` 的公共实现，并且必须使用程序集强名称签名。  
  
#### 创建调试操作向导  
  
1.  在“新项目”对话框框中，创建“Visual C\#”、“Windows”、“类库”项目，并命名为 `MyWizard`。  
  
2.  在新项目中，将 class1.cs 重命名为 MyWizard.cs。  
  
3.  将 MyWizard.cs 的内容替换为以下代码。  
  
    ```  
    using System; using System.Collections.Generic; using System.Linq; using System.Text; using Microsoft.VisualStudio.TemplateWizard; using System.Globalization; using EnvDTE; namespace MyWizard { public class MyWizard : IWizard { public void BeforeOpeningFile(ProjectItem projectItem) { } public void ProjectFinishedGenerating(Project project) { foreach (Configuration config in project.ConfigurationManager) { //Set up the debug options to run "devenv /rootsuffix Exp"; config.Properties.Item("StartAction").Value = 1; //Get the full path to devenv.exe through DTE.FullName config.Properties.Item("StartProgram").Value = project.DTE.FullName; config.Properties.Item("StartArguments").Value = "/rootsuffix Exp"; } } public void ProjectItemFinishedGenerating(ProjectItem projectItem) { } public void RunFinished() { } public void RunStarted(object automationObject, Dictionary<string, string> replacementsDictionary, WizardRunKind runKind, object[] customParams) { } public bool ShouldAddProjectItem(string filePath) { return true; } } }  
  
    ```  
  
4.  向项目添加以下引用。 如果有多个选择，选择具有指向 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 的路径那一个引用。  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
5.  右键单击 MyWizard 项目，然后单击“属性”。 在“签名”选项卡上，选择“为程序集签名”选项。  
  
6.  在“选择强名称密钥文件”列表中，选择“\<新建…\>”。 将显示“创建强名称密钥”对话框。  
  
7.  将“密钥文件名”设为 `key.snk`，并取消勾选“使用密码保护密钥文件”选项。  
  
     ![指定密钥文件](../misc/media/pcwc_strongname.png "PCWC\_StrongName")  
  
8.  单击“确定”将 key.snk 添加到此项目。  
  
9. 将 MyWizard 项目生成为发布版本。 该向导现可供使用。  
  
10. 关闭 MyWizard 解决方案。  
  
#### 纳入向导并重新创建模板  
  
1.  按照前文所述步骤，在 VSIX 扩展中创建 Web 控件项目模板，但进行如下增加和更改操作：  
  
    -   无需再次下载“将模板导出为 VSIX”向导。  
  
    -   在“将模板导出为 VSIX”向导的“选择 VSIX 选项”页的“向导”框中，浏览找到你在之前的步骤中创建的 \\bin\\Release\\MyWizard.dll 文件并选择它。  
  
         ![指定向导程序集](../misc/media/pcwc_wizardassembly.png "PCWC\_WizardAssembly")  
  
    -   系统提示是否覆盖现有的 VSIX 扩展输出文件时，单击“是”。  
  
2.  到达“测试新的 Web 控件”一节时，请按 F5。 这将启动一个 Visual Studio 实验实例。  
  
## 后续步骤  
 本演练演示了如何使用“将模板导出为 VSIX”向导来创建和分发项目模板。 如果需要更多地控制项目模板（例如，要选择出现在“新建项目”对话框中的图标），则必须显式创建项目模板并将其包装在 VSIX 扩展中。 有关详细信息，请参阅 Visual Studio 博客网站上的[Creating and Sharing Project & Item Templates（创建并共享项目和项模板）](http://go.microsoft.com/fwlink/?LinkId=194551)。  
  
## 请参阅  
 [传送 Visual Studio 扩展](../extensibility/shipping-visual-studio-extensions.md)