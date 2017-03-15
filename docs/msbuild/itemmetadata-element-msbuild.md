---
title: "ItemMetadata 元素 (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "<ItemMetadata> 元素 [MSBuild]"
  - "ItemMetadata 元素 [MSBuild]"
ms.assetid: e3db5122-202d-43a9-b2f4-3e0ec4ed3d08
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# ItemMetadata 元素 (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

包含用户定义的项元数据项，该项元数据项包含项元数据值。  一个项可以有任意数目的元数据键\/值对。  
  
## 语法  
  
```  
<ItemMetadataName> Item Metadata value </ItemMetadataName>  
```  
  
## 特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|说明|  
|--------|--------|  
|`Condition`|可选特性。<br /><br /> 要计算的条件。  有关更多信息，请参见 [条件](../msbuild/msbuild-conditions.md)。|  
  
### 子元素  
 无。  
  
### 父元素  
  
|元素|说明|  
|--------|--------|  
|[项](../msbuild/item-element-msbuild.md)|为生成过程定义输入的用户定义元素。|  
  
## 文本值  
 文本值是可选的。  
  
 此文本指定项元数据值，该值可以是文本，也可以是 XML。  
  
## 备注  
  
## 示例  
 下面的代码示例演示如何向 `CSFile` 项添加带有 `fr` 值的 `Culture` 元数据。  
  
```  
<ItemGroup>  
    <CSFile Include="main.cs" >  
        <Culture>fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
## 请参阅  
 [项目文件架构参考](../msbuild/msbuild-project-file-schema-reference.md)   
 [项](../msbuild/msbuild-items.md)