---
title: "CA1306：设置数据类型的区域设置 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1306"
  - "SetLocaleForDataTypes"
helpviewer_keywords: 
  - "CA1306"
  - "SetLocaleForDataTypes"
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1306：设置数据类型的区域设置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|SetLocaleForDataTypes|  
|CheckId|CA1306|  
|类别|Microsoft.Globalization|  
|是否重大更改|非重大更改|  
  
## 原因  
 某方法或构造函数创建了一个或多个 <xref:System.Data.DataTable?displayProperty=fullName> 或 <xref:System.Data.DataSet?displayProperty=fullName> 实例，但未显式设置区域设置属性（<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> 或 <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>）。  
  
## 规则说明  
 区域设置决定数据的区域性特定显示元素，例如，数值、货币符号和排序顺序所用的格式。  在创建 <xref:System.Data.DataTable> 或 <xref:System.Data.DataSet> 时，应显式设置区域设置。  默认情况下，这些类型的区域设置为当前区域性。  对于存储在数据库或文件中并且全局共享的数据，通常应将区域设置设置为固定区域性 \(<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>\)。  当数据跨区域性共享时，使用默认区域设置可能导致 <xref:System.Data.DataTable> 或 <xref:System.Data.DataSet> 的内容无法正确显示或解释。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请显式设置 <xref:System.Data.DataTable> 或 <xref:System.Data.DataSet> 的区域设置。  
  
## 何时禁止显示警告  
 当库或应用程序面向有限范围的本地用户、数据不进行共享或者默认设置可以为支持的所有情况生成所需行为时，可以安全地禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例创建两个 <xref:System.Data.DataTable> 实例。  
  
 [!code-cs[FxCop.Globalization.DataTable#1](../code-quality/codesnippet/CSharp/ca1306-set-locale-for-data-types_1.cs)]  
  
## 请参阅  
 <xref:System.Data.DataTable?displayProperty=fullName>   
 <xref:System.Data.DataSet?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>