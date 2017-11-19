---
title: "自定义可着色项 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b637e59b1e436c42b6b15f0dddaa1ed2ef6ff03c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="custom-colorable-items"></a>自定义可着色项
你可以重写类型的列表着色，如关键字和注释，通过实现自定义可着色项作为语言服务的一部分。  
  
## <a name="user-settings-of-colorable-items"></a>着色的项的用户设置  
 可以显示**字体和颜色**对话框中，通过选择**选项**上**工具**菜单上，，然后选择**字体和颜色**下**环境**。 当您选择显示，如**文本编辑器**或**命令窗口**、**显示项**列表框中显示该显示的着色的所有项。 你可以查看和更改字体、 大小、 前景颜色和每个可着色的项的背景色。 你的选择在注册表中缓存中存储和访问着色该项的名称。  
  
## <a name="presentation-of-colorable-items"></a>表示法的可着色项  
 因为 IDE 可处理的可着色项中的用户重写**字体和颜色**对话框中，你需要仅提供一个名称与每个自定义可着色项。 此名称将会出现在**显示项**列表。 按字母顺序显示可着色的项。 要进行分组语言服务的自定义可着色项，可以开始使用你语言的名称，每个名称，例如**NewLanguage-注释**和**NewLanguage-关键字**。  
  
> [!CAUTION]
>  你应在着色项名称，以避免与现有着色项名称冲突中包含的语言名称。 如果在开发期间更改其中一个着色项的名称，必须重置缓存创建第一次可着色项的访问。 你可以重置实验缓存的 CreateExpInstance 工具，它随 Visual Studio SDK，通常在目录中安装  
>   
>  **C:\Program 文件 (x86) \Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin**  
>   
>  若要重置缓存，调用`CreateExpInstance /Reset`。 有关 CreateExpInstance 的详细信息，请参阅[CreateExpInstance 实用工具](../../extensibility/internals/createexpinstance-utility.md)。  
  
 永远不会引用可着色项列表中的第一项。 第一项对应于着色项索引为 0，和[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]始终提供的默认文本颜色和该项的属性。 处理此未引用的项的最简单方法是提供你为第一项的列表中的占位符着色项。  
  
## <a name="implementing-custom-colorable-items"></a>实现自定义可着色项  
  
1.  定义什么必须在你的语言，例如关键字、 运算符和标识符着色。  
  
2.  创建这些可着色的项的枚举。  
  
3.  将从分析器或具有枚举值的扫描程序返回的令牌类型相关联。  
  
     例如，表示令牌的类型的值可能是自定义可着色项枚举中的相同值。  
  
4.  实现中<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法在你<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>对象，你从分析器或扫描程序返回的令牌类型所对应的自定义可着色项枚举中的值填充属性列表中。  
  
5.  同一个类中实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>接口，实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>接口和其两个方法，<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A>和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>。  
  
6.  实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> 接口。  
  
7.  如果你想要支持 24 位或高颜色值，还实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>接口。  
  
8.  在语言服务对象，创建的列表包含你<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>对象，每个可着色项分析器或扫描程序可以识别的一个对象。  
  
     你可以使用自定义可着色项枚举中的相应值来访问列表中的每个项。 使用作为索引到列表的枚举值。 绝不会访问列表中的第一个项，因为它对应于默认文本样式，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]始终处理本身。 可以通过在你列表的开头插入一个占位符着色项对此进行补偿。  
  
9. 实现中<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A>方法，你可着色的自定义项的列表中返回的项数。  
  
10. 实现中<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>方法，从列表中返回请求的着色项。  
  
 有关如何实现的示例<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>接口，请参阅<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>。  
  
## <a name="see-also"></a>另请参阅  
 [旧语言服务模型](../../extensibility/internals/model-of-a-legacy-language-service.md)   
 [语法着色中自定义编辑器](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [语法着色中旧语言服务](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [实现语法着色](../../extensibility/internals/implementing-syntax-coloring.md)   
 [如何：使用内置的可着色项](../../extensibility/internals/how-to-use-built-in-colorable-items.md)