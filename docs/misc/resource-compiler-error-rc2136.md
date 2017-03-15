---
title: "资源编译器错误 RC2136 | Microsoft Docs"
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
  - "RC2136"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2136"
ms.assetid: 4e9b2ff1-402c-4ec4-8610-fc8fd5f213c0
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# 资源编译器错误 RC2136
EXSTYLE\=\<flags\> 中缺少“\=”  
  
 **EXSTYLE**（扩展样式标志）语句中缺少等号 \(**\=**\)。 当 **EXSTYLE** 嵌入在 **DIALOG** 或 **MENU** 语句中时，它必须具有以下形式：  
  
```  
EXSTYLE=FLAGS  
```