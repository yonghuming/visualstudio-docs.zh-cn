---
title: "错误: 无法连接到计算机 &lt;name&gt;。无法在网络上找到该计算机。 | Microsoft Docs"
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
  - "vs.debug.remote.dcom_disabled"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "DCOM, 无法连接错误"
ms.assetid: b584b5db-ef52-45ed-8561-1314da3cc5b8
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 错误: 无法连接到计算机 &lt;name&gt;。无法在网络上找到该计算机。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果满足下列某项条件，则会发生此行为：  
  
-   您与远程计算机的连接中断。  
  
-   您在远程计算机上的用户帐户被禁用。  
  
-   您在远程计算机上的密码过期。  
  
### 解决此问题  
  
-   确保本地计算机和远程计算机处于同一个网络中。  若要执行此操作，请使用 Microsoft Windows 资源管理器（或文件资源管理器）尝试访问远程计算机。  
  
     \- 和 \-  
  
-   确保您用来连接远程计算机的用户帐户是启用的。  
  
     \- 和 \-  
  
-   确保您用来连接远程计算机的密码是有效的并且尚未过期。  
  
## 请参阅  
 [在设备上安装远程工具](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)   
 [调试设置和准备](../debugger/debugger-settings-and-preparation.md)