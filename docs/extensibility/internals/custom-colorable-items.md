---
title: "自定义可着色的项 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "可着色的项"
  - "语言服务，自定义可着色的项"
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# 自定义可着色的项
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

您可以重写的类型的列表着色，关键字和注释，例如通过实现自定义可着色的项作为语言服务的一部分。  
  
## 可着色的项的用户设置  
 您可以显示 **字体和颜色** 对话框中选择 **选项** 上 **工具** 菜单上，，然后选择 **字体和颜色** 下 **环境**。 当您选择显示，如 **文本编辑器** 或 **命令窗口**, 、 **显示项** 列表框中显示的显示的所有可着色的项。 您可以查看和更改字体、 大小、 前景颜色和每个可着色的项的背景色。 您的选择将存储在注册表中的缓存，并且通过可着色的项名称访问。  
  
## 可着色的项的演示文稿  
 由于 IDE 处理着色中的项的用户重写，因此 **字体和颜色** 对话框中，您需要仅提供一个名称与每个自定义可着色的项。 此名称就是显示在 **显示项** 列表。 按字母顺序显示可着色的项。 语言服务的自定义可着色的项目进行分组，可以开始使用你语言的名称，每个名称，例如 **NewLanguage\-注释** 和 **NewLanguage\-关键字**。  
  
> [!CAUTION]
>  应可着色的项名称，以避免冲突与现有的可着色的项名称中包括的语言名称。 如果您在开发过程中更改其中一个您可着色的项的名称，必须重置已访问了你可着色的项在首次创建缓存。 您可以重置实验 CreateExpInstance 工具，它随 Visual Studio SDK，通常在目录中缓存  
>   
>  **C:\\Program 文件 \(x86\) \\Microsoft Visual Studio 14.0\\VSSDK\\VisualStudioIntegration\\Tools\\Bin**  
>   
>  若要重置缓存，请调用 `CreateExpInstance /Reset`。 有关 CreateExpInstance 详细信息，请参阅 [CreateExpInstance 实用程序](../../extensibility/internals/createexpinstance-utility.md)。  
  
 永远不会引用可着色的项列表中的第一项。 第一项对应于可着色的项索引为 0，和 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 总是提供的默认文本颜色和为该项的属性。 处理此未引用的项的最简单方法是提供占位符可着色的项在列表中列为第一个项。  
  
## 实现自定义可着色的项  
  
1.  定义什么必须在您的语言，例如关键字、 运算符和标识符着色。  
  
2.  创建这些可着色的项的枚举。  
  
3.  将从使用枚举值的扫描仪或分析器返回的令牌类型相关联。  
  
     例如，表示令牌的类型的值可能是自定义可着色的项枚举中的相同值。  
  
4.  实现过程中 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 方法在您 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 对象，请使用对应于从分析器或扫描仪返回的令牌类型您自定义可着色的项枚举的值填充属性列表。  
  
5.  同一个类中实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> 接口，实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> 接口和其两个方法， <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> 和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>。  
  
6.  实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> 接口。  
  
7.  如果你想要支持 24 位或高颜色值，还应实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> 接口。  
  
8.  在语言服务对象，创建列表，其中包含您 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> 对象，一个分析器或者扫描仪可以确定每个可着色的项。  
  
     可以通过使用自定义可着色的项枚举中的相应值来访问列表中的每个项。 插入列表中，作为索引中使用的枚举值。 在列表中的第一项永远不会访问，因为它对应于默认文本样式， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 始终处理本身。 可以通过在您的列表的开头插入占位符可着色的项来对此进行补偿。  
  
9. 实现过程中 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> 方法中，在您的自定义可着色的项列表中返回的项数。  
  
10. 实现过程中 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> 方法中，从列表中返回请求可着色的项。  
  
 有关如何实现的示例 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> 和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> 接口，请参阅 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>。  
  
## 请参阅  
 [旧语言服务模型](../../extensibility/internals/model-of-a-legacy-language-service.md)   
 [语法着色中自定义编辑器](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [语法着色在传统语言服务](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [实现功能: 语法着色](../../extensibility/internals/implementing-syntax-coloring.md)   
 [如何: 使用内置可着色的项](../../extensibility/internals/how-to-use-built-in-colorable-items.md)