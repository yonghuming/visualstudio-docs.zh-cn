---
title: "“AddHandler”和“RemoveHandler”方法参数必须与包含事件具有相同的委托类型。 | Microsoft Docs"
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
  - "bc31136"
  - "vbc31136"
helpviewer_keywords: 
  - "BC31136"
ms.assetid: 199b2f7b-a85e-465d-9853-0995156e7ab6
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “AddHandler”和“RemoveHandler”方法参数必须与包含事件具有相同的委托类型。
`Custom Event` 声明必须具有 `AddHandler` 或 `RemoveHandler` 声明，其中每个采用由自定义事件的 `As` 子句所指定的委托类型的单个参数。  
  
 **错误 ID：**BC31136  
  
### 更正此错误  
  
-   将参数的类型改为与自定义事件的 `As` 子句所指定的委托类型相同的类型。  
  
## 示例  
 此示例演示针对 `AddHandler` 和 `RemoveHandler` 声明的具有正确的参数类型的自定义事件。  
  
 [!CODE [VbVbalrEventError#1](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrEventError#1)]  
  
## 请参阅  
 [Event 语句](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler \- delete](http://msdn.microsoft.com/zh-cn/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- delete](http://msdn.microsoft.com/zh-cn/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [事件](/dotnet/visual-basic/programming-guide/language-features/events/events)