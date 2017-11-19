---
title: "本地化 VSIX 包 |Microsoft 文档"
ms.custom: 
ms.date: 10/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6a8bb9332b30e5dbc410bdacea3800713b25b10f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="localizing-vsix-packages"></a>本地化 VSIX 包

你可以通过创建每个目标语言的 Extension.vsixlangpack 文件，然后将它们放在正确的文件夹本地化 VSIX 包。 安装本地化的包时，扩展的本地化的名称被显示以及本地化说明。 如果你提供一个本地化的许可证文件或指向本地化信息的 URL，则它们也会显示。

如果内容 VSIX 包包括 VSPackage 添加菜单命令或其他 UI，请参阅[本地化菜单命令](../extensibility/localizing-menu-commands.md)有关本地化的新 UI 元素。

## <a name="directory-structure"></a>目录结构

 当用户安装扩展，**扩展和更新**检查其名称与目标计算机的 Visual Studio 区域设置相匹配的文件夹的 VSIX 包的最高级别。 如果**扩展和更新**.vsixlangpack 找到文件的文件夹中，用替换该文件以了解的.vsixmanifest 文件中的相应值中的本地化的值。 当安装扩展后，不显示这些值。 下面的示例演示的 VSIX 包的本地化为西班牙语 (es ES) 和法语 (FR-FR) 的目录结构。  

```text
.
├── MyExtension.dll
├── Extension.vsixmanifest
├── [Content_Types].xml
├── es-ES
│   └── Extension.vsixlangpack
└── fr-FR
    └── Extension.vsixlangpack
```

> [!NOTE]
> 中的 VSIX 支持项目模板[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]生成 VSIX 清单并将其命名 source.extension.vsixmanifest。 Visual Studio 在生成项目时它将复制该文件的内容到 Extension.VsixManifest VSIX 包中。

## <a name="the-extensionvsixlangpack-file"></a>Extension.vsixlangpack 文件

Extension.vsixlangpack 文件遵循[VSIX 语言包架构 2.0](../extensibility/vsix-language-pack-schema-2-0-reference.md)。 此架构具有`PackageLanguagePackManifest`，其中后紧跟着`Metadata`子元素。 元数据元素可以包含最多 6 的子元素， `DisplayName`， `Description`， `MoreInfo`， `License`， `ReleaseNotes`，和`Icon`。 这些子元素对应于`DisplayName`， `Description`， `MoreInfo`， `License`， `ReleaseNotes`，和`Icon`的子元素`Metadata`Extension.vsixmanifest 文件的元素。

当创建 vsixlangpack 文件时，您必须设置`Include in Vsix`属性`true`。 否则，将忽略的本地化的安装文本。

### <a name="to-set-the-include-in-vsix-property"></a>若要设置在包括在 Vsix 属性

1. 在**解决方案资源管理器**，右键单击 Extension.vsixlangpack 文件，然后单击**属性**。

2.  在属性网格中，单击**包括在 Vsix 中的**，并将其值设置为`true`。

## <a name="example"></a>示例

### <a name="description"></a>描述

下面的示例演示 Extension.vsixmanifest 文件，以及西班牙语的相应 Extension.vsixlangpack 文件的相关部分。 如果目标计算机的 Visual Studio 区域设置设置为西班牙语，则语言包中的值替换清单中的值。

### <a name="code"></a>代码

 [Extension.vsixmanifest]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageManifest ...>
  <Metadata ...>
    <DisplayName>Family Tree</DisplayName>
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>
    <MoreInfo>http://www.contoso.com/products/FamilyTree.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
  <Installation .../>
  <Dependencies .../>
  <Prerequisites .../>
  <Assets .../>
</PackageManifest>
```

 [Extension.vsixlangpack]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</DisplayName>
    <Description> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</Description>
    <MoreInfo> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
</PackageLanguagePackManifest>
```

## <a name="see-also"></a>另请参阅

|标题|描述|
|-----------|-----------------|
|[VSIX LanguagePack 架构 2.0 参考](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|VSIX 语言包描述一个.vsix 部署文件的本地化信息。|
|[VSIX 包的剖析](../extensibility/anatomy-of-a-vsix-package.md)|描述的结构和 vsix 包的内容。|
|[本地化菜单命令](../extensibility/localizing-menu-commands.md)|演示如何本地化扩展中的其他文本资源。|