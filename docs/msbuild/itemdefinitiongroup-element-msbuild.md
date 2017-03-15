---
title: "ItemDefinitionGroup 元素 (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#ItemDefinitionGroup"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<ItemDefinitionGroup> 元素 [MSBuild]"
  - "ItemDefinitionGroup 元素 [MSBuild]"
ms.assetid: 4e9fb04b-5148-4ae5-a394-42861dd62371
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# ItemDefinitionGroup 元素 (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`ItemDefinitionGroup` 元素使您可以定义一组项定义，这些项定义默认是适用于项目中所有项的元数据值。  ItemDefinitionGroup 可取代 [CreateItem 任务](../msbuild/createitem-task.md) 和 [CreateProperty 任务](../msbuild/createproperty-task.md)。  有关更多信息，请参见[项定义](../msbuild/item-definitions.md)。  
  
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
  
|特性|说明|  
|--------|--------|  
|`Condition`|可选特性。  要计算的条件。  有关更多信息，请参见 [条件](../msbuild/msbuild-conditions.md)。|  
  
### 子元素  
  
|元素|说明|  
|--------|--------|  
|[项](../msbuild/item-element-msbuild.md)|为生成过程定义输入。  `ItemDefinitionGroup` 中可能有零个或零个以上的 `Item` 元素。|  
  
### 父元素  
  
|元素|说明|  
|--------|--------|  
|[Project](../msbuild/project-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 项目文件必需的根元素。|  
  
## 示例  
 下面的代码示例在一个 ItemDefinitionGroup 中定义两个元数据项：m 和 n。  在此示例中，默认元数据“m”应用于项“i”，原因是项“i”未显式定义元数据“m”。  但默认元数据“n”不应用于项“i”，原因是项“i”已定义元数据“n”。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemDefinitionGroup>  
        <i>  
            <m>m1</m>  
            <n>n1</n>  
        </i>        
    </ItemDefinitionGroup>  
    <ItemGroup>  
        <i Include="a">  
            <o>o1</o>  
            <n>n2</n>  
        </i>  
    </ItemGroup>  
    ...  
</Project>  
```  
  
## 请参阅  
 [项目文件架构参考](../msbuild/msbuild-project-file-schema-reference.md)   
 [项](../msbuild/msbuild-items.md)