---
title: "资源编译器错误 RC2115 | Microsoft Docs"
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
  - "RC2115"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2115"
ms.assetid: 1b90feb0-f1fb-4f3c-8a9a-c44f9f8dc366
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# 资源编译器错误 RC2115
文本字符串或控件中的预期序号  
  
 **DIALOG** 语句中 CONTROL 语句的 *text* 字段必须为一个文本字符串或对控件类型的引用的序号。 如果使用序号，请确保你有用于此控件的 `#define` 语句。