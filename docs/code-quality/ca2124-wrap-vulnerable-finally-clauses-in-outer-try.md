---
title: "CA2124：在外部 try 块中包装易受攻击的 finally 子句 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2124"
  - "WrapVulnerableFinallyClausesInOuterTry"
helpviewer_keywords: 
  - "CA2124"
  - "WrapVulnerableFinallyClausesInOuterTry"
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2124：在外部 try 块中包装易受攻击的 finally 子句
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|WrapVulnerableFinallyClausesInOuterTry|  
|CheckId|CA2124|  
|类别|Microsoft.Security|  
|是否重大更改|否|  
  
## 原因  
 在 1.0 和 1.1 版的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 中，公共或受保护的方法包含 `try`\/`catch`\/`finally` 数据块。  该 `finally` 块似乎要重置安全性状态，并且没有包括在 `finally` 块中。  
  
## 规则说明  
 此规则定位面向 1.0 和 1.1 版的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 的代码中的 `try`\/`finally` 块，这些块可能容易被调用堆栈中出现的恶意异常筛选器攻击。  如果敏感操作（如模拟）出现在 try 块中，将引发异常，筛选器可以在 `finally` 块之前执行。  对于模拟示例，这意味着筛选器将作为被模拟用户执行。  筛选器当前只能在 Visual Basic 中实现。  
  
> [!WARNING]
>  **注意：**在 2.0 版及更高版本的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 中，如果重置直接发生在包含异常数据块的方法内，运行时会自动保护 `try`\/`catch`\/ `finally` 数据块免遭恶意的异常筛选器攻击。  
  
## 如何解决冲突  
 将未包装的 `try`\/`finally` 放入外部 try 块中。  请参见后面的第二个示例。  这将强制 `finally` 在筛选器代码之前执行。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 伪代码示例  
  
### 说明  
 下面的伪代码演示该规则检测的模式。  
  
### 代码  
  
```  
try {  
   // Do some work.  
   Impersonator imp = new Impersonator("John Doe");  
   imp.AddToCreditCardBalance(100);  
}  
finally {  
   // Reset security state.  
   imp.Revert();  
}  
```  
  
## 示例  
 下面的伪代码演示可以用来保护代码并满足该规则的模式。  
  
```  
try {  
     try {  
        // Do some work.  
     }  
     finally {  
        // Reset security state.  
     }  
}  
catch()  
{  
    throw;  
}  
```