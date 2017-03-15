---
title: "/Project (devenv.exe) | Microsoft Docs"
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
  - "/project Devenv 开关"
  - "部署项目, 指定"
  - "Devenv, /project 开关"
  - "项目 Devenv 开关 (/project)"
  - "项目 [Visual Studio], 生成"
  - "项目 [Visual Studio], 清除"
  - "项目 [Visual Studio], 重新生成"
ms.assetid: 8b07859c-3439-436d-9b9a-a8ee744eee30
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Project (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

标识在指定的解决方案配置中要生成、清理、重新生成或部署的单个项目。  
  
## 语法  
  
```  
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName   
[/project ProjName] [/projectconfig ProjConfigName]   
```  
  
## 参数  
 \/build  
 生成 `/project` `ProjName` 指定的项目。  
  
 \/clean  
 清理在生成过程中创建的所有中间文件和输出目录。  
  
 \/rebuild  
 清理，然后生成 `/project` `ProjName` 指定的项目。  
  
 \/deploy  
 指定生成或重新生成后部署该项目。  
  
 `SolnConfigName`  
 必选。  将应用于在 `SolutionName` 中命名的解决方案的解决方案配置名称。  
  
 `SolutionName`  
 必选。  解决方案文件的完整路径和名称。  
  
 \/project `ProjName`  
 可选。  解决方案内的一个项目文件的路径和名称。  可以输入从 `SolutionName` 文件夹到项目文件的相对路径、项目的显示名称或项目文件的完整路径和名称。  
  
 \/projectconfig `ProjConfigName`  
 可选。  要应用于命名的 `/project` 的项目生成配置的名称。  
  
## 备注  
  
-   必须作为 `devenv /build`、\/`clean`、`/rebuild` 或 `/deploy` 命令的一部分使用。  
  
-   将包含空格的字符串引在双引号中。  
  
-   生成的摘要信息（包括错误）可以显示在**“命令”**窗口中或显示在使用 `/out` 开关指定的任何日志文件中。  
  
## 示例  
 此示例使用 `MySolution` 的 `Debug` 解决方案配置中的 `Debug` 项目生成配置来生成项目 `CSharpConsoleApp`。  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## 请参阅  
 [Devenv 命令行开关](../../ide/reference/devenv-command-line-switches.md)   
 [\/ProjectConfig](../../ide/reference/projectconfig-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Clean](../../ide/reference/clean-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Deploy](../../ide/reference/deploy-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)