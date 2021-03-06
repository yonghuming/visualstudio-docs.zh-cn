---
title: "泛型方法不能使用“Handles”子句。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32080"
  - "BC32080"
helpviewer_keywords: 
  - "BC32080"
ms.assetid: 88c62a1c-aee3-46b2-ad78-76790022c04c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 泛型方法不能使用“Handles”子句。
泛型 `Sub` 过程的声明中包含 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause) 子句。  
  
 `Handles` 子句指定 `Sub` 过程处理的事件列表。 若要成为事件处理程序，`Sub` 过程必须与其将要处理的每一个事件具有相同的签名。 可以使用 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 在编译时无法预测的签名多次创建泛型过程。 因此，[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 不能保证签名与 `Handles` 子句中事件的签名匹配。  
  
 **错误 ID：**BC32080  
  
### 更正此错误  
  
-   如果 `Sub` 过程需要为泛型，请从其声明中删除 `Handles` 子句。 使用 [AddHandler 语句](/dotnet/visual-basic/language-reference/statements/addhandler-statement)将此事件处理程序与事件关联。  
  
-   如果 `Sub` 过程需要使用 `Handles` 子句来关联事件，则从其声明中删除 [Of](/dotnet/visual-basic/language-reference/statements/of-clause) 子句。`Handles` 必须与非泛型过程一起使用。  
  
## 请参阅  
 [Visual Basic 中的泛型类型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [不在生成中：事件和事件处理程序](http://msdn.microsoft.com/zh-cn/95074a0d-1cbc-4221-a95a-964185c7f962)