---
title: "CLS 符合性警告 CLS01201 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLS01201"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01201"
ms.assetid: 8c3e6ce4-8ea5-487a-bbed-56a36eceb024
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS01201
类型和成员的可见性和可访问性应是这样的：只要任何成员是可见的且可访问的，则该成员签名中的类型应是可见且可访问的。 例如，在其程序集外部可见的公共构造函数不应具有其类型仅在程序集内可见的参数。  
  
 构造函数签名中的类型的可访问性必须大于或等于该构造函数可访问性。  例如，在其程序集外部可见的公共构造函数不应具有其类型仅在程序集内可见的参数。  
  
 有关 CLS 遵从性检查的详细信息，请参见[符合 CLS 的程序集](http://msdn.microsoft.com/zh-cn/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 以下示例生成 CLS01201：  
  
```  
/* CLS01201.cpp */ // compile with: /clr /LD // CLS01201 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; private ref class AssemblyLevelType {}; public ref class One { public: One(AssemblyLevelType^ parameter) {}   // not cls compliant }; private value class Two { public: Two(AssemblyLevelType^ parameter) {}   // OK };  
```