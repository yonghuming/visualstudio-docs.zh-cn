---
title: "如何：指定 ClickOnce 部署的详细日志文件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce 部署, 日志记录"
  - "日志, ClickOnce 部署"
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：指定 ClickOnce 部署的详细日志文件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 为所有部署维护活动日志文件。  这些日志记录有关安装、初始化、更新和卸载 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署的详细信息。  若希望 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 向这些日志文件中写入更详细的信息，请使用注册表编辑器 \(**regedit.exe**\) 指定详细级别。  
  
> [!CAUTION]
>  若注册表编辑器使用不当，可能会导致严重的问题，进而可能要求您重新安装操作系统。  使用注册表编辑器的风险由您自己承担。  
  
 以下过程介绍如何为当前用户的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 日志文件指定详细级别。  若要降低详细级别，请删除此注册表值。  
  
### 指定详细日志文件  
  
1.  打开 **Regedit.exe**。  
  
2.  定位到节点 `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`。  
  
3.  如有必要，可以新建一个字符串值，命名为 `LogVerbosityLevel`。  
  
4.  将 `LogVerbosityLevel` 值设置为 `1`。  
  
## 请参阅  
 [ClickOnce 部署疑难解答](../deployment/troubleshooting-clickonce-deployments.md)