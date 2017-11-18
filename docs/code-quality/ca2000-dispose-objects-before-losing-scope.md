---
title: "Ca2000： 超出范围前释放对象 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2000
- Dispose objects before losing scope
- DisposeObjectsBeforeLosingScope
helpviewer_keywords:
- CA2000
- DisposeObjectsBeforeLosingScope
ms.assetid: 0c3d7d8d-b94d-46e8-aa4c-38df632c1463
caps.latest.revision: "32"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 81c553a9ae45ed44e8c5d96f49f2063e6383e5ea
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000：超出范围前释放对象
|||  
|-|-|  
|TypeName|DisposeObjectsBeforeLosingScope|  
|CheckId|CA2000|  
|类别|Microsoft.Reliability|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 一个本地对象<xref:System.IDisposable>创建类型，但对对象的所有引用超出范围之前，不释放此对象。  
  
## <a name="rule-description"></a>规则说明  
 如果之前对它的所有引用超出范围，没有显式释放可释放的对象，则将在某个不确定的时间，垃圾回收器运行终结器的对象时释放此对象。 因为可能会发生异常事件，以避免终结器中运行的对象，该对象应显式释放相反。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，调用<xref:System.IDisposable.Dispose%2A>上之前对它的所有引用超出范围的对象。  
  
 请注意，你可以使用`using`语句 (`Using`中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 来包装实现的对象`IDisposable`。 以这种方式包装的对象将自动释放在结束时的`using`块。  
  
 以下是某些情况下，使用语句不足以保护 IDisposable 的对象，并可以导致 CA2000 发生。  
  
-   返回可释放的对象需要对象在外部使用 try/finally 块中的构造块。  
  
-   初始化可释放对象的成员不应在构造函数中的 using 语句。  
  
-   嵌套只能通过一个异常处理程序保护的构造函数。 例如，  
  
    ```csharp
    using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))  
    { ... }  
    ```
  
     导致 CA2000 发生因为 StreamReader 对象的构造中的失败可能会导致永远不会关闭的 FileStream 对象。  
  
-   动态对象应使用卷影对象来实现 IDisposable 的对象的释放模式。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不要禁止显示此规则发出的警告，除非您对您的对象调用了一个方法，而该方法调用 `Dispose`，例如 <xref:System.IO.Stream.Close%2A>；或者，如果引发警告的方法返回一个包装您的对象的 IDisposable 对象。  
  
## <a name="related-rules"></a>相关的规则  
 [CA2213：应释放可释放的字段](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
 [CA2202：不要多次释放对象](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)  
  
## <a name="example"></a>示例  
 如果你要实现返回一个可释放的对象的方法，使用 try/finally 块没有 catch 块来确保释放该对象。 通过使用 try/finally 块，你需要允许例外，以便在错误点引发，并确保释放该对象。  
  
 在 OpenPort1 方法中，以打开 ISerializable 对象无效/不调用或对 SomeMethod 的调用可能会失败。 此实现将引发 CA2000 警告。  
  
 在 OpenPort2 方法中，两个无效/不对象是声明并且已设置为 null:  
  
-   `tempPort`用于测试方法操作是否成功。  
  
-   `port`它用于方法的返回值。  
  
 `tempPort`构造并打开在`try`块，以及任何其他所需同一中执行工作`try`块。 在结束`try`块中，打开的端口分配给`port`将返回的对象和`tempPort`对象设置为`null`。  
  
 `finally`块检查的值`tempPort`。 如果不为 null，在方法中的操作已失败，和`tempPort`关闭以确保释放任何资源。 如果方法的操作成功，或如果操作失败，则将为空，则返回的端口对象将包含打开无效/不对象。  

```csharp
public SerialPort OpenPort1(string portName)
{
   SerialPort port = new SerialPort(portName);
   port.Open();  //CA2000 fires because this might throw
   SomeMethod(); //Other method operations can fail
   return port;
}

public SerialPort OpenPort2(string portName)
{
   SerialPort tempPort = null;
   SerialPort port = null;
   try
   {
      tempPort = new SerialPort(portName);
      tempPort.Open();
      SomeMethod();
      //Add any other methods above this line
      port = tempPort;
      tempPort = null;
      
   }
   finally
   {
      if (tempPort != null)
      {
         tempPort.Close();
      }
   }
   return port;
}
```

```vb
Public Function OpenPort1(ByVal PortName As String) As SerialPort

   Dim port As New SerialPort(PortName)
   port.Open()    'CA2000 fires because this might throw
   SomeMethod()   'Other method operations can fail
   Return port

End Function


Public Function OpenPort2(ByVal PortName As String) As SerialPort

   Dim tempPort As SerialPort = Nothing
   Dim port As SerialPort = Nothing

   Try
      tempPort = New SerialPort(PortName)
      tempPort.Open()
      SomeMethod()
      'Add any other methods above this line
      port = tempPort
      tempPort = Nothing

   Finally
      If Not tempPort Is Nothing Then
         tempPort.Close()
      End If


   End Try

   Return port

End Function
```
 
## <a name="example"></a>示例  
 默认情况下，[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]编译器已溢出检查的所有算术运算符。 因此，可能会引发任何 Visual Basic 算术运算<xref:System.OverflowException>。 这可能导致意外的冲突规则 （如 CA2000） 中。 例如，以下 CreateReader1 函数将生成 CA2000 冲突，因为 Visual Basic 编译器发出溢出检查用于可能会引发异常的会导致无法释放 StreamReader 添加指令。  
  
 若要解决此问题，您可以禁用你的项目中的 Visual Basic 编译器发出溢出检查，或者您可以修改代码，如下面的 CreateReader2 函数中所示。  
  
 要禁用发出溢出检查，请右键单击解决方案资源管理器中的项目名称，然后单击**属性**。 单击**编译**，单击**高级编译选项**，，然后检查**删除整数溢出检查**。  
  
  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope-vboverflow_1.vb)]

## <a name="see-also"></a>另请参阅  
 <xref:System.IDisposable>   
 [释放模式](/dotnet/standard/design-guidelines/dispose-pattern)