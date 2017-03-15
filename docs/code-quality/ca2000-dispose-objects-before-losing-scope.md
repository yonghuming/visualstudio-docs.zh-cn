---
title: "CA2000：超出范围前释放对象 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2000"
  - "Dispose objects before losing scope"
  - "DisposeObjectsBeforeLosingScope"
helpviewer_keywords: 
  - "CA2000"
  - "DisposeObjectsBeforeLosingScope"
ms.assetid: 0c3d7d8d-b94d-46e8-aa4c-38df632c1463
caps.latest.revision: 32
caps.handback.revision: 32
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2000：超出范围前释放对象
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DisposeObjectsBeforeLosingScope|  
|CheckId|CA2000|  
|类别|Microsoft.Reliability|  
|是否重大更改|非重大更改|  
  
## 原因  
 创建了 <xref:System.IDisposable> 类型的局部对象，但在对该对象的所有引用超出范围之前没有释放该对象。  
  
## 规则说明  
 如果在对某个可释放对象的所有引用超出范围之前未显式释放该对象，则当垃圾回收器运行该对象的终结器时，会在某个不确定时间释放该对象。  由于可能会发生阻止该对象的终结器运行的意外事件，因此应改为显式释放该对象。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请在对对象的所有引用超出范围之前对该对象调用 <xref:System.IDisposable.Dispose%2A>。  
  
 请注意，您可以使用 `using` 语句（在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中为 `Using`）来包装实现 `IDisposable` 的对象。  通过此方式包装的对象将在关闭 `using` 块时自动释放。  
  
 在下列情况下，using 语句不足以保护 IDisposable 对象，并且可能会导致引发 CA2000。  
  
-   返回可释放对象要求在 using 块以外的 try\/finally 块中构造该对象。  
  
-   不应在一个使用语句的构造函数中完成对可释放对象的成员的初始化。  
  
-   只能由一个异常处理程序嵌套受保护的构造函数。  例如，  
  
    ```  
    using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))  
    { ... }  
    ```  
  
     导致引发 CA2000，这是因为 StreamReader 对象结构中的故障可能会导致 FileStream 对象永远不被关闭。  
  
-   动态对象应使用阴影对象来实现 IDisposable 对象的 Dispose 模式。  
  
## 何时禁止显示警告  
 不要禁止从此规则的一个警告，除非已经调用了调用 `Dispose`，例如 <xref:System.IO.Stream.Close%2A>的对象中的一个的方法，或者，如果引发警告的方法返回包装您的对象的 IDisposable 对象。  
  
## 相关规则  
 [CA2213：应释放可释放的字段](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
 [CA2202：不要多次释放对象](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)  
  
## 示例  
 如果正在实施一个返回可释放对象的方法，使用不包含 catch 块的 try\/finally 块以确保对象已释放。  通过使用 try\/finally 块，允许在 fault 点引发异常，并确保释放该对象。  
  
 在 OpenPort 方法中，打开 ISerializable 对象 SerialPort 的调用或 SomeMethod 的调用可能会失败。  在此实现上引发 CA2000 警告。  
  
 在 OpenPort2 方法中，两个 SerialPort 对象被声明并设置为 null：  
  
-   `tempPort` 用于测试该方法操作是否成功。  
  
-   `port`，它用于方法的返回值。  
  
 `tempPort` 是在 `try` 块中构造并打开的，并且任何其他所需工作也是在相同的 `try` 块中执行的。  在 `try` 块的末尾，开放端口分配给将返回的 `port` 对象，并且 `tempPort` 对象设置为 `null`。  
  
 `finally` 块将检查 `tempPort` 的值。  如果它不为 null，则方法中的操作失败，并且 `tempPort` 关闭以确保任何资源都被释放。  如果该方法的操作成功，则返回的端口对象将包含打开的 SerialPort 对象，或者，如果操作失败，则将为空。  
  
 [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope_1.vb)]
 [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope_1.vb)]
 [!code-cs[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/CSharp/ca2000-dispose-objects-before-losing-scope_1.cs)]  
  
## 示例  
 默认情况下，[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 编译器检查所有算术运算符是否发生溢出。  因此，任何 Visual Basic 算术运算都可能引发一个 <xref:System.OverflowException>。  这可能导致规则（如 CA2000）上的意外冲突。  例如，下面的 CreateReader1 函数会产生 CA2000 冲突，因为 Visual Basic 编译器针对可能引发导致 StreamReader 不被释放的异常的添加发出溢出检查指令。  
  
 若要解决此问题，您可以在您的项目中禁用通过 Visual Basic 编译器发出溢出检查，或者您可以将您的代码修改为与以下 CreateReader2 函数一样。  
  
 若要禁用发出溢出检查，请在“解决方案资源管理器”中右击项目名称，再单击**“属性”**。  依次单击**“编译”**、**“高级编译选项”**和**“不做整数溢出检查”**。  
  
 [!CODE [FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1](FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1)]  
  
## 请参阅  
 <xref:System.IDisposable>   
 [释放模式](../Topic/Dispose%20Pattern.md)