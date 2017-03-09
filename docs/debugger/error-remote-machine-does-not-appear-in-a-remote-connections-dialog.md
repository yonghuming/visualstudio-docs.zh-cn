---
title: "错误：远程计算机未显示在“远程连接”对话框中 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 5fd98a5b-2cf3-4438-8b0f-6f1a742a62ce
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 错误：远程计算机未显示在“远程连接”对话框中
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果远程计算机未显示在“远程连接”对话框中，请检查以下常见原因。  
  
 如果你使用托管的兼容模式，请检查的 Visual Studio 2010 文档：[远程调试疑难解答 \- Visual Studio 2010](https://msdn.microsoft.com/en-us/library/2ys11ead\(v=vs.100\).aspx)。  
  
### 导致此错误的常见原因  
  
-   远程计算机正在位于不同子网中的计算机上运行。 若要解决此问题，在限定符对话框中手动键入计算机名称或 IP 地址  
  
-   远程调试器未在远程计算机上运行。 若要解决此问题，启动远程调试器。  
  
-   防火墙正在阻止 Visual Studio 和远程计算机之间的通信。 若要解决此问题，请将防火墙配置为允许 Visual Studio 和远程调试器 \(msvsmon\) 进行通信。  
  
-   防病毒软件正在阻止 Visual Studio 和远程计算机之间的通信。 若要解决此问题，请将防病毒软件配置为允许 Visual Studio 和远程调试器 \(msvsmon\) 进行通信。  
  
## 请参阅  
 [在设备上安装远程工具](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)