---
title: "如何：为 ClickOnce 部署错误设置一个自定义日志文件位置 | Microsoft Docs"
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
  - "ClickOnce 部署, 错误记录"
  - "ClickOnce 部署, 疑难解答"
  - "ClickOnce 部署疑难解答"
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：为 ClickOnce 部署错误设置一个自定义日志文件位置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 为所有部署维护激活日志文件。  这些日志记录与安装和初始化 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署有关的任何错误。  默认情况下，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 将为每个部署激活创建一个日志文件。  它会将这些日志文件存储在“Temporary Internet Files”文件夹中。  在出现激活失败且用户单击产生的错误对话框中的**“详细信息”**时，会向用户显示部署的日志文件。  
  
 可以通过使用注册表编辑器 \(**regedit.exe**\) 设置一个自定义日志文件路径来更改特定客户端的这一行为。  在这种情况下，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 将在一个文件中记录所有部署的激活成功和激活失败信息。  
  
> [!CAUTION]
>  错误地使用注册表编辑器可导致严重问题（可能需要重新安装操作系统）。  使用注册表编辑器的风险由您自己承担。  
  
> [!NOTE]
>  有时需要截断或删除日志文件，以防止其变得过大。  
  
 下面的过程描述如何为单个客户端设置自定义日志文件位置。  
  
### 设置自定义日志文件位置  
  
1.  打开 **Regedit.exe**。  
  
2.  定位到节点 `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`。  
  
3.  将字符串值 `LogFilePath` 设置为所需的自定义日志位置的完整路径和文件名。  
  
     该位置必须位于用户拥有写入访问权限的目录中。  例如，在 Windows Vista 上，创建下面的文件夹结构，并将 `LogFilePath` 设置为 C:\\Users\\\<username\>\\Documents\\Logs\\ClickOnce\\installation.log。  
  
## 请参阅  
 [ClickOnce 部署疑难解答](../deployment/troubleshooting-clickonce-deployments.md)