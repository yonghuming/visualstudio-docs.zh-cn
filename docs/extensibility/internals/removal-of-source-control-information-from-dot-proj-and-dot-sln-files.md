---
title: "从源代码管理信息的删除操作。Proj 和。Sln 文件 | Microsoft Docs"
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
  - "源代码管理插件、.sln 和.proj 文件"
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# 从源代码管理信息的删除操作。Proj 和。Sln 文件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在源代码管理插件 API 的 1.2 版 SCC 信息。 MSSCCPRJ.SCC 文件中。  MSSCCPRJ.SCC 文件的好处是 SCC 信息不是控件的源，如 .proj 和 .sln 文件。  
  
## 版本 1.2 更改  
 在基于源代码管理插件 API 1.1 版的源代码管理插件，有关源代码管理的信息在项目 \(.proj\) 和解决方案 \(.sln\) 文件中。  源代码管理信息的数据库位置由 AuxPath 指定，因此，在数据库中的特定位置由 ProjName 指定。  ，因为 ProjName 通常在无效的任何这些操作后，此行为可能在分支、分叉或复制操作之后会导致问题。  
  
 在源代码管理插件 API 1.1 版中， IDE 使用 ~SAK 文件检测插件是否支持存储源代码管理信息 MSSCCPRJ.SCC 方法。  源代码管理插件 API 1.2 版检测 MSSCCPRJ.SCC 文件的支持提供了一个新函数，而不使用 ~SAK 文件。  有关更多信息，请参见 [消除了 ~ SAK 文件](../../extensibility/internals/elimination-of-tilde-sak-files.md)。  
  
## 请参阅  
 [什么是源代码管理插件 API 版本 1.2 中的新增功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)