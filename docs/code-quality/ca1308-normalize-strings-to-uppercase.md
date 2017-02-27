---
title: "CA1308：将字符串规范化为大写 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1308"
  - "NormalizeStringsToUppercase"
helpviewer_keywords: 
  - "NormalizeStringsToUppercase"
  - "CA1308"
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA1308：将字符串规范化为大写
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|NormalizeStringsToUppercase|  
|CheckId|CA1308|  
|类别|Microsoft.Globalization|  
|是否重大更改|非重大更改|  
  
## 原因  
 某个操作将字符串正常化为小写字母。  
  
## 规则说明  
 字符串应正常化为大写字母。  少量字符转换为小写字母后不能再转换回来。  往返转换即是将字符从一个区域设置转换为另一个表示不同字符数据的区域设置，然后准确地从转换后的字符中检索到原始字符。  
  
## 如何解决冲突  
 更改将字符串转换为小写字母的操作，而将字符串转换为大写字母。  例如，将 `String.ToLower(CultureInfo.InvariantCulture)` 更改为 `String.ToUpper(CultureInfo.InvariantCulture)`。  
  
## 何时禁止显示警告  
 如果不根据结果作出安全决策，则可以安全地禁止显示警告消息（例如，在 UI 中显示警告消息时）。  
  
## 请参阅  
 [全球化警告](../code-quality/globalization-warnings.md)