---
title: "创建基本项目系统中，第 2 部分 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编写项目系统"
  - "项目系统"
  - "教程"
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
caps.latest.revision: 23
caps.handback.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
---
# 创建基本项目系统中，第 2 部分
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在此系列中，在第一个演练 [创建基本项目系统中，第 1 部分](../extensibility/creating-a-basic-project-system-part-1.md), ，演示如何创建基本项目系统。 本演练中的基础上基本项目系统添加 Visual Studio 模板、 属性页中，以及其他功能。 在开始此之前，必须完成第一个演练。  
  
 本演练介绍了如何创建具有项目文件名称扩展.myproj 的项目类型。 若要完成本演练，您无需创建您自己的语言，因为本演练中继承从现有的 Visual C\# 项目系统。  
  
 本演练介绍如何完成这些任务:  
  
-   创建 Visual Studio 模板。  
  
-   部署 Visual Studio 模板。  
  
-   创建项目类型的子节点，在 **新项目** 对话框。  
  
-   启用 Visual Studio 模板中的参数替换。  
  
-   创建的项目属性页。  
  
> [!NOTE]
>  在本演练中的步骤基于 C\# 项目。 但是，除了详细信息，例如，文件扩展名和代码，可以使用相同的步骤对于 Visual Basic 项目。  
  
## 创建 Visual Studio 模板  
 [创建基本项目系统中，第 1 部分](../extensibility/creating-a-basic-project-system-part-1.md) 演示如何创建基本项目模板并将其添加到项目系统。 它还演示如何通过使用与 Visual Studio 注册此模板 <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> 属性，它在系统注册表中写入 \\Templates\\Projects\\SimpleProject\\ 文件夹的完整路径。  
  
 通过使用 Visual Studio 模板 \(.vstemplate 文件\)，而不基本项目模板，您可以控制该模板中的显示方式 **新项目** 对话框中，将会替换模板参数如何。  .Vstemplate 文件是一个 XML 文件，描述源代码文件的方式使用项目系统模板创建一个项目时将包括在内。 项目系统本身是通过收集.vstemplate 文件和源文件.zip 文件中的生成并部署通过将该.zip 文件复制到 Visual Studio 可被识别的位置。 在本演练后面的更详细地说明此过程。  
  
1.  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ，打开按照创建 SimpleProject 解决方案 [创建基本项目系统中，第 1 部分](../extensibility/creating-a-basic-project-system-part-1.md)。  
  
2.  在 SimpleProjectPackage.cs 文件中查找 ProvideProjectFactory 属性。 如下所示将替换为 null，并且具有".\\\\NullPath"的第四个参数 \(项目模板文件夹的路径\) 的第二个参数 \(项目名称\)。  
  
    ```  
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null, "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj", ".\\NullPath", LanguageVsTemplate = "SimpleProject")]  
    ```  
  
3.  将添加到 \\Templates\\Projects\\SimpleProject\\ 文件夹名 SimpleProject.vstemplate 的 XML 文件。  
  
4.  SimpleProject.vstemplate 的内容替换为以下代码。  
  
    ```xml  
    <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"> <TemplateData> <Name>SimpleProject Application</Name> <Description> A project for creating a SimpleProject application </Description> <Icon>SimpleProject.ico</Icon> <ProjectType>SimpleProject</ProjectType> </TemplateData> <TemplateContent> <Project File="SimpleProject.myproj" ReplaceParameters="true"> <ProjectItem ReplaceParameters="true" OpenInEditor="true"> Program.cs </ProjectItem> <ProjectItem ReplaceParameters="true" OpenInEditor="false"> AssemblyInfo.cs </ProjectItem> </Project> </TemplateContent> </VSTemplate>  
    ```  
  
5.  在 **属性** 窗口中，选择所有五个文件中的 \\Templates\\Projects\\SimpleProject\\ 文件夹并设置 **生成操作** 到 **ZipProject**。  
  
 ![](../extensibility/media/simpproj2.png "SimpProj2")  
  
 \< TemplateData \> 部分确定的位置和 SimpleProject 项目类型中的外观 **新项目** 对话框中，按如下所示:  
  
-   \< 名称 \> 元素的名称作为 SimpleProject 应用程序的项目模板。  
  
-   \< 说明 \> 元素包含的说明，将出现在 **新项目** 对话框中选择项目模板时。  
  
-   \< I \> 元素指定与 SimpleProject 项目类型一起显示的图标。  
  
-   \< ProjectType \> 元素名称中的项目类型 **新项目** 对话框。 此名称将替换 ProvideProjectFactory 属性的项目名称参数。  
  
    > [!NOTE]
    >  \< 项目类型 \> 元素必须与匹配 `LanguageVsTemplate` 参数 `ProvideProjectFactory` SimpleProjectPackage.cs 文件中的属性。  
  
 \< TemplateContent \> 部分介绍创建一个新项目时，将生成这些文件:  
  
-   SimpleProject.myproj  
  
-   Program.cs  
  
-   AssemblyInfo.cs  
  
 所有三个文件都具有 `ReplaceParameters` 设置为 true，启用参数替换。  Program.cs 文件具有 `OpenInEditor` 设置为 true，这会导致要创建的项目时在代码编辑器中打开的文件。  
  
 有关 Visual Studio 模板架构中的元素的详细信息，请参阅 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)。  
  
> [!NOTE]
>  如果一个项目具有多个 Visual Studio 模板，每个模板是在单独的文件夹。 在该文件夹中的每个文件必须具有 **生成操作** 设置为 **ZipProject**。  
  
## 添加最小.vsct 文件  
 Visual Studio 必须在以识别新的或修改 Visual Studio 模板的安装模式下运行。 安装模式下需要.vsct 文件必须存在。 因此，必须将最小.vsct 文件添加到项目。  
  
1.  将添加到 SimpleProject 项目名 SimpleProject.vsct 的 XML 文件。  
  
2.  SimpleProject.vsct 文件的内容替换为以下代码。  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?> <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"> </CommandTable>  
    ```  
  
3.  设置 **生成操作** 到此文件的 **VSCTCompile**。 您可以执行此操作仅在.csproj 文件中，不在 **属性** 窗口。 请确保 **生成操作** 此文件设置为 **无** 此时。  
  
    1.  右键单击 SimpleProject 节点，然后单击 **编辑 SimpleProject.csproj**。  
  
    2.  在.csproj 文件中，找到 SimpleProject.vsct 的项目。  
  
        ```  
        <None Include="SimpleProject.vsct" />  
        ```  
  
    3.  更改对指定的生成操作 **VSCTCompile**。  
  
        ```  
        <VSCTCompile Include="SimpleProject.vsct" />  
        ```  
  
    4.  项目文件和关闭编辑器中。  
  
    5.  保存 SimpleProject 节点，然后在 **解决方案资源管理器** 单击 **重新加载项目**。  
  
## 检查 Visual Studio 模板生成步骤  
 VSPackage 项目生成系统通常在安装模式下运行 Visual Studio.vstemplate 文件发生更改或重新生成包含.vstemplate 文件的项目时。 通过将 MSBuild 的详细级别设置为 Normal 或更高版本，您可以追踪它。  
  
1.  在**“工具”**菜单上，单击**“选项”**。  
  
2.  展开 **项目和解决方案** 节点，并选择 **生成并运行**。  
  
3.  设置 **MSBuild 项目生成输出详细程度** 到 **正常**。 单击“确定”。  
  
4.  重新生成 SimpleProject 项目。  
  
 生成步骤来创建.zip 项目文件应类似于下面的示例。  
  
```  
ZipProjects: 1>  Zipping ProjectTemplates 1>  Zipping <path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip... 1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "<%LOCALAPPDATA%>\Microsoft\VisualStudio\14.0Exp\ProjectTemplates\\\\SimpleProject.zip". 1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "bin\Debug\\ProjectTemplates\\\\SimpleProject.zip". 1>  SimpleProject -> <path>\SimpleProject\SimpleProject\bin\Debug\ProjectTemplates\SimpleProject.zip 1>ZipItems: 1>  Zipping ItemTemplates 1>  SimpleProject ->  
```  
  
## 部署 Visual Studio 模板  
 Visual Studio 模板不包含路径信息。 因此，模板的.zip 文件必须部署到 Visual Studio 可被识别的位置。 ProjectTemplates 文件夹的位置通常是 **\< %LOCALAPPDATA%\> \\Microsoft\\VisualStudio\\14.0Exp\\ProjectTemplates**。  
  
 若要部署项目工厂，安装程序必须具有管理员权限。 部署 Visual Studio 安装节点下的模板: **...\\Microsoft Visual Studio 14.0\\Common7\\IDE\\ProjectTemplates**。  
  
## 测试的 Visual Studio 模板  
 测试您的项目工厂，以查看是否会它通过使用 Visual Studio 模板创建项目层次结构。  
  
1.  重置 Visual Studio SDK 实验实例。  
  
     在 [!INCLUDE[win7](../debugger/includes/win7_md.md)]: 在开始菜单中，找到 **Microsoft Visual Studio\/Microsoft Visual Studio SDK\/Tools** 文件夹，，然后选择 **重置 Microsoft Visual Studio 实验实例**。  
  
     在更高版本的 Windows: 开始屏幕中，键入 **重置 Microsoft Visual Studio \< 版本 \> 实验实例**。  
  
2.  出现一个命令提示符窗口。 当看到单词 `Press any key to continue`, ，单击 ENTER。 该窗口将关闭后，打开 Visual Studio。  
  
3.  重新生成 SimpleProject 项目并启动调试。 将显示的实验实例。  
  
4.  在实验实例中，将创建 SimpleProject 项目。 在 **新项目** 对话框中，选择 **SimpleProject**。  
  
5.  您应该看到 SimpleProject 的新实例。  
  
 ![](../extensibility/media/simpproj2_newproj.png "SimpProj2\_NewProj")  
  
 ![](../extensibility/media/simpproj2_myproj.png "SimpProj2\_MyProj")  
  
## 创建一个项目类型的子节点  
 可以将一个子节点添加到中的项目类型节点 **新项目** 对话框。  例如，对于 SimpleProject 项目类型，你可以为控制台应用程序、 应用程序窗口、 web 应用程序等的子节点。  
  
 通过更改项目文件并向 \< ZipProject \> 元素添加 \< OutputSubPath \> 子级创建子节点。 当生成或部署期间将会复制一个模板时，每一个子节点将成为项目模板文件夹的子文件夹。  
  
 本部分演示如何创建控制台 SimpleProject 项目类型的子节点。  
  
1.  \\Templates\\Projects\\SimpleProject\\ 文件夹重命名为 \\Templates\\Projects\\ConsoleApp\\。  
  
2.  在 **属性** 窗口中，选择 \\Templates\\Projects\\ConsoleApp\\ 文件夹中的所有五个文件，并确保 **生成操作** 设置为 **ZipProject**。  
  
3.  在 SimpleProject.vstemplate 文件中，\< TemplateData \> 部分中，就在结束标记之前的末尾添加以下行。  
  
    ```  
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
    ```  
  
     这会导致要显示在控制台中的子节点和 SimpleProject 父节点的子节点上一级中的控制台应用程序模板。  
  
4.  保存 SimpleProject.vstemplate 文件。  
  
5.  在.csproj 文件中，将 \< OutputSubPath \> 添加到每个 ZipProject 元素。 卸载项目，与以前一样，并编辑项目文件。  
  
6.  查找 \< ZipProject \> 元素。 为每个 \< ZipProject \> 元素中，添加 \< OutputSubPath \> 元素，并为其指定值控制台。 ZipProject  
  
    ```  
    <ZipProject Include="Templates\Projects\ConsoleApp\AssemblyInfo.cs"> <OutputSubPath>Console</OutputSubPath> </ZipProject> <ZipProject Include="Templates\Projects\ConsoleApp\Program.cs"> <OutputSubPath>Console</OutputSubPath> </ZipProject> <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.myproj"> <OutputSubPath>Console</OutputSubPath> </ZipProject> <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.vstemplate"> <OutputSubPath>Console</OutputSubPath> </ZipProject> <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.ico"> <OutputSubPath>Console</OutputSubPath> </ZipProject>  
    ```  
  
7.  将此 \< PropertyGroup \> 添加到项目文件:  
  
    ```  
    <PropertyGroup> <VsTemplateLanguage>SimpleProject</VsTemplateLanguage> </PropertyGroup>  
    ```  
  
8.  保存项目文件并重新加载项目。  
  
## 测试项目类型的子节点  
 测试已修改的项目文件，以查看是否 **控制台** 子节点将出现在 **新项目** 对话框。  
  
1.  运行 **重置 Microsoft Visual Studio 实验实例** 工具。  
  
2.  重新生成 SimpleProject 项目并启动调试。 应显示的实验实例  
  
3.  在 **新项目** 对话框中，单击 **SimpleProject** 节点。**控制台应用程序** 模板应出现在 **模板** 窗格。  
  
4.  展开 **SimpleProject** 节点。**控制台** 应显示的子节点。**SimpleProject 应用程序** 模板仍会出现在 **模板** 窗格。  
  
5.  . 单击 **取消** 和停止调试  
  
 ![](../extensibility/media/simpproj2_rollup.png "SimpProj2\_Rollup")  
  
 ![](../extensibility/media/simpproj2_subfolder.png "SimpProj2\_Subfolder")  
  
## 项目的模板参数替换  
 [创建基本项目系统中，第 1 部分](../extensibility/creating-a-basic-project-system-part-1.md) 介绍了如何覆盖 `ProjectNode.AddFileFromTemplate` 方法来执行一种基本类型的模板参数替换。 本部分介绍了如何使用更复杂的 Visual Studio 模板参数。  
  
 当使用中的 Visual Studio 模板创建一个项目 **新项目** 对话框中，将替换为参数的模板字符串以自定义项目。 一个模板参数是一个特殊的标记的开始和结束以美元符号，例如，$time$。 以下两个参数是用于启用基于模板的项目中的自定义特别有用:  
  
-   $GUID \[1\-10\] $ 替换为新的 Guid。 您可以指定最多 10 个唯一的 Guid，例如，$guid1$。  
  
-   $ $safeprojectname$ 是由用户在提供的名称 **新项目** 对话框中，修改，以删除所有不安全的字符和空格。  
  
 有关模板参数的完整列表，请参阅 [模板参数](../ide/template-parameters.md)。  如果你想要创建您自己的自定义模板参数，请参阅 [NIB: 如何: 将传递到模板的自定义参数](http://msdn.microsoft.com/zh-cn/5bc2ad11-84c7-4683-a276-e5e00d85d8fb)。  
  
#### 若要替换项目的模板参数  
  
1.  在 SimpleProjectNode.cs 文件中，删除 `AddFileFromTemplate` 方法。  
  
2.  在 \\Templates\\Projects\\ConsoleApp\\SimpleProject.myproj 文件中，找到 \< 根命名空间 \> 属性，并将其值更改为 $ $safeprojectname$。  
  
    ```  
    <RootNamespace>$safeprojectname$</RootNamespace>  
    ```  
  
3.  在 \\Templates\\Projects\\SimpleProject\\Program.cs 文件中，替换为以下代码替换文件的内容:  
  
    ```  
    using System; using System.Collections.Generic; using System.Text; using System.Runtime.InteropServices;    // Guid namespace $safeprojectname$ { [Guid("$guid1$")] public class $safeprojectname$ { static void Main(string[] args) { Console.WriteLine("Hello VSX!!!"); Console.ReadKey(); } } }  
    ```  
  
4.  重新生成 SimpleProject 项目并启动调试。 应显示的实验实例。  
  
5.  创建新的 SimpleProject 控制台应用程序。 \(在 **项目类型** 窗格中，选择 **SimpleProject**。 下 **Visual Studio 已安装的模板**, ，选择 **控制台应用程序**。\)  
  
6.  在新创建项目中，打开 Program.cs。 其外观应类似于以下内容 \(在文件中的 GUID 值会不同。\):  
  
    ```  
    using System; using System.Collections.Generic; using System.Text; using System.Runtime.InteropServices;    // Guid namespace Console_Application1 { [Guid("00000000-0000-0000-00000000-00000000)"] public class Console_Application1 { static void Main(string[] args) { Console.WriteLine("Hello VSX!!!"); Console.ReadKey(); } } }  
    ```  
  
## 创建项目属性页  
 可以为您的项目类型创建属性页，以便用户可以查看和更改基于模板的项目中的属性。 本部分演示如何创建独立于配置的属性页。 此基本属性页使用属性网格显示在属性页类中公开的公共属性。  
  
 派生属性页类从 `SettingsPage` 基类。 提供的属性网格 `SettingsPage` 类已意识到大多数基元数据类型，并且知道如何显示它们。  此外， `SettingsPage` 类知道如何保留到项目文件的属性值。  
  
 在本部分中创建的属性页允许您更改并保存这些项目属性:  
  
-   AssemblyName  
  
-   OutputType  
  
-   根命名空间。  
  
1.  在 SimpleProjectPackage.cs 文件中，添加以下 `ProvideObject` 属性设为 `SimpleProjectPackage` 类:  
  
    ```  
    [ProvideObject(typeof(GeneralPropertyPage))] public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
     这将会注册属性页类 `GeneralPropertyPage` com  
  
2.  在 SimpleProjectNode.cs 文件中，将添加到这两个重写的方法 `SimpleProjectNode` 类:  
  
    ```  
    protected override Guid[] GetConfigurationIndependentPropertyPages() { Guid[] result = new Guid[1]; result[0] = typeof(GeneralPropertyPage).GUID; return result; } protected override Guid[] GetPriorityProjectDesignerPages() { Guid[] result = new Guid[1]; result[0] = typeof(GeneralPropertyPage).GUID; return result; }  
    ```  
  
     这两种方法返回的属性页的 Guid 的数组。  GeneralPropertyPage GUID 是唯一元素在数组中，因此 **属性页** 对话框中将只显示一页。  
  
3.  添加到 SimpleProject 项目名为 GeneralPropertyPage.cs 类文件。  
  
4.  用下面的代码替换该文件的内容:  
  
    ```  
    using System; using System.Runtime.InteropServices; using Microsoft.VisualStudio; using Microsoft.VisualStudio.Project; using System.ComponentModel; namespace SimpleProject { [ComVisible(true)] [Guid("6BC7046B-B110-40d8-9F23-34263D8D2936")] public class GeneralPropertyPage : SettingsPage { private string assemblyName; private OutputType outputType; private string defaultNamespace; public GeneralPropertyPage() { this.Name = "General"; } [Category("AssemblyName")] [DisplayName("AssemblyName")] [Description("The output file holding assembly metadata.")] public string AssemblyName { get { return this.assemblyName; } } [Category("Application")] [DisplayName("OutputType")] [Description("The type of application to build.")] public OutputType OutputType { get { return this.outputType; } set { this.outputType = value; this.IsDirty = true; } } [Category("Application")] [DisplayName("DefaultNamespace")] [Description("Specifies the default namespace for added items.")] public string DefaultNamespace { get { return this.defaultNamespace; } set { this.defaultNamespace = value; this.IsDirty = true; } } protected override void BindProperties() { this.assemblyName = this.ProjectMgr.GetProjectProperty( "AssemblyName", true); this.defaultNamespace = this.ProjectMgr.GetProjectProperty( "RootNamespace", false); string outputType = this.ProjectMgr.GetProjectProperty( "OutputType", false); this.outputType = (OutputType)Enum.Parse(typeof(OutputType), outputType); } protected override int ApplyChanges() { this.ProjectMgr.SetProjectProperty( "AssemblyName", this.assemblyName); this.ProjectMgr.SetProjectProperty( "OutputType", this.outputType.ToString()); this.ProjectMgr.SetProjectProperty( "RootNamespace", this.defaultNamespace); this.IsDirty = false; return VSConstants.S_OK; } } }  
    ```  
  
     `GeneralPropertyPage` 类公开程序集名称、 OutputType 和根命名空间的三个公共属性。 由于程序集名称具有无设置方法，则将它显示为只读属性。 OutputType 是一个枚举的常量，因此它将显示为下拉列表中。  
  
     `SettingsPage` 基类提供了 `ProjectMgr` 要保持的属性。`BindProperties` 方法使用 `ProjectMgr` 检索并将持久化的属性值设置相应的属性。`ApplyChanges` 方法使用 `ProjectMgr` 获取属性的值并将其保留到项目文件。 该属性设置方法设置 `IsDirty` 为 true 以指示属性具有要保留。  当您保存项目或解决方案时，会发生持久性。  
  
5.  重新生成 SimpleProject 解决方案并启动调试。 应显示的实验实例。  
  
6.  在实验实例中，将创建一个新的 SimpleProject 应用程序。  
  
7.  Visual Studio 会调用您的项目工厂通过使用 Visual Studio 模板创建项目。 在代码编辑器中打开新的 Program.cs 文件。  
  
8.  用鼠标右键单击中的项目节点 **解决方案资源管理器**, ，然后单击 **属性**。**属性页** 中会显示对话框。  
  
 ![](../extensibility/media/simpproj2_proppage.png "SimpProj2\_PropPage")  
  
## 测试项目属性页  
 现在，你可以测试是否可以修改和更改属性值。  
  
1.  在 **{1\>myconsoleapplication 属性页** 对话框中，更改 **DefaultNamespace** 到 **MyApplication**。  
  
2.  选择 **OutputType** 属性，，再选择 **类库**。  
  
3.  单击 **应用**, ，然后单击 **确定**。  
  
4.  重新打开 **属性页** 对话框框中，验证是否已永久保存所做的更改。  
  
5.  关闭 Visual Studio 的实验实例。  
  
6.  重新打开的实验实例。  
  
7.  重新打开 **属性页** 对话框框中，验证是否已永久保存所做的更改。  
  
8.  关闭 Visual Studio 的实验实例。  
  
 ![](../extensibility/media/simpproj2_proppage2.png "SimpProj2\_PropPage2")