---
title: "CLS 遵从性警告 CLS01606 | Microsoft Docs"
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
  - "CLS01606"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01606"
ms.assetid: 24291af4-d2b1-4a91-b50f-fb61d8ff1687
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 遵从性警告 CLS01606
数组应具有符合 CLS 类型的元素，且数组的所有维度的下限应为零  
  
 数组应具有符合 CLS 类型的元素，且数组的所有维度的下限应为零。 各重载间只需区别：项是数组还是数组的元素类型。 当重载基于两个或更多数组类型时，元素类型应为命名类型。  
  
 有关 CLS 遵从性检查的详细信息，请参见[符合 CLS 的程序集](http://msdn.microsoft.com/zh-cn/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 下面的示例生成 CLS01606：  
  
```  
// CLS01606.cpp // compile with: /clr /LD // CLS01606 expected using namespace System; using namespace System::Reflection; using namespace cli::language; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; [CLSCompliant(true)] public ref class CompliantType {}; [CLSCompliant(false)] public ref class NotCompliantType {}; public ref class One { public: // CLS01606 array<NotCompliantType^>^ Method1() { return gcnew array<NotCompliantType^>(10); } // OK array<CompliantType^>^ Method2() { return gcnew array<CompliantType^>(10); } };  
```