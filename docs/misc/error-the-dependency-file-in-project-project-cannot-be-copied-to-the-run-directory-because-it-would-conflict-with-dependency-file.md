---
title: "错误：不能将项目“project”中的依赖项“file”复制到运行目录，因为它将与依赖项“file”冲突 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.copy_version_conflict"
ms.assetid: cd7de1eb-7d58-4e2c-9811-a7201f7817be
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 错误：不能将项目“project”中的依赖项“file”复制到运行目录，因为它将与依赖项“file”冲突
引用之间存在冲突；为使应用程序运行，将多个具有相同文件名的不同的依赖项复制到 bin 目录中。 由于没有任何依赖项是主引用，因此运行目录无法解决此冲突。  
  
 此错误将导致生成失败。  
  
 双击此“任务列表”项将跳转到在其中发生冲突的项目的引用节点。  
  
 **更正此错误**  
  
-   将某个程序集设为你项目的直接引用。 此方法可能存在的缺点是，不保证你所选择的程序集适用于需要引用程序集的某一其他版本的程序集。  
  
     \- 或 \-  
  
-   请确保程序集的这两个副本具有强名称且在全局程序集缓存中。 这样就无需将程序集复制到 bin 目录中。  
  
## 请参阅  
 [管理项目中的引用](../ide/managing-references-in-a-project.md)   
 [全局程序集缓存](../Topic/Global%20Assembly%20Cache.md)   
 [具有强名称的程序集](../Topic/Strong-Named%20Assemblies.md)   
 [程序集版本控制](../Topic/Assembly%20Versioning.md)   
 [如何：创建和移除项目依赖项](../Topic/How%20to:%20Create%20and%20Remove%20Project%20Dependencies.md)