---
title: "VSIX 语言包架构 2.0 参考 |Microsoft 文档"
ms.custom: 
ms.date: 10/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language pack
- localize vsix
- localize package
- localize extension
ms.assetid: 2a2932bc-cdbe-4d32-91fa-a3e0474f9098
caps.latest.revision: "8"
ms.author: dagriffe
author: dgriffen
manager: ghogen
ms.openlocfilehash: 15c63e446699f254ba33237c264c06c1da802811
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="vsix-language-pack-schema-20-reference"></a>VSIX 语言包架构 2.0 参考

VSIX 语言包架构提供 VSIX 包的本地化的安装信息。 此架构的版本 2.0 支持其他本地化的元素。

## <a name="language-pack-schema"></a>语言包架构

语言包文件的根元素是`<PackageLanguagePackManifest>`，使用的属性`Version`，即语言包格式的版本。 本主题介绍的语言包格式，这通过设置的清单中指定的版本 2.0`Version`属性的值`Version="2.0.0"`。 根元素包含一个子`<Metadata>`元素。

### <a name="packagelangaugepackmanifest-element"></a>PackageLangaugePackManifest 元素

在`<PackageLanguagePackManifest>`元素必须存在以下元素：
|标题|描述|
|-----------|-----------------|
|`<Metadata>`| 包含的所有本地化的包元数据元素

### <a name="metadata-element"></a>元数据元素

在`<Metadata>`元素可以包含以下元素：
|标题|描述|
|-----------|-----------------|
|`<DisplayName>`|若要安装扩展的本地化的名称|
|`<Description>`|要安装的扩展本地化的说明|
|`<License>`| 路径扩展的许可证的本地化版本|
|`<MoreInfo>`| 指向有关扩展的本地化信息的链接|
|`<ReleaseNotes>`| 一个路径或链接到的本地化版本的发行说明|
|`<Icon>`| 路径扩展图标的本地化版本|

### <a name="sample-manifest"></a>示例清单

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</LocalizedName>
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
|[本地化 VSIX 包](../extensibility/localizing-vsix-packages.md)|演示如何为 VSIX 包提供本地化的安装支持。|
|[VSIX 扩展架构 2.0 参考](../extensibility/vsix-extension-schema-2-0-reference.md)|VSIX 清单将描述启用要通过使用安装的 Visual Studio 扩展的.vsix 部署文件的内容**扩展和更新**对话框。|
|[查找和使用 Visual Studio 扩展](../ide/finding-and-using-visual-studio-extensions.md)|演示如何使用**扩展和更新**对话框中，若要安装、 删除、 激活和停用扩展。|