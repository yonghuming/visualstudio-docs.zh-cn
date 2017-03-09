---
title: "错误：本地计算机上的防火墙 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.firewall.localmachine"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: ab60dda9-7934-4891-aa2f-001380d2ed83
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 错误：本地计算机上的防火墙
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本地计算机（您从中运行 Visual Studio 的计算机）上的 Internet 连接防火墙未设置为允许进行远程调试。  为了使用默认传输进行托管或本机远程调试，必须为 DCOM 通信打开 TCP 135 端口。  必须打开文件和打印机共享，且必须将 devenv.exe 添加到例外列表。  可能还需要打开某些 IPSEC 端口。  
  
 有关详细信息，请参阅[在设备上安装远程工具](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)。