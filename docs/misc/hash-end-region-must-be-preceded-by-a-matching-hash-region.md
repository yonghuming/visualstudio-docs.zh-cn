---
title: "“#End Region”前面必须是匹配的“#Region” | Microsoft Docs"
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
  - "vbc30680"
  - "bc30680"
helpviewer_keywords: 
  - "BC30680"
ms.assetid: 1ea60620-c8dc-4957-8cf4-07b25d20da3b
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “#End Region”前面必须是匹配的“#Region”
当使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 代码编辑器的大纲显示功能时，可使用 `#Region` 指定要展开或折叠的代码块。`#Region` 语句的开始和结束必须在同一个代码块中。  
  
 **错误 ID：**BC30680  
  
### 更正此错误  
  
-   在相应的 `#End` `Region` 语句前的适当位置插入 `#Region`。  
  
## 请参阅  
 [\#Region 指令](/dotnet/visual-basic/language-reference/directives/region-directive)