---
title: "Option is not currently valid. | Microsoft Docs"
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
  - "vs.message.VS_E_INVALIDOPTION"
  - "vs.message.0x800a00e8"
ms.assetid: b31dc056-0f1f-4eaf-bb8d-3c08b94cd55a
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Option is not currently valid.
当为命令指定的参数或开关当前不可用时，通常会发生此错误。  例如，如果输入 `>Edit.Find test /sel` 而未在文件中选定内容，则 \/sel 开关不可用。  
  
### 更正此错误  
  
1.  验证输入的参数和开关当前是可用的。  有关更多信息，请参见[带参数的 Visual Studio 命令](../ide/reference/visual-studio-commands.md)。  
  
## 请参阅  
 [Visual Studio 命令](../ide/reference/visual-studio-commands.md)