---
title: "CA2232： 使用 STAThread 标记 Windows 窗体入口点 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6dadac882d5a1b6bf96e4cb0f713979ff566116f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232：使用 STAThread 标记 Windows 窗体的入口点
|||  
|-|-|  
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|  
|CheckId|CA2232|  
|类别|Microsoft.Usage|  
|是否重大更改|非重大更改|  
  
## <a name="cause"></a>原因  
 程序集引用<xref:System.Windows.Forms>命名空间，并且其入口点未用标记<xref:System.STAThreadAttribute?displayProperty=fullName>属性。  
  
## <a name="rule-description"></a>规则说明  
 <xref:System.STAThreadAttribute>指示的 COM 线程模型为应用程序是单线程单元。 使用 Windows 窗体的任何应用程序的入口点上必须存在此特性；如果没有此特性，则 Windows 组件可能无法正常工作。 如果该属性不存在，则应用程序使用多线程的单元模型，这不支持为 Windows 窗体。  
  
> [!NOTE]
>  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]使用应用程序框架的项目不需要将标记**Main**使用 STAThread 的方法。 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]编译器自动执行。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，将添加<xref:System.STAThreadAttribute>属性设为入口点。 如果<xref:System.MTAThreadAttribute?displayProperty=fullName>特性不存在，将其删除。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，如果你正在开发的.NET Compact Framework 中，为其<xref:System.STAThreadAttribute>属性是不必要和不受支持。  
  
## <a name="example"></a>示例  
 下面的示例演示的正确用法<xref:System.STAThreadAttribute>。  
  
 [!code-csharp[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
 [!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]