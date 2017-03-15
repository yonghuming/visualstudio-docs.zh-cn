---
title: "Argument is missing in &#39;\&#39; escape sequence. | Microsoft Docs"
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
  - "vs.message.VS_E_RE_ESCAPEMISSINGARG"
  - "vs.message.0x800A00BD"
ms.assetid: 5bd6559b-8cd9-450f-91c8-335ff1b1ef86
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Argument is missing in &#39;\&#39; escape sequence.
该错误通常发生在查找或替换时在搜索字符串中使用了正则表达式或通配符时。  该错误可能由模式末尾的单反斜杠 \(`\`\) 或输入 `\x` 或 `\u` 时未带有效的十六进制 Unicode 字符所致。  
  
### 更正此错误  
  
1.  若要用正则表达式转义符搜索，请输入 `\`。  
  
2.  若要搜索 unicode 字符，请输入后面为有效 Unicode 值的 `\x` 或 `\u`。  
  
3.  若要搜索双反斜杠，请使用 `\\`。  
  
## 请参阅  
 [在 Visual Studio 中使用正则表达式](../ide/using-regular-expressions-in-visual-studio.md)   
 [NIB: Find and Replace, Quick Find](http://msdn.microsoft.com/zh-cn/dad03582-4931-4893-83ba-84b37f5b1600)   
 [在文件中查找](../ide/find-in-files.md)