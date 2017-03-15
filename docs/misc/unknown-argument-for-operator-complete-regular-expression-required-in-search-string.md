---
title: "Unknown argument for &#39;:&#39; operator. Complete Regular Expression required in search string. | Microsoft Docs"
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
  - "vs.message.0x800A00BE"
  - "vs.message.VS_E_RE_SPECIALUNKNOWN"
ms.assetid: 8cbc2f7f-7ea1-4803-904c-1f716cd36376
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Unknown argument for &#39;:&#39; operator. Complete Regular Expression required in search string.
该错误通常发生在查找或替换时在搜索字符串中使用了正则表达式或通配符时。  输入了运算符冒号 \(`:`\)，但之后的参数为无效参数。  
  
> [!NOTE]
>  冒号运算符 \(`:`\) 的参数区分大小写。  
  
### 更正此错误  
  
1.  复查位于主题“正则表达式”中的正确正则表达式语法。  
  
2.  反复检查确保使用参数的正确大小写。  
  
3.  如正在使用输入法编辑器 \(IME\)，确保参数不以全角字符给出。  
  
## 请参阅  
 [在 Visual Studio 中使用正则表达式](../ide/using-regular-expressions-in-visual-studio.md)   
 [NIB: Find and Replace, Quick Find](http://msdn.microsoft.com/zh-cn/dad03582-4931-4893-83ba-84b37f5b1600)   
 [在文件中查找](../ide/find-in-files.md)