---
title: "CA2202：不要多次释放对象 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2202"
  - "Do not dispose objects multiple times"
  - "DoNotDisposeObjectsMultipleTimes"
helpviewer_keywords: 
  - "CA2202"
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2202：不要多次释放对象
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DoNotDisposeObjectsMultipleTimes|  
|CheckId|CA2202|  
|类别|Microsoft.Usage|  
|是否重大更改|否|  
  
## 原因  
 某个方法实现所包含的代码路径可能导致对同一对象多次调用 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 或与 Dispose 等效的方法（例如，用于某些类型的 Close\(\) 方法）。  
  
## 规则说明  
 正确实现的 <xref:System.IDisposable.Dispose%2A> 方法可以调用多次，而不会引发异常。  然而，这是无法保证的。为避免生成 <xref:System.ObjectDisposedException?displayProperty=fullName>，不应对一个对象调用 <xref:System.IDisposable.Dispose%2A> 多次。  
  
## 相关规则  
 [CA2000：超出范围前释放对象](../code-quality/ca2000-dispose-objects-before-losing-scope.md)  
  
## 如何解决冲突  
 若要修复与该规则的冲突，请更改实现，确保无论代码路径如何，只为对象调用一次 <xref:System.IDisposable.Dispose%2A>。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  即使已知对象的 <xref:System.IDisposable.Dispose%2A> 可以安全地调用多次，该方法的实现也有可能在将来更改。  
  
## 示例  
 嵌套的 `using` 语句（Visual Basic 中的 `Using`）可能会导致 CA2202 冲突警告。  如果嵌套的内部 `using` 语句的 IDisposable 资源包含外部 `using` 语句的资源，嵌套的资源的 `Dispose` 方法将释放被包含的资源。  发生这种情况时，外部 `using` 语句的 `Dispose` 方法会尝试第二次释放其资源。  
  
 在下面的示例中，以包含 `stream` 对象的 <xref:System.IO.StreamWriter> 对象的 Dispose 方法在内部的末尾使用语句释放在外部中使用语句创建的 <xref:System.IO.Stream> 对象。  在外部 `using` 语句的末尾，第二次释放 `stream` 对象。  第二个版本是 CA2202 冲突。  
  
```  
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))  
{  
    using (StreamWriter writer = new StreamWriter(stream))  
    {  
        // Use the writer object...  
    }  
}  
  
```  
  
## 示例  
 若要解决此问题，请使用 `try`\/`finally` 块，而不是使用外部 `using` 语句。  在 `finally` 块中，确保 `stream` 资源不为 null。  
  
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
  
## 请参阅  
 <xref:System.IDisposable?displayProperty=fullName>   
 [释放模式](../Topic/Dispose%20Pattern.md)