---
title: "MSBuild 特殊字符 | Microsoft Docs"
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
  - "转义符"
  - "转义字符"
  - "MSBuild 转义字符"
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild 特殊字符
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 保留一些专供在特定上下文中使用的字符。  如果要在字符被保留的上下文中按原义使用这些字符，只能对此类字符进行转义。  例如，只有在项定义的 `Include` 和 `Exclude` 特性以及对 `CreateItem` 的调用中，星号才具有特殊含义。  如果希望星号在上述某个上下文中显示为星号，则必须对其进行转义。  在其他所有上下文中，只需在需要显示它的位置键入星号即可。  
  
 使用语法 %*xx* 对特殊字符进行转义，其中 *xx* 表示字符的 ASCII 十六进制值。  有关更多信息，请参见[如何：转义 MSBuild 中的特殊字符](../msbuild/how-to-escape-special-characters-in-msbuild.md)。  
  
## 特殊字符  
 下表列出了 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 特殊字符：  
  
|**字符**|**ASCII**|**保留用法**|  
|------------|---------------|--------------|  
|%|%25|引用元数据|  
|$|%24|引用属性|  
|@|%40|引用项列表|  
|'|%27|条件和其他表达式|  
|;|%3B|列表分隔符|  
|?|%3F|用于 `Include` 和 `Exclude` 特性中的文件名的通配符|  
|\*|%2A|用于 `Include` 和 `Exclude` 特性中的文件名的通配符|  
  
## 请参阅  
 [高级概念](../msbuild/msbuild-advanced-concepts.md)   
 [项](../msbuild/msbuild-items.md)