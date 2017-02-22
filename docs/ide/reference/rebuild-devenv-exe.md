---
title: "/Rebuild (devenv.exe) | Microsoft Docs"
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
  - "/rebuild Devenv 开关"
  - "应用程序 [Visual Studio], 重新生成"
  - "Devenv, /rebuild 开关"
  - "项目 [Visual Studio], 重新生成"
  - "重新生成 Devenv 开关 (/rebuild)"
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Rebuild (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

清理，然后生成指定的解决方案配置。  
  
## 语法  
  
```  
devenv SolutionName /rebuild SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]  
```  
  
## 参数  
 `SolnConfigName`  
 必需。  用于重新生成在 `SolutionName` 中命名的解决方案的解决方案配置名称。  
  
 `SolutionName`  
 必需。  解决方案文件的完整路径和名称。  
  
 \/project `ProjName`  
 可选。  解决方案内的一个项目文件的路径和名称。  可以输入从 `SolutionName` 文件夹到项目文件的相对路径、项目的显示名称或项目文件的完整路径和名称。  
  
 \/projectconfig `ProjConfigName`  
 可选。  在重新生成命名的 `/project` 时要使用的项目生成配置的名称。  
  
## 备注  
  
-   此开关将同一个函数作为集成开发环境 \(IDE\) 中的**“重新生成解决方案”**菜单命令来执行。  
  
-   将包含空格的字符串引在双引号中。  
  
-   清理和生成的摘要信息（包括错误）可以显示在**“命令”**窗口中或显示在使用 `/out` 开关指定的任何日志文件中。  
  
## 示例  
 此示例使用 `MySolution` 的 `Debug` 解决方案配置中的 `Debug` 项目生成配置来清理和重新生成项目 `CSharpWinApp`。  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## 请参阅  
 [Devenv 命令行开关](../../ide/reference/devenv-command-line-switches.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Clean](../../ide/reference/clean-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)