---
title: "Command &lt;name&gt; is not available. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_DISABLEDCOMMAND"
  - "vs.message.0x800A00A6"
ms.assetid: 22d6033f-e00a-4479-9a62-025dd781ed34
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Command &lt;name&gt; is not available.
此错误通常发生在在**“命令”**窗口或**“查找\/命令”**框中输入了一个在 Visual Studio 的当前状态下为无效的命令时。  例如，如果 Visual Studio 中当前没有打开的解决方案，则 `File.CloseSolution`  命令将无效。  
  
### 更正此错误  
  
1.  选择一个不同的命令。  
  
     \- 或 \-  
  
     为要操作的命令选定不同的内容。  
  
## 请参阅  
 [“命令”窗口](../ide/reference/command-window.md)