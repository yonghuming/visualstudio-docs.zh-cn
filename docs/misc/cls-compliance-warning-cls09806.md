---
title: "CLS 符合性警告 CLS09806 | Microsoft Docs"
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
  - "CLS09806"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS09806"
ms.assetid: fc97cf0e-c72e-4c09-96be-f90f9840e76e
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS09806
有多个泛型方法不符合 CLS  
  
 有一个泛型方法不符合 CLS  
  
 有关公共语言子集 \(CLS\) 符合性检查的详细信息，请参阅[符合 CLS 的程序集](http://msdn.microsoft.com/zh-cn/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 下面的示例生成 CLS09806：  
  
```  
// CLS09806.cpp // compile with: /clr /LD /link /noentry // CLS09806 expected using namespace System::Reflection; [assembly:AssemblyKeyFile("clscompliance.snk")]; using namespace System; [assembly:CLSCompliant (true)]; generic <class T> public ref struct One { public: generic <class U> void Method1() {} };  
```