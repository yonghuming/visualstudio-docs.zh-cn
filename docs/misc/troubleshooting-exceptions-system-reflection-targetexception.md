---
title: "关于异常的疑难解答：System.Reflection.TargetException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.Reflection.TargetException 异常"
  - "TargetException 异常"
ms.assetid: 88b8e4b4-f1a3-4c4a-b1ef-cac176160803
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Reflection.TargetException
当尝试调用无效目标时引发的异常。  
  
## 备注  
 当尝试对 null 对象调用非静态方法时，将引发 <xref:System.Reflection.TargetException>。 这可能是由于调用方没有访问该成员的权限，或者目标没有定义该成员，或者类似情形。  
  
## 请参阅  
 <xref:System.Reflection.TargetException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)