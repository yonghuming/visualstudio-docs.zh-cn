---
title: "CA1060： 移动 P-时，将调用到 NativeMethods 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
helpviewer_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bb93a44eebd9380499394c612ee12c40d0c62271
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1060-move-pinvokes-to-nativemethods-class"></a>CA1060：将 P/Invoke 移动到 NativeMethods 类
|||  
|-|-|  
|TypeName|MovePInvokesToNativeMethodsClass|  
|CheckId|CA1060|  
|类别|Microsoft.Design|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 某方法使用平台调用服务访问非托管的代码，并且不是成员之一的**NativeMethods**类。  
  
## <a name="rule-description"></a>规则说明  
 平台调用方法，如那些使用标记<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>属性或通过使用定义的方法`Declare`中的关键字[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]，访问非托管的代码。 这些方法应处于以下类之一：  
  
-   **NativeMethods** -此类不会取消对非托管的代码权限的堆栈审核。 (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>必须不能应用于此类。)此类是用于可以任意位置使用，因为将执行堆栈审核的方法。  
  
-   **SafeNativeMethods** -此类取消非托管的代码权限的堆栈审核。 (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>应用于此类。)此类适用于的是安全的任何人都能够调用的方法。 这些方法的调用方不需要执行全面的安全检查，以确保使用的安全性，因为方法都是无害的任何调用方。  
  
-   **UnsafeNativeMethods** -此类取消非托管的代码权限的堆栈审核。 (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>应用于此类。)此类是潜在的危险的方法。 这些方法的任何调用方必须不执行全面的安全检查，以确保使用的安全性，因为将执行任何堆栈审核。  
  
 这些类声明为`internal`(`Friend`，在 Visual Basic 中)，并声明一个私有构造函数来阻止从正在创建的新实例。 这些类中的方法应`static`和`internal`(`Shared`和`Friend`在 Visual Basic 中)。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，请将方法移到相应**NativeMethods**类。 对于大多数应用程序，将 P/Invoke 移动到名为的新类**NativeMethods**就足够了。  
  
 但是，如果你正在开发的其他应用程序中使用的库，则应考虑定义两个调用其他类**SafeNativeMethods**和**UnsafeNativeMethods**。 这些类类似于**NativeMethods**类; 但是，被调用的特殊特性来标记**SuppressUnmanagedCodeSecurityAttribute**。 应用此属性时，运行时不执行完整的堆栈审核，以确保所有调用方拥有**UnmanagedCode**权限。 通常情况下，运行时所检查在启动此权限。 不执行该检查，因为它可以极大地提高对这些非托管方法的调用的性能，它还使具有有限的权限，以调用这些方法的代码。  
  
 但是，你应谨慎使用此属性。 如果它不正确地实现，也可能产生严重的安全隐患...  
  
 有关如何实现方法的信息，请参阅**NativeMethods**示例中， **SafeNativeMethods**示例中，和**UnsafeNativeMethods**示例。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
## <a name="example"></a>示例  
 下面的示例声明违反此规则的方法。 若要更正冲突， **RemoveDirectory**应将 P/Invoke 移动到适当的类，用于保存仅 P/Invoke。  
  
 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_1.vb)]
 [!code-csharp[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_1.cs)]  
  
## <a name="nativemethods-example"></a>NativeMethods 示例  
  
### <a name="description"></a>描述  
 因为**NativeMethods**不应使用标记为类**SuppressUnmanagedCodeSecurityAttribute**，将需要放入其中的 P/Invokes **UnmanagedCode**权限。 由于大多数应用程序从本地计算机上运行，并且完全信任下一起运行，这通常不是一个问题。 但是，如果你正在开发可重用库，则应考虑定义**SafeNativeMethods**或**UnsafeNativeMethods**类。  
  
 下面的示例演示**Interaction.Beep**方法包装**MessageBeep**从 user32.dll 函数。 **MessageBeep** P/Invoke 放在**NativeMethods**类。  
  
### <a name="code"></a>代码  
 [!code-csharp[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_2.cs)]
 [!code-vb[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_2.vb)]  
  
## <a name="safenativemethods-example"></a>SafeNativeMethods 示例  
  
### <a name="description"></a>描述  
 P/Invoke 方法，可以安全地公开的任何应用程序且不具有任何方面的副作用将被放入名为的类**SafeNativeMethods**。 无需支付极大的关注到其中从调用并不一定需权限。  
  
 下面的示例演示**Environment.TickCount**包装的属性**GetTickCount**从 kernel32.dll 函数。  
  
### <a name="code"></a>代码  
 [!code-vb[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_3.vb)]
 [!code-csharp[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_3.cs)]  
  
## <a name="unsafenativemethods-example"></a>UnsafeNativeMethods 示例  
  
### <a name="description"></a>描述  
 P/Invoke 方法，不能安全地调用和，可能会导致副作用将被放入名为的类**UnsafeNativeMethods**。 应严格检查这些方法，以确保它们不向公开用户无意中。 规则[CA2118： 检查 SuppressUnmanagedCodeSecurityAttribute 用法](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)对此有所帮助。 或者，方法应具有另一个权限，而不是要求**UnmanagedCode**当它们使用的位置。  
  
 下面的示例演示**Cursor.Hide**方法包装**ShowCursor**从 user32.dll 函数。  
  
### <a name="code"></a>代码  
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_4.vb)]
 [!code-csharp[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_4.cs)]  
  
## <a name="see-also"></a>另请参阅  
 [设计警告](../code-quality/design-warnings.md)