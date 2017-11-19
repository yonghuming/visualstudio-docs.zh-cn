---
title: "CA1409: Com 可见类型应该是可创建 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c8d9fe357142cf8b95be0298797c4a18e9ee0df7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409：Com 可见类型应该是可创建的
|||  
|-|-|  
|TypeName|ComVisibleTypesShouldBeCreatable|  
|CheckId|CA1409|  
|类别|Microsoft.Interoperability|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 专门标记为可见到组件对象模型 (COM) 的引用类型包含公共的参数化构造函数，但不包含公共的默认 （无参数） 构造函数。  
  
## <a name="rule-description"></a>规则说明  
 不能由 COM 客户端创建没有公共默认构造函数的类型。 但是，类型仍可以通过 COM 客户端如果另一种方法可创建类型并将其传递给客户端 （例如，通过方法调用的返回值）。  
  
 该规则忽略派生自的类型<xref:System.Delegate?displayProperty=fullName>。  
  
 默认情况下，以下是对 COM 可见： 程序集、 公共类型，公共类型中的公共实例成员和公共值类型的所有成员。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，添加公共默认构造函数，或删除<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>从类型。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，如果提供了其他方法来创建并将该对象传递给 COM 客户端。  
  
## <a name="related-rules"></a>相关的规则  
 [CA1017：用 ComVisibleAttribute 标记程序集](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## <a name="see-also"></a>另请参阅  
 [为互操作限定 .NET 类型](/dotnet/framework/interop/qualifying-net-types-for-interoperation)   
 [与非托管代码交互操作](/dotnet/framework/interop/index)