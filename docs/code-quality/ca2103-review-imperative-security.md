---
title: "CA2103：检查命令性安全 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2103"
  - "ReviewImperativeSecurity"
helpviewer_keywords: 
  - "CA2103"
  - "ReviewImperativeSecurity"
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2103：检查命令性安全
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|ReviewImperativeSecurity|  
|CheckId|CA2103|  
|类别|Microsoft.Security|  
|是否重大更改|是|  
  
## 原因  
 某个方法使用命令性安全，并且可能正在使用在要求处于活动状态时可以更改的状态信息或返回值来构造权限。  
  
## 规则说明  
 与声明性安全相比，命令性安全使用托管对象来指定代码执行期间的权限和安全操作。而声明性安全使用特性将权限和操作存储在元数据中。  命令性安全非常灵活，因为您可以使用直到运行时才可用的信息来设置权限对象的状态和选择安全操作。  伴随这种灵活性而来的是一定程度的风险：只要操作生效，用于确定权限状态的运行时信息就不会保持不变。  
  
 应尽可能使用声明性安全。  声明性需求更易于理解。  
  
## 如何解决冲突  
 检查命令性安全请求，以确保权限的状态不依赖于只要使用权限即会发生更改的信息。  
  
## 何时禁止显示警告  
 如果权限不依赖于发生更改的数据，则可以安全地禁止显示此规则发出的警告。  但是，最好还是要将命令性请求更改为其声明性等效项。  
  
## 请参阅  
 [代码安全维护指南](../Topic/Secure%20Coding%20Guidelines.md)   
 [数据和建模](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)