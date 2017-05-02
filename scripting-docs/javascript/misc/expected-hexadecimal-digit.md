---
title: "应为十六进制数字 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT1023"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 应为十六进制数字
您创建一个错误的 Unicode 转义序列。  Unicode 转义序列以 \\u 作为开头，后跟刚好四个十六进制数。  Unicode 十六进制数只能包含数字 0\-9、大写字母 A\-F 和小写字母 a\-f。  下面的示例介绍了格式正确的 Unicode 转义序列。  
  
```javascript  
z = "\u1A5F";  
```  
  
### 更正此错误  
  
-   确保 Unicode 十六进制数以 \\u 开头，只包含数字 0\-9、大写字母 A\-F 和小写字母 a\-f；并且按四个数字进行分组。  
  
    > [!NOTE]
    >  如果要在字符串中使用文本 \\u，请使用两个反斜杠 \(\\\\u\) \- 用于对第一个反斜杠进行转义。  
  
## 请参阅  
 [数据类型](../../javascript/data-types-javascript.md)