---
title: "/Deploy (devenv.exe) | Microsoft Docs"
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
  - "/deploy Devenv 开关"
  - "部署 Devenv 开关"
  - "部署应用程序 [Visual Studio], 生成后"
  - "Devenv, /deploy 开关"
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Deploy (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

生成或重新生成后部署解决方案。  仅适用于托管代码项目。  
  
## 语法  
  
```  
devenv SolutionName /deploy SolnConfigName [/project ProjName] [/projectconfig ProjConfigName] [/out LogFileName]  
```  
  
## 参数  
 `SolnConfigName`  
 必选。  用于生成在 `SolutionName` 中命名的解决方案的解决方案配置名称。  
  
 `SolutionName`  
 必选。  解决方案文件的完整路径和名称。  
  
 \/project `ProjName`  
 可选。  解决方案内的一个项目文件的路径和名称。  可以输入从 `SolutionName` 文件夹到项目文件的相对路径、项目的显示名称或项目文件的完整路径和名称。  
  
 \/projectconfig `ProjConfigName`  
 可选。  在重新生成命名的 `/project` 时要使用的项目生成配置的名称。  
  
## 备注  
 指定的项目必须是部署项目。  如果指定的项目不是部署项目，则当部署传递来的已生成项目时，会因错误而失败。  
  
 将包含空格的字符串引在双引号中。  
  
 生成的摘要信息（包括错误）可以显示在**“命令”**窗口中或显示在使用 `/out` 开关指定的任何日志文件中。  
  
## 示例  
 此示例使用 `MySolution` 的 `Release` 解决方案配置中的 `Release` 项目生成配置来部署项目 `CSharpConsoleApp`。  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release   
```  
  
## 请参阅  
 [Devenv 命令行开关](../../ide/reference/devenv-command-line-switches.md)   
 [\/Project](../../ide/reference/project-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Clean](../../ide/reference/clean-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)