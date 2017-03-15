---
title: "/Log (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/Log Devenv 开关"
  - "Devenv, /Log 开关"
  - "Log 开关 [devenv.exe]"
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Log (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

将所有活动记录到日志文件以用于疑难解答。  此文件在你至少调用一次 `devenv /log` 后显示。  默认情况下，日志文件为：  
  
 *%APPDATA%*\\Microsoft\\VisualStudio\\*Version*\\ActivityLog.xml  
  
 其中，*Version* 是 Visual Studio 的版本。  但是，可以指定一个不同的路径和文件名。  
  
## 语法  
  
```  
Devenv /log Path\NameOfLogFile  
```  
  
## 备注  
 此开关必须显示在命令行的结尾，位于所有其他开关之后。  
  
 对于你使用 \/log 开关调用的所有 Visual Studio 实例，都会记录日志。  对于不使用此开关调用的 Visual Studio 实例，将不记录日志。  
  
## 请参阅  
 [Devenv 命令行开关](../../ide/reference/devenv-command-line-switches.md)