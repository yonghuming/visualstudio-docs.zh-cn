---
title: "CLS 符合性警告 CLS00500 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLS00500"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS00500"
ms.assetid: faaf377e-3738-4c0d-9a51-09db4073564e
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS00500
符合 CLS 的范围中的所有名称均应是明显独立的类型  
  
 在符合 CLS 的范围中引入的所有名称都应是明显独立的类型，除非名称完全相同且通过重载解析。 对于 CLS，如果两个名称的小写映射相同，则这两个名称也相同。 只可重载属性和函数。 在重载时，属性和函数仅可基于其参数的数目和类型进行重载，但转换运算符除外，转换运算符也可基于其返回类型进行重载；更多详细信息，请参阅[用户定义的转换](/visual-cpp/dotnet/user-defined-conversions-cpp-cli)。  
  
 有关 CLS 符合性检查的详细信息，请参阅[符合 CLS 的程序集](http://msdn.microsoft.com/zh-cn/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 下面的示例生成 CLS00500：  
  
```  
// CLS00500.cpp // compile with: /clr /LD // CLS00500 expected using namespace System; using namespace System::Reflection; [assembly:AssemblyKeyFile("clscompliance.snk")]; [assembly:System::CLSCompliant(true)]; public ref class a {}; public ref class A {};   // CLS00500  
```