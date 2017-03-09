---
title: "MSBuild 错误 MSB1019 | Microsoft Docs"
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
  - "MSBuild.InvalidLoggerError"
helpviewer_keywords: 
  - "MSB1019"
ms.assetid: 5d0169f7-f878-433a-ac30-d9d6010130af
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB1019
**记录器开关的格式不正确。**  
  
 未正确指定 **\/logger** 开关。  若要指定记录器，必须至少提供记录器程序集；或者，如果要明确指定要加载的记录器，记录器类和记录器程序集都必须提供。  记录器参数是可选的。  
  
### 更正此错误  
  
1.  使用记录器类和记录器程序集两者指定记录器。  `<logger>` 语法为：  
  
     `<logger class>,<logger assembly>[;<logger parameters>]`  
  
     `<logger class>` 语法为：  
  
    ```  
    [<partial or full namespace>.]<logger class name>  
    ```  
  
     `<logger assembly>` 语法为：  
  
    ```  
    {<assembly name>[,<strong name>] | <assembly file>}  
    ```  
  
     `<logger parameters>` 是可选的，它们完全按您所键入的样子传递给记录器。  
  
     示例：\/`logger:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`  
  
## 请参阅  
 [命令行参考](../msbuild/msbuild-command-line-reference.md)   
 [生成记录器](../msbuild/build-loggers.md)