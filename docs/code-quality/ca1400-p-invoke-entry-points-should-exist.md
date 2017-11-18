---
title: "CA1400: P Invoke 入口点应该存在 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1400
- PInvokeEntryPointsShouldExist
helpviewer_keywords:
- PInvokeEntryPointsShouldExist
- CA1400
ms.assetid: 1d64e470-7b2f-4cca-8fb0-ac92829e6332
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: dd92619a652255f67c1e1558c40ea05840cd0eb5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400：P/Invoke 入口点应该存在
|||  
|-|-|  
|TypeName|PInvokeEntryPointsShouldExist|  
|CheckId|CA1400|  
|类别|Microsoft.Interoperability|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 公共或受保护的方法标记为<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>。 未能找到非托管库，或者未能将方法与库中的函数匹配。 如果规则找不到方法名称，严格按照指定，则查找 ANSI 或方法的宽字符版本通过在 A 或 W 的方法名。 如果不找到任何匹配项，则该规则将尝试使用 __stdcall 名称格式中定位函数 (_MyMethod@12，其中，12 表示自变量的长度)。 如果未找到匹配，并且方法名称以 '#' 开头，该规则会搜索该函数作为序号引用而非名称引用。  
  
## <a name="rule-description"></a>规则说明  
 没有编译时检查是可用于确保方法标记有<xref:System.Runtime.InteropServices.DllImportAttribute>位于引用非托管 DLL 中。 如果没有具有指定的名称的函数是在库中，或该方法的自变量不匹配的函数自变量，公共语言运行时将引发异常。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，更改该方法具有<xref:System.Runtime.InteropServices.DllImportAttribute>属性。 请确保非托管的库存在并处于正在与包含该方法的程序集相同的目录。 如果库已存在并正确引用，请验证方法名称、 返回类型和自变量签名匹配的库函数。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 与引用它的托管程序集位于同一目录中的非托管的库时不禁止显示此规则的警告。 它可以安全地禁止显示此规则在其中的非托管的库找不到的情况下的警告。  
  
## <a name="example"></a>示例  
 下面的示例演示与该规则冲突的类型。 函数名为`DoSomethingUnmanaged`kernel32.dll 中发生。  
  
 [!code-csharp[FxCop.Interoperability.DLLExists#1](../code-quality/codesnippet/CSharp/ca1400-p-invoke-entry-points-should-exist_1.cs)]  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>