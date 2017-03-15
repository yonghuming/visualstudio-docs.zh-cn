---
title: "CLS 遵从性警告 CLS01114 | Microsoft Docs"
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
  - "CLS01114"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01114"
ms.assetid: f3382da6-d3d0-4209-a229-400701c53ede
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 遵从性警告 CLS01114
显示在签名中的所有类型应符合 CLS  
  
 如果某个委托符合 CLS，则委托签名中的所有类型都必须符合 CLS。  
  
 有关 CLS 遵从性检查的详细信息，请参见[符合 CLS 的程序集](http://msdn.microsoft.com/zh-cn/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 以下示例生成 CLS01114：  
  
```  
// CLS01114.cpp // compile with: /clr /LD // CLS01114 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; [CLSCompliant(true)] public ref class CompliantType {}; [CLSCompliant(false)] public ref class NotCompliantType {}; // Public delegate public delegate CompliantType ^ PublicDelegate1(NotCompliantType^ param);   // CLS01114 public delegate CompliantType ^ PublicDelegate2(CompliantType^ param);   // OK  
```