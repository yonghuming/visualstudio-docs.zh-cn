---
title: "资源编译器错误 RC1122 | Microsoft Docs"
ms.custom: ""
ms.date: "09/30/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RC1122"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC1122"
ms.assetid: c1f80766-802e-4cd2-82bb-e1e914f1634d
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# 资源编译器错误 RC1122
写入文件时出现 I\/O 错误  
  
 资源编译器无法写入文件。  
  
### 通过检查以下可能的原因进行修复  
  
1.  磁盘空间不足。 可用空间必须约等于正在创建的可执行文件大小的两倍。  
  
2.  卷为只读。  
  
3.  坏扇区。  
  
4.  共享冲突。