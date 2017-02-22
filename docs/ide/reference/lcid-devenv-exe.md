---
title: "/LCID (devenv.exe) | Microsoft Docs"
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
  - "/l Devenv 开关"
  - "/lcid Devenv 开关"
  - "Devenv, /LCID 开关"
  - "语言默认设置"
  - "LCID devenv 开关"
  - "区域设置 ID"
  - "区域设置 ID, IDE 设置"
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /LCID (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

设置在集成开发环境 \(IDE\) 内文本、货币和其他值使用的默认语言。  
  
## 语法  
  
```  
devenv {/LCID|/l} LocaleID  
```  
  
## 参数  
 `LocaleID`  
 必选。  所指定语言的 LCID（区域设置 ID）。  
  
## 备注  
 加载 IDE 并设置环境的默认自然语言。  此更改在会话之间保持不变，并反映在 IDE 内**“选项”**对话框中**“环境”**选项的**“区域设置”**窗格上。  
  
 如果指定的语言在用户的系统上不可用，则 \/LCID 开关将被忽略。  
  
 下表列出 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 支持的语言的 LCID。  
  
|Language|LCID|  
|--------------|----------|  
|中文\(简体\)|2052|  
|中文\(繁体\)|1028|  
|英语|1033|  
|法语|1036|  
|德语|1031|  
|意大利语|1040|  
|日语|1041|  
|朝鲜语|1042|  
|西班牙语|3082|  
  
## 示例  
 此示例加载带有英语资源字符串的 IDE。  
  
```  
devenv /LCID 1033  
```  
  
## 请参阅  
 [Devenv 命令行开关](../../ide/reference/devenv-command-line-switches.md)   
 [“选项”对话框 \-\>“环境”\-\>“区域设置”](../../ide/reference/international-settings-environment-options-dialog-box.md)   
 [自定义窗口布局](../../ide/customizing-window-layouts-in-visual-studio.md)