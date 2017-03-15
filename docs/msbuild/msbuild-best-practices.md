---
title: "MSBuild 最佳做法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "最佳做法, MSBuild"
  - "MSBuild, 最佳做法"
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# MSBuild 最佳做法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

我们建议下列编写 MSBuild 脚本的最佳做法：  
  
-   默认属性值的最佳处理方式是使用 `Condition` 特性，而不是声明可在命令行中重写其默认值的属性。  例如，使用  
  
     `<MyProperty Condition="$(MyProperty)" == ''>`  
  
     `MyDefaultValue`  
  
     `</MyProperty>`  
  
-   在选择项目时，请避免使用通配符。  而应显式指定文件。  这使得跟踪在添加或删除文件时可能出现的错误更加简单。  
  
## 请参阅  
 [高级概念](../msbuild/msbuild-advanced-concepts.md)