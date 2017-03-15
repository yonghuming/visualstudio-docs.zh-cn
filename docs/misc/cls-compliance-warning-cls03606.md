---
title: "CLS 符合性警告 CLS03606 | Microsoft Docs"
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
  - "CLS03606"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS03606"
ms.assetid: 567b0b18-7487-4f48-a9ae-a4a4db53a409
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS03606
全局静态方法不符合 CLS  
  
 全局静态字段和方法不符合 CLS。  
  
 有关公共语言子集 \(CLS\) 符合性检查的详细信息，请参阅[符合 CLS 的程序集](http://msdn.microsoft.com/zh-cn/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 以下示例生成 CLS03606：  
  
```  
// CLS03606.cpp // compile with: /clr /LD // CLS03606 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; void MyGlobalFunction1() {}   // CLS03606 public ref class MyClass { public: void MemberFunction() {}   // OK };  
```