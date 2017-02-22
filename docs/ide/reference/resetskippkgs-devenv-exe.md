---
title: "/ResetSkipPkgs (devenv.exe) | Microsoft Docs"
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
  - "/ResetSkipPkgs Devenv 开关"
  - "Devenv, /ResetSkipPkgs 开关"
  - "ResetSkipPkgs 开关"
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
caps.latest.revision: 3
caps.handback.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /ResetSkipPkgs (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

清除所有选项，跳过由希望避免加载有问题的 VSPackage 的用户添加到 VSPackage 中的加载，然后启动 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## 语法  
  
```  
Devenv /ResetSkipPkgs  
```  
  
## 备注  
 出现 SkipLoading 标记将禁用加载 VSPackage；清除该标记可重新启用加载 VSPackage。  
  
## 示例  
 下面的示例清除所有 SkipLoading 标记。  
  
```  
Devenv.exe /ResetSkipPkgs  
```  
  
## 请参阅  
 [Devenv 命令行开关](../../ide/reference/devenv-command-line-switches.md)