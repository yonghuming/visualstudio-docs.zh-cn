---
title: "创建基本项目系统中，第 1 部分 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
caps.latest.revision: 47
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 47
---
# 创建基本项目系统中，第 1 部分
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 Visual Studio 中，项目是开发人员用于组织源代码文件和其他资产的容器。 项目显示为子级中的解决方案 **解决方案资源管理器**。 项目可以组织、 生成、 调试，并将源代码部署和创建对 Web 服务、 数据库和其他资源的引用。  
  
 项目文件中定义了项目，例如 Visual C\# 项目的.csproj 文件。 您可以创建您自己的项目类型具有自己的项目文件扩展名。 有关项目类型的详细信息，请参阅 [项目类型](../extensibility/internals/project-types.md)。  
  
> [!NOTE]
>  如果您需要使用自定义项目类型来扩展 Visual Studio，我们强烈建议利用 [Visual Studio 项目系统](https://github.com/Microsoft/VSProjectSystem) 具有数超过生成一个从零开始的项目系统的优势︰  
>   
>  -   更容易载入。  即便是基本项目系统要求进行过成千上万行代码。  利用 CPS 到几次单击减少载入成本之前准备好您的需要自定义它。  
> -   更便于维护。  通过利用 CPS，只需维护你自己的方案。  我们处理所有项目系统基础结构的保养。  
>   
>  如果需要目标版本的 Visual Studio 早于 Visual Studio 2013，您将不能在 Visual Studio 扩展中利用 CPS。  如果是这种情况，本演练将是一个好的入门。  
  
 本演练演示如何创建具有项目文件名称扩展.myproj 的项目类型。 本演练中从现有的 Visual C\# 项目系统中继承。  
  
> [!NOTE]
>  有关完整的语言项目系统的端到端示例，请参阅 IronPython 示例中的深入了解 [VSSDK 示例](../misc/vssdk-samples.md)。  
  
 本演练介绍如何完成这些任务︰  
  
-   创建基本项目类型。  
  
-   创建基本项目模板。  
  
-   注册 Visual Studio 项目模板。  
  
-   创建一个项目实例通过打开 **新项目** 对话框中，然后使用您的模板。  
  
-   创建项目系统的项目工厂。  
  
-   创建项目系统的项目节点。  
  
-   添加了项目系统的自定义图标。  
  
-   实现基本的模板参数替换。  
  
## 系统必备  
 启动 Visual Studio 2015 中，您并不安装 Visual Studio SDK 从下载中心获得。 它将包括作为 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
 你还必须下载的源代码 [项目的管理包框架](http://mpfproj12.codeplex.com/)。 将文件提取到您要创建的解决方案可以访问的位置。  
  
## 创建基本项目类型  
 创建一个名为 C\# VSIX 项目 **SimpleProject**。 \(**文件，新建、 项目** 然后 **C\# 中，可扩展性，Visual Studio 程序包**\)。 Visual Studio Package 项目项模板添加 \(在解决方案资源管理器，右键单击项目节点并选择 **添加 \/ 新项**, ，然后转到 **扩展性 \/ Visual Studio Package**\)。 命名该文件 **SimpleProjectPackage**。  
  
## 创建基本项目模板  
 现在，您可以修改此基本 VSPackage 来实现新.myproj 项目类型。 若要创建基于.myproj 项目类型的项目时，Visual Studio 必须知道哪些文件、 资源和要添加到新项目的引用。 为了提供此信息，请将项目模板文件夹中的项目文件。 当用户使用.myproj 项目创建项目时，文件复制到新项目。  
  
#### 若要创建基本项目模板  
  
1.  添加到项目中，一个在其他三个文件夹︰ **Templates\\Projects\\SimpleProject**。 \(在 **解决方案资源管理器**, ，用鼠标右键单击 **SimpleProject** 项目节点，指向 **添加**, ，然后单击 **新文件夹**。 将文件夹命名为 `Templates`。 在 **模板** 文件夹中，添加一个名为文件夹 `Projects`。 在 **项目** 文件夹中，添加一个名为文件夹 `SimpleProject`。\)  
  
2.  在 **Projects\\SimpleProject** 文件夹添加一个名为的图标文件 `SimpleProject.ico`。 当您单击 **添加**, ，图标编辑器随即打开。  
  
3.  使不同的图标。 此图标将出现在 **新项目** 更高版本在本演练中的对话框。  
  
     ![“简单项目”图标](../extensibility/media/simpleprojicon.png "SimpleProjIcon")  
  
4.  保存图标，并关闭图标编辑器。  
  
5.  在 **Projects\\SimpleProject** 文件夹中，添加 **类** 项名为 `Program.cs`。  
  
6.  将现有代码替换为以下行。  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
  
    namespace $nameSpace$  
    {  
        public class $className$  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
    > [!IMPORTANT]
    >  这不是 Program.cs 代码; 的最终形式替换参数将在后面的步骤得到处理。 您可能会看到编译错误，但只要文件的 **BuildAction** 是 **内容**, ，您应该能够生成并照常运行项目。  
  
1.  保存该文件。  
  
2.  从将 AssemblyInfo.cs 文件复制 **属性** 文件夹 **Projects\\SimpleProject** 文件夹。  
  
3.  在 **Projects\\SimpleProject** 文件夹中添加名为 XML 文件 `SimpleProject.myproj`。  
  
    > [!NOTE]
    >  这种类型的所有项目的文件扩展名是.myproj。 如果你想要将其更改，必须在本演练中提到的无处不在更改。  
  
4.  用以下行替换现有内容。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <SchemaVersion>2.0</SchemaVersion>  
        <ProjectGuid></ProjectGuid>  
        <OutputType>Exe</OutputType>  
        <RootNamespace>MyRootNamespace</RootNamespace>  
        <AssemblyName>MyAssemblyName</AssemblyName>  
        <EnableUnmanagedDebugging>false</EnableUnmanagedDebugging>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        <DebugSymbols>true</DebugSymbols>  
        <OutputPath>bin\Debug\</OutputPath>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">  
        <DebugSymbols>false</DebugSymbols>  
        <OutputPath>bin\Release\</OutputPath>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="mscorlib" />  
        <Reference Include="System" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Xml" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="AssemblyInfo.cs">  
          <SubType>Code</SubType>  
        </Compile>  
        <Compile Include="Program.cs">  
          <SubType>Code</SubType>  
        </Compile>  
      </ItemGroup>  
      <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />  
    </Project>  
    ```  
  
5.  保存该文件。  
  
6.  在 **属性** 窗口中，设置 **生成操作** AssemblyInfo.cs、 Program.cs、 SimpleProject.ico，和为 SimpleProject.myproj **内容**, ，并设置其 **包含在 VSIX** 属性设置为 **True**。  
  
 此项目模板介绍基本 Visual C\# 中具有的项目的调试配置和发布配置。 该项目包括两个源文件、 AssemblyInfo.cs 和 Program.cs 中，多个程序集的引用。 当从模板创建项目时，ProjectGuid 值将自动替换为新的 GUID。  
  
 在 **解决方案资源管理器**, ，已展开 **模板** 文件夹应出现，如下所示︰  
  
 模板  
  
 项目  
  
 SimpleProject  
  
 AssemblyInfo.cs  
  
 Program.cs  
  
 SimpleProject.ico  
  
 SimpleProject.myproj  
  
## 创建基本项目工厂  
 您必须告诉 Visual Studio 项目模板文件夹的位置。 若要执行此操作，将添加到 VSPackage 类，该类实现项目工厂，以便当生成 VSPackage，模板位置写入系统注册表的属性。 首先创建一个基本项目工厂，它由项目工厂的 GUID 标识。 使用 <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> 特性以将项目工厂连接到 SimpleProjectPackage 类。  
  
#### 若要创建基本项目工厂  
  
1.  在代码编辑器中打开 SimpleProjectPackageGuids.cs。  
  
2.  为您项目的工厂创建的 Guid \(上 **工具** 菜单上，单击 **创建 GUID**\)，或者使用下面的示例所示。 将 Guid 添加到 SimpleProjectPackageGuids 类。 GUID 格式和字符串格式必须为 Guid。 生成的代码应类似于下面的示例。  
  
    ```  
    static class SimpleProjectPackageGuids  
    {  
        public const string guidSimpleProjectPkgString =   
            "96bf4c26-d94e-43bf-a56a-f8500b52bfad";  
        public const string guidSimpleProjectCmdSetString =   
            "72c23e1d-f389-410a-b5f1-c938303f1391";  
        public const string guidSimpleProjectFactoryString =   
            "471EC4BB-E47E-4229-A789-D1F5F83B52D4";  
  
        public static readonly Guid guidSimpleProjectCmdSet =   
            new Guid(guidSimpleProjectCmdSetString);  
        public static readonly Guid guidSimpleProjectFactory =   
            new Guid(guidSimpleProjectFactoryString);  
    }  
    ```  
  
3.  将类添加到文件的顶部 **SimpleProject** 文件夹名为 `SimpleProjectFactory.cs`。  
  
4.  添加以下 using 语句︰  
  
    ```  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5.  将 Guid 属性添加到 SimpleProjectFactory 类。 该属性的值是新项目工厂的 GUID。  
  
    ```  
    [Guid(SimpleProjectGuids.guidSimpleProjectFactoryString)]  
    class SimpleProjectFactory  
    {  
    }  
    ```  
  
 现在，您可以注册您的项目模板。  
  
#### 若要注册此项目模板  
  
1.  在 SimpleProjectPackage.cs，添加 <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> 属性设为 SimpleProjectPackage 类，如下所示。  
  
    ```  
    [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",   
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",   
        @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]  
    [Guid(SimpleProjectGuids.guidSimpleProjectPkgString)]  
    public sealed class SimpleProjectPackage : Package  
    ```  
  
2.  重新生成解决方案并确认生成过程中未出现错误。  
  
     重新生成注册项目模板。  
  
 参数 `defaultProjectExtension` 和 `possibleProjectExtensions` 设置为项目文件扩展名 \(.myproj\)。`projectTemplatesDirectory` 参数设置为模板文件夹的相对路径。 在生成过程将转换为完全生成并添加到注册表来注册该项目系统中此路径。  
  
## 测试模板注册  
 模板注册会告知 Visual Studio 项目模板文件夹的位置，以便 Visual Studio 模板的名称和图标可以显示 **新项目** 对话框。  
  
#### 若要测试的模板注册  
  
1.  按 F5 开始调试 Visual Studio 的实验实例。  
  
2.  在实验实例中，创建一个新创建的项目类型的新项目。 在 **新项目** 对话框中，您应看到 **SimpleProject** 下 **已安装的模板**。  
  
 现在你已注册的项目工厂。 但是，它还不能创建一个项目。 项目包和项目工厂协同工作来创建和初始化一个项目。  
  
## 将管理包框架的代码添加  
 实现项目包和项目工厂之间的连接。  
  
-   导入管理包框架的源代码文件。  
  
    1.  卸载 SimpleProject 项目 \(在 **解决方案资源管理器**, ，选择项目节点，然后在上下文菜单上单击 **卸载项目**。\) 并在 XML 编辑器中打开项目文件。  
  
    2.  将以下块添加到项目文件 （正上方的 \< 导入 \> 块中）。 将 ProjectBasePath 设置为在管理包 Framework 代码中您刚下载的 ProjectBase.files 文件的位置。 您可能需要添加一个反斜杠到路径名。 如果不这样做，项目可能无法找到的管理包框架代码。  
  
        ```  
        <PropertyGroup>  
             <ProjectBasePath>your path here\</ProjectBasePath>  
             <RegisterWithCodebase>true</RegisterWithCodebase>  
          </PropertyGroup>  
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />  
        ```  
  
        > [!IMPORTANT]
        >  不要忘记在路径末尾的反斜杠。  
  
    3.  重新加载项目。  
  
    4.  添加对下列程序集的引用：  
  
        -   （在 \< VSSDK 安装 \> \\VisualStudioIntegration\\Common\\Assemblies\\v2.0\) Microsoft.VisualStudio.Designer.Interfaces  
  
        -   WindowsBase  
  
        -   Microsoft.Build.Tasks.v4.0  
  
#### 用以初始化项目工厂  
  
1.  在 SimpleProjectPackage.cs 文件中，添加以下 `using` 语句。  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
2.  派生 `SimpleProjectPackage` 类 `Microsoft.VisualStudio.Package.ProjectPackage`。  
  
    ```  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
3.  注册项目工厂。 添加以下代码行到 `SimpleProjectPackage.Initialize` 方法中，紧后面 `base.Initialize`。  
  
    ```  
    base.Initialize();  
    this.RegisterProjectFactory(new SimpleProjectFactory(this));  
    ```  
  
4.  实现的抽象属性 `ProductUserContext`:  
  
    ```c#  
    public override string ProductUserContext  
        {  
            get { return ""; }  
    }  
    ```  
  
5.  在 SimpleProjectFactory.cs，添加以下 `using` 后现有语句 `using` 语句。  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
6.  派生 `SimpleProjectFactory` 类 `ProjectFactory`。  
  
    ```  
    class SimpleProjectFactory : ProjectFactory  
    ```  
  
7.  添加到以下虚拟方法 `SimpleProjectFactory` 类。 您将在后面的部分实现此方法。  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        return null;  
    }  
    ```  
  
8.  添加以下字段和构造函数 `SimpleProjectFactory` 类。 这 `SimpleProjectPackage` 引用缓存在私有字段，以便可以在设置服务提供者站点使用它。  
  
    ```  
    private SimpleProjectPackage package;  
  
    public SimpleProjectFactory(SimpleProjectPackage package)  
        : base(package)  
    {  
        this.package = package;  
    }  
    ```  
  
9. 重新生成解决方案并确认生成过程中未出现错误。  
  
## 测试项目工厂实现  
 测试是否调用项目工厂实现的构造函数。  
  
#### 若要测试的项目工厂实现  
  
1.  在 SimpleProjectFactory.cs 文件中，在下一行中设置断点 `SimpleProjectFactory` 构造函数。  
  
    ```  
    this.package = package;  
    ```  
  
2.  按 F5 以启动 Visual Studio 的实验实例。  
  
3.  在实验实例中，首先创建新项目。在 **新项目** 对话框中，选择 SimpleProject 项目类型，然后单击 **确定**。 执行在断点处停止。  
  
4.  清除断点，并停止调试。 由于我们尚未尚未创建的项目节点，项目创建代码仍将引发异常。  
  
## 扩展项目节点类  
 现在，您可以实现 `SimpleProjectNode` 类，该类派生自 `ProjectNode` 类。`ProjectNode` 基类处理项目创建的以下任务︰  
  
-   将项目模板文件中，SimpleProject.myproj，复制到新的项目文件夹中。 根据在中输入的名称重命名该副本 **新项目** 对话框。`ProjectGuid` 属性值替换为新的 GUID。  
  
-   遍历的项目模板文件中，SimpleProject.myproj，MSBuild 元素，并查找 `Compile` 的元素。 每个 `Compile` 目标文件，将文件复制到新的项目文件夹。  
  
 在派生 `SimpleProjectNode` 类处理这些任务︰  
  
-   使项目和文件中的节点的图标 **解决方案资源管理器** 要创建或选择。  
  
-   使指定的其他项目模板参数替换。  
  
#### 若要扩展项目节点类  
  
1.  
  
2.  添加一个名为类 `SimpleProjectNode.cs`。  
  
3.  用下面的代码替换现有代码。  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Project;  
  
    namespace SimpleProject  
    {  
        public class SimpleProjectNode : ProjectNode  
        {  
            private SimpleProjectPackage package;  
  
            public SimpleProjectNode(SimpleProjectPackage package)  
            {  
                this.package = package;  
            }  
            public override Guid ProjectGuid  
            {  
                get { return SimpleProjectGuids.guidSimpleProjectFactory; }  
            }  
            public override string ProjectType  
            {  
                get { return "SimpleProjectType"; }  
            }  
  
            public override void AddFileFromTemplate(  
                string source, string target)  
            {  
                this.FileTemplateProcessor.UntokenFile(source, target);  
                this.FileTemplateProcessor.Reset();  
            }  
        }  
    }  
    ```  
  
 这 `SimpleProjectNode` 类实现了这些重写的方法︰  
  
-   `ProjectGuid`, 表示将返回项目工厂的 GUID。  
  
-   `ProjectType`, 它返回的项目类型的本地化的名称。  
  
-   `AddFileFromTemplate`, 它从模板文件夹将选定的文件复制到目标项目。 在后面部分进一步实现此方法。  
  
 `SimpleProjectNode` 构造函数、 like `SimpleProjectFactory` 构造函数中，将缓存 `SimpleProjectPackage` 中以供将来使用的私有字段的引用。  
  
 若要连接 `SimpleProjectFactory` 类 `SimpleProjectNode` 类，则必须实例化一个新 `SimpleProjectNode` 中 `SimpleProjectFactory.CreateProject` 方法并将其缓存在私有字段以供将来使用。  
  
#### 连接项目工厂类和在节点类  
  
1.  在 SimpleProjectFactory.cs 文件中，添加以下 `using` 语句︰  
  
    ```  
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
    ```  
  
2.  替换 `SimpleProjectFactory.CreateProject` 方法通过使用下面的代码使用。  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        SimpleProjectNode project = new SimpleProjectNode(this.package);  
  
        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));  
        return project;  
    }  
    ```  
  
3.  重新生成解决方案并确认生成过程中未出现错误。  
  
## 测试项目节点类  
 测试您的项目工厂，以查看它是否创建项目层次结构。  
  
#### 若要测试项目节点类  
  
1.  按 F5 开始调试。 在实验实例中，将创建新 SimpleProject。  
  
2.  Visual Studio 应调用您的项目工厂创建的项目。  
  
3.  关闭 Visual Studio 的实验实例。  
  
## 添加自定义项目节点图标  
 前面的部分中的项目节点图标是一个默认图标。 您可以将其更改为自定义图标。  
  
#### 若要添加自定义项目节点图标  
  
1.  在 **资源** 文件夹中，添加一个名为 SimpleProjectNode.bmp 的位图文件。  
  
2.  在 **属性** windows，减至 16 × 16 像素的位图。 使不同的位图。  
  
     ![简单项目命令](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")  
  
3.  在 **属性** 窗口中，更改 **生成操作** 为位图的 **嵌入的资源**。  
  
4.  在 SimpleProjectNode.cs，添加以下 `using` 语句︰  
  
    ```  
    using System.Drawing;  
    using System.Windows.Forms;  
    ```  
  
5.  将以下静态字段和构造函数添加 `SimpleProjectNode` 类。  
  
    ```  
    private static ImageList imageList;  
  
    static SimpleProjectNode()  
    {  
        imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));  
    }  
    ```  
  
6.  将以下属性添加到的开头 `SimpleProjectNode` 类。  
  
    ```  
    internal static int imageIndex;  
       public override int ImageIndex  
       {  
           get { return imageIndex; }  
       }  
    ```  
  
7.  实例构造函数替换为以下代码。  
  
    ```  
    public SimpleProjectNode(SimpleProjectPackage package)  
    {  
        this.package = package;  
  
        imageIndex = this.ImageHandler.ImageList.Images.Count;  
  
        foreach (Image img in imageList.Images)  
        {  
            this.ImageHandler.AddImage(img);  
        }  
    }  
    ```  
  
 在静态构造期间 `SimpleProjectNode` 从程序集清单资源检索项目节点位图，并将其缓存在私有字段以供将来使用。 请注意语法 <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> 图像路径。 若要查看嵌入到程序集中的清单资源的名称，使用 <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> 方法。 当此方法应用于 `SimpleProject` 程序集的结果应该是，如下所示︰  
  
-   SimpleProject.Resources.resources  
  
-   VisualStudio.Project.resources  
  
-   SimpleProject.VSPackage.resources  
  
-   Resources.imagelis.bmp  
  
-   Microsoft.VisualStudio.Project.DontShowAgainDialog.resources  
  
-   Microsoft.VisualStudio.Project.SecurityWarningDialog.resources  
  
-   SimpleProject.Resources.SimpleProjectNode.bmp  
  
 实例构造期间 `ProjectNode` 基类加载的 Resources.imagelis.bmp，在其中都是从 Resources\\imagelis.bmp 的嵌入常用的 16x16 位图。 此位图列表已提供给 `SimpleProjectNode` 作为 ImageHandler.ImageList。`SimpleProjectNode` 将项目节点位图追加到列表。 图像列表中的项目节点位图的偏移量缓存供以后使用的公钥的值作为 `ImageIndex` 属性。 Visual Studio 将使用此属性来确定要显示为项目节点图标的位图。  
  
## 测试自定义项目节点图标  
 测试您的项目工厂，以查看它是否可创建具有您自定义项目节点图标的项目层次结构。  
  
#### 若要测试自定义项目节点图标  
  
1.  开始调试，并在实验实例中创建新 SimpleProject。  
  
2.  在新创建的项目，请注意 SimpleProjectNode.bmp 用作项目节点图标。  
  
     ![简单项目“新建项目节点”](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")  
  
3.  在代码编辑器中打开 Program.cs。 您应看到类似于下面的代码的源代码。  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
  
    namespace $nameSpace$  
    {  
        public class $className$  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
     请注意，模板参数 $nameSpace$ 和 $className$ 不具有新值。 您将学习如何在下一节中实现模板参数替换。  
  
## 替换模板参数  
 在前面部分中，您的项目模板与 Visual Studio 使用注册的 `ProvideProjectFactory` 属性。 以这种方式注册模板文件夹的路径，你可以通过重写并扩展让基本模板参数替换 `ProjectNode.AddFileFromTemplate` 类。 有关详细信息，请参阅[生成新的项目: 实质上，第二部分](../Topic/New%20Project%20Generation:%20Under%20the%20Hood,%20Part%20Two.md)。  
  
 现在替换将代码添加到 `AddFileFromTemplate` 类。  
  
#### 若要替换模板参数  
  
1.  在 SimpleProjectNode.cs 文件中，添加以下 `using` 语句。  
  
    ```  
    using System.IO;  
    ```  
  
2.  替换 `AddFileFromTemplate` 方法通过使用下面的代码使用。  
  
    ```  
    public override void AddFileFromTemplate(  
        string source, string target)  
    {  
        string nameSpace =   
            this.FileTemplateProcessor.GetFileNamespace(target, this);  
        string className = Path.GetFileNameWithoutExtension(target);  
  
        this.FileTemplateProcessor.AddReplace("$nameSpace$", nameSpace);  
        this.FileTemplateProcessor.AddReplace("$className$", className);  
  
        this.FileTemplateProcessor.UntokenFile(source, target);  
        this.FileTemplateProcessor.Reset();  
    }  
    ```  
  
3.  设置在方法中，断点紧随其后 `className` 赋值语句。  
  
 赋值语句确定命名空间和新的类名的合理值。 这两个 `ProjectNode.FileTemplateProcessor.AddReplace` 方法调用通过使用这些新值来替换相应的模板参数值。  
  
## 测试的模板参数替换  
 现在，你可以测试模板参数替换。  
  
#### 若要测试的模板参数替换  
  
1.  开始调试，并在实验实例中创建新 SimpleProject。  
  
2.  中的断点处停止执行 `AddFileFromTemplate` 方法。  
  
3.  检查有关值 `nameSpace` 和 `className` 参数。  
  
    -   `nameSpace` 被授权 \\Templates\\Projects\\SimpleProject\\SimpleProject.myproj 项目模板文件中的 \< 根命名空间 \> 元素的值。 在这种情况下，值为"MyRootNamespace"。  
  
    -   `className` 都提供了此类源的文件名称，不带文件扩展名值。 在这种情况下，复制到目标文件夹中的第一个文件是 AssemblyInfo.cs;因此，类名的值是"程序集信息"。  
  
4.  删除断点，然后按 F5 以继续执行。  
  
     Visual Studio 应完成项目的创建。  
  
5.  在代码编辑器中打开 Program.cs。 您应看到类似于下面的代码的源代码。  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
  
    namespace MyRootNamespace  
    {  
        public class Program  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
     请注意，命名空间现在是"MyRootNamespace"的类名称现在为"计划"。  
  
6.  开始调试项目。 新的项目应编译、 运行和显示"Hello VSX\!\!\!" 在控制台窗口中。  
  
     ![简单项目命令](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")  
  
 祝贺你！ 您已实现基本的托管的项目系统。