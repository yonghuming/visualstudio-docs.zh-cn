---
title: "“AddHandler”和“RemoveHandler”方法参数不能声明为“ByRef” | Microsoft Docs"
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
  - "vbc31134"
  - "bc31134"
helpviewer_keywords: 
  - "BC31134"
ms.assetid: 942f0b91-e71a-499a-ad10-a5dfcb4e72b1
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “AddHandler”和“RemoveHandler”方法参数不能声明为“ByRef”
不能使用 `ByRef` 修饰符声明 `AddHandler` 和 `RemoveHandler` 方法的参数。  
  
 **错误 ID：**BC31134  
  
### 更正此错误  
  
-   从参数中删除 `ByRef` 关键字。  
  
## 请参阅  
 [Event 语句](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler \- delete](http://msdn.microsoft.com/zh-cn/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- delete](http://msdn.microsoft.com/zh-cn/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [ByRef](/dotnet/visual-basic/language-reference/modifiers/byref)   
 [事件](/dotnet/visual-basic/programming-guide/language-features/events/events)