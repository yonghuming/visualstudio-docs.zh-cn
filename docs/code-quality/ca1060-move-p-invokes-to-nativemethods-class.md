---
title: "CA1060：将 P/Invoke 移动到 NativeMethods 类 | Microsoft Docs"
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
  - "MovePInvokesToNativeMethodsClass"
  - "CA1060"
helpviewer_keywords: 
  - "CA1060"
  - "MovePInvokesToNativeMethodsClass"
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1060：将 P/Invoke 移动到 NativeMethods 类
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|MovePInvokesToNativeMethodsClass|  
|CheckId|CA1060|  
|类别|Microsoft.Design|  
|是否重大更改|是|  
  
## 原因  
 某方法使用平台调用服务访问非托管代码，该方法不是任何 **NativeMethods** 类的成员。  
  
## 规则说明  
 平台调用方法（例如，用 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> 特性标记的方法，或者在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中使用 `Declare` 关键字定义的方法）访问非托管代码。  这些方法必须位于下列类之一中：  
  
-   **NativeMethods** \- 此类不取消对非托管代码权限的堆栈审核。（<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> 不能应用于此类。）由于将执行堆栈审核，因此此类适用于可在任意位置使用的方法。  
  
-   **SafeNativeMethods** \- 此类取消对非托管代码权限的堆栈审核。（<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> 应用于此类。）此类适用于任何人都可安全调用的方法。  由于这些方法对于任何调用方来说都是无害的，因此这些方法的调用方无需进行全面的安全检查以确保使用的安全性。  
  
-   **UnsafeNativeMethods** \- 此类取消对非托管代码权限的堆栈审核。（<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> 应用于此类。）此类适用于存在潜在危险的方法。  由于不会执行任何堆栈审核，因此这些方法的任何调用方都必须进行全面的安全检查以确保使用的安全性。  
  
 这些类声明为 `internal`（在 Visual Basic 中为 `Friend`），并声明一个私有构造函数以防止创建新的实例。  这些类中的方法应为 `static` 和 `internal`（在 Visual Basic 中为 `Shared` 和 `Friend`）。  
  
## 如何解决冲突  
 若要解决与此规则的冲突，请将方法移动到适当的 **NativeMethods** 类。  对于大多数应用程序而言，将 P\/Invokes 移动到名为 **NativeMethods** 的新类就足够了。  
  
 但是，如果您在开发要用于其他应用程序的库，则应考虑定义两个名为 **SafeNativeMethods** 和 **UnsafeNativeMethods** 的其他类。  这些类与 **NativeMethods** 类相似，但它们用一个名为 **SuppressUnmanagedCodeSecurityAttribute** 的特殊特性来标记。  应用此特性时，运行时不通过执行完整的堆栈审核来确保所有调用方都拥有 **UnmanagedCode** 权限。  运行时通常在启动时检查此权限。  由于不执行该检查，因此可以显著提高这些非托管方法的调用性能。并且，还允许具有有限权限的代码调用这些方法。  
  
 但是，您应谨慎使用此特性。  如果它未正确实现，就可能有严重的安全含义。  
  
 有关如何实现这些方法的信息，请参见 **NativeMethods** 示例、**SafeNativeMethods** 示例和 **UnsafeNativeMethods** 示例。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例声明一个与该规则冲突的方法。  若要更正该冲突，应将 **RemoveDirectory** P\/Invoke 移动到设计为只存放 P\/Invokes 的适当类。  
  
 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_1.vb)]
 [!code-cs[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_1.cs)]  
  
## NativeMethods 示例  
  
### 说明  
 由于 **NativeMethods** 类不应使用 **SuppressUnmanagedCodeSecurityAttribute** 来标记，因此其中放置的 P\/Invoke 将需要 **UnmanagedCode** 权限。  由于大多数应用程序都从本地计算机中运行并在完全信任下一起运行，因此这通常不是问题。  但是，如果您在开发可重用的库，则应考虑定义一个 **SafeNativeMethods** 或 **UnsafeNativeMethods** 类。  
  
 下面的示例演示从 user32.dll 中包装 **MessageBeep** 函数的 **Interaction.Beep** 方法。  **MessageBeep** P\/Invoke 放置在 **NativeMethods** 类中。  
  
### 代码  
 [!code-cs[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_2.cs)]
 [!code-vb[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_2.vb)]  
  
## SafeNativeMethods 示例  
  
### 说明  
 可以安全地向任何应用程序公开并且没有任何负面影响的 P\/Invoke 方法应放置在名为 **SafeNativeMethods** 的类中。  您无需要求权限，也无需过多关注调用位置。  
  
 下面的示例演示从 kernel32.dll 中包装 **GetTickCount** 函数的 **Environment.TickCount** 属性。  
  
### 代码  
 [!CODE [FxCop.Design.NativeMethodsSafe#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe#1)]  
  
## UnsafeNativeMethods 示例  
  
### 说明  
 无法安全地调用而且可能造成负面影响的 P\/Invoke 方法应放置在名为 **UnSafeNativeMethods** 的类中。  应对这些方法进行严格检查，以确保未在无意中向用户公开这些方法。  [CA2118：检查 SuppressUnmanagedCodeSecurityAttribute 用法](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)这条规则对此有所帮助。  或者，在使用这些方法时，它们应该具有代替 **UnmanagedCode** 要求的另一个权限。  
  
 下面的示例演示从 user32.dll 中包装 **ShowCursor** 函数的 **Cursor.Hide** 方法。  
  
### 代码  
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_3.vb)]
 [!code-cs[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_3.cs)]  
  
## 请参阅  
 [设计警告](../code-quality/design-warnings.md)