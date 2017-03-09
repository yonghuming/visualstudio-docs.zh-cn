---
title: "CLS 遵从性警告 CLS02609 | Microsoft Docs"
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
  - "CLS02609"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS02609"
ms.assetid: ea1afa9a-03d2-4417-af14-68e3b03a858f
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 遵从性警告 CLS02609
属性及其访问器必须同为静态、同为虚拟或同为实例。  
  
 属性及其访问器在其静态、虚拟或实例限定符中应相同。  
  
 有关 CLS 遵从性检查的详细信息，请参见[符合 CLS 的程序集](http://msdn.microsoft.com/zh-cn/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 以下示例生成 CLS02609：  
  
```  
// CLS02609.cpp // compile with: /clr /LD // CLS02609 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class One { private: int InstanceMember; static int StaticMember; public: property int MyProperty1 {   // CLS02609 public: void set(int value) {} static int get() { return StaticMember; } } property int MyProperty2 {   // OK public: void set(int value) {} int get() { return StaticMember; } } };  
```