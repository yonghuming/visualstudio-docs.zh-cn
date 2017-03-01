---
title: "扩展编辑器和语言服务 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 4d04f4588b1005e9b5ccb42c6042d01aacb45710
ms.lasthandoff: 02/22/2017

---
# <a name="extending-the-editor-and-language-services"></a>扩展编辑器和语言服务
您可以将语言服务功能 （如 IntelliSense) 添加到您自己的编辑器和扩展 Visual Studio 代码编辑器中的大多数功能。  您可以扩展的完整列表，请参阅[语言服务和编辑器扩展点](../extensibility/language-service-and-editor-extension-points.md)。  
  
 使用 Managed Extensibility Framework (MEF) 来扩展编辑器的大部分功能。 例如，如果您想要扩展的编辑器功能，语法突出显示您可以编写 MEF*组成部分*，它定义要为其不同的颜色和要如何处理它们的分类。 该编辑器还支持相同的功能的多个扩展名。  
  
 编辑器的表示层基于 Windows Presentation Framework (WPF)。 WPF 图形库提供灵活的文本格式，并还提供了图形和动画之类的可视化效果。  
  
 Visual Studio SDK 提供了适配器称为*填充码*以支持 VSPackages 迁移为早期版本编写的。 不过，如果您有现有的 VSPackage，我们建议您向新的技术，以获得更好的性能和可靠性更新它。  
  
## <a name="related-topics"></a>相关主题  
  
|标题|说明|  
|-----------|-----------------|  
|[语言服务和编辑器扩展入门](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|说明如何创建编辑器的扩展。|  
|[在编辑器内](../extensibility/inside-the-editor.md)|描述编辑器的一般结构并列出它的某些功能。|  
|[在编辑器中的托管可扩展性框架](../extensibility/managed-extensibility-framework-in-the-editor.md)|说明如何使用编辑器使用 Managed Extensibility Framework (MEF)。|  
|[语言服务和编辑器扩展点](../extensibility/language-service-and-editor-extension-points.md)|列出编辑器中的扩展点。 扩展点表示的编辑器功能，可以对其进行扩展。|  
|[演练︰ 创建视图修饰、 命令和设置 （列指南）](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|遍历并介绍了构建绘制列 gudie 线，以帮助您使代码保持为显示宽度视图修饰。  此外显示读取和写入设置，以及声明和实现可以在命令窗口中调用的命令。|  
|[编辑器中导入](../extensibility/editor-imports.md)|列出扩展可以导入的服务。|  
|[调整到编辑器的旧代码](../extensibility/adapting-legacy-code-to-the-editor.md)|解释不同的方法，以适应旧代码 (预 Visual Studio 2010) 来扩展编辑器。|  
|[迁移早期语言服务](../extensibility/internals/migrating-a-legacy-language-service.md)|说明如何迁移 VSPackage 基于语言服务。|  
|[演练︰ 将内容类型链接到的文件扩展名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|演示如何将内容类型链接到的文件扩展名。|  
|[演练︰ 创建边缘字形](../extensibility/walkthrough-creating-a-margin-glyph.md)|演示如何将图标添加到边距。|  
|[演练︰ 突出显示文本](../extensibility/walkthrough-highlighting-text.md)|演示如何使用*标记*以突出显示文本。|  
|[演练︰ 大纲显示](../extensibility/walkthrough-outlining.md)|演示如何将添加特定类型的大括号的大纲显示。|  
|[演练︰ 显示匹配的大括号](../extensibility/walkthrough-displaying-matching-braces.md)|演示如何突出显示匹配的大括号。|  
|[演练︰ 显示快速信息工具提示](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|演示如何显示快速信息弹出窗口，用于描述代码如属性、 方法和事件的元素。|  
|[演练︰ 显示签名帮助](../extensibility/walkthrough-displaying-signature-help.md)|演示如何显示在签名中提供的数量和类型的参数有关的信息的弹出窗口。|  
|[演练：显示语句完成](../extensibility/walkthrough-displaying-statement-completion.md)|演示如何实现语句结束。|  
|[演练︰ 实现代码段](../extensibility/walkthrough-implementing-code-snippets.md)|演示如何实现代码段扩展。|  
|[演练︰ 显示变量的灯泡图标的建议](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|演示如何以显示电灯泡有关代码的建议。|  
|[演练︰ 使用外壳命令与编辑器扩展](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|演示如何将菜单命令在 VSPackage 中的与 MEF 组件相关联。|  
|[演练︰ 使用快捷键与编辑器扩展](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|演示如何将在 VSPackage 中的菜单快捷方式与 MEF 组件相关联。|  
|[托管可扩展性框架 (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|提供有关 Managed Extensibility Framework (MEF) 的信息。|  
|[Windows Presentation Foundation](http://msdn.microsoft.com/Library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|提供有关 Windows Presentation Foundation (WPF) 的信息。|  
  
## <a name="reference"></a>参考  
 Visual Studio 编辑器包含以下命名空间。  
  
 <xref:Microsoft.VisualStudio.Language.Intellisense></xref:Microsoft.VisualStudio.Language.Intellisense>  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification></xref:Microsoft.VisualStudio.Language.StandardClassification>  
  
 <xref:Microsoft.VisualStudio.Editor></xref:Microsoft.VisualStudio.Editor>  
  
 <xref:Microsoft.VisualStudio.Text></xref:Microsoft.VisualStudio.Text>  
  
 <xref:Microsoft.VisualStudio.Text.Adornments></xref:Microsoft.VisualStudio.Text.Adornments>  
  
 <xref:Microsoft.VisualStudio.Text.Classification></xref:Microsoft.VisualStudio.Text.Classification>  
  
 <xref:Microsoft.VisualStudio.Text.Differencing></xref:Microsoft.VisualStudio.Text.Differencing>  
  
 <xref:Microsoft.VisualStudio.Text.Document></xref:Microsoft.VisualStudio.Text.Document>  
  
 <xref:Microsoft.VisualStudio.Text.Editor></xref:Microsoft.VisualStudio.Text.Editor>  
  
 <xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods></xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods>  
  
 <xref:Microsoft.VisualStudio.Text.Formatting></xref:Microsoft.VisualStudio.Text.Formatting>  
  
 <xref:Microsoft.VisualStudio.Text.IncrementalSearch></xref:Microsoft.VisualStudio.Text.IncrementalSearch>  
  
 <xref:Microsoft.VisualStudio.Text.Operations></xref:Microsoft.VisualStudio.Text.Operations>  
  
 <xref:Microsoft.VisualStudio.Text.Outlining></xref:Microsoft.VisualStudio.Text.Outlining>  
  
 <xref:Microsoft.VisualStudio.Text.Projection></xref:Microsoft.VisualStudio.Text.Projection>  
  
 <xref:Microsoft.VisualStudio.Text.Tagging></xref:Microsoft.VisualStudio.Text.Tagging>  
  
 <xref:Microsoft.VisualStudio.Utilities></xref:Microsoft.VisualStudio.Utilities>
