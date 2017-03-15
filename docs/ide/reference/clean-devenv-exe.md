---
title: "/Clean (devenv.exe) | Microsoft Docs"
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
  - "/clean Devenv 开关"
  - "生成 [Team System], 清理文件"
  - "清理 Devenv 开关"
  - "Devenv, /clean 开关"
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Clean (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

清理所有中间文件和输出目录。  
  
## 语法  
  
```  
devenv FileName /Clean [ /project projectnameorfile [/projectconfig name ] ]  
```  
  
## 参数  
 `FileName`  
 必选。  解决方案或模板项目文件的完整路径和名称。  
  
 \/project `ProjName`  
 可选。  解决方案内的一个项目文件的路径和名称。  可以输入从 `SolutionName` 文件夹到项目文件的相对路径、项目的显示名称或项目文件的完整路径和名称。  
  
 \/projectconfig `ProjConfigName`  
 可选。  在清理命名的 `/project` 时要使用的项目生成配置的名称。  
  
## 备注  
 此开关将同一个函数作为集成开发环境 \(IDE\) 中的**“清理解决方案”**菜单命令来执行。  
  
 将包含空格的字符串引在双引号中。  
  
 清理和生成的摘要信息（包括错误）可以显示在**“命令”**窗口中或显示在使用 `/out` 开关指定的任何日志文件中。  
  
## 示例  
 第一个示例使用解决方案中指定的默认配置，清理 `MySolution` 解决方案。  
  
 第二个示例使用 `MySolution` 的 `Debug` 解决方案配置中的 `Debug` 项目生成配置来清理项目 `CSharpConsoleApp`。  
  
```  
Devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean  
  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"   
```  
  
## 请参阅  
 [Devenv 命令行开关](../../ide/reference/devenv-command-line-switches.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)