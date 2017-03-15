---
title: "/SafeMode (devenv.exe) | Microsoft Docs"
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
  - "/SafeMode Devenv 开关"
  - "Devenv, /SafeMode 开关"
  - "SafeMode 开关"
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /SafeMode (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

以安全模式启动 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，将仅加载默认的环境和服务。  
  
## 语法  
  
```  
devenv /SafeMode   
```  
  
## 备注  
 此开关可阻止在启动 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 时加载所有第三方 VSPackage，因此可确保稳定执行。  
  
## 说明  
 下面的示例以安全模式启动 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## 代码  
  
```  
Devenv.exe /SafeMode  
```  
  
## 请参阅  
 [Devenv 命令行开关](../../ide/reference/devenv-command-line-switches.md)