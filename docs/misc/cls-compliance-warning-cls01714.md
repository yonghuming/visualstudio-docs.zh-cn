---
title: "CLS 符合性警告 CLS01714 | Microsoft Docs"
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
  - "CLS01714"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01714"
ms.assetid: 8ba94d1e-ad27-4dd2-919a-19be75119e53
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS01714
非托管的指针类型不符合 CLS  
  
 符合 CLS 的委托签名不能包含非托管的指针类型。  
  
 有关公共语言子集 \(CLS\) 符合性检查的详细信息，请参阅[符合 CLS 的程序集](http://msdn.microsoft.com/zh-cn/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 以下示例生成 CLS01714：  
  
```  
// CLS01714.cpp // compile with: /clr /LD // CLS01714 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public delegate void MyDelegate1(int* Parameter);   // CLS01714  
```