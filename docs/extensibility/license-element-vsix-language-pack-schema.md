---
title: "许可证元素 (VSIX 语言包架构) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 57dac3b7-0cdd-405c-9af5-30ed9ca45e53
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# 许可证元素 (VSIX 语言包架构)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可选。 许可证文件的扩展插件的本地化版本的路径。  
  
## 语法  
  
```  
<License>FilePath\license.txt</License>  
```  
  
## 特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|描述|  
|--------|--------|  
|无||  
  
### 子元素  
  
|元素|描述|  
|--------|--------|  
|无||  
  
### 父元素  
  
|元素|说明|  
|--------|--------|  
|[VSIX LanguagePack 元素](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|必需。 VSIX 语言包提供的根元素。|  
  
## 文本值  
 要显示的本地化的许可证文件的相对路径。  
  
## 备注  
 如果 `License` 定义元素，则在指定的许可证文件的文本将显示在安装过程中并且用户必须接受许可协议，以便继续。  
  
## 元素信息  
  
|||  
|-|-|  
|命名空间|http:\/\/schemas.microsoft.com\/developer\/vsx\-schema\-lp\/2010|  
|架构名称|VSIX 语言包架构|  
|验证文件|VSIXLanguagePackSchema.xsd|  
|可以为空|不适用|  
  
## 请参阅  
 [VSX 语言包架构引用](../extensibility/vsx-language-pack-schema-reference.md)   
 [本地化 VSIX 包](../extensibility/localizing-vsix-packages.md)   
 [VSIX 扩展架构 1.0 引用](http://msdn.microsoft.com/zh-cn/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)