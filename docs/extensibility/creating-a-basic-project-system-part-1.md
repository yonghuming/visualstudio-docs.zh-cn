---
title: "创建基本项目系统，第 1 部分 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
caps.latest.revision: "47"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e61c0d681dac52e85c3854325ee20ada29d74d4c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="creating-a-basic-project-system-part-1"></a>创建基本项目系统中，第 1 部分
在 Visual Studio 中，项目是开发人员使用可组织源代码文件和其他资产的容器。 项目显示为子级中的解决方案的**解决方案资源管理器**。 项目可以组织、 生成、 调试和部署源代码和创建对 Web 服务、 数据库和其他资源的引用。  
  
 项目文件中定义了项目，例如 Visual C# 项目的.csproj 文件。 你可以创建自己的项目类型具有自己的项目文件扩展名。 有关项目类型的详细信息，请参阅[项目类型](../extensibility/internals/project-types.md)。  
  
> [!NOTE]
>  如果你需要用来扩展 Visual Studio 自定义项目类型，则强烈建议利用[Visual Studio 项目系统](https://github.com/Microsoft/VSProjectSystem)具有很多通过生成一个从零开始的项目系统的优点：  
>   
>  -   更轻松的载入。  即便是基本项目系统需要成千上万的代码的行。  利用 CPS 可以载入成本减少到几次单击，然后你就可以与你的需求进行自定义。  
> -   更容易维护。  通过综合利用 CPS，只需维护自己的方案。  我们处理保养的所有项目系统基础结构。  
>   
>  如果需要目标版本的 Visual Studio 早于 Visual Studio 2013，你将无法在 Visual Studio 扩展中利用 CPS。  如果是这种情况，本演练将是一个好的开始。  
  
 本演练演示了如何创建具有项目文件名称扩展.myproj 的项目类型。 本演练从现有的 Visual C# 项目系统中继承。  
  
> [!NOTE]
>  扩展项目的更多示例，请参阅[VSSDK 示例](http://aka.ms/vs2015sdksamples)。  
  
 本演练介绍如何完成这些任务：  
  
-   创建基本项目类型。  
  
-   创建基本项目模板。  
  
-   注册 Visual Studio 项目模板。  
  
-   通过打开创建一个项目实例**新项目**对话框中，然后使用你的模板。  
  
-   创建项目工厂，以你的项目系统。  
  
-   创建你的项目系统的项目节点。  
  
-   添加了项目系统的自定义图标。  
  
-   实现基本的模板参数替换。  
  
## <a name="prerequisites"></a>先决条件  
 从 Visual Studio 2015 开始，你并不安装 Visual Studio SDK 从下载中心。 它将包括作为 Visual Studio 安装程序中的可选功能。 你还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
 你还必须下载的源代码[项目的托管包框架](http://mpfproj12.codeplex.com/)。 将文件提取到你将要创建的解决方案可以访问的位置。  
  
## <a name="creating-a-basic-project-type"></a>创建基本项目类型  
 创建一个名为的 C# VSIX 项目**SimpleProject**。 (**文件，新建、 项目**然后**C#，扩展性，Visual Studio 包**)。 添加 Visual Studio 包项目项模板 (在解决方案资源管理器，右键单击项目节点并选择**添加 / 新项**，然后转到**扩展性 / Visual Studio 包**)。 命名该文件**SimpleProjectPackage**。  
  
## <a name="creating-a-basic-project-template"></a>创建基本项目模板  
 现在，你可以修改此基本 VSPackage 实现新.myproj 项目类型。 若要创建基于.myproj 项目类型的项目，Visual Studio 必须知道哪些文件、 资源和引用将添加到新项目。 若要提供此信息，请将项目文件放入项目模板文件夹。 当用户使用.myproj 项目创建项目时，文件将复制到新项目。  
  
#### <a name="to-create-a-basic-project-template"></a>要创建基本项目模板  
  
1.  将三个文件夹添加到项目中，一个在其他： **Templates\Projects\SimpleProject**。 (在**解决方案资源管理器**，右键单击**SimpleProject**项目节点，指向**添加**，然后单击**新文件夹**。 将该文件夹命名为 `Templates`注册一个免费试用帐户。 在**模板**文件夹中，添加名为的文件夹`Projects`。 在**项目**文件夹中，添加名为的文件夹`SimpleProject`。)  
  
2.  在**Projects\SimpleProject**文件夹添加一个名为的图标文件`SimpleProject.ico`。 当你单击**添加**，图标编辑器随即打开。  
  
3.  使不同的图标。 此图标将出现在**新项目**稍后在演练中的对话框。  
  
     ![简单项目图标](../extensibility/media/simpleprojicon.png "SimpleProjIcon")  
  
4.  保存图标，并关闭图标编辑器。  
  
5.  在**Projects\SimpleProject**文件夹中，添加**类**项名为`Program.cs`。  
  
6.  用以下行替换现有代码。  
  
    ```csharp  
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
    >  这不是 Program.cs 代码中; 的最终形式替换参数将在稍后的步骤得到处理。 你可能会看到编译错误，但只要文件的**BuildAction**是**内容**，你应该能够生成并按常规方式运行项目。  
  
1.  保存该文件。  
  
2.  从将 AssemblyInfo.cs 文件复制**属性**文件夹**Projects\SimpleProject**文件夹。  
  
3.  在**Projects\SimpleProject**文件夹添加一个名为的 XML 文件`SimpleProject.myproj`。  
  
    > [!NOTE]
    >  此类型的所有项目的文件扩展名是.myproj。 如果你想要对其进行更改，必须在该演练中提到的无处不在更改。  
  
4.  现有内容替换为以下行。  
  
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
  
6.  在**属性**窗口中，设置**生成操作**的 AssemblyInfo.cs、 Program.cs、 SimpleProject.ico，和到 SimpleProject.myproj**内容**，并设置其**将包括在 VSIX**属性设置为**True**。  
  
 此项目模板描述基本 Visual C# 项目具有的调试配置和发布配置。 该项目包括两个源文件、 AssemblyInfo.cs 和 Program.cs 中，和多个程序集引用。 当从模板创建一个项目时，ProjectGuid 值都自动替换为新的 GUID。  
  
 在**解决方案资源管理器**，展开**模板**文件夹应出现，如下所示：  
  
 模板  
  
 项目  
  
 SimpleProject  
  
 AssemblyInfo.cs  
  
 Program.cs  
  
 SimpleProject.ico  
  
 SimpleProject.myproj  
  
## <a name="creating-a-basic-project-factory"></a>创建基本项目工厂  
 你必须告知 Visual Studio 项目模板文件夹的位置。 若要执行此操作，请将属性添加到 VSPackage 实现的类的项目工厂，以便生成 VSPackage 时，模板位置将写入系统注册表。 首先创建一个基本项目工厂，它由项目工厂 GUID 标识。 使用<xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute>属性连接到 SimpleProjectPackage 类的项目工厂。  
  
#### <a name="to-create-a-basic-project-factory"></a>若要创建基本项目工厂  
  
1.  在代码编辑器中打开 SimpleProjectPackageGuids.cs。  
  
2.  为你的项目工厂创建 Guid (上**工具**菜单上，单击**创建 GUID**)，或使用下面的示例中的一个。 将 Guid 添加到 SimpleProjectPackageGuids 类。 GUID 格式和字符串格式必须为 Guid。 生成的代码应类似于下面的示例。  
  
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
  
3.  将类添加到顶部**SimpleProject**文件夹名为`SimpleProjectFactory.cs`。  
  
4.  添加以下 using 语句：  
  
    ```  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5.  将 Guid 属性添加到 SimpleProjectFactory 类。 属性的值为新项目工厂 GUID。  
  
    ```  
    [Guid(SimpleProjectGuids.guidSimpleProjectFactoryString)]  
    class SimpleProjectFactory  
    {  
    }  
    ```  
  
 现在你可以注册你的项目模板。  
  
#### <a name="to-register-the-project-template"></a>若要注册的项目模板  
  
1.  在 SimpleProjectPackage.cs，添加<xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute>属性设为 SimpleProjectPackage 类，如下所示。  
  
    ```  
    [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",   
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",   
        @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]  
    [Guid(SimpleProjectGuids.guidSimpleProjectPkgString)]  
    public sealed class SimpleProjectPackage : Package  
    ```  
  
2.  重新生成解决方案并确认生成过程中未出现错误。  
  
     重新生成注册项目模板。  
  
 参数`defaultProjectExtension`和`possibleProjectExtensions`设置为项目文件扩展名 (.myproj)。 `projectTemplatesDirectory`参数设置为模板文件夹的相对路径。 在生成过程将转换为完全生成并添加到注册表来注册该项目系统此路径。  
  
## <a name="testing-the-template-registration"></a>测试模板注册  
 模板注册告知 Visual Studio 项目模板文件夹的位置，以便 Visual Studio 可以显示的模板名称和图标**新项目**对话框。  
  
#### <a name="to-test-the-template-registration"></a>若要测试的模板注册  
  
1.  按 F5 开始调试 Visual Studio 的实验实例。  
  
2.  在实验实例中，创建你的新创建的项目类型的新项目。 在**新项目**对话框中，你应看到**SimpleProject**下**已安装的模板**。  
  
 现在你已注册的项目工厂。 但是，它无法尚未创建项目。 项目包和项目工厂协同工作来创建和初始化一个项目。  
  
## <a name="add-the-managed-package-framework-code"></a>将托管包框架的代码添加  
 实现项目包和项目工厂之间的连接。  
  
-   为托管包框架导入的源代码文件。  
  
    1.  卸载 SimpleProject 项目 (在**解决方案资源管理器**，选择项目节点，然后在上下文菜单上单击**卸载项目**。) 并在 XML 编辑器中打开项目文件。  
  
    2.  将下面的块添加到项目文件 (上方\<导入 > 块)。 将 ProjectBasePath 设置为你刚下载的托管包框架代码中的 ProjectBase.files 文件的位置。 你可能需要添加一个反斜杠到路径名。 如果不这样做，项目可能无法找到托管包框架代码。  
  
        ```  
        <PropertyGroup>  
             <ProjectBasePath>your path here\</ProjectBasePath>  
             <RegisterWithCodebase>true</RegisterWithCodebase>  
          </PropertyGroup>  
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />  
        ```  
  
        > [!IMPORTANT]
        >  不要忘记在路径末尾反斜杠。  
  
    3.  重新加载项目。  
  
    4.  添加对下列程序集的引用：  
  
        -   Microsoft.VisualStudio.Designer.Interfaces (在\<VSSDK 安装 > \VisualStudioIntegration\Common\Assemblies\v2.0)  
  
        -   WindowsBase  
  
        -   Microsoft.Build.Tasks.v4.0  
  
#### <a name="to-initialize-the-project-factory"></a>若要初始化项目工厂  
  
1.  在 SimpleProjectPackage.cs 文件中，添加以下`using`语句。  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
2.  派生`SimpleProjectPackage`类`Microsoft.VisualStudio.Package.ProjectPackage`。  
  
    ```  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
3.  注册项目工厂。 添加以下行将对`SimpleProjectPackage.Initialize`方法中，紧后面`base.Initialize`。  
  
    ```  
    base.Initialize();  
    this.RegisterProjectFactory(new SimpleProjectFactory(this));  
    ```  
  
4.  实现抽象属性`ProductUserContext`:  
  
    ```csharp  
    public override string ProductUserContext  
        {  
            get { return ""; }  
    }  
    ```  
  
5.  在 SimpleProjectFactory.cs，添加以下`using`后现有语句`using`语句。  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
6.  派生`SimpleProjectFactory`类`ProjectFactory`。  
  
    ```  
    class SimpleProjectFactory : ProjectFactory  
    ```  
  
7.  添加以下 dummy 方法`SimpleProjectFactory`类。 将在后面的部分中实现此方法。  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        return null;  
    }  
    ```  
  
8.  添加以下字段和构造函数`SimpleProjectFactory`类。 这`SimpleProjectPackage`引用缓存的私有字段，以便可以在设置服务提供者站点使用它。  
  
    ```  
    private SimpleProjectPackage package;  
  
    public SimpleProjectFactory(SimpleProjectPackage package)  
        : base(package)  
    {  
        this.package = package;  
    }  
    ```  
  
9. 重新生成解决方案并确认生成过程中未出现错误。  
  
## <a name="testing-the-project-factory-implementation"></a>测试项目工厂实现  
 测试是否调用你的项目工厂实现的构造函数。  
  
#### <a name="to-test-the-project-factory-implementation"></a>若要测试的项目工厂实现  
  
1.  在 SimpleProjectFactory.cs 文件中，在中的以下行上设置断点`SimpleProjectFactory`构造函数。  
  
    ```  
    this.package = package;  
    ```  
  
2.  按 F5 启动 Visual Studio 的实验实例。  
  
3.  在实验实例中，开始创建新项目。在**新项目**对话框中，选择 SimpleProject 项目类型，然后单击**确定**。 执行在断点处停止。  
  
4.  清除断点和停止调试。 由于我们尚未尚未创建的项目节点，则项目创建代码仍将引发异常。  
  
## <a name="extending-the-project-node-class"></a>扩展项目节点类  
 现在你可以实现`SimpleProjectNode`类，该类派生自`ProjectNode`类。 `ProjectNode`基类处理项目创建的以下任务：  
  
-   将项目模板文件中，SimpleProject.myproj，复制到新的项目文件夹中。 根据输入中的名称重命名副本**新项目**对话框。 `ProjectGuid`属性值将替换为新的 GUID。  
  
-   遍历的项目模板文件中，SimpleProject.myproj，MSBuild 元素，并查找`Compile`元素。 每个`Compile`目标文件，将文件复制到新的项目文件夹。  
  
 派生`SimpleProjectNode`类处理这些任务：  
  
-   使项目和文件中的节点的图标**解决方案资源管理器**中创建或选择。  
  
-   使指定的其他项目模板参数替换。  
  
#### <a name="to-extend-the-project-node-class"></a>扩展项目节点类  
  
1.  
  
2.  添加一个名为类`SimpleProjectNode.cs`。  
  
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
  
 这`SimpleProjectNode`类实现具有这些重写的方法：  
  
-   `ProjectGuid`它返回的项目工厂 GUID。  
  
-   `ProjectType`它返回的项目类型的本地化的名称。  
  
-   `AddFileFromTemplate`其中的模板文件夹中将选定的文件复制到目标项目。 在后面的部分中进一步实现此方法。  
  
 `SimpleProjectNode`构造函数、 like`SimpleProjectFactory`构造函数中，缓存`SimpleProjectPackage`中供以后使用私有字段的引用。  
  
 若要连接`SimpleProjectFactory`类到`SimpleProjectNode`类，你必须实例化一个新`SimpleProjectNode`中`SimpleProjectFactory.CreateProject`方法并将其缓存在私有字段以供将来使用。  
  
#### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>将项目工厂类和在节点类连接  
  
1.  在 SimpleProjectFactory.cs 文件中，添加以下`using`语句：  
  
    ```  
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
    ```  
  
2.  替换`SimpleProjectFactory.CreateProject`通过使用下面的代码的方法。  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        SimpleProjectNode project = new SimpleProjectNode(this.package);  
  
        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));  
        return project;  
    }  
    ```  
  
3.  重新生成解决方案并确认生成过程中未出现错误。  
  
## <a name="testing-the-project-node-class"></a>测试项目节点类  
 测试你的项目工厂，以查看它是否创建项目层次结构。  
  
#### <a name="to-test-the-project-node-class"></a>若要测试的项目节点类  
  
1.  按 F5 开始调试。 在实验实例中，创建新 SimpleProject。  
  
2.  Visual Studio 应调用你的项目工厂创建项目。  
  
3.  关闭 Visual Studio 的实验实例。  
  
## <a name="adding-a-custom-project-node-icon"></a>添加一个自定义项目节点图标  
 如前面章节中的项目节点图标是一个默认图标。 你可以将其更改为自定义图标。  
  
#### <a name="to-add-a-custom-project-node-icon"></a>若要添加自定义项目节点图标  
  
1.  在**资源**文件夹中，添加一个名为 SimpleProjectNode.bmp 的位图文件。  
  
2.  在**属性**windows，减至 16x16 像素的位图。 请位图不同。  
  
     ![简单项目命令](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")  
  
3.  在**属性**窗口中，更改**生成操作**的位图转换**嵌入的资源**。  
  
4.  在 SimpleProjectNode.cs，添加以下`using`语句：  
  
    ```  
    using System.Drawing;  
    using System.Windows.Forms;  
    ```  
  
5.  将以下静态字段和构造函数添加`SimpleProjectNode`类。  
  
    ```  
    private static ImageList imageList;  
  
    static SimpleProjectNode()  
    {  
        imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));  
    }  
    ```  
  
6.  将以下属性添加到的开头`SimpleProjectNode`类。  
  
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
  
 在静态构造期间`SimpleProjectNode`从程序集清单资源中检索项目节点位图，并将其缓存在私有字段以供将来使用。 请注意的语法<xref:System.Reflection.Assembly.GetManifestResourceStream%2A>映像路径。 若要查看的嵌入到程序集中的清单资源的名称，使用<xref:System.Reflection.Assembly.GetManifestResourceNames%2A>方法。 当此方法适用于`SimpleProject`程序集，则结果应是，如下所示：  
  
-   SimpleProject.Resources.resources  
  
-   VisualStudio.Project.resources  
  
-   SimpleProject.VSPackage.resources  
  
-   Resources.imagelis.bmp  
  
-   Microsoft.VisualStudio.Project.DontShowAgainDialog.resources  
  
-   Microsoft.VisualStudio.Project.SecurityWarningDialog.resources  
  
-   SimpleProject.Resources.SimpleProjectNode.bmp  
  
 在实例构造期间`ProjectNode`基类加载的 Resources.imagelis.bmp，在其中都是从 Resources\imagelis.bmp 的嵌入常用的 16 x 16 位图。 此位图列表将提供给`SimpleProjectNode`作为 ImageHandler.ImageList。 `SimpleProjectNode`将项目节点位图追加到列表。 为更高版本的公钥的值用作缓存的项目节点位图的图像列表中的偏移量`ImageIndex`属性。 Visual Studio 使用此属性来确定要显示为节点项目图标的位图。  
  
## <a name="testing-the-custom-project-node-icon"></a>测试自定义项目的节点图标  
 测试你的项目工厂，以查看它是否创建具有您自定义项目节点的图标的项目层次结构。  
  
#### <a name="to-test-the-custom-project-node-icon"></a>若要测试自定义项目的节点图标  
  
1.  开始调试，并在实验实例中创建新 SimpleProject。  
  
2.  在新建的项目中，请注意 SimpleProjectNode.bmp 用作节点项目图标。  
  
     ![简单项目新项目节点](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")  
  
3.  在代码编辑器中打开 Program.cs。 你应看到类似于下面的代码的源代码。  
  
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
  
     请注意，模板参数 $nameSpace$ 和 $className$ 没有新值。 您将学习如何在下一节中实现模板参数替换。  
  
## <a name="substituting-template-parameters"></a>替换模板参数  
 在早期的部分中，你的项目模板与 Visual Studio 使用注册`ProvideProjectFactory`属性。 以这种方式注册模板文件夹的路径，你可以通过重写并展开让基本模板参数替换`ProjectNode.AddFileFromTemplate`类。 有关详细信息，请参阅[新项目生成： 高级选项、 第二](../extensibility/internals/new-project-generation-under-the-hood-part-two.md)。  
  
 现在替换将代码添加到`AddFileFromTemplate`类。  
  
#### <a name="to-substitute-template-parameters"></a>要替换模板参数  
  
1.  在 SimpleProjectNode.cs 文件中，添加以下`using`语句。  
  
    ```  
    using System.IO;  
    ```  
  
2.  替换`AddFileFromTemplate`通过使用下面的代码的方法。  
  
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
  
3.  设置在方法中，断点紧随其后`className`赋值语句。  
  
 赋值语句确定命名空间和新的类名称的合理值。 这两个`ProjectNode.FileTemplateProcessor.AddReplace`方法调用通过使用这些新值来替换相应的模板参数值。  
  
## <a name="testing-the-template-parameter-substitution"></a>测试模板参数替换  
 现在，你可以测试模板参数替换。  
  
#### <a name="to-test-the-template-parameter-substitution"></a>若要测试模板参数替换  
  
1.  开始调试，并在实验实例中创建新 SimpleProject。  
  
2.  执行在中的断点处停止`AddFileFromTemplate`方法。  
  
3.  检查有关值`nameSpace`和`className`参数。  
  
    -   `nameSpace`提供的值\<RootNamespace > \Templates\Projects\SimpleProject\SimpleProject.myproj 项目模板文件中的元素。 在这种情况下，值为"MyRootNamespace"。  
  
    -   `className`提供类源的文件名称，不带文件扩展名的值。 在这种情况下，第一个文件复制到目标文件夹是 AssemblyInfo.cs;因此，类名的值是"AssemblyInfo"。  
  
4.  移除断点，然后按 F5 以继续执行。  
  
     Visual Studio 应完成创建一个项目。  
  
5.  在代码编辑器中打开 Program.cs。 你应看到类似于下面的代码的源代码。  
  
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
  
     请注意，命名空间现在是"MyRootNamespace"和类名称现在是"程序"。  
  
6.  开始调试项目。 新项目应编译、 运行和显示"Hello VSX!!!" 显示文本字符串“Hello World!”。  
  
     ![简单项目命令](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")  
  
 祝贺你！ 你已实现的基本托管的项目系统。