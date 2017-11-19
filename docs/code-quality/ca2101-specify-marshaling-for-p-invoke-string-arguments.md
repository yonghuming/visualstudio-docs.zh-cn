---
title: "CA2101： 指定对 P Invoke 字符串自变量封送处理 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SpecifyMarshalingForPInvokeStringArguments
- CA2101
helpviewer_keywords:
- CA2101
- SpecifyMarshalingForPInvokeStringArguments
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a759662b35024add1666e99c89433f0b369676b7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101：指定对 P/Invoke 字符串参数进行封送处理
|||  
|-|-|  
|TypeName|SpecifyMarshalingForPInvokeStringArguments|  
|CheckId|CA2101|  
|类别|Microsoft.Globalization|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 平台调用成员允许部分受信任调用方，具有一个字符串参数，并且不显式封送字符串。  
  
## <a name="rule-description"></a>规则说明  
 当从 Unicode 转换为 ANSI 时，有可能可以在特定的 ANSI 代码页中表示不是所有 Unicode 字符。 *最佳的映射*尝试通过用替换的字符不能表示的字符来解决此问题。 此功能的使用可能导致潜在的安全漏洞，因为您无法控制为所选的字符。 例如，恶意代码有意会创建包含在特定代码页中，找不到该文件系统的特殊字符会转换为的字符的 Unicode 字符串.. 或 /。 另请注意，特殊字符的安全检查经常发生之前字符串转换为 ANSI。  
  
 最佳的映射是默认值为非托管的转换，WChar 到 mb 的磁盘。 除非显式禁用最佳的映射时，你的代码可能包含可利用的安全漏洞，由于此问题。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，显式封送字符串数据类型。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
## <a name="example"></a>示例  
 下面的示例演示的方法违反了此规则，然后演示如何修复此冲突。  
  
 [!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../code-quality/codesnippet/CSharp/ca2101-specify-marshaling-for-p-invoke-string-arguments_1.cs)]