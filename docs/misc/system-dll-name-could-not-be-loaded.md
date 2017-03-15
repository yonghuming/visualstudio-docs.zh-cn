---
title: "System DLL &lt;name&gt; could not be loaded. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VB_E_TERRSYSDLLNOTLOADED"
  - "vs.message.0x800A0085"
ms.assetid: d4ccb3b1-fbc3-4395-a9b1-be50a4d7bf44
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# System DLL &lt;name&gt; could not be loaded.
找不到操作系统提供的 .dll 文件，如 DDEML.DLL、VERSION.DLL 或 WINSPOOL.DRV。  该错误通常发生在下列情况之一为真时：文件不在正确的路径上，DLL 已损坏或删除，或者没有足够的内存。  
  
### 更正此错误  
  
1.  检查确保 DLL 在 Windows 系统路径上。  
  
     \- 或 \-  
  
     重新加载 DLL。  
  
     \- 或 \-  
  
     尝试关闭其他打开的应用程序以释放内存。