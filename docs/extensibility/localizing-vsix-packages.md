---
title: "本地化 VSIX 包 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "本地化包"
  - "本地化扩展"
  - "已本地化的部署"
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# 本地化 VSIX 包
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以通过创建用于每种目标语言的 Extension.vsixlangpack 文件，然后将它们放在正确的文件夹中本地化 VSIX 包。 安装本地化的包时，都会随的本地化说明一起显示的扩展插件的本地化的名称。 如果您提供本地化的许可文件或指向本地化信息的 URL，则它们也会显示。  
  
 如果本文内容 VSIX 包包括对添加的 VSPackage 菜单命令或其他 UI，请参阅 [本地化的菜单命令](../extensibility/localizing-menu-commands.md) 本地化新的用户界面元素有关的信息。  
  
## 目录结构  
 当用户安装扩展， **扩展和更新** 检查其名称与目标计算机的 Visual Studio 区域设置相匹配的文件夹的 VSIX 包的最高级别。 如果 **扩展和更新** .vsixlangpack 找到文件的文件夹中，都将替换该文件以了解.vsixmanifest 文件中的相应值中的本地化的值。 在安装该扩展时，会显示这些值。 下面的示例显示已本地化为西班牙语 \(es ES\) 和法语 \(FR\-FR\) 一个 VSIX 包的目录结构。  
  
 MyExtension.dll  
  
 Extension.vsixmanifest  
  
 \[Content\_Types\].xml  
  
 es\-ES  
  
 Extension.vsixlangpack  
  
 fr\-FR  
  
 Extension.vsixlangpack  
  
> [!NOTE]
>  中的 VSIX 支持的项目模板 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 生成 VSIX 清单并将其命名为 source.extension.vsixmanifest。 Visual Studio 生成项目以后，它将复制该文件的内容到 Extension.VsixManifest VSIX 包中。  
  
## Extension.vsixlangpack 文件  
 Extension.vsixlangpack 文件遵循 [VSIX 语言包架构](../extensibility/vsx-language-pack-schema-reference.md)。 此架构具有 [VSIXLanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md) 根元素和这些四个子元素︰ [LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md), ，[LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md), ，[其他信息 Url](../extensibility/moreinfourl-element-vsix-language-pack-schema.md), ，和 [许可证](../extensibility/license-element-vsix-language-pack-schema.md)。 这些子元素对应于 `Name`, ，`Description`, ，`MoreInfoURL`, ，和 `License` 的子元素 `Identifier` Extension.vsixmanifest 文件中的元素。  
  
 当创建 vsixlangpack 文件时，必须设置 `Include in Vsix` 属性设置为 `true`。 否则，本地化的安装文本将被忽略。  
  
#### 若要设置在包括在 Vsix 属性  
  
1.  在 **解决方案资源管理器**, ，右键单击 Extension.vsixlangpack 文件，然后单击 **属性**。  
  
2.  在属性网格中，单击 **包含在 Vsix**, ，并将其值设置为 `true`。  
  
## 示例  
  
### 描述  
 下面的示例演示 Extension.vsixmanifest 文件，以及西班牙语的相应 Extension.vsixlangpack 文件的相关部分。 如果目标计算机的 Visual Studio 区域设置设置为西班牙语，语言包中的值替换清单中的值。  
  
### 代码  
 \[\] Extension.vsixmanifest  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VSIX ...>  
  <Identifier ...>  
    <Name>Family Tree</Name>  
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>  
    <License>EULA.rtf</License>  
    <MoreInfoURL>http://www.contoso.com/products/FamilyTree.htm</MoreInfoURL>  
    ...  
  </Identifier>  
  <References .../>  
  <Content .../>  
</VSIX>  
```  
  
 \[\] Extension.vsixlangpack  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VsixLanguagePack Version="1.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema-lp/2010">  
  <LocalizedName>Arbol de Familia</LocalizedName>  
  <LocalizedDescription> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</LocalizedDescription>  
  <License>es\Eula.rtf</License>  
  <MoreInfoUrl> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfoUrl>  
</VsixLanguagePack>  
```  
  
## 请参阅  
 [VSIX LanguagePack 元素](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)   
 [VSIX 包的剖析](../extensibility/anatomy-of-a-vsix-package.md)   
 [VSIX 项目模板](../extensibility/vsix-project-template.md)