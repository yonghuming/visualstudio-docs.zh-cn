---
title: "/Runexit (devenv.exe) | Microsoft Docs"
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
  - "/runexit Devenv 开关"
  - "Devenv, /runexit 开关"
  - "runexit Devenv 开关"
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Runexit (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

编译并运行指定的项目或解决方案，然后关闭集成开发环境 \(IDE\)。  
  
## 语法  
  
```  
devenv /runexit {SolutionName|ProjectName}  
```  
  
## 参数  
 `SolutionName`  
 必选。  解决方案文件的完整路径和名称。  
  
 `ProjectName`  
 必选。  项目文件的完整路径和名称。  
  
## 备注  
 根据为活动解决方案配置指定的设置，编译并运行指定的项目或解决方案。  当运行项目或解决方案时，此开关最小化 IDE，并在项目或解决方案完成运行后关闭 IDE。  
  
-   将包含空格的字符串引在双引号中。  
  
-   摘要信息（包括错误）可以显示在**“命令”**窗口中或显示在使用 `/out` 开关指定的任何日志文件中。  
  
## 示例  
 此示例使用活动部署配置在最小化的 IDE 中运行 `MySolution` 解决方案，然后关闭 IDE。  
  
```  
devenv /runexit "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"  
```  
  
## 请参阅  
 [Devenv 命令行开关](../../ide/reference/devenv-command-line-switches.md)   
 [\/Run](../../ide/reference/run-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)