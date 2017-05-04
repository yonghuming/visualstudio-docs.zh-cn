---
title: "演练：使用项目模板创建网站栏项目项（第 2 部分） | Microsoft Docs"
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
  - "项目项 [Visual Studio 中的 SharePoint 开发]，创建模板向导"
  - "SharePoint 项目项，创建模板向导"
  - "Visual Studio 中的 SharePoint 开发，定义新项目项类型"
ms.assetid: da14207d-ac09-41ba-b387-c7f881b2a366
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# 演练：使用项目模板创建网站栏项目项（第 2 部分）
  在定义 SharePoint 项目项的自定义类型并将其与 Visual Studio 中的项目模板关联后，可能还需要提供模板向导。  当用户使用模板创建包含项目项的新项目时，您可以使用此向导收集用户的信息。  收集的信息可用于初始化项目项。  
  
 在本演练中，您将为[演练：使用项目模板创建网站栏项目项（第 1 部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)中演示的“网站栏”项目模板添加向导。  当用户创建“网站栏”项目时，此向导将收集有关该网站栏的信息（如其基类型和组），并将此信息添加到新项目的 Elements.xml 文件中。  
  
 本演练将演示以下任务：  
  
-   为与项目模板关联的自定义 SharePoint 项目项类型创建向导。  
  
-   定义一个自定义向导 UI，它类似于 Visual Studio 中的 SharePoint 项目的内置向导。  
  
-   创建两个 *SharePoint 命令*，用于在向导运行时调入本地 SharePoint 网站。  SharePoint 命令是一些方法，Visual Studio 扩展可使用这些方法来调用 SharePoint 服务器对象模型中的 API。  有关详细信息，请参阅[Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)。  
  
-   通过可替换参数使用此向导中收集的数据来初始化 SharePoint 项目文件。  
  
-   在每个新“网站栏”项目实例中创建一个新的 .snk 文件。  此文件用于对项目输出进行签名，以便能将 SharePoint 解决方案程序集部署到全局程序集缓存。  
  
-   调试并测试向导。  
  
> [!NOTE]  
>  可从以下位置下载一个示例，该示例包含此演练的已完成项目、代码和其他文件： [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=191369](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## 系统必备  
 若要执行本演练，必须先通过完成[演练：使用项目模板创建网站栏项目项（第 1 部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)来创建 SiteColumnProjectItem 解决方案。  
  
 还需要在开发计算机上安装以下组件才能完成本演练：  
  
-   支持 Microsoft Windows、SharePoint 和 Visual Studio 版本。  有关详细信息，请参阅[开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio SDK  本演练使用 SDK 中的**“VSIX 项目”**模板来创建 VSIX 包以部署项目项。  有关详细信息，请参阅[Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
 了解以下概念很有用，但对于完成本演练并不是必需的：  
  
-   Visual Studio 中的项目和项模板的向导。  有关更多信息，请参见[如何：使用向导来处理项目模板](../Topic/How%20to:%20Use%20Wizards%20with%20Project%20Templates.md)和 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 接口。  
  
-   SharePoint 中的网站栏。  有关更多信息，请参见 [列](http://go.microsoft.com/fwlink/?LinkId=183547)。  
  
##  <a name="wizardcomponents"></a> 了解向导组件  
 本演练中演示的向导包含几个组件。  下表描述了这些组件。  
  
|组件|描述|  
|--------|--------|  
|向导实现|这是一个名为 `SiteColumnProjectWizard` 的类，用于实现 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 接口。  此接口定义了 Visual Studio 在向导启动和完成时以及向导运行过程中的特定时间调用的方法。|  
|向导 UI|这是一个基于 WPF 的窗口，名为 `WizardWindow`。  此窗口包含两个用户控件，分别名为 `Page1` 和 `Page2`。  这两个用户控件表示向导的两个页面。<br /><br /> 在本演练中，向导实现的 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> 方法将显示向导 UI。|  
|向导数据模型|这是一个名为 `SiteColumnWizardModel` 的中介类，它在向导 UI 和向导实现之间提供了一个层。  本示例使用此类来帮助将向导实现和向导 UI 彼此隔开；此类不是所有向导的必需组件。<br /><br /> 在本演练中，向导实现会在显示向导 UI 时将 `SiteColumnWizardModel` 对象传递到向导窗口。  向导 UI 使用此对象的方法来保存 UI 中控件的值，并执行与验证输入网站 URL 是否有效类似的任务。  在用户完成该向导后，向导实现将使用 `SiteColumnWizardModel` 对象确定 UI 的最终状态。|  
|项目签名管理器|这是一个名为 `ProjectSigningManager` 的帮助程序类，向导实现会使用此类在每个新的项目实例中创建一个新的 key.snk 文件。|  
|SharePoint 命令|向导实现模型可使用这两种方法在向导运行时调入本地 SharePoint 网站。  由于 SharePoint 命令必须面向 .NET Framework 3.5，因此将在不同于剩余向导代码的程序集中实现这些命令。|  
  
## 创建项目  
 若要完成本演练，需要向在[演练：使用项目模板创建网站栏项目项（第 1 部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)中创建的 SiteColumnProjectItem 解决方案添加多个项目：  
  
-   一个 WPF 项目。  您将实现 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 接口并定义此项目中的向导 UI。  
  
-   一个用于定义 SharePoint 命令的类库项目。  此项目必须面向 .NET Framework 3.5。  
  
 从创建项目开始本演练。  
  
#### 创建 WPF 项目  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中打开 SiteColumnProjectItem 解决方案。  
  
2.  在“解决方案资源管理器”中，打开 **SiteColumnProjectItem** 解决方案节点的快捷菜单，选择“添加”，然后选择“新建项目”。  
  
    > [!NOTE]  
    >  在 Visual Basic 项目中，解决方案节点仅当在[“选项”对话框 \-\>“项目和解决方案”\-\>“常规”](http://msdn.microsoft.com/zh-cn/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)中选中**“总是显示解决方案”**复选框时显示。  
  
3.  在 "添加新项目" 对话框顶部，确保 **.NET Framework 4.5** 在 .NET Framework 的版本列表中选中。  
  
4.  展开 **Visual C\#** 节点或 **Visual Basic** 节点，然后选择 “窗口” 节点。  
  
5.  在项目模板列表中，选择 “WPF 用户控件库”，将项目命名为 **ProjectTemplateWizard**，然后选择 “确定” 按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 将“ProjectItemTypeDefinition”项目添加到解决方案中，并打开默认的 UserControl1.xaml文件。  
  
6.  从项目中删除 UserControl1.xaml 文件。  
  
#### 创建 SharePoint 命令项目  
  
1.  在“解决方案资源管理器”中，打开 SiteColumnProjectItem 解决方案节点的快捷菜单，选择“添加”，然后选择“新建项目”。  
  
2.  在 “添加新项目” 对话框的顶部，选择在 .NET Framework 的版本列表的 “.NET Framework 3.5”。  
  
3.  展开 **Visual C\#** 节点或 **Visual Basic** 节点，然后选择 “窗口” 节点。  
  
4.  选择 "类库" 项目模板，将项目命名为 **SharePointCommands**，然后选择"确定"  按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 将“SharePointCommands”项目添加到解决方案中，并打开默认的 Class1 代码文件。  
  
5.  从项目中删除 Class1 代码文件。  
  
## 配置项目  
 在创建向导之前，必须向项目中添加一些代码文件和程序集引用。  
  
#### 配置向导项目  
  
1.  在“解决方案资源管理器”中，打开“ProjectTemplateWizard”项目节点的快捷菜单，然后选择“属性”。  
  
2.  在 “项目设计器”，选择 Visual c\# 项目的“应用程序” 选项卡或 Visual Basic 项目中 “编译” 选项卡。  
  
3.  确保目标框架设置为 .NET Framework 4.5，而不是 .NET Framework 4.5 客户端配置文件。  
  
     有关详细信息，请参阅[如何：面向 .NET Framework 的某个版本](../Topic/How%20to:%20Target%20a%20Version%20of%20the%20.NET%20Framework.md)。  
  
4.  打开 “ProjectTemplateWizard”项目节点的快捷菜单，选择“添加”，然后选择 “新项目”。  
  
5.  选择 “窗口 \(WPF\)” 项目，将项目命名为 **WizardWindow**，然后选择 “添加” 按钮。  
  
6.  添加两个 “用户控件 \(WPF\)” 项到项目，并将它们命名为 **Page1** 和 **Page2**。  
  
7.  在 项目中添加四个代码文件，将其命名为以下名字：  
  
    -   SiteColumnProjectWizard  
  
    -   SiteColumnWizardModel  
  
    -   ProjectSigningManager  
  
    -   CommandIds  
  
8.  打开“ProjectTemplateWizard”项目节点中的快捷菜单，然后选择“添加引用”.。  
  
9. 展开 “程序集” 节点，选择 “扩展” 节点，然后选择程序集旁边的复选框：  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.OLE.Interop  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.Shell.11.0  
  
    -   Microsoft.VisualStudio.Shell.Interop.10.0  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
10. 选择 “确定” 按钮将程序集添加到项目中。  
  
11. 在“解决方案资源管理器”中，在 “ProjectTemplateWizard” 项目的“引用”文件夹下，选择“EnvDTE”。  
  
    > [!NOTE]  
    >  在 Visual Basic 项目中，**“引用”**文件夹仅当在[“选项”对话框 \-\>“项目和解决方案”\-\>“常规”](http://msdn.microsoft.com/zh-cn/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)中选中**“总是显示解决方案”**复选框时显示。  
  
12. 在“属性”窗口中，将“嵌入互操作类型”属性更改为“False”。  
  
13. 如果正在开发 Visual Basic 项目，请使用“项目设计器”将 ProjectTemplateWizard 命名空间导入您的项目。  
  
     有关详细信息，请参阅[如何：添加或移除导入的命名空间 &#40;Visual Basic&#41;](../Topic/How%20to:%20Add%20or%20Remove%20Imported%20Namespaces%20(Visual%20Basic).md)。  
  
#### 配置 SharePointCommands 项目  
  
1.  在“解决方案资源管理器”中，单击“SharePointCommands”项目节点。  
  
2.  在菜单栏上，选择“项目”、“添加存在项”。  
  
3.  在“添加现有项”对话框中，浏览包含 ProjectTemplateWizard 项目的代码文件，然后选择“CommandIds”代码文件。  
  
4.  在 “添加” 按钮旁边的下箭头，然后在出现的菜单中的 “添加为链接” 选项。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 将代码文件作为链接添加到“ SharePointCommands”  项目中。  这代码文件位于 “ProjectTemplateWizard” 项目中，但文件中的代码还是在 “SharePointCommands” 项目中进行编译。  
  
5.  在“SharePointCommands”项目中添加名为 Commands 的其他代码文件。  
  
6.  选择 SharePointCommands 项目，然后在菜单栏上，选择 “项目”，“添加引用”。  
  
7.  展开 “程序集” 节点，选择 “扩展” 节点，然后选择程序集旁边的复选框：  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
8.  选择 “确定” 按钮将程序集添加到项目中。  
  
## 创建向导模型、签名管理器和 SharePoint 命令 ID  
 将代码添加到 ProjectTemplateWizard 项目中以实现示例中的以下组件：  
  
-   SharePoint 命令 ID。  这些字符串是用于标识向导使用的 SharePoint 命令。  在本演练的后面部分，您将向 SharePointCommands 项目中添加代码以实现这些命令。  
  
-   向导数据模型。  
  
-   项目签名管理器。  
  
 有关这些组件的更多信息，请参见[了解向导组件](#wizardcomponents)。  
  
#### 定义 SharePoint 命令 ID  
  
1.  在 ProjectTemplateWizard 项目中，打开 CommandIds 代码文件，用以下代码替换该文件的整个内容。  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#5](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/commandids.cs#5)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#5](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/commandids.vb#5)]  
  
#### 创建向导模型  
  
1.  打开 SiteColumnWizardModel 代码文件，然后用以下代码替换该文件的整个内容。  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/sitecolumnwizardmodel.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/sitecolumnwizardmodel.vb#6)]  
  
#### 创建项目签名管理器  
  
1.  打开 ProjectSigningManager 代码文件，然后用以下代码替换该文件的整个内容。  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#8](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/projectsigningmanager.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#8](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/projectsigningmanager.vb#8)]  
  
## 创建向导 UI  
 添加 XAML 以定义向导窗口的 UI 和两个提供向导页的 UI 的用户控件，并添加代码以定义窗口和用户控件的行为。  您创建的向导类似于 Visual Studio. 中的 SharePoint 项目的内置向导。  
  
> [!NOTE]  
>  在以下步骤中将 XAML 或代码添加到项目中后，您的项目将出现某些编译错误。  在添加后面的步骤中的代码之后，这些错误将消失。  
  
#### 创建向导窗口 UI  
  
1.  在 ProjectTemplateWizard 项目中，打开 WizardWindow.xaml 文件的快捷菜单，然后选择 "打开" 在设计器中打开窗口。  
  
2.  在设计器的 XAML 视图中，用以下 XAML 替换当前的 XAML。  XAML 定义一个 UI，该 UI 包含一个标题、一个包含向导页的 <xref:System.Windows.Controls.Grid> 以及位于窗口底部的导航按钮。  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#10](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/wizardwindow.xaml#10)]  
  
    > [!NOTE]  
    >  在此 XAML 中创建的窗口派生自 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> 基类。  在向 Visual Studio 添加自定义 WPF 对话框时，建议您从该类派生对话框，以获得与其他 Visual Studio 对话框一致的样式并避免可能发生的模式对话框问题。  有关详细信息，请参阅[创建和管理有模式对话框](../extensibility/creating-and-managing-modal-dialog-boxes.md)。  
  
3.  如果正在开发 Visual Basic 项目，请从 `Window` 元素的 `x:Class` 特性中的 `WizardWindow` 类名称中移除 `ProjectTemplateWizard` 命名空间。  此元素位于 XAML 的第一行中。  完成上述操作以后，第一行应类似于下面样例：  
  
    ```  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  打开 WizardWindow.xaml 文件的代码隐藏文件。  
  
5.  用下面的代码替换该文件的内容，除了在文件的顶部 `using` 声明。  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/wizardwindow.xaml.cs#4)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/wizardwindow.xaml.vb#4)]  
  
#### 创建第一个向导页 UI  
  
1.  在 ProjectTemplateWizard 项目中，打开 Page1.xaml 文件的快捷菜单，然后选择 "打开" 在设计器中用户控件。  
  
2.  在设计器的 XAML 视图中，用以下 XAML 替换当前的 XAML。  XAML 定义包括文本框的 UI，用户可以输入想要调试的本地网站URL。  用户界面还包括用户可以指定项目是否为沙盒的选项按钮。  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#11](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/page1.xaml#11)]  
  
3.  如果正在开发 Visual Basic 项目，请从 `UserControl` 元素的 `x:Class` 特性中的 `Page1` 类名称中移除 `ProjectTemplateWizard` 命名空间。  此命名空间位于 XAML 的第一行中。  完成上述操作以后，第一行应类似于下面这样：  
  
    ```  
    <UserControl x:Class="Page1"  
    ```  
  
4.  用下面的代码替换Page1.xaml文件的内容，除了在文件的顶部 `using` 声明。  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/page1.xaml.cs#2)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/page1.xaml.vb#2)]  
  
#### 创建第二个向导页 UI  
  
1.  在 ProjectTemplateWizard 项目中，打开 Page2.xaml 文件的快捷菜单，然后选择 “打开”。  
  
     该用户控件即在设计器中打开。  
  
2.  在 XAML 视图中，用下面的 XAML 替换 当前XAML。  该 XAML 定义了一个 UI，此 UI 包含一个下拉列表（用于选择网站栏的基类型）、一个组合框（用于指定在其下显示库中的网站栏的内置或自定义组）和一个文本框（用于指定网站栏的名称）。  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#12](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/page2.xaml#12)]  
  
3.  如果正在开发 Visual Basic 项目，请从 `UserControl` 元素的 `x:Class` 特性中的 `Page2` 类名称中移除 `ProjectTemplateWizard` 命名空间。  此命名空间位于 XAML 的第一行中。  完成上述操作以后，第一行应类似于下面这样：  
  
    ```  
    <UserControl x:Class="Page2"  
    ```  
  
4.  用下面的代码替换Page2.xaml 文件的代码隐藏文件的内容 ，除了在文件的顶部 `using` 声明。  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#3](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/page2.xaml.cs#3)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/page2.xaml.vb#3)]  
  
## 实现向导  
 通过实现 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 接口定义向导的主要功能。  此接口定义了 Visual Studio 在向导启动和完成时以及向导运行过程中的特定时间调用的方法。  
  
#### 实现向导  
  
1.  在 ProjectTemplateWizard 项目中，打开 SiteColumnProjectWizard 代码文件。  
  
2.  将此文件的全部内容替换为以下代码。  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#7](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/sitecolumnprojectwizard.cs#7)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#7](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/sitecolumnprojectwizard.vb#7)]  
  
## 创建 SharePoint 命令  
 创建可调入 SharePoint 服务器对象模型的两个自定义命令。  一个命令将确定用户在向导中键入的网站 URL 是否有效。  另一个命令将从指定的 SharePoint 网站中获取所有字段类型，以便用户能选择要用作其新网站栏的基础的类型。  
  
#### 定义 SharePoint 命令  
  
1.  在 **SharePointCommands** 项目中，打开 Commands 代码文件。  
  
2.  将此文件的全部内容替换为以下代码。  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#9](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/sharepointcommands/commands.cs#9)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#9](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/sharepointcommands/commands.vb#9)]  
  
## 检查点  
 演练进行到此时，向导的所有代码都位于项目中。  生成项目以确保编译项目时不会出错。  
  
#### 生成项目  
  
1.  在菜单栏上，依次选择**“生成”**、**“生成解决方案”**。  
  
## 从项目模板中删除 key.snk 文件  
 在[演练：使用项目模板创建网站栏项目项（第 1 部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)中，您创建的项目模板包含一个用于对每个“网站栏”项目实例进行签名的 key.snk 文件。  不再需要此 key.snk 文件，因为向导现在会为每个项目生成一个新的 key.snk 文件。  从项目模板中删除 key.snk 文件，并删除对此文件的引用。  
  
#### 从项目模板中删除 key.snk 文件  
  
1.  在“解决方案资源管理器”中，在“SiteColumnProjectTemplate”节点下，打开“key.snk”文件的快捷菜单，然后选择“删除”。  
  
2.  在出现的“验证”对话框中，选择“确定”按钮。  
  
3.  在 “SiteColumnProjectTemplate” 节点下，打开 SiteColumnProjectTemplate.vstemplate 文件，然后从中删除以下元素。  
  
    ```  
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
    ```  
  
4.  保存并关闭文件。  
  
5.  在 **SiteColumnProjectTemplate** 节点下，打开 ProjectTemplate.csproj 或 ProjectTemplate.vbproj 文件，然后从中移除以下 `PropertyGroup` 元素。  
  
    ```  
    <PropertyGroup>  
      <SignAssembly>true</SignAssembly>  
      <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
    </PropertyGroup>  
    ```  
  
6.  删除以下 `None` 元素。  
  
    ```  
    <None Include="key.snk" />  
    ```  
  
7.  保存并关闭文件。  
  
## 将向导与项目模板关联  
 现在，您已实现向导，您必须将向导与**“网站栏”**项目模板关联。  为此，您必须完成以下三个过程：  
  
1.  用强名称对向导程序集进行签名。  
  
2.  获取向导程序集的公钥标记。  
  
3.  在**“网站栏”**项目模板的 .vstemplate 文件中添加对向导程序集的引用。  
  
#### 用强名称对向导程序集进行签名  
  
1.  在“解决方案资源管理器”中，打开“ProjectTemplateWizard”项目的快捷菜单，然后选择“属性”。  
  
2.  在**“签名”**选项卡上，选中**“为程序集签名”**复选框。  
  
3.  在“选择强名称密钥文件”列表中，选择“\<New...\>”。  
  
4.  在“创建强名称密钥”对话框中，输入新密钥文件的名称，然后清除“使用密码保护密钥文件”复选框，然后选择“确定”按钮 。  
  
5.  打开 “ProjectTemplateWizard” 项目的快捷菜单，然后选择 “生成” 创建 ProjectTemplateWizard.dll 文件。  
  
#### 获取向导程序集的公钥标记  
  
1.  在“开始菜单”中，选择“所有程序”，选择“Microsoft Visual Studio”，选择“Visual Studio 工具”，然后选择“开发人员命令提示”。  
  
     打开“Visual Studio 命令提示”窗口。  
  
2.  运行一下命令，将 *PathToWizardAssembly* 替换为已在开发计算机上为 ProjectTemplateWizard 项目生成的 ProjectTemplateWizard.dll 程序集的完整路径。  
  
    ```  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     ProjectTemplateWizard.dll 程序集的公钥标记会写入到 Visual Studio 命令提示符窗口中。  
  
3.  将 Visual Studio 命令提示符窗口保持打开状态。  在下面的过程中，将需要公钥标记。  
  
#### 在 .vstemplate 文件中添加对向导程序集的引用  
  
1.  在**“解决方案资源管理器”**中，展开**“SiteColumnProjectTemplate”**项目节点，然后打开 SiteColumnProjectTemplate.vstemplate 文件。  
  
2.  在该文件末尾附近的 `</TemplateContent>` 和 `</VSTemplate>` 标记之间添加以下 `WizardExtension` 元素。  将  `PublicKeyToken`特性的 *your token* 值替换为上一过程中获得的公钥标记。  
  
    ```  
    <WizardExtension>  
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>  
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     有关 `WizardExtension` 元素的更多信息，请参见 [WizardExtension 元素（Visual Studio 模板）](../extensibility/wizardextension-element-visual-studio-templates.md)。  
  
3.  保存并关闭文件。  
  
## 将可替换参数添加到项目模板的 Elements.xml 文件中  
 将多个可替换参数添加到 SiteColumnProjectTemplate 项目中的 Elements.xml 文件中。  将在之前定义的 `SiteColumnProjectWizard` 类的 `RunStarted` 方法中初始化这些参数。  当用户创建“网站栏”项目时，Visual Studio 会自动将新项目中的 Elements.xml 文件中的这些参数替换为在向导中指定的值。  
  
 可替换参数是以美元符号 \($\) 字符开始和结束的标记。  除了定义您自己的可替换参数外，还可以使用由 SharePoint 项目系统定义和初始化的内置参数。  有关详细信息，请参阅[可替换参数](../sharepoint/replaceable-parameters.md)。  
  
#### 向 Elements.xml 文件添加可替换参数  
  
1.  在SiteColumnProjectTemplate项目中，用下面的 XML 替换 Elements.xml 文件的内容。  
  
    ```  
  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <Field ID="{$guid5$}"   
             Name="$fieldname$"   
             DisplayName="$fieldname$"   
             Type="$selectedfieldtype$"   
             Group="$selectedgrouptype$">  
      </Field>  
    </Elements>  
    ```  
  
     新的 XML 会将 `Name`、`DisplayName`、`Type` 和 `Group` 特性的值更改为自定义的可替换参数。  
  
2.  保存并关闭文件。  
  
## 向 VSIX 包添加向导  
 若要将向导与包含“网站栏”项目模板的 VSIX 包一起部署，请将对向导项目和 SharePoint 命令项目的引用添加到 VSIX 项目中的 source.extension.vsixmanifest 文件中。  
  
#### 向 VSIX 包添加向导  
  
1.  在“解决方案资源管理器”中，在“SiteColumnProjectItemr”项目中，打开“source.extension.vsixmanifest”节点的快捷菜单，然后选择“打开”。  
  
     Visual Studio 将在清单编辑器中打开该文件。  
  
2.  在编辑器的 “资产” 选项卡中，选择 “新建” 按钮。  
  
     打开“添加新资产”对话框。  
  
3.  在 “类型” 列表中，选择 “Microsoft.VisualStudio.Assembly”。  
  
4.  在 “源” 列表中，选择 “当前解决方案中的项目”。  
  
5.  在“项目”列表中，选择“ProjectTemplateWizard”，然后选择“确定”按钮。  
  
6.  在编辑器的 “资产” 选项卡中，再次选择 “新建” 按钮。  
  
     打开“添加新资产”对话框。  
  
7.  在 “类型” 列表中，输入 “SharePoint.Commands.v4”。  
  
8.  在 “源” 列表中，选择 “当前解决方案中的项目”。  
  
9. 在 “项目” 列表中，选择 “SharePointCommands” 项目，然后选择 “确定” 按钮。  
  
10. 在菜单栏上，依次选择 “生成”，“生成解决方案”，然后确保解决方案在生成时不会出错。  
  
## 测试向导  
 现在已经准备好对向导进行测试。  首先，在 Visual Studio 的实验实例中开始调试 SiteColumnProjectItem 解决方案。  然后，在 Visual Studio 的实验实例中测试“网站栏”项目的向导。  最后，生成并运行项目以验证网站栏是否按预期方式运行。  
  
#### 开始调试解决方案  
  
1.  利用管理员证书重新启动 Visual Studio，然后打开 SiteColumnProjectItem 解决方案。  
  
2.  在 ProjectTemplateWizard 项目中，打开 SiteColumnProjectWizard 代码文件并向 `RunStarted` 方法中的第一行代码中添加一个断点。  
  
3.  从菜单栏选择“调试”和“异常”。  
  
4.  在“异常”对话框中，确保已清除“公共语言运行时异常”的“引发”和“用户未处理的”复选框,然后选择“确定”按钮。  
  
5.  通过选择 “F5” 键或在菜单栏上，选择 “调试”，“启动调试”开始调试。  
  
     Visual Studio 将扩展安装到 %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0Exp\\Extensions\\Contoso\\Site Column\\1.0 并启动 Visual Studio 的实验实例。  您将在此 Visual Studio 实例中测试项目项。  
  
#### 在 Visual Studio 中测试向导  
  
1.  在 Visual Studio 的实验实例中，在“文件”菜单上指向“新建”，然后单击“项目”。  
  
2.  展开 **Visual C\#** 节点或 **Visual Basic** 节点 \(具体取决于项目模板支持的语言\)，再展开 **SharePoint** 节点，然后选择 **2010** 节点。  
  
3.  在模板列表中，选择“网站列”模板，将其命名为**SiteColumnWizardTest**，然后选择“确定” 按钮。  
  
4.  验证另一个 Visual Studio 实例中的代码是否会在您之前在 `RunStarted` 方法中设置的断点处停止。  
  
5.  选择 “F5” 键继续调试该项目，或在菜单栏上，选择 “调试”，“继续”。  
  
6.  在“SharePoint 自定义向导”中，键入要用于调试的网站的 URL，并单击“下一个” 按钮。  
  
7.  在**“SharePoint 自定义向导”**的第二页中，进行以下选择：  
  
    -   在“类型”列表中，选择“布尔”。  
  
    -   在 “组” 列表中，选择 “是\/否自定义列”。  
  
    -   在 “名称” 框中，输入我的是\/否列，然后选择 “完成” 按钮。  
  
     “解决方案资源管理器”中将出现一个新项目，其中包含一个名为“Field1”的项目项，并且 Visual Studio 将在编辑器中打开 Elements.xml 文件。  
  
8.  验证 Elements.xml 是否包含您在向导中指定的值。  
  
#### 在 SharePoint 中测试网站栏  
  
1.  在 Visual Studio 的实验实例中选择F5键。  
  
     这将对网站栏进行打包并将其部署到由项目的“网站 URL”属性指定的 SharePoint 网站中。  Web 浏览器将打开此网站的默认页。  
  
    > [!NOTE]  
    >  如果出现“脚本调试被禁用”对话框，请单击“是”继续调试该项目。  
  
2.  在“网站操作”菜单上，单击“网站设置”。  
  
3.  在"网站设置"页，“库”下，选择 “网站列” 链接。  
  
4.  在网站栏列表中，验证“自定义‘是\/否’栏”组是否存在包含一个名为“我的‘是\/否’栏”的列，然后关闭web浏览器。  
  
## 清理开发计算机  
 测试完项目项之后，从 Visual Studio 的实验实例中删除项目模板。  
  
#### 清理开发计算机  
  
1.  在 Visual Studio 的实验实例中，在菜单栏上选择 “工具”，“扩展和更新”。  
  
     “扩展和更新”对话框将打开。  
  
2.  在扩展列表中，选择 "网站栏"，然后选择 "卸载" 按钮。  
  
3.  在出现的对话框中，选择 "是" 以确认您要卸载该扩展，然后选择 "立即重新启动" 按钮来完成卸载。  
  
4.  关闭 Visual Studio 的两个实例以及 CustomActionProjectItem 解决方案中已打开的实例。  
  
     有关如何部署 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]扩展的更多信息，请参见[传送 Visual Studio 扩展](../extensibility/shipping-visual-studio-extensions.md)。  
  
## 请参阅  
 [演练：使用项目模板创建网站栏项目项（第 1 部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)   
 [如何：使用向导来处理项目模板](../Topic/How%20to:%20Use%20Wizards%20with%20Project%20Templates.md)  
  
  