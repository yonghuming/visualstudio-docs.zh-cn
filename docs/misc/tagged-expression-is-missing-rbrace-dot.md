---
title: "Tagged expression is missing &#39;}&#39;. | Microsoft Docs"
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
  - "vs.message.VS_E_RE_TAGMISSINGCLOSE"
  - "vs.message.0x800A00D6"
ms.assetid: 832905d3-0faa-43c8-9c37-37130e66e6d2
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Tagged expression is missing &#39;}&#39;.
该错误通常发生在在查找字符串中指定了左大括号 \(`{`\) 却遗漏了右大括号 \(`}`\) 时。  
  
### 更正此错误  
  
1.  若要搜索原义字符 `{`，请使用 `\{`。  
  
2.  若要标记表达式，请输入遗漏的 `}`。  
  
## 请参阅  
 [在 Visual Studio 中使用正则表达式](../ide/using-regular-expressions-in-visual-studio.md)   
 [NIB: Find and Replace, Quick Find](http://msdn.microsoft.com/zh-cn/dad03582-4931-4893-83ba-84b37f5b1600)   
 [在文件中查找](../ide/find-in-files.md)