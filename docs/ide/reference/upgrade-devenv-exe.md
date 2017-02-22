---
title: "/Upgrade (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/upgrade Devenv 开关"
  - "Devenv, /upgrade 开关"
  - "升级 Devenv 开关"
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
caps.latest.revision: 18
caps.handback.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Upgrade (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

将解决方案文件及其所有项目文件或指定的项目文件更新为这些文件的当前 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 格式。  
  
## 语法  
  
```  
devenv SolutionFile | ProjectFile /upgrade  
```  
  
## 实参  
 `SolutionFile`  
 如果您升级整个解决方案及其项目，则是必需的。  解决方案文件的路径和名称。  可以只输入解决方案文件的名称，也可以输入解决方案文件的完整路径和名称。  如果命名的文件夹或文件尚不存在，将创建该文件夹或文件。  
  
 `ProjectFile`  
 如果升级单个项目，则是必需的。  解决方案内的一个项目文件的路径和名称。  可以只输入项目文件的名称，也可以输入项目文件的完整路径和名称。  如果命名的文件夹或文件尚不存在，将创建该文件夹或文件。  
  
## 备注  
 备份文件自动创建并复制到一个名为 Backup 的目录中，该目录是在当前目录中创建的。  
  
 要升级源代码控制的解决方案或项目，必须先将其签出。  
  
 使用 `/upgrade` 开关不会启动 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  可以在解决方案或项目的开发语言的升级报告中看到升级结果。  将不返回任何错误或用法信息。  有关在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 中升级项目的更多信息，请参见 [如何：升级 Visual Studio 项目失败疑难解答](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)。  
  
## 示例  
 此示例升级 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 解决方案的默认文件夹中名为“MyProject.sln”的解决方案文件。  
  
```  
devenv "MyProject.sln" /upgrade  
```  
  
## 请参阅  
 [如何：升级 Visual Studio 项目失败疑难解答](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)   
 [Devenv 命令行开关](../../ide/reference/devenv-command-line-switches.md)