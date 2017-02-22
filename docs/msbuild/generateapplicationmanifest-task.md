---
title: "GenerateApplicationManifest 任务 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GenerateApplicationManifest"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "GenerateApplicationManifest 任务 [MSBuild]"
  - "HostInBrowser 属性 (MSBuild)"
  - "MSBuild, GenerateApplicationManifest 任务"
ms.assetid: a494102b-0cb2-4755-8e2a-d2c0f39fac1d
caps.latest.revision: 24
caps.handback.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# GenerateApplicationManifest 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

生成 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序清单或本机清单。  本机清单描述组件的方法是：为组件定义一个唯一的标识，并标识组成组件的所有程序集和文件。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序清单通过指示应用程序的入口点并指定应用程序的安全级别来扩展本机清单。  
  
## 参数  
 下表描述了 `GenerateApplicationManifest` 任务的参数。  
  
|Parameter|描述|  
|---------------|--------|  
|`AssemblyName`|可选 `String` 参数。<br /><br /> 为生成的清单指定程序集标识的 `Name` 字段。  如果未指定此参数，将从 `EntryPoint` 或 `InputManifest` 参数推断出该名称。  如果无法创建任何名称，该任务将引发错误。|  
|`AssemblyVersion`|可选 `String` 参数。<br /><br /> 为生成的清单指定程序集标识的 `Version` 字段。  如果未指定此参数，则使用默认值“1.0.0.0”。|  
|`ClrVersion`|可选 `String` 参数。<br /><br /> 指定应用程序所需的公共语言运行时 \(CLR\) 的最低版本。  默认值是生成系统正在使用的 CLR 版本。  如果任务正在生成本机清单，将忽略此参数。|  
|`ConfigFile`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 指定哪个项包含应用程序配置文件。  如果任务正在生成本机清单，将忽略此参数。|  
|`Dependencies`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 指定为生成的清单定义一组依赖程序集的项列表。  可以通过项元数据对每个项进行进一步的描述，以指示更多部署状态和依赖项类型。  有关更多信息，请参见下面的“项元数据”部分。|  
|`Description`|可选 `String` 参数。<br /><br /> 指定应用程序或组件的说明。|  
|`EntryPoint`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 指定用于指示生成的清单程序集的入口点的单个项。<br /><br /> 对于 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序清单，此参数指定在应用程序运行时启动的程序集。|  
|`ErrorReportUrl`|可选 [String](assetId:///String?qualifyHint=False&autoUpgrade=True) 参数。<br /><br /> 指定在 ClickOnce 安装的错误报告期间对话框中显示的网页的 URL。|  
|`FileAssociations`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 指定与 ClickOnce 部署清单关联的一个或多个文件类型的列表。<br /><br /> 文件关联只在针对 .NET Framework 3.5 或更高版本时才有效。|  
|`Files`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 要包含在清单中的文件。  指定每个文件的完整路径。|  
|`HostInBrowser`|可选 [Boolean](assetId:///Boolean?qualifyHint=False&autoUpgrade=True) 参数。<br /><br /> 如果为 `true`，则应用程序承载于浏览器中（与 WPF Web 浏览器应用程序一样）。|  
|`IconFile`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 指示应用程序图标文件。  应用程序图标在生成的应用程序清单中表示，可用于“开始”菜单和“添加\/删除程序”对话框。  如果未指定此输入，将使用默认图标。  如果任务正在生成本机清单，将忽略此参数。|  
|`InputManifest`|可选 <xref:Microsoft.Build.Framework.ITaskItem> 参数。<br /><br /> 指示要用作清单生成器的基础的输入 XML 文档。  这样，结构数据（如应用程序安全或自定义清单定义）就可以反映在输出清单中。  XML 文档中的根元素必须是 asmv1 命名空间中的程序集节点。|  
|`IsolatedComReferences`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 指定要在生成的清单中隔离的 COM 组件。  此参数支持隔离 COM 组件的功能，以实现“免注册 COM”部署。  它的工作方式是通过标准 COM 注册定义来自动生成清单。  但是，为保证正常工作，必须在生成计算机上注册这些 COM 组件。|  
|`ManifestType`|可选 `String` 参数。<br /><br /> 指定要生成哪种类型的清单。  此参数可以具有下列值：<br /><br /> -   `Native`<br />-   `ClickOnce`<br /><br /> 如果未指定此参数，则该任务默认为 `ClickOnce`。|  
|`MaxTargetPath`|可选 `String` 参数。<br /><br /> 指定 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序部署中文件路径的最大允许长度。  如果指定了此值，则会根据此限制检查应用程序中每个文件路径的长度。  超出该限制的任何项都会引发一个生成警告。  如果此输入未指定或者为零，那么将不执行检查。  如果任务正在生成本机清单，将忽略此参数。|  
|`OSVersion`|可选 `String` 参数。<br /><br /> 指定应用程序所需的最低操作系统 \(OS\) 版本。  例如，值“5.1.2600.0”表示操作系统为 Windows XP。  如果未指定此参数，将使用值“4.10.0.0”，这表示 Windows 98 Second Edition，即 .NET Framework 支持的最低操作系统版本。  如果任务正在生成本机清单，将忽略此输入。|  
|`OutputManifest`|可选 <xref:Microsoft.Build.Framework.ITaskItem> 输出参数。<br /><br /> 指定生成的输出清单文件的名称。  如果未指定此参数，将从生成的清单的标识中推断出该输出文件的名称。|  
|`Platform`|可选 `String` 参数。<br /><br /> 指定应用程序的目标平台。  此参数可以具有下列值：<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> 如果未指定此参数，则该任务默认为 `AnyCPU`。|  
|`Product`|可选 `String` 参数。<br /><br /> 指定应用程序的名称。  如果未指定此参数，将从生成的清单的标识中推断出该名称。  此名称用于“开始”菜单中的快捷名称，并且是“添加\/删除程序”对话框中显示的名称的一部分。|  
|`Publisher`|可选 `String` 参数。<br /><br /> 指定应用程序的发行者。  如果未指定此参数，将从注册用户或生成的清单的标识中推断出该名称。  此名称用于“开始”菜单中的文件夹名，并且是“添加\/删除程序”对话框中显示的名称的一部分。|  
|`RequiresMinimumFramework35SP1`|可选 `Boolean` 参数。<br /><br /> 如果为 true，则该应用程序要求 .NET Framework 3.5 SP1 或更新的版本。|  
|`TargetCulture`|可选 `String` 参数。<br /><br /> 标识应用程序的区域性，并为生成的清单指定程序集标识的 `Language` 字段。  如果未指定此参数，则假定该应用程序不依赖于区域性。|  
|`TargetFrameworkMoniker`|可选 assetId:///String?qualifyHint=False&autoUpgrade=True 参数。<br /><br /> 指定目标框架名字对象。|  
|`TargetFrameworkProfile`|可选 assetId:///String?qualifyHint=False&autoUpgrade=True 参数。<br /><br /> 指定目标框架配置文件。|  
|`TargetFrameworkSubset`|可选 assetId:///String?qualifyHint=False&autoUpgrade=True 参数。<br /><br /> 指定要面向的 .NET Framework 子集的名称。|  
|`TargetFrameworkVersion`|可选 assetId:///String?qualifyHint=False&autoUpgrade=True 参数。<br /><br /> 指定项目的目标 .NET Framework。|  
|`TrustInfoFile`|可选 <xref:Microsoft.Build.Framework.ITaskItem> 参数。<br /><br /> 指示用于指定应用程序安全性的 XML 文档。  XML 文档中的根元素必须是 asmv2 命名空间中的 trustInfo 节点。  如果任务正在生成本机清单，将忽略此参数。|  
|`UseApplicationTrust`|可选 assetId:///Boolean?qualifyHint=False&autoUpgrade=True 参数。<br /><br /> 如果为 true，则将 `Product`、`Publisher` 和 `SupportUrl` 属性写入应用程序清单中。|  
  
## 备注  
 除了上面列出的参数，此任务还将从 <xref:Microsoft.Build.Tasks.GenerateManifestBase> 类继承参数，此类本身从 <xref:Microsoft.Build.Utilities.Task> 类继承。  有关 Task 类的参数列表，请参见 [任务基类](../msbuild/task-base-class.md)类。  
  
 有关如何使用 `GenerateDeploymentManifest` 任务的信息，请参见 [GenerateApplicationManifest Task](../msbuild/generateapplicationmanifest-task.md)。  
  
 可以使用项元数据对依赖项和文件的输入进行进一步的修饰，以便为每个项指定更多部署状态。  
  
## 项的元数据  
  
|元数据名称|描述|  
|-----------|--------|  
|`DependencyType`|指示依赖项是随应用程序一起发布并安装还是一个必备组件。  此元数据对所有依赖项均有效，但不可用于文件。  可用于此元数据的值有：<br /><br /> -   `Install`<br />-   `Prerequisite`<br /><br /> Install 是默认值。|  
|`AssemblyType`|指示依赖项是托管程序集还是本机程序集。  此元数据对所有依赖项均有效，但不可用于文件。  可用于此元数据的值有：<br /><br /> -   `Managed`<br />-   `Native`<br />-   `Unspecified`<br /><br /> `Unspecified` 是默认值，指示清单生成器将自动确定程序集类型。|  
|`Group`|指示用于按需下载其他文件的组。  组名由应用程序定义，可以是任何字符串。  默认值是空字符串，这表示该文件不是下载组的一部分。  不在组中的文件是初始应用程序下载的一部分。  组中包含的文件只有当应用程序使用 <xref:System.Deployment.Application> 显式请求时才下载。<br /><br /> 此元数据对于 `IsDataFile` 为 `false` 的所有文件以及 `DependencyType` 为 `Install` 的所有依赖项均有效。|  
|`TargetPath`|指定应如何在生成的清单中定义该路径。  此特性对所有文件均有效。  如果未指定此特性，将使用项规范。  此特性对于所有文件以及 `DependencyType` 值为 `Install` 的依赖项均有效。|  
|`IsDataFile`|指示文件是否为数据文件的 `Boolean` 元数据值。  数据文件的特殊性在于它可以在应用程序更新之间迁移。  此元数据仅对文件有效。  `False` 为默认值。|  
  
## 示例  
 此示例针对具有单个程序集的应用程序，使用 `GenerateApplicationManifest` 任务生成 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序清单，并使用`GenerateDeploymentManifest` 任务生成部署清单。  然后，使用 `SignFile` 任务对这些清单进行签名。  
  
 这阐释了可能的最为简单的清单生成方案，在此方案中，将为单个程序生成 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 清单。  从清单的程序集可以推断出默认的名称和标识。  
  
> [!NOTE]
>  在下面的示例中，为将重点放在清单生成方面上，预先生成了所有的应用程序二进制文件。  此示例将产生一个可完全正常工作的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署。  
  
> [!NOTE]
>  有关在此示例的 `SignFile` 任务中使用的 `Thumbprint` 属性的更多信息，请参见 [SignFile 任务](../msbuild/signfile-task.md)。  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            EntryPoint="@(EntryPoint)">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
            EntryPoint="@(ApplicationManifest)">  
            <Output  
                ItemName="DeployManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## 示例  
 此示例针对具有单个程序集的应用程序，分别使用 `GenerateApplicationManifest` 和 `GenerateDeploymentManifest` 任务生成 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序清单和部署清单，并指定了清单的名称和标识。  
  
 此示例除了显式指定清单的名称和标识之外，其他方面均与上一个示例类似。  此外，此示例还被配置为联机应用程序，而不是安装的应用程序。  
  
> [!NOTE]
>  在下面的示例中，为将重点放在清单生成方面上，预先生成了所有的应用程序二进制文件。  此示例将产生一个可完全正常工作的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署。  
  
> [!NOTE]
>  有关在此示例的 `SignFile` 任务中使用的 `Thumbprint` 属性的更多信息，请参见 [SignFile 任务](../msbuild/signfile-task.md)。  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            AssemblyName="SimpleWinApp.exe"  
            AssemblyVersion="1.0.0.0"  
            EntryPoint="@(EntryPoint)"  
            OutputManifest="SimpleWinApp.exe.manifest">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
                AssemblyName="SimpleWinApp.application"  
                AssemblyVersion="1.0.0.0"  
                EntryPoint="@(ApplicationManifest)"  
                Install="false"  
                OutputManifest="SimpleWinApp.application">  
                <Output  
                    ItemName="DeployManifest"  
                    TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## 示例  
 此示例针对具有多个文件和程序集的应用程序，分别使用 `GenerateApplicationManifest` 和 `GenerateDeploymentManifest` 任务生成 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序清单和部署清单。  
  
> [!NOTE]
>  在下面的示例中，为将重点放在清单生成方面上，预先生成了所有的应用程序二进制文件。  此示例将产生一个可完全正常工作的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署。  
  
> [!NOTE]
>  有关在此示例的 `SignFile` 任务中使用的 `Thumbprint` 属性的更多信息，请参见 [SignFile 任务](../msbuild/signfile-task.md)。  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
        <DeployUrl>  
            <!-- Insert the deployment URL here -->  
        </DeployUrl>  
        <SupportUrl>  
            <!-- Insert the support URL here -->  
        </SupportUrl>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe"/>  
        <Dependency Include="ClassLibrary1.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
        </Dependency>  
        <Dependency Include="ClassLibrary2.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
            <Group>Secondary</Group>  
        </Dependency>  
        <Dependency Include="MyAddIn1.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
            <TargetPath>Addins\MyAddIn1.dll</TargetPath>  
        </Dependency>  
        <Dependency Include="ClassLibrary3.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Prerequisite</DependencyType>  
        </Dependency>  
  
        <File Include="Text1.txt">  
            <TargetPath>Text\Text1.txt</TargetPath>  
            <Group>Text</Group>  
        </File>  
        <File Include="DataFile1.xml ">  
            <TargetPath>Data\DataFile1.xml</TargetPath>  
            <IsDataFile>true</IsDataFile>  
        </File>  
  
        <IconFile Include="Heart.ico"/>  
        <ConfigFile Include="app.config">  
            <TargetPath>SimpleWinApp.exe.config</TargetPath>  
        </ConfigFile>  
        <BaseManifest Include="app.manifest"/>  
    </ItemGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            AssemblyName="SimpleWinApp.exe"  
            AssemblyVersion="1.0.0.0"  
            ConfigFile="@(ConfigFile)"  
            Dependencies="@(Dependency)"  
            Description="TestApp"  
            EntryPoint="@(EntryPoint)"  
            Files="@(File)"  
            IconFile="@(IconFile)"  
            InputManifest="@(BaseManifest)"  
            OutputManifest="SimpleWinApp.exe.manifest">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
            AssemblyName="SimpleWinApp.application"  
            AssemblyVersion="1.0.0.0"  
            DeploymentUrl="$(DeployToUrl)"  
            Description="TestDeploy"  
            EntryPoint="@(ApplicationManifest)"  
            Install="true"  
            OutputManifest="SimpleWinApp.application"  
            Product="SimpleWinApp"  
            Publisher="Microsoft"  
            SupportUrl="$(SupportUrl)"  
            UpdateEnabled="true"  
            UpdateInterval="3"  
            UpdateMode="Background"  
            UpdateUnit="weeks">  
            <Output  
                ItemName="DeployManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## 示例  
 此示例使用 `GenerateApplicationManifest` 任务为应用程序 Test.exe 生成本机清单，并引用本机组件 Alpha.dll 和独立的 COM 组件 Bravo.dll。  
  
 此示例产生 Test.exe.manifest，从而使得该应用程序可以借助“免注册 COM”进行 XCOPY 部署。  
  
> [!NOTE]
>  在下面的示例中，为将重点放在清单生成方面上，预先生成了所有的应用程序二进制文件。  此示例将产生一个可完全正常工作的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署。  
  
```  
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <File Include="Test.exe" />  
        <Dependency Include="Alpha.dll">  
            <AssemblyType>Native</AssemblyType>  
            <DependencyType>Install</DependencyType>  
        </Dependency>  
        <ComComponent Include="Bravo.dll" />  
    </ItemGroup>  
  
    <Target Name="Build">  
        <GenerateApplicationManifest  
            AssemblyName="Test.exe"  
            AssemblyVersion="1.0.0.0"  
            Dependencies="@(Dependency)"  
            Files="@(File)"  
            IsolatedComReferences="@(ComComponent)"  
            ManifestType="Native">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
    </Target>  
</Project>  
```  
  
## 请参阅  
 [任务](../msbuild/msbuild-tasks.md)   
 [GenerateDeploymentManifest 任务](../msbuild/generatedeploymentmanifest-task.md)   
 [SignFile 任务](../msbuild/signfile-task.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)