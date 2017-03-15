---
title: "错误：远程计算机未能启动 DCOM 通信 | Microsoft Docs"
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
  - "vs.debug.error.unmarshal_callback_failed"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: bbba0766-2502-4ef1-a75d-bf1f0db39e37
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 错误：远程计算机未能启动 DCOM 通信
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

当远程计算机尝试与本地计算机通信时，发生 DCOM 错误。  本地计算机是  
  
 运行 Visual Studio 的计算机。  出现此错误的原因可能有多种：  
  
-   本地计算机启用了防火墙。  
  
-   从远程计算机到本地计算机的 Windows 身份验证不起作用。  
  
### 更正此错误  
  
1.  如果本地计算机已启用 Windows 防火墙，则请参见[在设备上安装远程工具](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)中有关如何针对本地调试配置防火墙的说明。  
  
2.  通过尝试从远程服务器打开本地计算机上的文件共享来测试 Windows 身份验证。  
  
3.  若要还原 Windows 身份验证，请尝试重新启动本地计算机和远程计算机。  检查本地和远程计算机上的事件日志以找出 Kerberos 错误，并与域管理员联系以了解已知问题。  
  
## 请参阅  
 [在设备上安装远程工具](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)