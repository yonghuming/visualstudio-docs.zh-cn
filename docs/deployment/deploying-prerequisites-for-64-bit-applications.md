---
title: "部署 64 位应用程序的必备组件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "64 位 [Visual Studio]"
  - "64 位应用程序 [Visual Studio]"
  - "64 位编程 [Visual Studio]"
  - "部署应用程序 [Visual Studio], 64 "
ms.assetid: 87399e20-5510-41e4-b5b7-4a87c5773f21
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 部署 64 位应用程序的必备组件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ClickOnce 部署支持 64 位平台上的应用程序安装。  目标平台为**“x86”**（32 位平台）、**“x64”**（支持 AMD64 和 EM64T 指令集的计算机）以及**“Itanium”**（64 位 Itanium 处理器）。  
  
## 先决条件  
 下表列出了可用作 64 位应用程序安装的系统必备组件的可再发行组件。  
  
 如果选择不具有 64 位组件的系统必备组件，则可能会看到一条警告，该警告声明选择的程序包不能用于 64 位平台。  
  
|可再发行组件|x64 支持|IA64 支持|  
|------------|------------|-------------|  
|[!INCLUDE[vsto_runtime](../deployment/includes/vsto_runtime_md.md)]|是|否|  
|Visual C\+\+ 2010 运行库 \(IA64\)|否|是|  
|Visual C\+\+ 2010 运行库 \(x64\)|是|否|  
|Microsoft .NET Framework 4（x86 和 x64）|是||  
|Microsoft .NET Framework 4 Client Profil（x86 和 x64）|是||  
  
## 请参阅  
 [部署应用程序、服务器和组件](../deployment/deploying-applications-services-and-components.md)   
 [如何：与 ClickOnce 应用程序一起安装系统必备组件](../Topic/How%20to:%20Install%20Prerequisites%20with%20a%20ClickOnce%20Application.md)   
 [64 位应用程序](../Topic/64-bit%20Applications.md)