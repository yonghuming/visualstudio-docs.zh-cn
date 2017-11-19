---
title: "VSIX 清单设计器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eaf35854aede65b605b4578ca9ee71375ad7a479
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="vsix-manifest-designer"></a>VSIX 清单设计器
修改 VSIX 包清单文件，它设置 Visual Studio 扩展的安装行为。  
  
 **VSIX 清单设计器**映射到基础的 VSIX 架构。 可以通过使用设计器中的一个相应控件设置架构中的每个元素。 有关架构的详细信息，请参阅[VSIX 扩展架构 2.0 引用](../extensibility/vsix-extension-schema-2-0-reference.md)。  
  
 若要打开**VSIX 清单设计器**，定位 source.extension.vsixmanifest 文件中的**解决方案资源管理器**，并打开该文件。 如果文件不包含有效的 XML，将不会打开在清单设计器。  
  
> [!NOTE]
>  Source.extension.vsixmanifest 时生成软件包时，将输出到 extension.vsixmanifest。  
  
## <a name="uielement-list"></a>UIElement 列表  
 **VSIX 清单设计器**包含对应于架构的这些顶级元素的四个部分：  
  
-   元数据  
  
-   安装目标  
  
-   资产  
  
-   依赖项  
  
 标题区域包含以下控件。  
  
 **产品名称**  
 描述扩展名称。  
  
 **产品 ID**  
 指定此包的唯一标识信息。  
  
 **作者**  
 指定扩展的作者的名称。  
  
 **Version**  
 指定扩展的版本号。  
  
 **元数据**选项卡包含以下控件。  
  
 **描述**  
 提供的扩展，在中显示的文本说明**扩展管理器**。  
  
 **语言**  
 指定包，其中对应于在清单中的文本数据的默认语言。 `Language`属性对于资源程序集，例如，en 遵循公共语言运行时 (CLR) 区域设置代码约定-我们、 en、 fr fr。 默认情况下，值是特定的;这意味着，包将 Visual Studio 的任何语言版本上运行。  
  
 **许可证**  
 如果存在，请指定包含用户许可协议的文本文件。  
  
 **图标**  
 指定包含要在中显示的图标的图形文件 （.png、.bmp、.jpeg、.ico）**扩展管理器**，如果图标。 图标图像必须是 32 x 32 像素，否则它将调整到这些维度。 如果未指定图标，**扩展管理器**使用默认图标。  
  
 **预览图像**  
 指定包含要在中显示的预览图像的图形文件 （.png、.bmp、.jpeg、.ico）**扩展管理器**、 预览图像是否存在。 在预览图像必须是 200 x 200 像素。 如果不指定任何预览图像，则**扩展管理器**使用默认映像。  
  
 **标记**  
 添加文本标记要用于搜索提示。  
  
 **发行说明**  
 指定包含发行说明的文件 （.txt、.rtf）。 此外将显示的发行说明的网站的 URL。  
  
 **快速入门指南**  
 指定包含有关如何使用 VSIX 包中的扩展或内容信息的文件 （.txt、.rtf）。 当扩展安装完成时，将显示本指南。 此外将显示该指南的网站的 URL。  
  
 **详细信息 URL**  
 指定包含有关产品的其他信息的网站的 URL。  
  
 **安装目标**选项卡包含以下控件。  
  
 **安装类型**  
 列出**Visual Studio 扩展**和**扩展 SDK**作为针对安装类型。 选项因你选择的类型而异。  
  
 **Visual Studio 扩展**  
 列出**InstallationTarget**描述了如何可以安装此包和到哪些 Visual Studio 产品可以安装此扩展的元素。 每个产品都由名称和版本或版本范围单独标识。  可以添加到列表、 修改和删除产品。 名称和产品的版本对应于**Id**和**版本**属性关联的**InstallationTarget**元素。  
  
 **版本范围**是 [12.0，14.0]，并使用以下表示法：  
  
-   [-非独占的最低版本  
  
-   ]-非独占的最高版本  
  
-   (-独占的最低版本  
  
-   )-独占的最高版本  
  
-   单个版本 #-仅指定的版本  
  
 **扩展 SDK**  
 指定不应用范围限定为特定的产品和版本的全局安装。 **目标平台标识符**是如"Windows"，你面向的平台。 **指定的目标平台版本**是版本，例如 8.0 的目标平台。 **SDK 名称**和**SDK 版本**分别是的名称和的 sdk 的版本号。  
  
 **此 VSIX 针对所有用户安装 （需要在安装的提升）**复选框  
 如果选中此复选框，此扩展插件是针对所有用户; 安装否则，它是仅为当前用户安装。  
  
 **由 Windows 安装程序安装此 VSIX**复选框  
 如果选中此复选框，将此扩展安装 Windows installer （.msi 文件）;否则，可作为典型的 VSIX 包 （.vsix 文件） 进行安装。  
  
 **资产**选项卡包含以下控件。  
  
 **列出的资产列表**  
 列出的资产元素介绍扩展或内容元素，此包图面。 每个扩展或内容元素的源、 类型和路径单独列出。 可以添加到列表、 修改和删除扩展和内容的元素。 类型和路径以扩展或内容元素对应于`Type`和`Path`属性关联的`Asset`元素。 是已知的以下类型：  
  
-   Microsoft.VisualStudio.Package  
  
-   Microsoft.VisualStudio.MefComponent  
  
-   Microsoft.VisualStudio.ToolboxControl  
  
-   Microsoft.VisualStudio.Samples  
  
-   Microsoft.VisualStudio.ProjectTemplate  
  
-   Microsoft.VisualStudio.ItemTemplate  
  
-   Microsoft.VisualStudio.Assembly  
  
-   Microsoft.ExtensionSDK  
  
 要添加或编辑资产，必须指定资产类型中，资产当前解决方案中的项目或文件中是否文件系统和项目的名称。 你还可以指定要嵌入在其中的文件夹的名称。  
  
 你还可以创建您自己的类型和为其提供唯一的名称。  
  
 **依赖关系**选项卡包含以下控件。  
  
 **名称、 源和版本范围**  
 列出了此包的依赖项元素作为此包依赖于其他包。 如果指定依赖项包，则它必须安装之前将安装此包;否则，此包必须安装它。  
  
 依赖项包指定标识符、 名称、 版本范围、 源和依赖项的解析方式。 每个依赖项包的名称、 版本和源单独列出。 可以添加到列表、 修改和删除依赖项包。  
  
 标识符必须与匹配`ID`的依赖项包元数据的属性。 源可以是当前的解决方案、 当前安装的扩展或文件中的项目。 **如何为依赖关系解析**设置可以是嵌套的包相对路径或依赖项的下载位置的 URL。 ID、 版本和依赖项包的分辨率对应于`Id`， `Version`，和`Location`属性关联的`Dependency`元素。  
  
## <a name="see-also"></a>另请参阅  
 [VSIX 扩展架构 2.0 参考](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [VSIX 包的剖析](../extensibility/anatomy-of-a-vsix-package.md)