---
title: "DA0013：String.Split 或 String.Substring 的使用率高 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.13"
  - "vs.performance.rules.DAAvoidStringSubstr"
  - "vs.performance.DA0013"
  - "vs.performance.rules.DA0013"
helpviewer_keywords: 
  - "vs.performance.13"
  - "vs.performance.rules.DA0013"
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0013：String.Split 或 String.Substring 的使用率高
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|规则 ID|DA0013|  
|类别|.NET Framework 使用指南|  
|分析方法|采样|  
|消息|请考虑减少使用 String.Split 和 String.Substring 函数。|  
|规则类型|警告|  
  
## 原因  
 对 System.String.Split 或 System.String.Substring 方法的调用在分析数据中占很大比例。  如果要测试字符串中是否存在子字符串，请考虑使用 System.String.IndexOf 或 System.String.IndexOfAny。  
  
## 规则说明  
 拆分方法将对 String 对象进行操作，并返回一个新的 String 数组，该数组包含原始字符串的子字符串。  该函数为返回的数组对象分配内存，并为其找到每个数组元素分配一个新的字符串对象。  同样，Substr 方法对 String 对象进行操作，并返回一个新的 String 值，它等效于请求的子字符串。  
  
 如果在应用程序中管理内存分配是关键，请考虑使用 String.Split 和 String.Substr 方法的替代项。  例如，可以使用 IndexOf 或 IndexOfAny 方法定位字符 String 中特定的子字符串，无需创建一个 String 类的新实例。  
  
## 如何调查警告  
 双击“错误列表”窗口中的该消息以导航到采样分析数据的[函数详细信息视图](../profiling/function-details-view.md)。  检查调用函数来查找最频繁使用 System.String.Split 或 System.String.Substr 方法的程序节。  如果可能，使用 IndexOf 或 IndexOfAny 方法定位字符 String 中特定的子字符串，无需创建一个 String 类的新实例。