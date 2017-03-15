---
title: "CLS 遵从性警告 CLS03002 | Microsoft Docs"
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
  - "CLS03002"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS03002"
ms.assetid: b3254410-e21c-430b-a2fd-d110d6f5f38a
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 遵从性警告 CLS03002
事件及其访问器的可访问性应相同  
  
 事件及其访问器方法在可访问性方面不应有差别。  
  
 有关 CLS 遵从性检查的详细信息，请参见[符合 CLS 的程序集](http://msdn.microsoft.com/zh-cn/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 下面的示例生成 CLS03002：  
  
```  
// CLS03002.cpp // compile with: /clr /LD // CLS03002 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public delegate void MyDelegate(int parameter); public ref class One { public: event MyDelegate^ MyEvent {   // CLS03002 public: void add(MyDelegate^ paramter) {} void remove(MyDelegate^ parameter) {} protected: void raise(int parameter)   {} } event MyDelegate^ MyEvent2 {   // OK public: void add(MyDelegate^ paramter) {} void remove(MyDelegate^ parameter) {} void raise(int parameter)   {} } };  
```