---
title: "CLS 遵从性警告 CLS01106 | Microsoft Docs"
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
  - "CLS01106"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01106"
ms.assetid: 0c964444-387d-4348-aed5-05f1ccc241c8
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 遵从性警告 CLS01106
**显示在签名中的所有类型应符合 CLS**  
  
 如果某个类型符合 CLS，那么，该类型中的所有函数都必须具有符合 CLS 的类型参数，除非标记为不符合 CLS。  
  
 有关 CLS 遵从性检查的详细信息，请参见[符合 CLS 的程序集](http://msdn.microsoft.com/zh-cn/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 下面的示例生成 CLS01106：  
  
```  
// CLS01106.cpp // compile with: /clr /LD // CLS01106 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; [CLSCompliant(true)] public ref class CompliantType {}; [CLSCompliant(false)] public ref class NotCompliantType {}; [CLSCompliant(true)] public ref class One { public: NotCompliantType^ Method1(NotCompliantType^ parameter) { return parameter; } CompliantType^ Method2(CompliantType^ parameter) {   // OK return parameter; } [CLSCompliant(false)] NotCompliantType^ Method3(NotCompliantType^ parameter) {   // OK return parameter; } };  
```