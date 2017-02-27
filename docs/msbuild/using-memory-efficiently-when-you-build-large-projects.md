---
title: "在生成大型项目时有效使用内存 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "缓存 (MSBuild)"
  - "内存使用 (MSBuild)"
  - "msbuild, 生成大型树时的高效内存使用"
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# 在生成大型项目时有效使用内存
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

大型项目通常包含许多子项目和其他依赖项，这在生成时会占用大量系统内存。  当可用的系统内存减少时，系统性能也会降低。  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 项目的早期版本保留在内存中，或者在 3.5 版中已将项目删除，但仍在缓存中保留生成结果以便于以后检索。  
  
 版本 4.0 可自动处理此内存管理，使得项目不必使用 `UnloadProjectsOnCompletion` 和 `UseResultsCache` 等属性。  
  
## 请参阅  
 [并行生成多个项目](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)