---
title: "/Edit (devenv.exe) | Microsoft Docs"
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
  - "/Edit Devenv 开关"
  - "Devenv, /edit 开关"
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Edit (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的现有实例中打开指定的文件。  
  
## 语法  
  
```  
Devenv /edit [file1[ file2]]  
```  
  
## 参数  
 `file1`  
 可选。  要在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的现有实例中打开的文件。  如果 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的实例不存在，则系统将创建一个具有简化的窗口布局的新实例，并在新实例中打开 `file1`。  
  
 `file2`  
 可选。  要在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的现有实例中打开的一个或多个其他文件。  
  
## 备注  
 如果没有指定文件且存在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的现有实例，则 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的现有实例接收焦点。  如果没有指定文件且不存在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的现有实例，则系统将创建一个具有简化窗口布局的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 新实例。  
  
 如果 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的现有实例处于模式状态（例如，[“选项”对话框](../../ide/reference/options-dialog-box-visual-studio.md)已打开），则在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 退出模式状态后，文件将在现有实例中打开。  
  
## 示例  
 以下示例在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的现有实例中打开文件 `MyFile.cs`，如果不存在现有实例，则在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的新实例中打开文件。  
  
```  
devenv /edit MyFile.cs  
```  
  
## 请参阅  
 [Devenv 命令行开关](../../ide/reference/devenv-command-line-switches.md)