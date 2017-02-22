---
title: "CA1720：标识符不应包含类型名称 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1720"
  - "IdentifiersShouldNotContainTypeNames"
helpviewer_keywords: 
  - "IdentifiersShouldNotContainTypeNames"
  - "CA1720"
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1720：标识符不应包含类型名称
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|IdentifiersShouldNotContainTypeNames|  
|CheckId|CA1720|  
|类别|Microsoft.Naming|  
|是否重大更改|是|  
  
## 原因  
 外部可见成员中的参数名称包含数据类型名称。  
  
 \- 或 \-  
  
 外部可见成员的名称包含特定于语言的数据类型名称。  
  
## 规则说明  
 参数和成员的名称最好用来传达它们的含义，而不是用来说明它们的类型，它们的类型应由开发工具提供。  对于成员的名称，如果必须使用数据类型名称，请使用与语言无关的名称，而不要使用特定于语言的名称。  例如，请使用与语言无关的数据类型名称 Int32，而不要使用 C\# 类型名称“int”。  
  
 将对照以下特定于语言的数据类型名称检查参数名称或成员名称中的每个离散标记，检查时不区分大小写：  
  
-   Bool  
  
-   WChar  
  
-   Int8  
  
-   UInt8  
  
-   Short  
  
-   UShort  
  
-   Int  
  
-   UInt  
  
-   Integer  
  
-   UInteger  
  
-   Long  
  
-   ULong  
  
-   Unsigned  
  
-   Signed  
  
-   Float  
  
-   Float32  
  
-   Float64  
  
 此外，还会对照以下与语言无关的数据类型名称检查参数的名称，检查时不区分大小写：  
  
-   对象  
  
-   Obj  
  
-   Boolean  
  
-   Char  
  
-   String  
  
-   SByte  
  
-   Byte  
  
-   UByte  
  
-   Int16  
  
-   UInt16  
  
-   Int32  
  
-   UInt32  
  
-   Int64  
  
-   UInt64  
  
-   IntPtr  
  
-   Ptr  
  
-   指针  
  
-   UInptr  
  
-   UPtr  
  
-   UPointer  
  
-   Single  
  
-   Double  
  
-   Decimal  
  
-   Guid  
  
## 如何解决冲突  
 **如果是针对参数引发的：**  
  
 请将相应参数名称中的数据类型标识符替换为能够更好地描述其含义的词语，或更具一般性的词语，如“value”。  
  
 **如果是针对成员激发的：**  
  
 请将相应成员名称中的特定于语言的数据类型标识符替换为能够更好地描述其含义的词语、与语言无关的等效项或更具一般性的词语，如“value”。  
  
## 何时禁止显示警告  
 偶尔使用基于类型的参数和成员名称也可能是恰当的。  但是，对于新的开发，在已知情况中尚未发现应该禁止显示此规则发出的警告的情况。  对于以前发布的库，则可能必须禁止显示此规则发出的警告。  
  
## 相关规则  
 [CA1709：标识符的大小写应当正确](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708：标识符不应仅以大小写进行区分](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707：标识符不应包含下划线](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)  
  
 [CA1719：参数名不应与成员名冲突](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)