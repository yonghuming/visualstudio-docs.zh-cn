---
title: "友元程序集引用 &lt;reference&gt; 无效。 不能为 InternalsVisibleTo 声明指定版本、区域性、公钥标记或处理器结构。 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31534"
  - "vbc31534"
helpviewer_keywords: 
  - "BC31534"
ms.assetid: ae1e470e-3105-48f2-87b1-466e395a7d44
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 友元程序集引用 &lt;reference&gt; 无效。 不能为 InternalsVisibleTo 声明指定版本、区域性、公钥标记或处理器结构。
传递给 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 特性构造函数的程序集名称包含一个 `Version`、`Culture`、`PublicKeyToken` 或 `processorArchitecture` 特性。  
  
 **错误 ID：**BC31534  
  
### 更正此错误  
  
1.  从传递给 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 特性构造函数的程序集名称中删除`Version`、`Culture`、`PublicKeyToken` 或 `processorArchitecture` 特性。  
  
## 请参阅  
 <xref:System.Reflection.AssemblyName>   
 [不在生成中：友元程序集 \(Visual Basic\)](http://msdn.microsoft.com/zh-cn/80e7a33a-ca91-450b-a00e-c5a7986e228c)