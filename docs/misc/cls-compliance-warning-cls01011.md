---
title: "CLS 符合性警告 CLS01011 | Microsoft Docs"
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
  - "CLS01011"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01011"
ms.assetid: e4141e15-14fd-491c-9639-f3f3a47d7865
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS01011
重写继承的方法时，不应更改其可访问性  
  
 请确保重写方法的可见性与它所重写的方法相同。  重写继承的方法时，不应更改其可访问性（重写一个继承自其他可访问系列或程序集的程序集的方法除外）。 在此情况下，重写应可访问系列。  
  
 有关 CLS 遵从性检查的详细信息，请参见[符合 CLS 的程序集](http://msdn.microsoft.com/zh-cn/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 下面的示例生成 CLS01011：  
  
```  
// CLS01011.cpp // compile with: /clr /LD // CLS01011 expected using namespace System; using namespace System::Reflection; using namespace cli::language; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class BaseType { public protected: virtual void BaseTypeMethod() {} }; public ref class One : public BaseType { public: void BaseTypeMethod() {}   // CLS01011 // OK // public protected: //    void BaseTypeMethod() {} };  
```