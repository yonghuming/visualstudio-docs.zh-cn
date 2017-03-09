---
title: "Could not create output directory &#39;directory&#39;. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannot_create_output_dir"
ms.assetid: b4d1d19f-f582-49d0-a9a9-d3f4ce0a447b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Could not create output directory &#39;directory&#39;. &lt;reason&gt;
项目系统未能创建项目目录。  
  
 项目系统将尝试在打开项目时立即创建所有的输出目录。  以下是项目系统创建的输出目录的列表：  
  
 *projectfolder*\\obj\\`configname`  
 临时的特定于配置的输出目录。  
  
 *projectfolder*\\obj\\`configname`\\temp  
 编译器使用的工作区域。  
  
 *projectfolder*\\obj\\`configname`\\temppe  
 设计人员在设计时使用的临时程序集在此创建。  
  
 outputdir  
 由“输出路径”属性指定的目录。  有关更多信息，请参见[“项目设计器”\-\>“生成”页 \(C\#\)](../ide/reference/build-page-project-designer-csharp.md)。  
  
 无法在 obj 文件夹下创建以上目录之一的最常见原因是超过目录名的 MAX\_PATH 限制。  
  
 比较少见的错误包括权限被拒绝和磁盘空间用尽。  
  
 **更正此错误**  
  
-   如果路径过长，则更改项目位置或缩短项目配置的名称。  
  
     若发生此错误，则生成进程将会失败。  
  
## 请参阅  
 [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/zh-cn/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)