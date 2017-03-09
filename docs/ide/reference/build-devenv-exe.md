---
title: -Build (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- builds [Team System], command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
caps.latest.revision: 15
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: b87c3eb43cd36154f7cbe75cc02c103fe63bc340
ms.lasthandoff: 02/22/2017

---
# <a name="build-devenvexe"></a>/Build (devenv.exe)
使用指定解决方案配置文件生成解决方案。  
  
## <a name="syntax"></a>语法  
  
```  
Devenv SolutionName /build SolnConfigName [/project ProjName [/projectconfig ProjConfigName]]  
```  
  
## <a name="arguments"></a>参数  
 `SolutionName`  
 必需。 解决方案文件的完整路径和名称。  
  
 `SolnConfigName`  
 必需。 `SolutionName` 中指定了将用于生成解决方案的解决方案配置的名称。  
  
 /project `ProjName`  
 可选。 解决方案中项目文件的路径和名称。 可以输入从 `SolutionName` 文件夹到项目文件的相对路径、项目的显示名称或项目文件的完整路径和名称。  
  
 /projectconfig `ProjConfigName`  
 可选。 指定了生成命名的 `/project` 时要使用的项目生成配置的名称。  
  
## <a name="remarks"></a>备注  
 在集成开发环境 (IDE) 中，此开关执行与**生成解决方案**菜单命令相同的功能。  
  
 用双引号将含有空格的字符串引起来。  
  
 “命令”窗口或使用 `/out` 开关指定的任何日志文件中都可显示生成的摘要信息（包括错误）。  
  
 此命令仅生成自上次生成后已更改的项目。 若要生成解决方案中的所有项目，请使用[/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)。  
  
## <a name="example"></a>示例  
 本示例使用 `MySolution` 的 `Debug` 解决方案配置中的 `Debug` 项目生成配置来生成 `CSharpConsoleApp` 项目。  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## <a name="see-also"></a>另请参阅  
 [在 Visual Studio 中生成和清理项目和解决方案](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Devenv 命令行开关](../../ide/reference/devenv-command-line-switches.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
