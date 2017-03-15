---
title: "Command requires one argument. | Microsoft Docs"
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
  - "vs.message.VS_E_INCORRECTPARAMCOUNT1"
  - "vs.message.0x800A00C3"
ms.assetid: b4d98e6d-6970-42fb-b1de-43f2e952fb9d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Command requires one argument.
该错误通常发生在为命令输入的信息不够或因为使用了不正确的参数组合时。  
  
 例如，如果为 `alias` 命令输入了 `alias` `/delete sample1 sample2`，由于别名 `/delete` 只能接受一个别名而非两个，将发生该错误。  别名不包含空格，因此“查找\/命令”框和“命令”窗口将 `sample1 sample2` 解释为两个不同的别名。  
  
### 更正此错误  
  
1.  在文档中查看该命令的正确语法，然后重试。  
  
## 请参阅  
 [Visual Studio 命令](../ide/reference/visual-studio-commands.md)