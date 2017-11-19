---
title: "CA1063： 实现 IDisposable 正确 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 55784b95f12d83318b8d217282c3a2bb8933d76b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063：正确实现 IDisposable
|||  
|-|-|  
|TypeName|ImplementIDisposableCorrectly|  
|CheckId|CA1063|  
|类别|Microsoft.Design|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 `IDisposable`实现不正确。 这里列出了此问题的一些原因：  
  
-   在类中重新实现 IDisposable。  
  
-   完成重新中被重写。  
  
-   释放被重写。  
  
-   Dispose （） 不是公共的密封类，或名为释放。  
  
-   Dispose(bool) 不是受保护、 虚拟的或未密封。  
  
-   在未密封的类型，dispose （） 必须调用 Dispose(true)。  
  
-   对于未密封的类型，Finalize 实现不调用其中一种或两个 Dispose(bool) 或事例类终结器。  
  
 任何一种这些模式的冲突将触发此警告。  
  
 每个未密封的根 IDisposable 的类型必须提供其自己受保护的虚拟 void Dispose(bool) 方法。 Dispose （） 应调用 Dipose(true) 和 Finalize 应调用 Dispose(false)。 如果要创建未密封的根 IDisposable 的类型，你必须定义 Dispose(bool)，调用它。 有关详细信息，请参阅[清洗向上非托管资源](/dotnet/standard/garbage-collection/unmanaged)中[Framework 设计准则](/dotnet/standard/design-guidelines/index).NET Framework 文档的部分。  
  
## <a name="rule-description"></a>规则说明  
 所有的 IDisposable 类型都应当正确实现 Dispose 模式。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 检查你的代码并确定哪些以下解决方法将修复此冲突。  
  
-   从的由 {0} 实现，而是重写基类释放实现的接口列表中删除 IDisposable。  
  
-   从类型 {0} 中删除终结器，重写释放 （bool 释放），并且将终止逻辑放入的代码路径其中释放是 false。  
  
-   删除 {0}，重写释放 （bool 释放），并且将释放逻辑放入的代码路径其中释放为 true。  
  
-   请确保该 {0} 被声明为公共和密封。  
  
-   重命名为释放"{0}，并确保它被声明为公共和密封。  
  
-   请确保该 {0} 声明为受保护，虚拟的并且未密封。  
  
-   修改 {0}，使它调用 Dispose(true)，然后调用 GC。当前对象实例上的 SuppressFinalize (this 或 Me 中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])，然后返回。  
  
-   修改 {0}，以便它调用 Dispose(false)，然后返回。  
  
-   如果你正在编写一个未密封的根 IDisposable 的类，请确保 IDisposable 的实现遵循本节中前面介绍的模式。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
## <a name="pseudo-code-example"></a>伪代码示例  
 下面的伪代码提供应如何使用托管的类中实现 Dispose(bool) 和本机资源的常规示例。  
  
```  
public class Resource : IDisposable   
{  
    private IntPtr nativeResource = Marshal.AllocHGlobal(100);  
    private AnotherResource managedResource = new AnotherResource();  
  
// Dispose() calls Dispose(true)  
    public void Dispose()  
    {  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
    // NOTE: Leave out the finalizer altogether if this class doesn't   
    // own unmanaged resources itself, but leave the other methods  
    // exactly as they are.   
    ~Resource()   
    {  
        // Finalizer calls Dispose(false)  
        Dispose(false);  
    }  
    // The bulk of the clean-up code is implemented in Dispose(bool)  
    protected virtual void Dispose(bool disposing)  
    {  
        if (disposing)   
        {  
            // free managed resources  
            if (managedResource != null)  
            {  
                managedResource.Dispose();  
                managedResource = null;  
            }  
        }  
        // free native resources if there are any.  
        if (nativeResource != IntPtr.Zero)   
        {  
            Marshal.FreeHGlobal(nativeResource);  
            nativeResource = IntPtr.Zero;  
        }  
    }  
}  
```