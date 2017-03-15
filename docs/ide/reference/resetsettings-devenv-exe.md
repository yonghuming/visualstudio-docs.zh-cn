---
title: "/ResetSettings (devenv.exe) | Microsoft Docs"
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
  - "/ResetSettings Devenv 开关"
  - "Devenv, /ResetSettings 开关"
  - "ResetSettings 开关"
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /ResetSettings (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

还原 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 默认设置和自动生成 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE。  可以选择将这些设置重置为指定的 .vssettings 文件。  
  
 默认设置取决于 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 首次生成时选择的配置文件。  
  
## 语法  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## 实参  
 `SettingsFile`  
 要应用于 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的 .vssettings 文件的完整路径和名称。  
  
 若要还原常规开发设置分析，请使用 `General`。  
  
## 备注  
 如果未指定 `SettingsFile`，则会提示您选择下一次启动 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 时的设置的默认集合。  
  
## 示例  
 以下命令行应用存储在 `MySettings.vssettings` 文件中的设置。  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## 请参阅  
 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Devenv 命令行开关](../../ide/reference/devenv-command-line-switches.md)