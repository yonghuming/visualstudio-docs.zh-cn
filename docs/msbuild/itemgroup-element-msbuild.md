---
title: "ItemGroup 元素 (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#ItemGroup"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "ItemGroup 元素 [MSBuild]"
  - "<ItemGroup> 元素 [MSBuild]"
ms.assetid: aac894e3-a9f1-4bbc-a796-6ef07001f35b
caps.latest.revision: 24
caps.handback.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ItemGroup 元素 (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

包含一组用户定义的 [Item](../msbuild/item-element-msbuild.md) 元素。  必须将 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 项目中使用的每个项都指定为 `ItemGroup` 元素的子元素。  
  
## 语法  
  
```  
<ItemGroup Condition="'String A' == 'String B'">  
    <Item1>... </Item1>  
    <Item2>... </Item2>  
</ItemGroup>  
```  
  
## 特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|描述|  
|--------|--------|  
|`Condition`|可选特性。  要计算的条件。  有关更多信息，请参见[条件](../msbuild/msbuild-conditions.md)。|  
  
### 子元素  
  
|元素|描述|  
|--------|--------|  
|[项](../msbuild/item-element-msbuild.md)|为生成过程定义输入。  `ItemGroup` 中可能有零个或零个以上的 `Item` 元素。|  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|[项目](../msbuild/project-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 项目文件必需的根元素。|  
|[目标](../msbuild/target-element-msbuild.md)|从 .NET Framework 3.5 开始，`ItemGroup` 元素可以出现在  `Target` 元素内。  有关更多信息，请参见[目标](../msbuild/msbuild-targets.md)。|  
  
## 备注  
  
## 示例  
 下面的代码示例演示了用户定义的项集合 `Res` 和 `CodeFiles`，这些项集合在 `ItemGroup` 元素的内部声明。  `Res` 项集合中的每个项都包含用户定义的子 [ItemMetadata](../msbuild/itemmetadata-element-msbuild.md) 元素。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Res Include = "Strings.fr.resources" >  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include = "Dialogs.fr.resources" >  
            <Culture>fr</Culture>  
        </Res>  
  
        <CodeFiles Include="**\*.cs" Exclude="**\generated\*.cs" />  
        <CodeFiles Include="..\..\Resources\Constants.cs" />  
    </ItemGroup>  
...  
</Project>  
```  
  
## 请参阅  
 [项目文件架构参考](../msbuild/msbuild-project-file-schema-reference.md)   
 [项](../msbuild/msbuild-items.md)   
 [常用的 MSBuild 项目项](../msbuild/common-msbuild-project-items.md)