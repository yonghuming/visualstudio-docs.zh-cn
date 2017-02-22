---
title: "CA1700：不要命名“Reserved”枚举值 | Microsoft Docs"
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
  - "CA1700"
  - "DoNotNameEnumValuesReserved"
helpviewer_keywords: 
  - "DoNotNameEnumValuesReserved"
  - "CA1700"
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1700：不要命名“Reserved”枚举值
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DoNotNameEnumValuesReserved|  
|CheckId|CA1700|  
|类别|Microsoft.Naming|  
|是否重大更改|是|  
  
## 原因  
 枚举成员的名称包含单词“reserved”。  
  
## 规则说明  
 此规则假定当前不使用名称中包含“reserved”的枚举成员，而是将其作为一个占位符，以在将来的版本中重命名或移除它。  重命名或移除成员是一项重大更改。  您不应指望用户只因为成员名称包含“reserved”就会忽略该成员，也不能依赖用户阅读或遵守文档。  而且，因为保留成员既出现在对象浏览器中也出现在智能集成开发环境中，它们可能对实际使用了哪个成员造成混淆。  
  
 在将来的版本中将不使用保留成员，而是向枚举添加新成员。  在大多数情况下，只要添加新成员不会引起原始成员的值更改，添加新成员就不是重大更改。  
  
 在有限的几种情况下，即使原始成员保留其原始值，添加成员也属于重大更改。  主要原因是，新成员在从现有代码路径返回时，必须中断对包含整个成员列表并在默认情况下引发异常的返回值使用 `switch`（在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中为 `Select`）语句的调用方。  其次，客户端代码可能不处理反射方法的行为的更改，如 <xref:System.Enum.IsDefined%2A?displayProperty=fullName>。  因此，如果要从现有的方法返回具有新的成员，或者由于使用较差的反射而发生已知的应用程序不兼容，则唯一的无间断解决方法是：  
  
1.  添加一个新的枚举，其中包含原始成员和新成员。  
  
2.  用 <xref:System.ObsoleteAttribute?displayProperty=fullName> 特性标记原始枚举。  
  
 对任何外部可见并公开原始枚举的类型或成员均执行相同的过程。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请移除或重命名成员。  
  
## 何时禁止显示警告  
 对于当前正在使用的成员或以前提供的库，可以安全地禁止显示此规则发出的警告。  
  
## 相关规则  
 [CA2217：不要使用 FlagsAttribute 标记枚举](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1712：不要将类型名用作枚举值的前缀](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
 [CA1028：枚举存储应为 Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)  
  
 [CA1008：枚举应具有零值](../code-quality/ca1008-enums-should-have-zero-value.md)  
  
 [CA1027：用 FlagsAttribute 标记枚举](../code-quality/ca1027-mark-enums-with-flagsattribute.md)