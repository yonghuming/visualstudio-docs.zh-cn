---
title: "CA1713：事件不应具有 before 或 after 前缀 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EventsShouldNotHaveBeforeOrAfterPrefix"
  - "CA1713"
helpviewer_keywords: 
  - "CA1713"
  - "EventsShouldNotHaveBeforeOrAfterPrefix"
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA1713：事件不应具有 before 或 after 前缀
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|EventsShouldNotHaveBeforeOrAfterPrefix|  
|CheckId|CA1713|  
|类别|Microsoft.Naming|  
|是否重大更改|是|  
  
## 原因  
 事件的名称以“Before”或“After”开头。  
  
## 规则说明  
 事件名称应当说明引发事件的操作。  若要命名按特定顺序引发的相关事件，请使用现在时或过去时指示一系列操作中的相对位置。  例如，当命名关闭资源时引发的一对事件时，可以将其命名为“Closing”和“Closed”，而不是“BeforeClose”和“AfterClose”。  
  
 命名约定为所有针对公共语言运行时的库提供了通用的外观。  这提高了学习新软件库的效率，并使客户进一步认为该软件库是由某位具有开发托管代码专门技术的人员所开发。  
  
## 如何解决冲突  
 从事件名称中移除前缀，考虑将名称更改为使用动词的现在时或过去时。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。