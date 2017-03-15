---
title: "Alias definition is recursive. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.0x800A00DA"
  - "vs.message.VS_E_RECURSIVEALIAS"
ms.assetid: e48a2908-9b94-4c6a-9807-beeeba71531c
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Alias definition is recursive.
该错误通常发生在定义了直接或间接引用其本身的别名时。  
  
### 更正此错误  
  
1.  更改别名的定义并重试。  
  
     \- 或 \-  
  
2.  通过在“命令”窗口中输入 `>alias` 复查别名的当前列表及其定义，然后重试。  
  
## 请参阅  
 [“别名”命令](../ide/reference/alias-command.md)   
 [Visual Studio 命令别名](../ide/reference/visual-studio-command-aliases.md)