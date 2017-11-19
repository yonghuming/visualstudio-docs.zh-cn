---
title: "扩展编辑器和语言服务 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8490ddefaca1d170c1dbf379364cdf91b41b7803
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="extending-the-editor-and-language-services"></a>扩展编辑器和语言服务
你可以将语言服务功能 （例如 IntelliSense) 添加到您自己的编辑器，并扩展 Visual Studio 代码编辑器中的大多数功能。  你可以扩展的完整列表，请参阅[语言服务和编辑器扩展点](../extensibility/language-service-and-editor-extension-points.md)。  
  
 使用 Managed Extensibility Framework (MEF) 扩展编辑器的大部分功能。 例如，如果你想要扩展的编辑器功能语法着色，你可以编写 MEF*组件一部分*，它定义要为其不同的颜色设置和你希望如何处理它们的分类。 此编辑器还支持相同功能的多个的扩展。  
  
 编辑器表示层基于 Windows Presentation Framework (WPF)。 WPF 图形库提供灵活的文本格式设置，并提供如图形和动画的可视化效果。  
  
 Visual Studio SDK 提供了名为的适配器*填充码*以支持的早期版本编写的 Vspackage。 不过，如果你有现有的 VSPackage，我们建议，你将其更新为新的技术，以获取更好的性能和可靠性。  
  
## <a name="related-topics"></a>相关主题  
  
|标题|描述|  
|-----------|-----------------|  
|[语言服务和编辑器扩展入门](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|说明如何创建编辑器的扩展。|  
|[编辑器内](../extensibility/inside-the-editor.md)|描述编辑器的一般结构并列出它的某些功能。|  
|[编辑器中的 Managed Extensibility Framework](../extensibility/managed-extensibility-framework-in-the-editor.md)|说明如何使用编辑器中使用 Managed Extensibility Framework (MEF)。|  
|[语言服务和编辑器扩展点](../extensibility/language-service-and-editor-extension-points.md)|列出编辑器的扩展点。 扩展点表示的编辑器功能，可以对其进行扩展。|  
|[演练：创建视图修饰、命令和设置（列参考线）](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|将指导完成并说明生成绘制列 gudie 线来帮助你使代码保持某些显示宽度视图修饰。  此外显示读取和写入设置，以及声明和实现可从命令窗口中调用的命令。|  
|[编辑器导入](../extensibility/editor-imports.md)|列出扩展可以导入的服务。|  
|[调整到编辑器的旧代码](../extensibility/adapting-legacy-code-to-the-editor.md)|说明改编旧代码 (预 Visual Studio 2010) 来扩展编辑器的不同方式。|  
|[迁移旧版语言服务](../extensibility/internals/migrating-a-legacy-language-service.md)|说明如何将基于的 VSPackage 语言服务迁移。|  
|[演练：将内容类型链接到文件扩展名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|演示如何将内容类型链接到文件扩展名。|  
|[演练：创建边距字形](../extensibility/walkthrough-creating-a-margin-glyph.md)|演示如何将图标添加到边距。|  
|[演练：突出显示文本](../extensibility/walkthrough-highlighting-text.md)|演示如何使用*标记*以突出显示文本。|  
|[演练：大纲显示](../extensibility/walkthrough-outlining.md)|演示如何将添加特定类型的大括号的大纲显示。|  
|[演练：显示匹配括号](../extensibility/walkthrough-displaying-matching-braces.md)|演示如何以突出显示匹配的大括号。|  
|[演练：显示 QuickInfo 工具提示](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|演示如何显示描述如属性、 方法和事件的代码的元素的快速信息弹出窗口。|  
|[演练：显示签名帮助](../extensibility/walkthrough-displaying-signature-help.md)|演示如何显示在签名中提供的数量和类型参数的有关信息的弹出窗口。|  
|[演练：显示语句完成](../extensibility/walkthrough-displaying-statement-completion.md)|演示如何实现语句结束。|  
|[演练：实现代码片段](../extensibility/walkthrough-implementing-code-snippets.md)|演示如何实现代码段扩展。|  
|[演练：显示灯泡建议](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|演示如何显示电灯泡有关代码的建议。|  
|[演练：在编辑器扩展中使用 Shell 命令](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|演示如何将 VSPackage 中的菜单命令与 MEF 组件相关联。|  
|[演练：在编辑器扩展中使用快捷键](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|演示如何将在 VSPackage 中的菜单快捷方式与 MEF 组件相关联。|  
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|提供有关 Managed Extensibility Framework (MEF) 的信息。|  
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|提供有关 Windows Presentation Foundation (WPF) 的信息。|  
  
## <a name="reference"></a>参考  
 Visual Studio 编辑器包括以下命名空间。  
  
 <xref:Microsoft.VisualStudio.Language.Intellisense>  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification>  
  
 <xref:Microsoft.VisualStudio.Editor>  
  
 <xref:Microsoft.VisualStudio.Text>  
  
 <xref:Microsoft.VisualStudio.Text.Adornments>  
  
 <xref:Microsoft.VisualStudio.Text.Classification>  
  
 <xref:Microsoft.VisualStudio.Text.Differencing>  
  
 <xref:Microsoft.VisualStudio.Text.Document>  
  
 <xref:Microsoft.VisualStudio.Text.Editor>  
  
 <xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods>  
  
 <xref:Microsoft.VisualStudio.Text.Formatting>  
  
 <xref:Microsoft.VisualStudio.Text.IncrementalSearch>  
  
 <xref:Microsoft.VisualStudio.Text.Operations>  
  
 <xref:Microsoft.VisualStudio.Text.Outlining>  
  
 <xref:Microsoft.VisualStudio.Text.Projection>  
  
 <xref:Microsoft.VisualStudio.Text.Tagging>  
  
 <xref:Microsoft.VisualStudio.Utilities>