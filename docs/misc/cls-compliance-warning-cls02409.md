---
title: "CLS 遵从性警告 CLS02409 | Microsoft Docs"
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
  - "CLS02409"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS02409"
ms.assetid: 71d566ce-59c2-4d3d-97ff-72f4e9bd21ee
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 遵从性警告 CLS02409
实现属性的 getter 和 setter 方法的方法应在元数据中标记为 SpecialName  
  
 实现属性的 getter 和 setter 方法的方法未在元数据中标记为 **specialname**。  
  
 有关 CLS 遵从性检查的详细信息，请参见[符合 CLS 的程序集](http://msdn.microsoft.com/zh-cn/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 以下函数声明（使用 MSIL 程序集语言）显示可能导致 CLS02409 的原因：  
  
```  
.method public instance int32 get_MyProperty() cil managed  
```  
  
 通过添加 **specialname** 关键字，可解决此警告：  
  
```  
.method public specialname instance int32 get_MyProperty() cil managed  
```