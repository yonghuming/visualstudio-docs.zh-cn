---
title: "&lt;name&gt; is not a valid project name. | Microsoft Docs"
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
  - "vs.message.VS_E_INVALIDPROJECTNAME"
  - "vs.message.0x800A00D2"
ms.assetid: 2e8f3e58-f5f0-4f12-bae9-3acc58c0dca6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# &lt;name&gt; is not a valid project name.
该错误通常发生在从**命令**窗口或**查找\/命令**框发出 `File.NewProject` 命令，而为 *projectname* 输入的项目名不正确时。  
  
### 更正此错误  
  
1.  验证确保项目名不包含多余空格并且不是保留字，如 NUL、CON 或 AUX。  
  
     \- 或 \-  
  
     重新键入命令并省略项目名。  
  
## 请参阅  
 [“命令”窗口](../ide/reference/command-window.md)