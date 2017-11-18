---
title: "CA2201： 不要引发保留的异常类型 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotRaiseReservedExceptionTypes
- CA2201
helpviewer_keywords:
- CA2201
- DoNotRaiseReservedExceptionTypes
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 713018b96aed70d52b1b11e75b0c2993312ef474
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2201-do-not-raise-reserved-exception-types"></a>CA2201：不要引发保留的异常类型
|||  
|-|-|  
|TypeName|DoNotRaiseReservedExceptionTypes|  
|CheckId|CA2201|  
|类别|Microsoft.Usage|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 某方法引发的异常类型过于一般或者保留的运行时。  
  
## <a name="rule-description"></a>规则说明  
 下面的异常类型是太通用，向用户提供足够的信息：  
  
-   <xref:System.Exception?displayProperty=fullName>  
  
-   <xref:System.ApplicationException?displayProperty=fullName>  
  
-   <xref:System.SystemException?displayProperty=fullName>  
  
 下面的异常类型保留，并且应仅由公共语言运行时引发：  
  
-   <xref:System.ExecutionEngineException?displayProperty=fullName>  
  
-   <xref:System.IndexOutOfRangeException?displayProperty=fullName>  
  
-   <xref:System.NullReferenceException?displayProperty=fullName>  
  
-   <xref:System.OutOfMemoryException?displayProperty=fullName>  
  
 **不会引发一般异常**  
  
 如果您引发一般异常类型，如<xref:System.Exception>或<xref:System.SystemException>在库或框架中，它会强制使用者能够捕捉所有异常，包括它们不知道如何处理的未知的异常。  
  
 请改为引发派生程度更大的类型在框架中，已存在，或者创建你自己的类型派生自<xref:System.Exception>。  
  
 **引发特定异常**  
  
 下表显示参数和验证的参数，包括值参数中的一个属性 set 访问器时引发的异常：  
  
|参数说明|例外|  
|---------------------------|---------------|  
|`null`引用|<xref:System.ArgumentNullException?displayProperty=fullName>|  
|超出允许的范围的值 （如集合或列表的索引）|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|  
|无效`enum`值|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|  
|包含不符合的一种方法的参数规范的格式 (如的格式字符串`ToString(String)`)|<xref:System.FormatException?displayProperty=fullName>|  
|否则为无效|<xref:System.ArgumentException?displayProperty=fullName>|  
  
 当操作对对象引发的当前状态无效<xref:System.InvalidOperationException?displayProperty=fullName>  
  
 对已释放的对象执行操作时引发<xref:System.ObjectDisposedException?displayProperty=fullName>  
  
 当不支持操作 (如在被重写**Stream.Write**打开以进行读取流中) 引发<xref:System.NotSupportedException?displayProperty=fullName>  
  
 当转换会导致溢出 （如显式强制转换运算符重载） 时引发<xref:System.OverflowException?displayProperty=fullName>  
  
 对于所有其他情况下，请考虑创建您自己的派生自类型<xref:System.Exception>并引发该异常。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，将更改为不是保留的类型之一的特定类型的引发的异常的类型。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
## <a name="related-rules"></a>相关的规则  
 [CA1031：不要捕捉一般异常类型](../code-quality/ca1031-do-not-catch-general-exception-types.md)