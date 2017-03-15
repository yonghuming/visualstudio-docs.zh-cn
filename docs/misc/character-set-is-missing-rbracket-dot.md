---
title: "Character set is missing &#39;]&#39;. | Microsoft Docs"
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
  - "vs.message.VS_E_RE_SETMISSINGCLOSE"
  - "vs.message.0x800A00C0"
ms.assetid: 97d2436c-498d-4eb0-a08c-8efcc7797fc0
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Character set is missing &#39;]&#39;.
该错误通常发生在在查找或替换字符串中指定的正则表达式缺少右括号 \(`]`\) 时。  
  
### 更正此错误  
  
1.  若要查找字符 `]`，请使用 `\]`。  
  
2.  若要匹配字符集，请输入缺少的中括号 `]`。  
  
## 请参阅  
 [在 Visual Studio 中使用正则表达式](../ide/using-regular-expressions-in-visual-studio.md)   
 [NIB: Find and Replace, Quick Find](http://msdn.microsoft.com/zh-cn/dad03582-4931-4893-83ba-84b37f5b1600)   
 [在文件中查找](../ide/find-in-files.md)