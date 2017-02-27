---
title: "VSIX 清单设计器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.Sdk.VsixManifestEditor"
helpviewer_keywords: 
  - "vsixmanifest"
  - "vsix 清单"
  - "清单设计器"
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# VSIX 清单设计器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

修改 VSIX 程序包清单文件，这会将设置 Visual Studio 扩展的安装行为。  
  
 **VSIX 清单设计器** 映射到基础的 VSIX 架构。 可以通过在设计器中使用相应的控件设置在架构中的每个元素。 有关架构的详细信息，请参阅 [VSIX 扩展架构 2.0 参考](../extensibility/vsix-extension-schema-2-0-reference.md)。  
  
 若要打开 **VSIX 清单设计器**, ，找到的源 source.extension.vsixmanifest 文件中 **解决方案资源管理器**, ，并打开该文件。 如果该文件不包含有效的 XML，将无法打开清单设计器中。  
  
> [!NOTE]
>  生成包时，源 Source.extension.vsixmanifest 被输出到 extension.vsixmanifest。  
  
## UIElement 列表  
 **VSIX 清单设计器** 包含对应于这些架构的顶级元素的四个部分︰  
  
-   元数据  
  
-   安装目标  
  
-   资产  
  
-   依赖项  
  
 标题区域包含以下控件。  
  
 **产品名称**  
 介绍了扩展插件名称。  
  
 **产品 ID**  
 指定此包的唯一标识信息。  
  
 **作者**  
 指定的扩展插件作者的姓名。  
  
 **版本**  
 指定扩展的版本号。  
  
 **元数据** 选项卡包含以下控件。  
  
 **描述**  
 提供扩展中显示的文本说明 **扩展管理器**。  
  
 **语言**  
 指定了在清单中的文本数据相对应的包的默认语言。`Language` 属性对于资源程序集，例如，en 遵循公共语言运行时 \(CLR\) 区域设置代码约定\-我们，en，fr\-fr 的。 默认情况下，值为 neutral;这意味着包将在 Visual Studio 的任何语言版本上运行。  
  
 **许可证**  
 指定的文件，包含用户许可协议，如果不存在。  
  
 **图标**  
 指定包含要在中显示的图标的图形文件 （.png、.bmp、.jpeg、.ico） **扩展管理器**, ，如果存在一个图标。 图标图像必须是 32 x 32 像素，或者它将为那些尺寸调整大小。 如果指定无图标，则 **扩展管理器** 使用默认图标。  
  
 **预览图像**  
 指定包含要在中显示的预览图像的图形文件 （.png、.bmp、.jpeg、.ico） **扩展管理器**, 、 预览图像是否存在。 预览图像必须是 200 x 200 像素。 如果指定无预览图像，则 **扩展管理器** 使用默认图像。  
  
 **标记**  
 添加要用于搜索提示的文本标记。  
  
 **发行说明**  
 指定包含发行说明文件 （.txt、.rtf）。 此外会显示的发行说明的网站的 URL。  
  
 **快速入门指南**  
 指定包含有关如何在 VSIX 包中使用的扩展插件或内容的信息的文件 （.txt、.rtf）。 扩展安装完成后，将显示本指南。 此外会显示该指南的网站的 URL。  
  
 **更多的信息 URL**  
 指定包含有关该产品的其他信息的网站的 URL。  
  
 **安装目标** 选项卡包含以下控件。  
  
 **安装类型**  
 列出 **Visual Studio 扩展** 和 **扩展 SDK** 目标类型的安装。 选项因您选择的类型而异。  
  
 **Visual Studio 扩展**  
 列出 **InstallationTarget** 描述如何可以安装的包和到哪些 Visual Studio 产品可以安装此扩展插件的元素。 每种产品均由名称和版本或版本范围分别标识。  可以添加到列表、 修改和删除产品。 名称和产品的版本对应于 **Id** 和 **版本** 属性关联的 **InstallationTarget** 元素。  
  
 **版本范围** 是 \[12.0、 14.0\]，并使用以下表示法︰  
  
-   \[\-非独占的最低版本  
  
-   \] – 最高版本 （含）  
  
-   \(\-独占的最低版本  
  
-   \) – 排他的最高版本  
  
-   单个版本 \#\-仅指定的版本  
  
 **扩展 SDK**  
 指定不作用域限定为特定的产品和版本的全局安装。**目标平台标识符** 是平台，如"Windows"，您的目标。**目标平台版本** 是版本，如 8.0，您的目标平台。**SDK 名称** 和 **SDK 版本** 分别为的名称和版本号的 sdk。  
  
 **为所有用户安装此 VSIX （要求安装提升）** 复选框  
 所有用户; 如果选中此复选框，都安装此扩展插件否则，它是仅针对当前用户安装。  
  
 **由 Windows 安装程序安装此 VSIX** 复选框  
 如果选中此复选框，Windows Installer （.msi 文件）; 将安装此扩展插件否则，它是作为典型的 VSIX 包 （.vsix 文件） 安装。  
  
 **资产** 选项卡包含以下控件。  
  
 **资产的列表**  
 列出的资产的元素，描述扩展或内容元素此包的曲面。 每个扩展插件或内容元素是由源、 类型和路径单独列出。 可以添加到列表、 修改和删除扩展和内容的元素。 类型和路径的扩展名或内容的元素对应于 `Type` 和 `Path` 属性关联的 `Asset` 元素。 是已知的以下类型︰  
  
-   Microsoft.VisualStudio.Package  
  
-   Microsoft.VisualStudio.MefComponent  
  
-   Microsoft.VisualStudio.ToolboxControl  
  
-   Microsoft.VisualStudio.Samples  
  
-   Microsoft.VisualStudio.ProjectTemplate  
  
-   Microsoft.VisualStudio.ItemTemplate  
  
-   Microsoft.VisualStudio.Assembly  
  
-   Microsoft.ExtensionSDK  
  
 要添加或编辑资源，必须指定资产类型中，资产是当前解决方案中的项目或文件在文件系统和项目的名称。 此外可以指定在其中嵌入的文件夹的名称。  
  
 您还可以创建您自己的类型和为其提供唯一名称。  
  
 **依赖关系** 选项卡包含以下控件。  
  
 **名称、 源和版本范围**  
 列出此包的依赖关系元素是其他依赖于此包的包。 如果指定依赖项包，则它必须安装之前安装此程序包;否则，此包必须安装它。  
  
 依赖项包由标识符、 名称、 版本范围、 源和解析依赖关系的方式指定。 按名称、 版本和源分别列出每个依赖项包。 可以添加到列表中，修改，或删除依赖项包。  
  
 标识符必须匹配 `ID` 的依赖项包元数据属性。 源可以是当前解决方案、 当前已安装的扩展或文件中的项目。**的依赖关系解析方式** 设置可以是嵌套的软件包的相对路径或依赖关系的下载位置的 URL。 ID、 版本和依赖项包的分辨率对应于 `Id`, ，`Version`, ，和 `Location` 属性关联的 `Dependency` 元素。  
  
## 请参阅  
 [VSIX 扩展架构 2.0 参考](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [VSIX 包的剖析](../extensibility/anatomy-of-a-vsix-package.md)