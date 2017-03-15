---
title: "/Out (devenv.exe) | Microsoft Docs"
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
  - "/out Devenv 开关"
  - "生成 [Visual Studio], 错误"
  - "生成 [Visual Studio], 日志"
  - "Devenv, /out 开关"
  - "错误日志 [Visual Studio]"
  - "错误日志 [Visual Studio], 命令行生成错误"
  - "错误 [Visual Studio], 生成"
  - "out Devenv 开关"
  - "输出文件, 生成错误"
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Out (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定当运行、生成、重新生成或部署解决方案时用于存储和显示错误的文件。  
  
## 语法  
  
```  
devenv /out FileName  
```  
  
## 参数  
 `FileName`  
 必选。  当生成可执行文件时，接收错误的文件的路径和名称。  
  
## 备注  
 如果指定的文件名不存在，则自动创建该文件。  如果文件已经存在，则结果将追加到文件现有内容的结尾处。  
  
 命令行生成错误显示在**“命令”**窗口和**“输出”**窗口的“解决方案生成器”视图中。  当运行无人参与的生成并需要查看结果时，此选项很有用。  
  
## 示例  
 此示例运行 `MySolution` 并将错误写入文件 `MyErrorLog.txt` 中。  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"  
```  
  
## 请参阅  
 [Devenv 命令行开关](../../ide/reference/devenv-command-line-switches.md)   
 [\/Run](../../ide/reference/run-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Deploy](../../ide/reference/deploy-devenv-exe.md)