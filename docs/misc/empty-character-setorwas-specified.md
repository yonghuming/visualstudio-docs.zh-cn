---
title: "已指定空字符集或。 | Microsoft Docs"
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
  - "vs.message.VS_E_RE_EMPTYSET"
  - "vs.message.0x800A00DF"
ms.assetid: 27ed2ebe-a492-4bc9-ab33-a09fba6cf1d3
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 已指定空字符集或。
当选择正则表达式选项，但为模式“字符集 \[\]”或“不在集合中的字符 \[^\]”指定包含不完整语法的字符串时，通常会发生此错误。  例如 `[}`。  
  
### 更正此错误  
  
1.  查看“正则表达式”主题以获得关于该模式的正确语法的信息，然后重新输入字符串。  
  
## 请参阅  
 [在 Visual Studio 中使用正则表达式](../ide/using-regular-expressions-in-visual-studio.md)   
 [NIB: Find and Replace, Quick Find](http://msdn.microsoft.com/zh-cn/dad03582-4931-4893-83ba-84b37f5b1600)   
 [在文件中查找](../ide/find-in-files.md)   
 [查找和替换文本](../ide/finding-and-replacing-text.md)