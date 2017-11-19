---
title: "VSIX 扩展架构 2.0 引用 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c1c81a34a290b34207f505d6b1ab46fa8b11cd8d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="vsix-extension-schema-20-reference"></a>VSIX 扩展架构 2.0 参考
VSIX 部署清单文件描述 VSIX 包的内容。 文件格式受架构。 此架构的 2.0 版支持的自定义类型和属性添加。  清单的架构是可扩展的。 清单加载程序将忽略 XML 元素和属性，它不理解。  
  
> [!IMPORTANT]
>  Visual Studio 2015 可以加载 Visual Studio 2010、 Visual Studio 2012 或 Visual Studio 2013 格式中的 VSIX 文件。  
  
## <a name="package-manifest-schema"></a>包清单架构  
 清单 XML 文件的根元素是`<PackageManifest>`，与单个属性`Version`，即清单格式的版本。 如果对格式进行了重大更改，将更改的版本格式。 本主题介绍清单格式版本 2.0 中，通过设置在清单中指定`Version`属性设为值 Version ="2.0"。  
  
### <a name="packagemanifest-element"></a>PackageManifest 元素  
 在`<PackageManifest>`根元素，你可以使用以下元素：  
  
-   `<Metadata>`元数据和有关包本身的广告信息。 只有一个`Metadata`元素允许在清单中。  
  
-   `<Installation>`-此节定义可以安装此扩展包，包括可安装到应用程序 Sku 的方式。 只有一个`Installation`元素允许在清单中。 必须具有一个清单`Installation`元素或此包不会安装到任何 SKU。  
  
-   `<Dependencies>`此处定义了此包的依赖项的可选列表。  
  
-   `<Assets>`-此部分包含的所有资产包含在此包。 本部分中，没有此包不会出现任何内容。  
  
-   `<AnyElement>*`-清单架构的灵活程度足以允许任何其他元素。 无法识别清单加载程序的任何子元素都作为额外 XmlElement 对象公开扩展管理器 API 中。 使用这些子元素，VSIX 扩展可在 Visual Studio 中运行的代码可以在运行时访问清单文件中定义其他数据。 请参见<xref:Microsoft.VisualStudio.ExtensionManager.IExtension.AdditionalElements%2A>和<xref:Microsoft.VisualStudio.ExtensionManager.IExtension.LocalizedAdditionalElements%2A>。  
  
### <a name="metadata-element"></a>元数据元素  
 本节是有关包、 其标识和播发信息的元数据。 `<Metadata>`包含下列元素：  
  
-   `<Identity>`-这定义为此包的标识信息，包括以下属性：  
  
    -   `Id`-此特性必须是由其作者选择的包的唯一 ID。 名称，应限定 CLR 类型的名称空间相同的方式： Company.Product.Feature.Name。 `Id`特性被限制为 100 个字符。  
  
    -   `Version`-这定义了此包和其内容的版本。 此属性应遵循 CLR 程序集版本控制格式： Major.Minor.Build.Revision (1.2.40308.00)。 具有更高版本的版本号的包被视为更新到包中，并且可以安装在现有的已安装版本上。  
  
    -   `Language`-此属性是包的默认语言，并且对应于此清单中的文本数据。 此属性遵循 CLR 区域设置代码约定对于资源程序集，例如： en-我们、 en、 fr fr。 你可以指定`neutral`声明将在 Visual Studio 的任何版本运行的非特定于语言的扩展。 默认值为 `neutral`。  
  
    -   `Publisher`-此属性用于标识此包，公司或单独的名称的发布者。 `Publisher`特性被限制为 100 个字符。  
  
-   `<DisplayName>`-此元素指定的用户友好的包名，在扩展管理器 UI 中显示。 `DisplayName`内容被限制为 50 个字符。  
  
-   `<Description>`-这一可选元素是在扩展管理器 UI 中显示的包和其内容的简短说明。 `Description`内容可以包含你想，但它具有的任何文本限制为 1000年个字符。  
  
-   `<MoreInfo>`-这一可选元素是指向联机包含此包的完整描述的页面的 URL。 必须将协议指定为 http。  
  
-   `<License>`-这一可选元素是包中包含的许可证文件 （.txt、.rtf） 的相对路径。  
  
-   `<ReleaseNotes>`-这一可选元素是到包 （.txt、.rtf），否则显示发行说明的网站的 URL 中包含的发行说明文件的相对路径。  
  
-   `<Icon>`-这一可选元素是包中包含某个图像文件 （png、 bmp、 jpeg、 ico） 的相对路径。 图标图像应为 32 x 32 像素 （或将收缩到该大小），并显示在 listview UI。 如果没有`Icon`指定元素，UI 将使用默认值。  
  
-   `<PreviewImage>`-这一可选元素是包中包含某个图像文件 （png、 bmp、 jpeg） 的相对路径。 在预览图像应为 200 x 200 像素，并显示在 UI 的详细信息。 如果没有`PreviewImage`指定元素，UI 将使用默认值。  
  
-   `<Tags>`-这一可选元素列出用于搜索提示的以分号分隔的附加文本标记。 `Tags`元素被限制为 100 个字符。  
  
-   `<GettingStartedGuide>`-这一可选元素为某一 HTML 文件的相对路径或指向包含有关如何使用扩展或此包中的内容的信息的网站的 URL。 本指南作为安装的一部分启动。  
  
-   `<AnyElement>*`-清单架构的灵活程度足以允许任何其他元素。 清单加载程序不能被识别任何子元素都公开为 XmlElement 对象的列表。 使用这些子元素，VSIX 扩展可在清单文件中定义的其他数据，并在运行时枚举它们。  
  
### <a name="installation-element"></a>安装元素  
 本部分定义在安装此包的方式和可安装到应用程序 Sku。 本部分包含以下属性：  
  
-   `Experimental`-将设置此属性为 true，如果你有当前为所有用户安装的扩展，但你正在开发的同一计算机上的更新的版本。 例如，如果已为所有用户安装 MyExtension 1.0，但你想要在同一台计算机上进行调试 MyExtension 2.0，设置实验 ="true"。 此属性是在 Visual Studio 2015 Update 1 中可用及更高版本。  
  
-   `Scope`-此特性可以采用"全局"或"ProductExtension"的值：  
  
    -   "全局"，则指定安装不限于特定 SKU。 例如，扩展 SDK 的安装时使用此值。  
  
    -   "ProductExtension"指定安装了传统 VSIX 扩展 （1.0 版） 应用范围限定为单个 Visual Studio Sku。 这是默认值。  
  
-   `AllUsers`-此可选属性指定是否将为所有用户安装此包。 默认情况下，此属性为 false，指定包是每个用户。 （当此值设置为 true 时，执行安装的用户必须将提升至要安装生成 VSIX 的管理权限级别。  
  
-   `InstalledByMsi`-此可选属性指定此包是否已安装 MSI。 安装 MSI 包安装，并托管通过 MSI （程序和功能） 和不通过 Visual Studio 扩展管理器。  默认情况下，此属性为 false，指定未由 MSI 安装的包。  
  
-   `SystemComponent`-此可选属性指定此包是否应考虑系统组件。 系统组件不再显示在扩展管理器 UI 中，无法更新。 默认情况下，此属性为 false，指定的程序包不系统组件。  
  
-   `AnyAttribute*`-`Installation`元素接受将在作为名称 / 值对字典的运行时公开的属性的开放式集。  
  
-   `<InstallationTarget>`-此元素控制其中 VSIX 安装程序会安装包的位置。 如果值`Scope`属性是"ProductExtension"包必须为目标的 SKU 它上面安装清单文件作为其内容以播发其可用性方面对扩展的一部分。 `<InstallationTarget>`元素具有以下属性时`Scope`属性具有显式或默认值"ProductExtension":  
  
    -   `Id`-此特性标识的包。  该属性遵循的命名空间约定： Company.Product.Feature.Name。 `Id`属性只能包含字母数字字符，且最多 100 个字符。 预期值：  
  
        -   Microsoft.VisualStudio.IntegratedShell  
  
        -   Microsoft.VisualStudio.Pro  
  
        -   Microsoft.VisualStudio.Premium  
  
        -   Microsoft.VisualStudio.Ultimate  
  
        -   Microsoft.VisualStudio.VWDExpress  
  
        -   Microsoft.VisualStudio.VPDExpress  
  
        -   Microsoft.VisualStudio.VSWinExpress  
  
        -   Microsoft.VisualStudio.VSLS  
  
        -   My.Shell.App  
  
    -   `Version`-此属性与此 SKU 的最小和最大受支持版本指定版本范围。 包可以详细介绍的 Sku 它所支持的版本。 版本范围表示法是 [10.0-11.0] 其中  
  
        -   [-非独占的最低版本。  
  
        -   ]-最高版本 （含）。  
  
        -   (-独占的最低版本。  
  
        -   )-独占的最高版本。  
  
        -   单个版本 #-仅指定的版本。  
  
        > [!IMPORTANT]
        >  Visual Studio 2012 中引入了 VSIX 架构的版本 2.0。 若要使用此架构你必须安装 Visual Studio 2012 或更高版本的计算机上安装并使用是该产品的一部分 VSIXInstaller.exe。 你可以面向早期版本的 Visual Studio 与 Visual Studio 2012 或更高版本 VSIXInstaller，但只能通过使用更高版本的安装程序。  
  
    -   `AnyAttribute*`-`<InstallationTarget>`元素允许将在作为名称 / 值对字典的运行时公开的属性的开放式集。  
  
### <a name="dependencies-element"></a>依赖关系元素  
 此元素包含此包声明的依赖项的列表。 如果未指定任何依赖关系，这些包 (由其`Id`) 必须之前已安装。  
  
-   `<Dependency>`元素的此子元素具有以下属性：  
  
    -   `Id`-此属性必须为依赖的包的唯一 ID。 此标识值必须匹配`<Metadata><Identity>Id`依赖于此包的包的属性。 `Id`属性遵循的命名空间约定： Company.Product.Feature.Name。 该属性只能包含字母数字字符，且最多 100 个字符。  
  
    -   `Version`-此属性与此 SKU 的最小和最大受支持版本指定版本范围。 包可以详细介绍的 Sku 它所支持的版本。 版本范围表示法 [12.0，13.0]，位置：  
  
        -   [-非独占的最低版本。  
  
        -   ]-最高版本 （含）。  
  
        -   (-独占的最低版本。  
  
        -   )-独占的最高版本。  
  
        -   单个版本 #-仅指定的版本。  
  
    -   `DisplayName`-此特性是包的依赖在 UI 元素，例如对话框和错误消息中使用的显示名称。 该属性是可选的除非通过 MSI 安装从属包。  
  
    -   `Location`-此可选属性指定在嵌套的 VSIX 包到此 VSIX 中的相对路径或依赖项的下载位置的 URL。 此属性用于帮助用户找到系统必备包。  
  
    -   `AnyAttribute*`-`Dependency`元素接受将在作为名称 / 值对字典的运行时公开的属性的开放式集。  
  
### <a name="assets-element"></a>资产元素  
 此元素包含的列表`<Asset>`扩展或内容的每个元素的标记显示此包。  
  
-   `<Asset>`-此元素包含以下特性和元素：  
  
    -   `Type`-这是扩展或此元素所表示的内容的类型。 每个`<Asset>`元素必须具有单个`Type`，但多个`<Asset>`元素可能具有相同`Type`。 根据命名空间约定，应为完全限定的名称，表示此属性。 已知的类型包括：  
  
        1.  Microsoft.VisualStudio.VsPackage  
  
        2.  Microsoft.VisualStudio.MefComponent  
  
        3.  Microsoft.VisualStudio.ToolboxControl  
  
        4.  Microsoft.VisualStudio.Samples  
  
        5.  Microsoft.VisualStudio.ProjectTemplate  
  
        6.  Microsoft.VisualStudio.ItemTemplate  
  
        7.  Microsoft.VisualStudio.Assembly  
  
         可以创建您自己的类型，并为他们提供唯一的名称。 在 Visual Studio 内的运行时，你的代码可枚举并通过扩展管理器 API 访问这些自定义的类型。  
  
    -   路径的文件或包中包含资产的文件夹的相对路径。  
  
    -   `AnyAttribute*`的将在作为名称 / 值对字典的运行时公开的属性开放式集。  
  
         `<AnyElement>*`-任何结构化的内容允许之间`<Asset>`开始和结束标记。 所有元素都公开为 XmlElement 对象的列表。 VSIX 扩展可在清单文件中定义结构化的特定类型的元数据，并在运行时枚举它们。  
  
### <a name="sample-manifest"></a>示例清单  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">  
  <Metadata>  
    <Identity Id="0000000-0000-0000-0000-000000000000" Version="1.0" Language="en-US" Publisher="Company" />  
    <DisplayName>Test Package</DisplayName>  
    <Description>Information about my package</Description>  
    <MoreInfo>http://www.fabrikam.com/Extension1/</MoreInfo>  
    <License>eula.rtf</License>  
    <ReleaseNotes>notes.txt</ReleaseNotes>  
    <Icon>Images\icon.png</Icon>  
    <PreviewImage>Images\preview.png</PreviewImage>  
  </Metadata>  
  <Installation InstalledByMsi="false" AllUsers="false" SystemComponent="false" Scope="ProductExtension">  
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="[11.0, 12.0]" />  
  </Installation>  
  <Dependencies>  
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="[4.5,)" />  
    <Dependency Id="Microsoft.VisualStudio.MPF.12.0" DisplayName="Visual Studio MPF 12.0" d:Source="Installed" Version="[12.0]" />  
  </Dependencies>  
  <Assets>  
    <Asset Type="Microsoft.VisualStudio.VsPackage" d:Source="Project" d:ProjectName="%CurrentProject%" Path="|%CurrentProject%;PkgdefProjectOutputGroup|" />  
  </Assets>  
</PackageManifest>  
```  
  
## <a name="see-also"></a>另请参阅  
 [传送 Visual Studio 扩展](../extensibility/shipping-visual-studio-extensions.md)