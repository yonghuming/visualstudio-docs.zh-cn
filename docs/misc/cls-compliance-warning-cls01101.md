---
title: "CLS 遵从性警告 CLS01101 | Microsoft Docs"
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
  - "CLS01101"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01101"
ms.assetid: 01034537-eee8-40e6-9139-d1788612738a
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 遵从性警告 CLS01101
显示在签名中的所有类型应符合 CLS  
  
 当类型符合 CLS 时，类型中的所有构造函数必须具有符合 CLS 的类型形参，除非标记为不符合 CLS。  
  
 有关 CLS 遵从性检查的详细信息，请参见[符合 CLS 的程序集](http://msdn.microsoft.com/zh-cn/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
## 示例  
 下面的示例生成 CLS01101:  
  
```  
// CLS01101.cpp // compile with: /clr /LD // CLS01101 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; [CLSCompliant(true)] public ref class CompliantType {}; [CLSCompliant(false)] public ref class NotCompliantType {}; [CLSCompliant(true)] public ref class One { public: One(NotCompliantType^ parameter) {}   // CLS01101 One(CompliantType^ parameter) {}   // OK [CLSCompliant(false)] One(NotCompliantType^ param1, NotCompliantType^ param2) {}   // OK };  
```