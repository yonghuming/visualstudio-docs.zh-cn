---
title: "CLS 遵从性警告 CLS01214 | Microsoft Docs"
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
  - "CLS01214"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01214"
ms.assetid: 5968af20-3d3e-4c7b-ad61-c06979cc9efd
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 遵从性警告 CLS01214
类型和成员的可见性和可访问性应是这样的：只要任何成员是可见的且可访问的，则该成员签名中的类型应是可见且可访问的。 例如，在其程序集外部可见的委托不应具有其类型仅在程序集内可见的参数。  
  
 委托签名中的类型的可访问性必须大于或等于该委托的可访问性。  例如，在其程序集外部可见的委托不应具有其类型仅在程序集内可见的参数。  
  
 有关 CLS 遵从性检查的详细信息，请参见[符合 CLS 的程序集](http://msdn.microsoft.com/zh-cn/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 以下示例生成 CLS01214：  
  
```  
/* CLS01214.cpp */ // compile with: /clr /LD // CLS01214 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class PublicType {}; private ref class AssemblyType {}; public delegate PublicType^ AssemblyDelegate(AssemblyType^ parameter);   // not cls compliant public delegate PublicType^ AssemblyDelegate2(PublicType^ parameter);   //cls compliant  
```