---
title: "演练： 使用项目模板创建网站栏项目项，第 2 部分 |Microsoft 文档"
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
ms.assetid: da14207d-ac09-41ba-b387-c7f881b2a366
caps.latest.revision: "54"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 82a3793920b1e35f9077ee68eaa2f18db07d2d04
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2"></a>演练：使用项目模板创建网站栏项目项（第 2 部分）
  定义自定义类型的 SharePoint 项目项并将其与 Visual Studio 中的项目模板后，你可能还想要模板提供的向导。 该向导可用于从用户收集信息，在他们使用你的模板来创建一个包含项目项的新项目。 你收集的信息可以用于初始化项目项。  
  
 在本演练中，你将对网站栏项目模板中所示添加向导[演练： 使用项目模板，第 1 部分中创建网站栏项目项](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)。 当用户创建网站栏项目时，该向导将收集有关站点列 （如其基类型和组） 的信息，并将此信息添加到新的项目中的 Elements.xml 文件。  
  
 本演练演示了下列任务：  
  
-   创建自定义 SharePoint 项目项类型与项目模板的向导。  
  
-   定义自定义向导 UI 类似于 Visual Studio 中的 SharePoint 项目中的内置的向导。  
  
-   创建两个*SharePoint 命令*，用于运行该向导时调入的本地 SharePoint 站点。 SharePoint 命令是 Visual Studio 扩展可用于调用 SharePoint 服务器对象模型中的 Api 的方法。 有关详细信息，请参阅[调入 SharePoint 对象模型](../sharepoint/calling-into-the-sharepoint-object-models.md)。  
  
-   使用可替换参数来初始化此向导中收集的数据与 SharePoint 项目文件。  
  
-   在每个新的网站栏项目实例中创建新的.snk 文件。 此文件用于输出，以便可以将 SharePoint 解决方案程序集部署到全局程序集缓存对项目进行签名。  
  
-   调试和测试该向导。  
  
> [!NOTE]  
>  你可以下载包含已完成的项目、 代码和从以下位置在本演练中的其他文件的示例： [http://go.microsoft.com/fwlink/?LinkId=191369](http://go.microsoft.com/fwlink/?LinkId=191369)。  
  
## <a name="prerequisites"></a>先决条件  
 若要执行本演练，你必须首先创建 SiteColumnProjectItem 解决方案通过完成[演练： 使用项目模板，第 1 部分中创建网站栏项目项](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)。  
  
 你还需要以下组件来完成本演练的开发计算机上：  
  
-   受支持的 Windows、 SharePoint 和 Visual Studio 的版本。 有关详细信息，请参阅[有关开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio SDK。 本演练使用**VSIX 项目**SDK 创建 VSIX 包来部署项目项中的模板。 有关详细信息，请参阅[扩展 Visual Studio 中的 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
 以下概念的知识将会很有用，但不是要求必须完成本演练：  
  
-   用于 Visual Studio 中的项目和项模板的向导。 有关详细信息，请参阅[如何： 使用项目模板时使用向导](../extensibility/how-to-use-wizards-with-project-templates.md)和<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>接口。  
  
-   在 SharePoint 中的网站栏。 有关详细信息，请参阅[列](http://go.microsoft.com/fwlink/?LinkId=183547)。  
  
##  <a name="wizardcomponents"></a>了解向导组件  
 在本演练演示了此向导包含多个组件。 下表介绍这些组件。  
  
|组件|描述|  
|---------------|-----------------|  
|向导实现|这是一个类，名为`SiteColumnProjectWizard`，该类实现<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>接口。 此接口定义 Visual Studio 会调用向导启动和完成后，、 在某些时候向导时运行时的方法。|  
|向导 UI|这是基于 WPF 的窗口中，名为`WizardWindow`。 此窗口包含两个用户控件，名为`Page1`和`Page2`。 这些用户控件表示这两页的向导。<br /><br /> 在此演练中，<xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>向导实现的方法会显示向导 UI。|  
|向导数据模型|这是名为一个中间类`SiteColumnWizardModel`，该属性提供之间向导 UI 和向导实现的一层。 此示例使用此类来帮助抽象向导实现和向导 UI 相互;此类不是所有向导的必需的组件。<br /><br /> 在本演练中，向导实现传递`SiteColumnWizardModel`向导窗口显示向导 UI 时的对象。 向导 UI 使用此对象的方法，以将控件的值保存在 UI 中，并执行任务，例如验证输入的站点 URL 有效。 用户完成向导后，向导实现使用`SiteColumnWizardModel`对象确定 UI 的最终状态。|  
|项目签名管理器|这是一个帮助器类，名为`ProjectSigningManager`，用于通过向导实现每个新的项目实例中创建新的 key.snk 文件。|  
|SharePoint 命令|这些是向导数据模型用于到本地 SharePoint 站点中运行该向导时调用的方法。 因为 SharePoint 命令必须以.NET Framework 3.5 为目标，另一个程序集比其余向导代码中实现这些命令。|  
  
## <a name="creating-the-projects"></a>创建项目  
 若要完成本演练，你需要将多个项目添加到你在中创建 SiteColumnProjectItem 解决方案[演练： 使用项目模板，第 1 部分中创建网站栏项目项](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md):  
  
-   WPF 项目。 将实现<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>接口，并在此项目中定义的向导 UI。  
  
-   一个定义 SharePoint 命令的类库项目。 此项目必须面向.net Framework 3.5。  
  
 首先演练创建项目。  
  
#### <a name="to-create-the-wpf-project"></a>创建 WPF 项目  
  
1.  在[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，打开 SiteColumnProjectItem 解决方案。  
  
2.  在**解决方案资源管理器**，打开快捷菜单**SiteColumnProjectItem**解决方案节点，选择**添加**，然后选择**新项目**.  
  
3.  在顶部**添加新项目**对话框框中，请确保**.NET Framework 4.5**选择在列表中的.NET framework 的版本。  
  
4.  展开**Visual C#**节点或**Visual Basic**节点，然后选择**Windows**节点。  
  
5.  在项目模板列表中，选择**WPF 用户控件库**，命名该项目**ProjectTemplateWizard**，然后选择**确定**按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]将添加**ProjectTemplateWizard**到解决方案的项目，并打开默认 UserControl1.xaml 文件。  
  
6.  从项目中删除 UserControl1.xaml 文件。  
  
#### <a name="to-create-the-sharepoint-commands-project"></a>若要创建 SharePoint 命令项目  
  
1.  在**解决方案资源管理器**，打开 SiteColumnProjectItem 解决方案节点的快捷菜单，选择**添加**，然后选择**新项目**。  
  
2.  在顶部**添加新项目**对话框框中，选择**.NET Framework 3.5**在列表中的.NET framework 的版本。  
  
3.  展开**Visual C#**节点或**Visual Basic**节点，然后选择**Windows**节点。  
  
4.  选择**类库**项目模板，将项目**SharePointCommands**，然后选择**确定**按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]将添加**SharePointCommands**到解决方案的项目并打开默认 Class1 代码文件。  
  
5.  从项目中删除 Class1 代码文件。  
  
## <a name="configuring-the-projects"></a>配置项目  
 在创建该向导之前，必须添加某些代码文件和项目的程序集引用。  
  
#### <a name="to-configure-the-wizard-project"></a>若要配置向导项目  
  
1.  在**解决方案资源管理器**，打开快捷菜单**ProjectTemplateWizard**项目节点，，然后选择**属性**。  
  
2.  在**项目设计器**，选择**应用程序**对于 Visual C# 项目的选项卡或**编译**Visual Basic 项目的选项卡。  
  
3.  请确保目标框架设置为.NET Framework 4.5，而非.NET Framework 4.5 客户端配置文件。  
  
     有关详细信息，请参阅[如何：面向 .NET Framework 的某个版本](../ide/how-to-target-a-version-of-the-dotnet-framework.md)。  
  
4.  打开的快捷菜单**ProjectTemplateWizard**项目，选择**添加**，然后选择**新项**。  
  
5.  选择**Window (WPF)**项，该项**WizardWindow**，然后选择**添加**按钮。  
  
6.  添加两个**用户控件 (WPF)**项目到项目中，并将它们命名**页 1**和**Page2**。  
  
7.  将四个代码文件添加到项目中，并为他们提供以下名称：  
  
    -   SiteColumnProjectWizard  
  
    -   SiteColumnWizardModel  
  
    -   ProjectSigningManager  
  
    -   CommandIds  
  
8.  打开的快捷菜单**ProjectTemplateWizard**项目节点，，然后选择**添加引用**。  
  
9. 展开**程序集**节点，选择**扩展**节点，，然后选择以下程序集旁边的复选框：  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.OLE.Interop  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.visualstudio.shell.11.0 的引用  
  
    -   Microsoft.VisualStudio.Shell.Interop.10.0  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
10. 选择**确定**按钮以将程序集添加到项目。  
  
11. 在**解决方案资源管理器**下**引用**文件夹**ProjectTemplateWizard**项目，选择**EnvDTE**。  
  
12. 在**属性**窗口中，更改的值**嵌入互操作类型**属性**False**。  
  
13. 如果你要开发 Visual Basic 项目，ProjectTemplateWizard 命名空间导入你的项目使用**项目设计器**。  
  
     有关详细信息，请参阅[如何： 添加或删除已导入命名空间 &#40;Visual Basic &#41;](../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md).  
  
#### <a name="to-configure-the-sharepointcommands-project"></a>若要配置 SharePointCommands 项目  
  
1.  在**解决方案资源管理器**，选择**SharePointCommands**项目节点。  
  
2.  在菜单栏上，选择**项目**，**添加现有项**。  
  
3.  在**添加现有项**对话框中，浏览到包含 ProjectTemplateWizard 项目的代码文件的文件夹，然后选择**CommandIds**代码文件。  
  
4.  选择箭头旁边**添加**按钮，，然后选择**添加为链接**上显示的菜单中的选项。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]将添加到代码文件**SharePointCommands**为链接的项目。 代码文件位于**ProjectTemplateWizard**项目，但文件中的代码也会被编译中**SharePointCommands**项目。  
  
5.  在**SharePointCommands**项目中，添加名为命令的另一个代码文件。  
  
6.  选择 SharePointCommands 项目，然后，在菜单栏上，选择**项目**，**添加引用**。  
  
7.  展开**程序集**节点，选择**扩展**节点，，然后选择以下程序集旁边的复选框：  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
8.  选择**确定**按钮以将程序集添加到项目。  
  
## <a name="creating-the-wizard-model-signing-manager-and-sharepoint-command-ids"></a>创建向导模型，签名管理器中，和 SharePoint 命令 Id  
 将代码添加到 ProjectTemplateWizard 项目以在此示例中实现以下组件：  
  
-   SharePoint 命令 Id。 这些字符串确定此向导使用的 SharePoint 命令。 稍后在本演练中，将向 SharePointCommands 项目来实现命令来添加代码。  
  
-   向导数据模型。  
  
-   项目签名管理器。  
  
 有关这些组件的详细信息，请参阅[了解向导组件](#wizardcomponents)。  
  
#### <a name="to-define-the-sharepoint-command-ids"></a>若要定义 SharePoint 命令 Id  
  
1.  在 ProjectTemplateWizard 项目中，打开 CommandIds 代码文件，然后将此文件的全部内容替换为以下代码。  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/commandids.cs#5)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/commandids.vb#5)]  
  
#### <a name="to-create-the-wizard-model"></a>若要创建向导模型  
  
1.  打开 SiteColumnWizardModel 代码文件中，并将此文件的全部内容替换为下面的代码。  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.vb#6)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.cs#6)]  
  
#### <a name="to-create-the-project-signing-manager"></a>若要创建的项目签名管理器  
  
1.  打开 ProjectSigningManager 代码文件中，然后将此文件的全部内容替换为以下代码。  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.vb#8)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.cs#8)]  
  
## <a name="creating-the-wizard-ui"></a>创建向导 UI  
 添加 XAML 定义用户界面的向导窗口和用户界面提供向导页中，两个用户控件并添加代码以定义窗口和用户控件的行为。 你创建向导类似于 Visual Studio 中的 SharePoint 项目的内置向导。  
  
> [!NOTE]  
>  以下步骤中，将 XAML 或代码添加到你的项目后，你的项目将出现一些编译错误。 在后续步骤中添加代码，这些错误将会消失。  
  
#### <a name="to-create-the-wizard-window-ui"></a>若要创建向导窗口 UI  
  
1.  在 ProjectTemplateWizard 项目中，打开 WizardWindow.xaml 文件的快捷菜单，然后选择**打开**以在设计器中打开窗口。  
  
2.  在设计器的 XAML 视图中，将当前的 XAML 替换下面的 XAML。 XAML 定义的用户界面可包含一个标题、<xref:System.Windows.Controls.Grid>包含向导页中，并在窗口底部的导航按钮。  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#10](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml#10)]  
  
    > [!NOTE]  
    >  在此 XAML 中创建的窗口派生自<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>基类。 当向 Visual Studio 添加自定义 WPF 对话框中时，我们建议从已与其他 Visual Studio 对话框一致样式并避免可能出现的模式对话框问题此类派生对话框。 有关详细信息，请参阅[创建和管理模式对话框](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes)。  
  
3.  如果你要开发 Visual Basic 项目，删除`ProjectTemplateWizard`命名空间从`WizardWindow`中的类名称`x:Class`属性`Window`元素。 此元素是在第一行中的 XAML。 完成后，第一行应类似下面的示例。  
  
    ```  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  打开 WizardWindow.xaml 文件的代码隐藏文件。  
  
5.  此文件的内容替换除`using`替换为以下代码的文件顶部的声明。  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.vb#4)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.cs#4)]  
  
#### <a name="to-create-the-first-wizard-page-ui"></a>若要创建第一个向导页 UI  
  
1.  在 ProjectTemplateWizard 项目中，打开 Page1.xaml 文件的快捷菜单，然后选择**打开**以在设计器中打开用户控件。  
  
2.  在设计器的 XAML 视图中，将当前的 XAML 替换下面的 XAML。 XAML 定义 UI，其中包含一个文本框，用户可以在其中输入他们想要用于调试的本地站点的 URL。 UI 还包括与该用户可以指定的项目是否沙盒的选项按钮。  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#11](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page1.xaml#11)]  
  
3.  如果你正在开发的 Visual Basic 项目，删除`ProjectTemplateWizard`命名空间从`Page1`中的类名称`x:Class`属性`UserControl`元素。 这是在第一行中的 XAML。 完成后，第一行应类似以下。  
  
    ```  
    <UserControl x:Class="Page1"  
    ```  
  
4.  Page1.xaml 文件的内容替换除`using`替换为以下代码的文件顶部的声明。  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.cs#2)]  
  
#### <a name="to-create-the-second-wizard-page-ui"></a>若要创建第二个向导页 UI  
  
1.  在 ProjectTemplateWizard 项目中，打开 Page2.xaml 文件的快捷菜单，然后选择**打开**。  
  
     用户控件将在设计器中打开。  
  
2.  在 XAML 视图中，将当前的 XAML 替换下面的 XAML。 XAML 定义的用户界面可包括选择的网站栏、 用于指定要在库中显示的网站栏在其下的内置或自定义组的组合框和文本框中指定名称的网站栏的基类型的下拉列表。  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#12](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page2.xaml#12)]  
  
3.  如果你正在开发的 Visual Basic 项目，删除`ProjectTemplateWizard`命名空间从`Page2`中的类名称`x:Class`属性`UserControl`元素。 这是在第一行中的 XAML。 完成后，第一行应类似以下。  
  
    ```  
    <UserControl x:Class="Page2"  
    ```  
  
4.  Page2.xaml 文件中，代码隐藏文件的内容替换除`using`替换为以下代码的文件顶部的声明。  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.vb#3)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.cs#3)]  
  
## <a name="implementing-the-wizard"></a>实现向导  
 通过实现定义的向导的主要功能<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>接口。 此接口定义 Visual Studio 会调用向导启动和完成后，、 在某些时候向导时运行时的方法。  
  
#### <a name="to-implement-the-wizard"></a>若要实现向导  
  
1.  在 ProjectTemplateWizard 项目中，打开 SiteColumnProjectWizard 代码文件。  
  
2.  此文件的全部内容替换为以下代码。  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.cs#7)]  
  
## <a name="creating-the-sharepoint-commands"></a>创建 SharePoint 命令  
 创建调入 SharePoint 服务器对象模型的两个自定义命令。 一个命令将确定用户键入向导中的站点 URL 是否有效。 其他命令获取所有的字段类型从指定的 SharePoint 站点，以便用户可以选择要用作其新的网站栏基础哪一。  
  
#### <a name="to-define-the-sharepoint-commands"></a>若要定义 SharePoint 命令  
  
1.  在**SharePointCommands**项目中，打开命令代码文件。  
  
2.  此文件的全部内容替换为以下代码。  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/sharepointcommands/commands.vb#9)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/sharepointcommands/commands.cs#9)]  
  
## <a name="checkpoint"></a>检查点  
 此时在本演练中，该向导的所有代码现在都是项目中。 生成项目，以确保它在编译时没有错误。  
  
#### <a name="to-build-your-project"></a>若要生成你的项目  
  
1.  在菜单栏上，依次选择 **“生成”**、 **“生成解决方案”**。  
  
## <a name="removing-the-keysnk-file-from-the-project-template"></a>从项目模板中删除的 key.snk 文件  
 在[演练： 使用项目模板，第 1 部分中创建网站栏项目项](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)，你创建的项目模板包含一个命名为 key.snk 文件，用于对每个网站栏项目实例进行签名。 此命名为 key.snk 文件不再有必要，因为该向导现在将生成新的 key.snk 文件，每个项目。 从项目模板中删除的 key.snk 文件，并删除对此文件的引用。  
  
#### <a name="to-remove-the-keysnk-file-from-the-project-template"></a>若要从项目模板中删除的 key.snk 文件  
  
1.  在**解决方案资源管理器**下**SiteColumnProjectTemplate**节点，打开快捷菜单**key.snk**文件，然后依次**删除**.  
  
2.  在出现确认对话框中，选择**确定**按钮。  
  
3.  下**SiteColumnProjectTemplate**节点，打开 SiteColumnProjectTemplate.vstemplate 文件，然后从其删除下面的元素。  
  
    ```  
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
    ```  
  
4.  保存并关闭文件。  
  
5.  下**SiteColumnProjectTemplate**节点，打开 ProjectTemplate.csproj 或 ProjectTemplate.vbproj 文件，，然后删除以下`PropertyGroup`从它的元素。  
  
    ```  
    <PropertyGroup>  
      <SignAssembly>true</SignAssembly>  
      <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
    </PropertyGroup>  
    ```  
  
6.  删除以下`None`元素。  
  
    ```  
    <None Include="key.snk" />  
    ```  
  
7.  保存并关闭文件。  
  
## <a name="associating-the-wizard-with-the-project-template"></a>将向导与项目模板相关联  
 现在，你已实现了向导，你必须将关联了向导，并且**网站栏**项目模板。 有三个过程，你必须完成以执行此操作：  
  
1.  向导程序集具有强名称签名。  
  
2.  获取令牌向导程序集的公钥。  
  
3.  .Vstemplate 文件中添加对向导程序集的引用**网站栏**项目模板。  
  
#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>若要使用强名称对向导程序集签名  
  
1.  在**解决方案资源管理器**，打开快捷菜单**ProjectTemplateWizard**项目，，然后选择**属性**。  
  
2.  上**签名**选项卡上，选择**对程序集签名**复选框。  
  
3.  在**选择强名称密钥文件**列表中，选择**\<新建 … >**。  
  
4.  在**创建强名称密钥**对话框框中，清除输入新的密钥文件的名称**保护我使用密码的密钥文件**复选框，然后依次**确定**按钮。  
  
5.  打开的快捷菜单**ProjectTemplateWizard**项目，，然后选择**生成**创建 ProjectTemplateWizard.dll 文件。  
  
#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>若要获取的公钥令牌向导程序集  
  
1.  上**开始菜单**，选择**所有程序**，选择**Microsoft Visual Studio**，选择**Visual Studio Tools**，然后选择**开发人员命令提示**。  
  
     Visual Studio 命令提示符窗口将打开。  
  
2.  运行以下命令，替换*PathToWizardAssembly*替换为你的开发计算机上的 ProjectTemplateWizard 项目的生成 ProjectTemplateWizard.dll 程序集的完整路径：  
  
    ```  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     ProjectTemplateWizard.dll 程序集的公钥令牌写入 Visual Studio 命令提示符窗口。  
  
3.  使 Visual Studio 命令提示符窗口保持打开。 在下面的过程，你将需要公钥标记。  
  
#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>若要添加的.vstemplate 文件中的向导程序集的引用  
  
1.  在**解决方案资源管理器**，展开**SiteColumnProjectTemplate**项目节点并打开 SiteColumnProjectTemplate.vstemplate 文件。  
  
2.  该文件的末尾添加以下`WizardExtension`之间的元素`</TemplateContent>`和`</VSTemplate>`标记。 替换*你的令牌*值`PublicKeyToken`具有你在前面的过程中获得的公钥令牌属性。  
  
    ```  
    <WizardExtension>  
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>  
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     有关详细信息`WizardExtension`元素，请参阅[WizardExtension 元素 &#40;Visual Studio 模板 &#41;](/visualstudio/extensibility/wizardextension-element-visual-studio-templates).  
  
3.  保存并关闭文件。  
  
## <a name="adding-replaceable-parameters-to-the-elementsxml-file-in-the-project-template"></a>将可替换参数添加到项目模板中的 Elements.xml 文件  
 将多个可替换参数添加到 SiteColumnProjectTemplate 项目中的 Elements.xml 文件。 这些参数以进行初始化`RunStarted`中的方法`SiteColumnProjectWizard`前面定义的类。 当用户创建网站栏项目时，Visual Studio 自动将新的项目中的 Elements.xml 文件中的这些参数替换它们在向导中指定的值。  
  
 可替换参数是开始和结束的美元符号 （$） 字符的标记。 除了定义你自己的可替换参数，你可以使用内置的参数定义并由 SharePoint 项目系统初始化。 有关详细信息，请参阅[可替换参数](../sharepoint/replaceable-parameters.md)。  
  
#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>若要向 Elements.xml 文件中添加可替换参数  
  
1.  在 SiteColumnProjectTemplate 项目中，用下列 XML 替换 Elements.xml 文件的内容。  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <Field ID="{$guid5$}"   
             Name="$fieldname$"   
             DisplayName="$fieldname$"   
             Type="$selectedfieldtype$"   
             Group="$selectedgrouptype$">  
      </Field>  
    </Elements>  
    ```  
  
     新的 XML 更改的值`Name`， `DisplayName`， `Type`，和`Group`特性以自定义的可替换参数。  
  
2.  保存并关闭文件。  
  
## <a name="adding-the-wizard-to-the-vsix-package"></a>将向导添加到 VSIX 包  
 若要部署与包含网站栏项目模板的 VSIX 包向导，将对向导项目和 SharePoint 命令项目的引用添加到 VSIX 项目中的 source.extension.vsixmanifest 文件中。  
  
#### <a name="to-add-the-wizard-to-the-vsix-package"></a>将向导添加到 VSIX 包  
  
1.  在**解决方案资源管理器**中**SiteColumnProjectItem**项目中，打开快捷菜单**source.extension.vsixmanifest**文件，然后依次**打开**。  
  
     Visual Studio 将在清单编辑器中打开该文件。  
  
2.  上**资产**选项卡的编辑器中，选择**新建**按钮。  
  
     **添加新资产**对话框随即打开。  
  
3.  在**类型**列表中，选择**Microsoft.VisualStudio.Assembly**。  
  
4.  在**源**列表中，选择**当前解决方案中的项目**。  
  
5.  在**项目**列表中，选择**ProjectTemplateWizard**，然后选择**确定**按钮。  
  
6.  上**资产**选项卡的编辑器中，选择**新建**再次按钮。  
  
     **添加新资产**对话框随即打开。  
  
7.  在**类型**列表中，输入**SharePoint.Commands.v4**。  
  
8.  在**源**列表中，选择**当前解决方案中的项目**。  
  
9. 在**项目**列表中，选择**SharePointCommands**项目，，然后选择**确定**按钮。  
  
10. 在菜单栏上，选择**生成**，**生成解决方案**，并确保解决方案已生成且未发生错误。  
  
## <a name="testing-the-wizard"></a>测试向导  
 现在你就可以测试该向导。 首先，开始调试 Visual Studio 的实验实例中的 SiteColumnProjectItem 解决方案。 然后，在 Visual Studio 的实验实例中测试网站栏项目的向导。 最后，生成并运行项目，以验证站点列按预期方式工作。  
  
#### <a name="to-start-debugging-the-solution"></a>若要开始调试解决方案  
  
1.  使用管理凭据，重新启动 Visual Studio，然后打开 SiteColumnProjectItem 解决方案。  
  
2.  在 ProjectTemplateWizard 项目中，打开 SiteColumnProjectWizard 代码文件中，并将断点添加到代码中的第一行`RunStarted`方法。  
  
3.  在菜单栏上，选择**调试**，**异常**。  
  
4.  在**异常**对话框框中，请确保**引发**和**用户未处理**对应的复选框**公共语言运行时异常**已清除，然后选择**确定**按钮。  
  
5.  开始调试通过选择**F5**关键的或在菜单栏中，选择**调试**，**启动调试**。  
  
     Visual Studio 将在 %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Site Column\1.0 安装扩展，并启动 Visual Studio 的实验实例。 你将在 Visual Studio 的此实例中测试的项目项。  
  
#### <a name="to-test-the-wizard-in-visual-studio"></a>在 Visual Studio 中测试该向导  
  
1.  在实验实例中的 Visual Studio 中，在菜单栏上，选择**文件**，**新建**，**项目**。  
  
2.  展开**Visual C#**节点或**Visual Basic**节点 （具体取决于你的项目模板支持的语言），展开**SharePoint**节点，然后选择**2010年**节点。  
  
3.  在项目模板列表中，选择**网站栏**，命名该项目**SiteColumnWizardTest**，然后选择**确定**按钮。  
  
4.  验证在 Visual Studio 的其他实例中在代码停止在更早版本中设置的断点处`RunStarted`方法。  
  
5.  继续通过选择调试项目**F5**关键的或在菜单栏中，选择**调试**，**继续**。  
  
6.  在**SharePoint 自定义向导**，输入你想要用于调试，站点的 URL，然后选择**下一步**按钮。  
  
7.  中的第二页**SharePoint 自定义向导**，进行以下选择：  
  
    -   在**类型**列表中，选择**布尔**。  
  
    -   在**组**列表中，选择**自定义否列**。  
  
    -   在**名称**框中，输入**我否列**，然后选择**完成**按钮。  
  
     在**解决方案资源管理器**，新的项目出现，其中包含名为的项目项**Field1**，和 Visual Studio 在编辑器中打开项目的 Elements.xml 文件。  
  
8.  确认 Elements.xml 文件包含你在向导中指定的值。  
  
#### <a name="to-test-the-site-column-in-sharepoint"></a>若要在 SharePoint 中测试的网站栏  
  
1.  在 Visual Studio 的实验实例中，选择 F5 键。  
  
     网站栏将被打包并部署到 SharePoint 站点**站点 URL**的项目的属性指定。 Web 浏览器将打开到此站点的默认页面。  
  
    > [!NOTE]  
    >  如果**脚本调试已禁用**对话框出现时，选择**是**按钮以继续调试项目。  
  
2.  上**站点操作**菜单上，选择**站点设置**。  
  
3.  在站点设置页上，在**库**，选择**站点列**链接。  
  
4.  在站点列列表中，确认**自定义否列**组包含名为的列**我否列**，然后关闭 web 浏览器。  
  
## <a name="cleaning-up-the-development-computer"></a>清理开发计算机  
 完成项目项的测试后，从 Visual Studio 的实验实例中删除项目模板。  
  
#### <a name="to-clean-up-the-development-computer"></a>若要清理的开发计算机  
  
1.  在实验实例中的 Visual Studio 中，在菜单栏上，选择**工具**，**扩展和更新**。  
  
     此时，“扩展和更新”对话框打开。  
  
2.  在扩展的列表中，选择**网站栏**，然后选择**卸载**按钮。  
  
3.  在显示的对话框中，选择**是**按钮以确认你要卸载扩展，然后选择**立即重新启动**按钮以完成卸载。  
  
4.  关闭 Visual Studio 的实验实例和 CustomActionProjectItem 解决方案处于打开状态的实例。  
  
     有关如何部署信息[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]扩展，请参阅[传送 Visual Studio 扩展](/visualstudio/extensibility/shipping-visual-studio-extensions)。  
  
## <a name="see-also"></a>另请参阅  
 [演练： 使用项目模板，第 1 部分中创建网站栏项目项](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [定义自定义 SharePoint 项目项类型](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [为 SharePoint 项目项创建项模板和项目模板](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Visual Studio 模板架构参考](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [如何：使用向导来处理项目模板](../extensibility/how-to-use-wizards-with-project-templates.md)  
  
  