---
title: "CA2101：指定对 P/Invoke 字符串参数进行封送处理 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SpecifyMarshalingForPInvokeStringArguments"
  - "CA2101"
helpviewer_keywords: 
  - "CA2101"
  - "SpecifyMarshalingForPInvokeStringArguments"
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA2101：指定对 P/Invoke 字符串参数进行封送处理
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|SpecifyMarshalingForPInvokeStringArguments|  
|CheckId|CA2101|  
|类别|Microsoft.Globalization|  
|是否重大更改|非重大更改|  
  
## 原因  
 某平台调用成员允许部分受信任的调用方，具有一个字符串参数，并且不显式封送该字符串。  
  
## 规则说明  
 在从 Unicode 转换为 ANSI 时，并不是所有的 Unicode 字符都能在特定的 ANSI 代码页中表示。  最佳映射通过用一个字符替换无法表示的字符来解决此问题。  使用此功能会导致潜在的安全漏洞，因为您无法控制选择的字符。  例如，恶意代码会有意创建一个包含在特定代码页中无法找到的字符的 Unicode 字符串，而这些字符会转换为“..”或“\/”等特殊的文件系统字符。  另外还要注意，特殊字符的安全检查经常在将字符串转换为 ANSI 之前发生。  
  
 最佳映射是非托管转换（WChar 到 MByte）的默认设置。  除非显式禁用了最佳映射，否则代码可能由于此问题而包含可利用的安全漏洞。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请显式封送字符串数据类型。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示一个与该规则冲突的方法，然后演示如何修复该冲突。  
  
 [!code-cs[FxCop.Security.PinvokeAnsiUnicode#1](../code-quality/codesnippet/CSharp/ca2101-specify-marshaling-for-p-invoke-string-arguments_1.cs)]