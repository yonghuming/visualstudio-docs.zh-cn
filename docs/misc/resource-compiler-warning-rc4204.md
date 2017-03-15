---
title: "资源编译器警告 RC4204 | Microsoft Docs"
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
  - "RC4204"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC4204"
ms.assetid: f9a83b3c-d696-4b38-9576-945d1f6d0063
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# 资源编译器警告 RC4204
ASCII 字符不等价于虚拟键代码  
  
 字符串文本已用于 VIRTKEY 类型快捷键中的虚拟键代码。  
  
 此警告允许你继续操作，但请注意，生成的快捷键可能与你指示的字符串不匹配。 （VIRTKEYs 与 ASCII 快捷键使用不同的键代码。）  
  
 当字符串文本在语法上有效时，只能通过使用 WINDOWS.h 中的 **VK\_\*** `#define` 值确保获取你想要的快捷键。