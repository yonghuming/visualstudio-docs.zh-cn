---
title: "创建一个软件开发工具包 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
caps.latest.revision: 54
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 1d5ea891137bff643ebfcb67cd739aefeb74c2df
ms.lasthandoff: 02/22/2017

---
# <a name="creating-a-software-development-kit"></a>创建一个软件开发工具包
软件开发工具包 (SDK) 是 Api，您可以将作为 Visual Studio 中的单个项引用的集合。 **引用管理器**对话框将列出与项目相关的所有 Sdk。 当向项目中添加 SDK 的 Api 是 Visual Studio 中提供。  
  
 有两种类型的 Sdk:  
  
-   平台 Sdk 是开发平台的应用程序的必需组件。 例如，[!INCLUDE[win81](../debugger/includes/win81_md.md)]开发所需的 SDK[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]应用程序。  
  
-   扩展 Sdk 是扩展一个平台，但不是必需的开发平台的应用程序的可选组件。  
  
 下列各节描述 Sdk 以及如何创建 platform SDK 的常规基础结构和扩展 SDK。  
  
-   [平台 Sdk](#PlatformSDKs)  
  
-   [扩展 Sdk](#ExtensionSDKs)  
  
##  <a name="a-nameplatformsdksa-platform-sdks"></a><a name="PlatformSDKs"></a>平台 Sdk  
 开发平台的应用程序所需平台 Sdk。 例如，[!INCLUDE[win81](../debugger/includes/win81_md.md)]开发适用于应用程序所需的 SDK [!INCLUDE[win81](../debugger/includes/win81_md.md)]。  
  
### <a name="installation"></a>安装  
 所有平台 Sdk 将在 HKLM\Software\Microsoft\Microsoft Sdk 都安装\\[TPI] \v [TPV]\\ @InstallationFolder = [SDK root]。 相应地，[!INCLUDE[win81](../debugger/includes/win81_md.md)]在 HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1 安装 SDK。  
  
### <a name="layout"></a>布局  
 平台 Sdk 将具有如下布局︰  
  
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
|引用文件夹|包含二进制文件包含可对编码的 Api。 这些可能包括 Windows 元数据 (WinMD) 文件或程序集。|  
|DesignTime 文件夹|包含仅在预运行/调试时需要的文件。 这些可能包括 XML 文档、 库、 标头，工具箱的设计时二进制文件、 MSBuild 项目等<br /><br /> XML 文档，理想情况下，被放在 \DesignTime 文件夹中，但引用的 XML 文档将继续与 Visual Studio 中的引用文件一起放置。 例如，XML 文档中的引用 \References\\[配置]\\[arch]\sample.dll 将 \References\\[配置]\\[arch]\sample.xml，并且该文档的本地化的版本将 \References\\[配置]\\[arch]\\[locale]\sample.xml。|  
|配置文件夹|可以有只有三个文件夹︰ 调试、 零售和 CommonConfiguration。 如果应使用同一组 SDK 文件，而不考虑 SDK 使用者将目标配置，SDK 作者可放置在 CommonConfiguration 下的其文件。|  
|体系结构文件夹|可以存在的任何支持的体系结构文件夹。 Visual Studio 支持以下体系结构︰ x86、 x64、 ARM 和非特定语言。 注意︰ Win32 将映射到 x86，而 anycpu 映射到非特定语言。<br /><br /> MSBuild 仅在 \CommonConfiguration\neutral 下寻找平台 Sdk。|  
|SDKManifest.xml|该文件介绍了 Visual Studio 应如何使用 SDK。 看一看 SDK 清单[!INCLUDE[win81](../debugger/includes/win81_md.md)]:<br /><br /> `<FileList             DisplayName = “Windows”             PlatformIdentity = “Windows, version=8.1”             TargetFramework = “.NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1”             MinVSVersion = “14.0”>              <File Reference = “Windows.winmd”>                <ToolboxItems VSCategory = “Toolbox.Default” />             </File> </FileList>`<br /><br /> **DisplayName:**对象浏览器显示在浏览列表中的值。<br /><br /> **PlatformIdentity:**存在此特性告知 Visual Studio 和 MSBuild SDK 是一个平台 SDK 和添加从它的引用不应将复制本地。<br /><br /> **TargetFramework:** Visual Studio 使用此属性以确保，只有项目中的同一个框架中此值指定属性可以使用 SDK。<br /><br /> **MinVSVersion:** Visual Studio 使用此属性来使用仅应用于它的 Sdk。<br /><br /> **参考︰**此属性必须指定包含控件的这些引用。 有关如何指定一个引用是否包含控件的信息，请参阅下面。|  
  
##  <a name="a-nameextensionsdksa-extension-sdks"></a><a name="ExtensionSDKs"></a>扩展 Sdk  
 以下各节描述了您需要执行的操作部署扩展 SDK。  
  
### <a name="installation"></a>安装  
 扩展 Sdk 可以而无需指定注册表项为特定用户还是为所有用户安装。 若要安装的所有用户的 SDK，请使用以下路径︰  
  
 `%Program Files%\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 对于特定于用户的安装，使用以下路径︰  
  
 `%USERPROFILE%\AppData\Local\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 如果您想要使用的其他位置，必须执行两个操作之一︰  
  
1.  注册表项中指定它︰  
  
     `HKLM\Software\Microsoft\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs\<SDKName>\<SDKVersion>\`  
  
     并将其值为一个 （默认值） 子项添加`<path to SDK><SDKName><SDKVersion>`。  
  
2.  将添加 MSBuild 属性`SDKReferenceDirectoryRoot`到你的项目文件。 此属性的值是您想要引用扩展 Sdk 驻留在其中的目录的半部分号分隔列表。  
  
### <a name="installation-layout"></a>安装布局  
 扩展 Sdk 包含以下安装布局︰  
  
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
  
1.  \\<>\>\\<>\>︰ 名称和版本的 SDK 源自于 SDK 根路径中对应的文件夹名称的扩展。 MSBuild 将使用此标识来在磁盘上，在此找到 SDK 和 Visual Studio 将显示在此标识**属性**窗口和**引用管理器**对话框。  
  
2.  引用文件夹︰ 包含了 Api 的二进制文件。 它们可能是 Windows 元数据 (WinMD) 文件或程序集。  
  
3.  Redist 文件夹︰ 所需的运行时/调试且应作为用户的应用程序的一部分获取已打包的文件。 所有二进制文件应放置在 \redist 下\\<>\>\\<>\>，并且二进制名称应采用以下格式来确保唯一性︰ **\<公司&1;>。\<产品&1;>。\<目的&1;>。\<extension>**. 例如，Microsoft.Cpp.Build.dll。 使用其他 sdk （例如，javascript、 css、 pri、 xaml、 png 和 jpg 文件） 的文件名称可能发生冲突的名称的所有文件应都放置在 \redist 下\\<>\>\\<>\>\\<>\>\ XAML 与相关联的文件除外控制。 这些文件应放置在 \redist 下\\<>\>\\<>\>\\<>\>\\。  
  
4.  DesignTime 文件夹︰ 在只有前-运行/调试需要的文件时间，并不应将其打包为用户的应用程序的一部分。 它们可能是 XML 文档、 库、 标头，工具箱的设计时二进制文件、 MSBuild 项目等。 适用于在使用本机项目必须有任何 SDK *SDKName*.props 文件。 下面显示此类型的文件的示例。  
  
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
  
     与引用文件位于 XML 参考文档。 例如，XML 参考文档为**\References\\<>\>\\<>\>\sample.dll**程序集是**\References\\<>\>\\<>\>\sample.xml**，并且该文档的本地化的版本是**\References\\<>\>\\<>\>\\<>\>\sample.xml**。  
  
5.  配置文件夹︰ 三个子文件夹︰ 调试、 零售版和 CommonConfiguration。 SDK 作者可放置其文件在 CommonConfiguration 下的，应使用同一组 SDK 文件，而不考虑目标由 SDK 使用者配置。  
  
6.  体系结构文件夹︰ 支持以下体系结构︰ x86、 x64、 ARM、 非特定语言。 Win32 映射到 x86，而 anycpu 映射到非特定语言。  
  
### <a name="sdkmanifestxml"></a>SDKManifest.xml  
 该文件介绍了 Visual Studio 应如何使用 SDK。 下面是一个示例。  
  
```  
<FileList>  
DisplayName = “My SDK”  
ProductFamilyName = “My SDKs”  
TargetFramework = “.NETCore, version=v4.5.1; .NETFramework, version=v4.5.1”  
MinVSVersion = “14.0”  
MaxPlatformVersion = "8.1"  
AppliesTo = "WindowsAppContainer + WindowsXAML"  
SupportPrefer32Bit = “True”  
SupportedArchitectures = “x86;x64;ARM”  
SupportsMultipleVersions = “Error”  
CopyRedistToSubDirectory = “.”  
DependsOn = “SDKB, version=2.0”  
MoreInfo = “http://msdn.microsoft.com/MySDK”>  
<File Reference = “MySDK.Sprint.winmd” Implementation = “XNASprintImpl.dll”>  
<Registration Type = “Flipper” Implementation = “XNASprintFlipperImpl.dll” />  
<Registration Type = “Flexer” Implementation = “XNASprintFlexerImpl.dll” />  
<ToolboxItems VSCategory = “Toolbox.Default” />  
</File>  
</FileList>  
```  
  
 以下列表提供了该文件的元素。  
  
1.  DisplayName︰ 在引用管理器、 解决方案资源管理器、 对象浏览器和 Visual Studio 用户界面中的其他位置中显示的值。  
  
2.  ProductFamilyName︰ 总体 SDK 产品名称。 例如， [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] SDK 名为"Microsoft.WinJS.1.0"和"Microsoft.WinJS.2.0"属于相同的系列 SDK 产品系列的成员，"Microsoft.WinJS"。 此特性使 Visual Studio 和 MSBuild，以使该连接。 如果此属性不存在，则 SDK 名称用作产品家族名称。  
  
3.  FrameworkIdentity︰ 指定一个或多个 Windows 组件库的此属性的值放入使用应用程序的清单上的依赖项。 此属性是仅适用于 Windows 组件库。  
  
4.  TargetFramework︰ 指定引用管理器和工具箱中可用的 Sdk。 这是以分号分隔列表的目标框架名字对象，例如".NET Framework，version = v2.0;.NET Framework，version = v4.5.1"。 如果指定了多个相同的目标框架版本，引用管理器供筛选之使用指定的最低版本。 例如，如果".NET Framework，version = v2.0;.NET Framework，version = v4.5.1"指定，则将使用引用管理器".NET Framework，version = v2.0"。 如果指定特定的目标框架配置文件，则只有该配置文件将供筛选之使用引用管理器。 例如，当"Silverlight 中，版本 = v4.0，profile = WindowsPhone"指定，则引用管理器的筛选器仅 Windows Phone 配置文件;面向完整的 Silverlight 4.0 框架的项目看不见 SDK 在引用管理器。  
  
5.  MinVSVersion︰ 最小 Visual Studio 的版本。  
  
6.  MaxPlatformVerson︰ 最大目标平台版本应该用于指定在其扩展 SDK 不起作用的平台版本。 例如，Microsoft Visual c + + 运行时软件包 v11.0 应被 Windows 8 项目引用。 因此，Windows 8 项目 MaxPlatformVersion 是 8.0。 也就是说，引用管理器筛选出 Microsoft Visual c + + 运行时包对于 Windows 8.1 项目，并且 MSBuild 将引发错误时[!INCLUDE[win81](../debugger/includes/win81_md.md)]项目引用它。 注意︰ 此元素支持从[!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]。  
  
7.  AppliesTo︰ 指定均可在引用管理器中通过指定适用的 Visual Studio 项目类型的 Sdk。 识别&9; 个值︰ WindowsAppContainer、 VisualC、 VB、 CSharp、 WindowsXAML、 JavaScript、 托管和本机。 可以使用 SDK 作者和 ("+)，或 ("|")，而不 ("！")若要指定确切的作用域应用于 SDK 的项目类型的运算符。  
  
     WindowsAppContainer 标识项目类型提供的[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]应用程序。  
  
8.  SupportPrefer32Bit︰ 支持的值为"True"和"False"。 默认值为"True"。 如果值设置为"False"，MSBuild 将返回错误的[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]项目 （或对于桌面项目的警告） 引用 SDK 的项目是否已启用的 Prefer32Bit。 有关 Prefer32Bit 详细信息，请参阅[生成页，项目设计器 (C#)](../ide/reference/build-page-project-designer-csharp.md)或[编译页，项目设计器 (Visual Basic 中)](../ide/reference/compile-page-project-designer-visual-basic.md)。  
  
9. SupportedArchitectures︰ 以分号分隔的 SDK 支持的体系结构的列表。 如果在使用的项目的目标的 SDK 体系结构不受支持，MSBuild 将显示一个警告。 如果未指定此特性，MSBuild 将永远不会显示此类型的警告。  
  
10. SupportsMultipleVersions︰ 如果此属性设置为**错误**或**警告**，MSBuild 指示相同的项目不能引用相同的 SDK 系列的多个版本。 如果此属性不存在，或者设置为**允许**，MSBuild 不会显示这种类型的错误或警告。  
  
11. AppX︰ 指定在磁盘上的 Windows 组件库的应用程序包的路径。 本地调试过程中此值传递给 Windows 组件库的注册组件。 文件名称的命名约定是**\<公司&1;>。\<产品&1;>。\<体系结构&1;>。\<配置&1;>。\<版本&1;>.appx**。 配置和体系结构会参数是可选的属性名称和属性值，如果它们没有适用于 Windows 组件库。 此值是仅适用于 Windows 组件库。  
  
12. CopyRedistToSubDirectory︰ 指定相对于应用程序的包根目录 \redist 文件夹下的文件应复制到其中 (即，**包位置**在创建应用程序包向导中选择) 和运行时布局的根元素。 默认位置为应用程序包和 F5 布局的根。  
  
13. DependsOn︰ 定义此 SDK 所依赖的 Sdk 的 SDK 标识的列表。 此属性将显示在详细信息窗格中的引用管理器。  
  
14. MoreInfo︰ 指向提供了帮助和更多信息的网页的 URL。 在右窗格中的引用管理器的详细信息链接中使用此值。  
  
15. 注册类型︰ 应用程序清单中指定的 WinMD 注册，并且所必需的本机 WinMD，有一个对应的实现 DLL。  
  
16. 文件参考资料︰ 指定包含控件或本机 Winmd 的引用。 有关如何指定一个引用是否包含控件的信息，请参阅[指定位置工具箱项](#ToolboxItems)下面。  
  
##  <a name="a-nametoolboxitemsa-specifying-the-location-of-toolbox-items"></a><a name="ToolboxItems"></a>指定的工具箱项的位置  
 SDKManifest.xml 架构的 ToolBoxItems 元素指定的平台和扩展 Sdk 中的类别和工具箱项的位置。 下面的示例演示如何指定不同的位置。 这是适用于 WinMD 或 DLL 的引用。  
  
1.  将控件放在工具箱的默认类别。  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Toolbox.Default”/>       
    </File>  
    ```  
  
2.  放置在特定类别名称的下方的控件。  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory= “MyCategoryName”/>  
    </File>  
    ```  
  
3.  放置在特定类别名称下的控件。  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Graph”>  
        <ToolboxItems/>  
        <ToolboxItems VSCategory = “Data”>  
        <ToolboxItems />  
    </File>  
    ```  
  
4.  在 Blend 和 Visual Studio 中放置在不同的类别名称下的控件。  
  
    ```  
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Graph” BlendCategory = “Controls/sample/Graph”>   
        <ToolboxItems />  
    </File>  
    ```  
  
5.  枚举以不同的方式在 Blend 和 Visual Studio 中的特定控件。  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Graph”>  
        <ToolboxItems/>  
        <ToolboxItems BlendCategory = “Controls/sample/Graph”>  
        <ToolboxItems/>  
    </File>  
    ```  
  
6.  枚举具体的控件，并将其放置在 Visual Studio 常见路径下或仅在所有的控件组。  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Toolbox.Common”>  
        <ToolboxItems />  
        <ToolboxItems VSCategory = “Toolbox.All”>  
        <ToolboxItems />  
    </File>  
    ```  
  
7.  枚举具体的控件，并没有它们在 ChooseItems 中显示指定的一组要在工具箱中。  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Toolbox.ChooseItemsOnly”>  
        <ToolboxItems />  
    </File>  
    ```  
  
## <a name="see-also"></a>另请参阅  
 [演练︰ 创建使用 c + + 的 SDK](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [演练︰ 创建使用 C# 或 Visual Basic 的 SDK](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [管理项目中的引用](../ide/managing-references-in-a-project.md)
