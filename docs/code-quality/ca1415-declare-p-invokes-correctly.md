---
title: "CA1415: P 调用正确声明 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a9edc52bbc1cd05ed1a3a726dcfb49f26574ccc1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415：正确声明 P/Invoke
|||  
|-|-|  
|TypeName|DeclarePInvokesCorrectly|  
|CheckId|CA1415|  
|类别|Microsoft.Interoperability|  
|是否重大更改|无间断-如果将参数声明 P/Invoke 无法程序集外可见。 中断性-如果将参数声明 P/Invoke 可以程序集外可见。|  
  
## <a name="cause"></a>原因  
 平台调用方法未正确声明。  
  
## <a name="rule-description"></a>规则说明  
 平台调用方法访问非托管的代码，而且使用定义`Declare`中的关键字[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]或<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>。 目前，此规则查找针对平台调用目标有一个指针指向 OVERLAPPED 结构参数的 Win32 函数的方法声明和对应的托管的参数不是一个指向<xref:System.Threading.NativeOverlapped?displayProperty=fullName>结构。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，正确声明平台调用方法。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
## <a name="example"></a>示例  
 平台调用方法，与该规则冲突并满足该规则的以下示例所示。  
  
 [!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../code-quality/codesnippet/CSharp/ca1415-declare-p-invokes-correctly_1.cs)]  
  
## <a name="see-also"></a>另请参阅  
 [与非托管代码交互操作](/dotnet/framework/interop/index)