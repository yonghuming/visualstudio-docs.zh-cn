---
title: "“NotInheritable”类不能将成员声明为“&lt;specifiername&gt;” | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30607"
  - "bc30607"
helpviewer_keywords: 
  - "BC30607"
ms.assetid: c800e24e-d055-402f-b378-6d2f4041ff16
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “NotInheritable”类不能将成员声明为“&lt;specifiername&gt;”
`NotInheritable` 类不能使用重写修饰符，因为其成员不能被重写。  
  
 **错误 ID：**BC30607  
  
### 更正此错误  
  
-   从类定义中删除重写修饰符，如 `Overridable``NotOverridable` 或 `MustOverride`。  
  
## 请参阅  
 [Overridable](/dotnet/visual-basic/language-reference/modifiers/overridable)   
 [NotOverridable](/dotnet/visual-basic/language-reference/modifiers/notoverridable)   
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [不在生成中：重写属性和方法](http://msdn.microsoft.com/zh-cn/2167e8f5-1225-4b13-9ebd-02591ba90213)