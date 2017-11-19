---
title: "CA2202： 不要释放对象多次 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2202
- Do not dispose objects multiple times
- DoNotDisposeObjectsMultipleTimes
helpviewer_keywords: CA2202
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ab5acc92df96c416cd614ac18ac66ff34d142a22
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202：不要多次释放对象
|||  
|-|-|  
|TypeName|DoNotDisposeObjectsMultipleTimes|  
|CheckId|CA2202|  
|类别|Microsoft.Usage|  
|是否重大更改|非重大更改|  
  
## <a name="cause"></a>原因  
 方法实现所包含的代码路径可能导致对多个调用<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>或与 Dispose 等效，如对同一对象的某些类型的 close （） 方法。  
  
## <a name="rule-description"></a>规则说明  
 正确实现<xref:System.IDisposable.Dispose%2A>方法可以多次调用而不引发异常。 但是，不保证和以避免生成<xref:System.ObjectDisposedException?displayProperty=fullName>不应调用<xref:System.IDisposable.Dispose%2A>对象上的不止一次。  
  
## <a name="related-rules"></a>相关的规则  
 [CA2000：超出范围前释放对象](../code-quality/ca2000-dispose-objects-before-losing-scope.md)  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，请更改的代码路径中，因此，无论实现<xref:System.IDisposable.Dispose%2A>称为对象只能有一个时间。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。 即使<xref:System.IDisposable.Dispose%2A>为已知对象可以安全地调用多次，该实现可能在以后更改。  
  
## <a name="example"></a>示例  
 嵌套`using`语句 (`Using`在 Visual Basic 中) 可能会导致违反 CA2202 警告的情况。 如果嵌套的内部的 IDisposable 资源`using`语句包含的外部资源`using`语句，`Dispose`方法的嵌套资源释放所包含的资源。 当出现这种情况时，`Dispose`方法的外部`using`语句尝试第二次释放其资源。  
  
 在下面的示例中，<xref:System.IO.Stream>在外部创建的对象使用语句在内部的 Dispose 方法中，使用语句结束时释放<xref:System.IO.StreamWriter>对象，其中包含`stream`对象。 末尾的外部`using`语句，`stream`第二次在释放对象。 第二个版本是 ca2202 冲突。  
  
```  
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))  
{  
    using (StreamWriter writer = new StreamWriter(stream))  
    {  
        // Use the writer object...  
    }  
}  
  
```  
  
## <a name="example"></a>示例  
 若要解决此问题，请使用`try` / `finally`块而不是外部`using`语句。 在`finally`阻止，请确保`stream`资源不是 null。  
  
```  
Stream stream = null;  
try  
{  
    stream = new FileStream("file.txt", FileMode.OpenOrCreate);  
    using (StreamWriter writer = new StreamWriter(stream))  
    {  
        stream = null;  
        // Use the writer object...  
    }  
}  
finally  
{  
    if(stream != null)  
        stream.Dispose();  
}  
  
```  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.IDisposable?displayProperty=fullName>   
 [释放模式](/dotnet/standard/design-guidelines/dispose-pattern)