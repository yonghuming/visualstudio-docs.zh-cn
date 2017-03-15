---
title: "The selected Add-In has not been confirmed to be &#39;Command Line Safe&#39;, and may require some user intervention (possible UI). | Microsoft Docs"
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
  - "vs.message.0x800A0031"
  - "vs.message.VB_E_IDWADDINCMDLINE"
ms.assetid: 19dd24d4-b0f5-4c92-9005-aad48ffda7d9
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The selected Add-In has not been confirmed to be &#39;Command Line Safe&#39;, and may require some user intervention (possible UI).
如果选择从命令提示（DOS 提示）处使用外接程序，但该外接程序未将本身列为对命令行是安全的，则通常会发生此错误。  该外接程序可能会显示干扰命令行使用的 UI。  
  
### 更正此错误  
  
1.  从**工具**菜单中选择**外接程序管理器**。  
  
2.  在**外接程序管理器**对话框中，清除该外接程序的**命令行**。  
  
## 请参阅  
 [如何：使用外接程序管理器控制外接程序](../Topic/How%20to:%20Control%20Add-Ins%20By%20Using%20the%20Add-In%20Manager.md)   
 [如何：创建外接程序](../Topic/How%20to:%20Create%20an%20Add-In.md)