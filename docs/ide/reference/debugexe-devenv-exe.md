---
title: "/DebugExe (devenv.exe) | Microsoft Docs"
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
  - "/DebugExe [devenv.exe]"
  - "DebugExe 开关"
  - "Devenv, /DebugExe 开关"
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /DebugExe (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

打开要调试的指定可执行文件。  
  
## 语法  
  
```  
Devenv /debugexe ExecutableFile  
```  
  
## 参数  
 `ExecutableFile`  
 必选。  .exe 文件的路径和文件名。  
  
 如果未找到 .exe 文件或该文件不存在，则不显示警告或错误，并且 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 将正常启动。  
  
## 备注  
 将 `ExecutableFile` 参数之后的所有字符串作为参数传递给该文件。  
  
## 示例  
 下面的示例打开 `MyApplication.exe` 文件以进行调试。  
  
```  
Devenv.exe /debugexe MyApplication.exe  
```  
  
## 请参阅  
 [Devenv 命令行开关](../../ide/reference/devenv-command-line-switches.md)