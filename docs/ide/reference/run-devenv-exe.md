---
title: "/Run (devenv.exe) | Microsoft Docs"
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
  - "/r Devenv 开关"
  - "/run Devenv"
  - "应用程序 [Visual Studio], 运行"
  - "Devenv, /run 开关"
  - "r Devenv 开关 (/r)"
  - "运行 Devenv 开关"
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Run (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

编译并运行指定的项目或解决方案。  
  
## 语法  
  
```  
devenv {/run|/r} {SolutionName|ProjectName}  
```  
  
## 参数  
 `SolutionName`  
 必选。  解决方案文件的完整路径和名称。  
  
 `ProjectName`  
 必选。  项目文件的完整路径和名称。  
  
## 备注  
 根据为活动解决方案配置指定的设置，编译并运行指定的项目或解决方案。  此开关启动集成开发环境 \(IDE\) 并在项目或解决方案完成运行后使 IDE 处于活动状态。  
  
-   将包含空格的字符串引在双引号中。  
  
-   摘要信息（包括错误）可以显示在**“命令”**窗口中或显示在使用 `/out` 开关指定的任何日志文件中。  
  
## 示例  
 此示例使用活动部署配置运行 `MySolution` 解决方案。  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"  
```  
  
## 请参阅  
 [Devenv 命令行开关](../../ide/reference/devenv-command-line-switches.md)   
 [\/Runexit](../../ide/reference/runexit-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)