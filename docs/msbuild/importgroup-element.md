---
title: "ImportGroup 元素 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<ImportGroup> 元素 [MSBuild]"
  - "ImportGroup 元素 [MSBuild]"
ms.assetid: dac3fa2d-6678-4017-af35-93686f53f302
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ImportGroup 元素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

包含在可选条件下进行分组的 `Import` 元素的集合。  有关更多信息，请参见 [Import 元素 \(MSBuild\)](../msbuild/import-element-msbuild.md)。  
  
## 语法  
  
```  
<ImportGroup Condition="'String A' == 'String B'">  
    <Import ... />  
    <Import ... />  
</ImportGroup>  
```  
  
## 特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|说明|  
|--------|--------|  
|`Condition`|可选特性。<br /><br /> 要计算的条件。  有关更多信息，请参见 [条件](../msbuild/msbuild-conditions.md)。|  
  
### 子元素  
  
|元素|说明|  
|--------|--------|  
|[导入](../msbuild/import-element-msbuild.md)|将一个项目文件的内容导入另一个项目文件。|  
  
### 父元素  
  
|元素|说明|  
|--------|--------|  
|[Project](../msbuild/project-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 项目文件必需的根元素。|  
  
## 备注  
  
## 示例  
 下面的代码示例演示 `ImportGroup` 元素。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ImportGroup>  
        <Import Project="$(Targets1.targets) />  
        <Import Project="$(Targets2.targets) />  
    </ImportGroup>  
...  
</Project>  
```  
  
## 请参阅  
 [项目文件架构参考](../msbuild/msbuild-project-file-schema-reference.md)   
 [项](../msbuild/msbuild-items.md)