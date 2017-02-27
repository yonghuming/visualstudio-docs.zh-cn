---
title: "实现端口提供程序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "调试 [调试 SDK]、 实现端口供应商"
  - "端口供应商实现"
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# 实现端口提供程序
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

端口提供程序提供端口会议的根据需要调试管理器 \(SDM\)。  端口提供程序需要实现，在调试对非 DCOM 计算机或时，新设备需要支持时。  例如，提供调试对移动，可实现可能提供端口连接到移动的端口提供程序 \(通过红外线或单元格连接\) 并枚举过程并运行在发出的过程。  
  
 对于基于 windows 的计算机上调试程序 \(包括远程调试， Visual Studio 为本机提供端口提供程序，公共语言运行 \(CLR\)时处理，因此不需要实现在这些情况下拥有端口提供程序。  
  
## 本节内容  
 [实现和注册端口提供程序](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 讨论 SDM 如何使用端口提供程序及其端口进行交互。  
  
 [所需的端口供应商接口](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 文档必须实现获取端口提供的接口。  
  
## 相关章节  
 [调试器概念](../../extensibility/debugger/debugger-concepts.md)  
 描述主要调试体系结构概念。  
  
## 请参阅  
 [Visual Studio 调试器可扩展性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)