---
title: "CLS 符合性警告 CLS02011 | Microsoft Docs"
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
  - "CLS02011"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS02011"
ms.assetid: 9466be1e-9558-49e8-9ea4-5cfc54a22066
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS02011
符合 CLS 的类、值类型和接口不应要求实现不符合 CLS 的接口  
  
 标记为符合 CLS 的类型具有一个或多个不符合 CLS 的基类型。  
  
 有关 CLS 遵从性检查的详细信息，请参见[符合 CLS 的程序集](http://msdn.microsoft.com/zh-cn/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 下面的示例生成 CLS02011：  
  
```  
// CLS02011.cpp // compile with: /clr /LD // CLS02011 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; [CLSCompliant(true)] public interface class CompliantInterface {}; [CLSCompliant(false)] public interface class NotCompliantInterface {}; public ref class One : public NotCompliantInterface {};   // CLS02011 public ref class Two : public CompliantInterface {};   // OK  
```