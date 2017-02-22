---
title: "符号提供程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "符号处理程序"
  - "调试 [调试 SDK]，符号处理程序"
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# 符号提供程序
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

实现必须访问符号调试信息的表达式计算器的语言编译器生成为了计算变量与表达式。  它通过使用，也称为符号处理程序的符号 \(SP\)提供的接口来实现。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 托管代码的提供 SPs 以及使用程序数据库 \(PDB\)符号文件格式的本机代码。  除非具有强需要程序使用在一个自定义格式存储的符号，建议您使用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供的 SPs。  
  
## 实现批注  
 使用公共语言运行时接口， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 调试引擎应该与 SPs \(CLR\) 连接。  因此，与 Visual Studio 结合使用的 SP 调试引擎必须支持 CLR。  完整的所有 CLR 调试接口可在 debugref.doc 找到，是 [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]的一部分。  
  
 如果 SP 仅与该自定义使用调试引擎，可以实现 SP，应根据调试引擎的需要根据为。  
  
## 请参阅  
 [调试程序组件](../../extensibility/debugger/debugger-components.md)