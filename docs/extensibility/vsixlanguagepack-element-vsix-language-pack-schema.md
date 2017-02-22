---
title: "VSIXLanguagePack 元素 (VSIX 语言包架构) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 767f5c22-8b87-49ca-92aa-a7a3f026469f
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# VSIXLanguagePack 元素 (VSIX 语言包架构)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

必需。 VSIX 语言包提供的根元素。 VSIX 语言包提供了一个 VSIX 包的本地化的安装信息。  
  
## 语法  
  
```  
<VSIXLanguagePack>  
  <LocalizedName>...</LocalizedName>  
  <LocalizedDescription>...</LocalizedDescription>  
  <MoreInfoURL>...</MoreInfoURL>  
  <License>...</License>  
</VSIXLanguagePack>  
```  
  
## 特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|描述|  
|--------|--------|  
|`xmlns`|在其中定义该 VSIX 语言包架构的 XML 命名空间。|  
  
## xmlns 属性  
  
|值|说明|  
|-------|--------|  
|`http://schemas.microsoft.com/developer/vsx-schema-lp/2010`|必需。 定义了语言包的架构文件的位置。|  
  
### 子元素  
  
|元素|描述|  
|--------|--------|  
|[LocalizedName 元素](../extensibility/localizedname-element-vsix-language-pack-schema.md)|必需。 要安装的扩展插件的本地化的名称。|  
|[LocalizedDescription 元素](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)|必需。 要安装的扩展插件的本地化的说明。|  
|[其他信息 Url 元素](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)|可选。 指向有关扩展的本地化信息的链接。|  
|[许可证元素](../extensibility/license-element-vsix-language-pack-schema.md)|可选。 许可证文件的扩展插件的本地化版本的路径。|  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|无||  
  
## 元素信息  
  
|||  
|-|-|  
|命名空间|http:\/\/schemas.microsoft.com\/developer\/vsx\-schema\-lp\/2010|  
|架构名称|VSIX 语言包架构|  
|验证文件|VSIXLanguagePackSchema.xsd|  
|可以为空|No|  
  
## 请参阅  
 [VSX 语言包架构引用](../extensibility/vsx-language-pack-schema-reference.md)   
 [本地化 VSIX 包](../extensibility/localizing-vsix-packages.md)   
 [VSIX 扩展架构 1.0 引用](http://msdn.microsoft.com/zh-cn/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)