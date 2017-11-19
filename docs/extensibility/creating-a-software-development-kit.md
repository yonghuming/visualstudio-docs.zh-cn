---
title: "创建软件开发工具包 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
caps.latest.revision: "54"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6a301085cd00e20d5c4e931ac144e454718ad152
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="creating-a-software-development-kit"></a>创建软件开发工具包
软件开发工具包 (SDK) 是 api，你可以将 Visual Studio 中的单个项目作为引用集合。 **引用管理器**对话框将列出与项目相关的所有 Sdk。 当你添加到项目的 SDK 时，都提供 Visual Studio 中的 Api。  
  
 有两种类型的 Sdk:  
  
-   平台 Sdk 是开发平台的应用程序的必需组件。 例如，[!INCLUDE[win81](../debugger/includes/win81_md.md)]开发所需的 SDK[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]应用。  
  
-   扩展 Sdk 是扩展一个平台，但不强制开发该平台的应用程序的可选组件。  
  
 下列各节描述了 Sdk 以及如何创建平台 SDK 的常规基础结构和扩展 SDK。  
  
-   [平台 Sdk](#PlatformSDKs)  
  
-   [扩展 Sdk](#ExtensionSDKs)  
  
##  <a name="PlatformSDKs"></a>平台 Sdk  
 开发适用于平台的应用所需平台 Sdk。 例如，[!INCLUDE[win81](../debugger/includes/win81_md.md)]开发应用程序所需的 SDK [!INCLUDE[win81](../debugger/includes/win81_md.md)]。  
  
### <a name="installation"></a>安装  
 所有平台 Sdk 将都安装在 HKLM\Software\Microsoft\Microsoft Sdk\\[TPI] \v [TPV]\\ @InstallationFolder = [SDK 根]。 相应地，[!INCLUDE[win81](../debugger/includes/win81_md.md)]在 HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1 安装 SDK。  
  
### <a name="layout"></a>布局  
 平台 Sdk 将具有以下布局：  
  
```  
\[InstallationFolder root]  
            SDKManifest.xml  
            \References  
                  \[config]  
                        \[arch]  
            \DesignTime  
                  \[config]  
                        \[arch]  
```  
  
|节点|描述|  
|----------|-----------------|  
|引用文件夹|包含包含 Api 可以对编码的二进制文件。 这些可能包括 Windows 元数据 (WinMD) 文件或程序集。|  
|DesignTime 文件夹|包含仅在调试前运行/时间需要的文件。 这些文档可能为 XML 文档、 库、 标头、 工具箱设计时二进制文件、 MSBuild 项目和等<br /><br /> XML 文档，理想情况下，被放在 \DesignTime 文件夹中，但引用的 XML 文档将继续与 Visual Studio 中的参考文件一起放置。 例如，XML 文档中的引用 \References\\[config]\\[arch]\sample.dll 将 \References\\[config]\\[arch]\sample.xml 和该文档的本地化的版本将 \References\\[config]\\[体系结构]\\[locale]\sample.xml。|  
|配置文件夹|可以有只有三个文件夹： 调试、 零售和 CommonConfiguration。 如果应使用相同的 SDK 文件集，而不考虑 SDK 使用者将目标配置，SDK 作者可放置在 CommonConfiguration 其文件。|  
|体系结构文件夹|可以存在的任何支持的体系结构文件夹。 Visual Studio 支持以下体系结构： x86、 x64、 ARM、 和特定。 注意： Win32 将映射为 x86，而 AnyCPU 映射到非特定语言。<br /><br /> 仅在 \CommonConfiguration\neutral MSBuild 查找平台 Sdk。|  
|SDKManifest.xml|此文件描述 Visual Studio 应如何使用 SDK。 看一看 SDK 清单[!INCLUDE[win81](../debugger/includes/win81_md.md)]:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **DisplayName:**对象浏览器将显示浏览列表中的值。<br /><br /> **PlatformIdentity:**此属性是否存在告知 Visual Studio 和 MSBuild SDK 是一个平台 SDK 和添加从它的引用，不应复制本地。<br /><br /> **TargetFramework:** Visual Studio 使用此属性以确保仅集来投射该目标中的值指定相同的框架特性可以使用 SDK。<br /><br /> **MinVSVersion:** Visual Studio 使用此属性使用仅应用于它的 Sdk。<br /><br /> **参考：**此属性必须指定用于包含控件的这些引用。 有关如何指定引用是否包含控件的信息，请参阅下面。|  
  
##  <a name="ExtensionSDKs"></a>扩展 Sdk  
 以下各节描述了你需要为部署的扩展 SDK 执行的操作。  
  
### <a name="installation"></a>安装  
 扩展 Sdk 可以不指定注册表项的情况下为特定用户还是为所有用户安装。 若要安装适用于所有用户的 SDK，请使用以下路径：  
  
 `%Program Files%\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 对于特定于用户的安装，使用以下路径：  
  
 `%USERPROFILE%\AppData\Local\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 如果你想要使用的不同位置，你必须执行两项操作之一：  
  
1.  在注册表项中指定它：  
  
     `HKLM\Software\Microsoft\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs\<SDKName>\<SDKVersion>\`  
  
     并添加的值为一个 （默认值） 子项`<path to SDK><SDKName><SDKVersion>`。  
  
2.  将添加 MSBuild 属性`SDKReferenceDirectoryRoot`到你的项目文件。 此属性的值是 semi 分号分隔的一系列你想要引用扩展 Sdk 驻留在其中的目录。  
  
### <a name="installation-layout"></a>安装布局  
 扩展 Sdk 具有以下安装布局：  
  
```  
\<ExtensionSDKs root>  
           \<SDKName>  
                 \<SDKVersion>  
                        SDKManifest.xml  
                        \References  
                              \<config>  
                                    \<arch>  
                        \Redist  
                              \<config>  
                                    \<arch>  
                        \DesignTime  
                               \<config>  
                                     \<arch>  
  
```  
  
1.  \\< SDKName\>\\< SDKVersion\>： 的名称和版本的 SDK 源自到 SDK 根路径中的相应文件夹名称的扩展。 MSBuild 使用此标识来在磁盘上，查找 SDK 和 Visual Studio 将显示在此标识**属性**窗口和**引用管理器**对话框。  
  
2.  引用文件夹： 包含 Api 的二进制文件。 这些可以是 Windows 元数据 (WinMD) 文件或程序集。  
  
3.  Redist 文件夹： 所需的运行时/调试和应获取打包为用户的应用程序的一部分的文件。 所有二进制文件应放置在 \redist 下\\< 配置\>\\< 体系结构\>，二进制名称应具有以下格式来确保唯一性： **\<公司 >。\<产品 >。\<目的 >。\<扩展 >**。 例如，Microsoft.Cpp.Build.dll。 与从其他 Sdk （例如，javascript、 css、 pri、 xaml、 png、 和 jpg 文件） 的文件名可能发生冲突的名称的所有文件应都放置在 \redist 下\\< 配置\>\\< 体系结构\>\\< sdkname\>\ 与 XAML 相关联的文件除外控制。 这些文件应放置在 \redist 下\\< 配置\>\\< 体系结构\>\\< componentname\>\\。  
  
4.  DesignTime 文件夹： 在只有前-运行/调试需要的文件时间和不应将其打包为用户的应用程序的一部分。 这些可以是 XML 文档、 库、 标头、 工具箱设计时二进制文件、 MSBuild 项目和等。 适用于在使用本机项目必须具有任何 SDK *SDKName*.props 文件。 下面显示的此类型的文件的示例。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <ExecutablePath>C:\Temp\ExecutablePath;$(ExecutablePath)</ExecutablePath>  
        <IncludePath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\CommonConfiguration\Neutral\include;$(IncludePath)</IncludePath>  
        <AssemblyReferencePath>C:\Temp\AssemblyReferencePath;(AssemblyReferencePath)</AssemblyReferencePath>  
        <LibraryPath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\Debug\ARM;$(LibraryPath)</LibraryPath>  
        <SourcePath>C:\Temp\SourcePath\X64;$(SourcePath)</SourcePath>  
        <ExcludePath>C:\Temp\ExcludePath\X64;$(ExcludePath)</ExcludePath>  
        <_PropertySheetDisplayName>DevILSDK, 1.0</_PropertySheetDisplayName>  
      </PropertyGroup>  
    </Project>  
  
    ```  
  
     XML 参考文档位于一起的参考文件。 例如，引用针对 XML 文档**\References\\< 配置\>\\< 体系结构\>\sample.dll**程序集是**\References\\< 配置\>\\< 体系结构\>\sample.xml**，该文档的本地化的版本为**\References\\< 配置\>\\<体系结构\>\\< 区域设置\>\sample.xml**。  
  
5.  配置文件夹： 三个子文件夹： 调试、 零售版和 CommonConfiguration。 SDK 作者可放置在 CommonConfiguration 其文件，应使用相同的 SDK 文件集，而不考虑针对 SDK 使用者的配置。  
  
6.  体系结构文件夹： 支持以下体系结构： x86、 x64、 ARM、 非特定语言。 Win32 映射为 x86，而 AnyCPU 映射到非特定语言。  
  
### <a name="sdkmanifestxml"></a>SDKManifest.xml  
 此文件描述 Visual Studio 应如何使用 SDK。 下面是一个示例。  
  
```  
<FileList>  
DisplayName = "My SDK"  
ProductFamilyName = "My SDKs"  
TargetFramework = ".NETCore, version=v4.5.1; .NETFramework, version=v4.5.1"  
MinVSVersion = "14.0"  
MaxPlatformVersion = "8.1"  
AppliesTo = "WindowsAppContainer + WindowsXAML"  
SupportPrefer32Bit = "True"  
SupportedArchitectures = "x86;x64;ARM"  
SupportsMultipleVersions = "Error"  
CopyRedistToSubDirectory = "."  
DependsOn = "SDKB, version=2.0"  
MoreInfo = "http://msdn.microsoft.com/MySDK">  
<File Reference = "MySDK.Sprint.winmd" Implementation = "XNASprintImpl.dll">  
<Registration Type = "Flipper" Implementation = "XNASprintFlipperImpl.dll" />  
<Registration Type = "Flexer" Implementation = "XNASprintFlexerImpl.dll" />  
<ToolboxItems VSCategory = "Toolbox.Default" />  
</File>  
</FileList>  
```  
  
 以下列表提供了文件的元素。  
  
1.  DisplayName： 在引用管理器、 解决方案资源管理器、 对象浏览器和 Visual Studio 用户界面中的其他位置中显示的值。  
  
2.  ProductFamilyName： 总体 SDK 产品名称。 例如， [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] SDK 名为"Microsoft.WinJS.1.0"和"Microsoft.WinJS.2.0"属于相同的一系列 SDK 产品系列，"Microsoft.WinJS"。 此属性允许 Visual Studio 和 MSBuild 建立该连接。 如果此属性不存在，则 SDK 名称用作产品系列名称。  
  
3.  FrameworkIdentity： 在一个或多个 Windows 组件库的此属性的值放入使用方应用程序的清单上指定的依赖项。 此属性是仅适用于 Windows 组件库。  
  
4.  TargetFramework： 指定可用于引用管理器和工具箱的 Sdk。 这是以分号分隔列表的目标框架名字对象，例如".NET Framework，version = v2.0;.NET Framework，version = v4.5.1"。 如果指定了多个相同的目标框架版本，引用管理器将使用供筛选之最低的指定的版本。 例如，如果".NET Framework，version = v2.0;.NET Framework，version = v4.5.1"指定，则将使用引用管理器".NET Framework，version = v2.0"。 如果指定特定的目标框架配置文件，则仅该配置文件将供筛选之使用引用管理器。 例如，当"Silverlight，版本 = v4.0，配置文件 = WindowsPhone"指定，则引用管理器仅 Windows Phone 配置文件; 上的筛选器面向完整 Silverlight 4.0 Framework 的项目未看到 SDK 在引用管理器。  
  
5.  MinVSVersion： 最小 Visual Studio 版本。  
  
6.  MaxPlatformVerson： 最大目标平台版本应该用于指定在其扩展 SDK 不起作用的平台版本。 例如，Microsoft Visual c + + 运行时包 v11.0 应被 Windows 8 项目引用。 因此，Windows 8 项目 MaxPlatformVersion 是 8.0。 这意味着，引用管理器筛选出 Microsoft Visual c + + 运行时包对于 Windows 8.1 项目，并 MSBuild 引发错误时[!INCLUDE[win81](../debugger/includes/win81_md.md)]项目引用它。 注意： 此元素是从开始受支持[!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]。  
  
7.  AppliesTo： 指定在引用管理器提供了通过指定适用的 Visual Studio 项目类型的 Sdk。 识别 9 个值： WindowsAppContainer、 visual c、 VB、 CSharp、 WindowsXAML、 JavaScript、 托管和本机。 可以使用 SDK 作者和 ("+)，或 ("&#124;")，不 ("！")指定完全适用于 SDK 的项目类型的作用域的运算符。  
  
     WindowsAppContainer 标识项目类型提供的[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]应用。  
  
8.  SupportPrefer32Bit： 支持的值为"True"和"False"。 默认值为"True"。 如果值设置为"False"，MSBuild 将返回有关错误[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]项目 （或对于桌面项目警告） 如果引用 SDK 项目具有 Prefer32Bit 启用。 有关 Prefer32Bit 的详细信息，请参阅[生成页上，项目设计器 (C#)](../ide/reference/build-page-project-designer-csharp.md)或[编译页，项目设计器 (Visual Basic 中)](../ide/reference/compile-page-project-designer-visual-basic.md)。  
  
9. SupportedArchitectures： 用分号分隔的 SDK 支持的体系结构的列表。 如果使用的项目中的目标的 SDK 体系结构不受支持，MSBuild 将显示警告。 如果未指定此属性，MSBuild 将永远不会显示此类型的警告。  
  
10. SupportsMultipleVersions： 如果此属性设置为**错误**或**警告**，MSBuild 指示相同的项目不能引用相同的 SDK 系列的多个版本。 如果此属性不存在，或者设置为**允许**，MSBuild 不会显示此类型的错误或警告。  
  
11. AppX： 指定磁盘上的 Windows 组件库的应用包的路径。 在本地调试期间，此值被传递给 Windows 组件库的注册组件。 文件名称的命名约定是**\<公司 >。\<产品 >。\<体系结构 >。\<配置 >。\<版本 >.appx**。 配置和体系结构会在属性名称和属性值中为可选，如果它们不会应用到 Windows 组件库。 此值是仅适用于 Windows 组件库。  
  
12. CopyRedistToSubDirectory： 指定相对于应用程序包根目录下 \redist 文件夹的文件应复制到其中 (即，**包位置**在创建应用程序包向导中选择) 和运行时布局的根元素。 默认位置为应用程序包和 F5 布局的根。  
  
13. DependsOn： 定义此 SDK 所依赖的 Sdk 的 SDK 标识的列表。 此属性将显示在详细信息窗格中的引用管理器。  
  
14. MoreInfo： 指向提供了帮助和更多信息的网页的 URL。 在右窗格中的引用管理器的详细信息链接中使用此值。  
  
15. 注册类型： 应用程序清单中指定 WinMD 注册，并需要本机 WinMD，有一个对应的实现 DLL。  
  
16. 文件引用： 指定包含控件或本机 Winmd 的引用。 有关如何指定引用是否包含控件的信息，请参阅[指定位置工具箱项](#ToolboxItems)下面。  
  
##  <a name="ToolboxItems"></a>指定的工具箱项的位置  
 SDKManifest.xml 架构的 ToolBoxItems 元素指定平台和扩展 Sdk 中的类别和工具箱项的位置。 下面的示例演示如何指定不同的位置。 这是适用于 WinMD 或 DLL 的引用。  
  
1.  将控件放在工具箱默认类别。  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Default"/>       
    </File>  
    ```  
  
2.  放置在一个特定的类别名称下的控件。  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory= "MyCategoryName"/>  
    </File>  
    ```  
  
3.  放置在特定的类别名称的控件。  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems VSCategory = "Data">  
        <ToolboxItems />  
    </File>  
    ```  
  
4.  在 Blend 和 Visual Studio 中放置不同的类别名称下的控件。  
  
    ```  
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">   
        <ToolboxItems />  
    </File>  
    ```  
  
5.  枚举特定控件 Blend 和 Visual Studio 中以不同方式。  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems BlendCategory = "Controls/sample/Graph">  
        <ToolboxItems/>  
    </File>  
    ```  
  
6.  枚举特定的控件，并将其放在 Visual Studio 通用路径下或仅在所有控件组。  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Common">  
        <ToolboxItems />  
        <ToolboxItems VSCategory = "Toolbox.All">  
        <ToolboxItems />  
    </File>  
    ```  
  
7.  枚举特定的控件，并在 ChooseItems 中显示指定的一组，如果没有它们是在工具箱。  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">  
        <ToolboxItems />  
    </File>  
    ```  
  
## <a name="see-also"></a>另请参阅  
 [演练： 创建使用 c + + 的 SDK](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [演练： 创建使用 C# 或 Visual Basic 的 SDK](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [管理项目中的引用](../ide/managing-references-in-a-project.md)