---
title: "CA1412： 将 ComSource 接口标记为 IDispatch |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b8a53053588670fef616f4df7633b3a25fb45712
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412：将 ComSource 接口标记为 IDispatch
|||  
|-|-|  
|TypeName|MarkComSourceInterfacesAsIDispatch|  
|CheckId|CA1412|  
|类别|Microsoft.Interoperability|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 类型将标有<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>属性和至少一个指定的接口未用标记<xref:System.Runtime.InteropServices.InterfaceTypeAttribute>属性设置为`InterfaceIsDispatch`值。  
  
## <a name="rule-description"></a>规则说明  
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>用于标识向组件对象模型 (COM) 客户端类公开的事件接口。 这些接口必须公开为`InterfaceIsIDispatch`若要启用 Visual Basic 6 COM 客户端接收事件通知。 默认情况下，如果接口未用标记<xref:System.Runtime.InteropServices.InterfaceTypeAttribute>属性，它作为双重接口公开。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，添加或修改<xref:System.Runtime.InteropServices.InterfaceTypeAttribute>特性，使其值设为使用指定的所有接口 InterfaceIsIDispatch<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>属性。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
## <a name="example"></a>示例  
 下面的示例演示一个类的实例之一与该规则的冲突。  
  
 [!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA1408：请不要使用 AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)  
  
## <a name="see-also"></a>另请参阅  
 [如何：引发 COM 接收器所处理的事件](http://msdn.microsoft.com/en-us/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd)   
 [与非托管代码交互操作](/dotnet/framework/interop/index)