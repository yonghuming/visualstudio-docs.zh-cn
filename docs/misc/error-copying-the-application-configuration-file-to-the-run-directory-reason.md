---
title: "Error copying the application configuration file to the run directory. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cant_copy_appcfg_file"
ms.assetid: 15699a76-16ef-40a8-8ed4-5eef4d2c0e72
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error copying the application configuration file to the run directory. &lt;reason&gt;
项目系统无法将 app.config 文件复制到正在从其中运行该项目的目录中。  若发生此错误，则生成进程将会失败。  
  
 此错误只有当生成 .exe 文件时才产生。  
  
 生成系统尝试在项目的根文件夹中查找名为 app.config 的文件。  然后将该文件复制到项目的输出目录中；其名称在输出目录中将为 *outputfile.*config。  
  
 此错误的原因包括：  
  
-   磁盘空间不足  
  
-   超过 MAX\_PATH  
  
 可能还要确保应用程序没有正在运行的其他副本。  
  
## 请参阅  
 [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/zh-cn/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)