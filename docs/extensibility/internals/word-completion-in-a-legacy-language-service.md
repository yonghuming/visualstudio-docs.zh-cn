---
title: "在早期语言服务中的单词自动完成 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "语言服务 [托管的包框架] 智能感知完成单词"
  - "智能感知完成单词"
  - "完成单词"
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# 在早期语言服务中的单词自动完成
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

单词完成填写部分键入的单词上缺少的字符。 如果只有一种可能完成，输入完成字符时完成该单词。 如果部分单词匹配多个可能性，将显示可能的完整形式的列表。 完成字符可以是任何不用于标识符的字符。  
  
 旧的语言服务实现为作为 VSPackage 的一部分，但实现语言服务功能的较新方法是使用 MEF 扩展。 若要获得详细信息，请参阅 [扩展编辑器和语言服务](../../extensibility/extending-the-editor-and-language-services.md)。  
  
> [!NOTE]
>  我们建议在开始尽可能快地使用新的编辑器 API。 这将提高您的语言服务的性能，并让您充分利用新的编辑器功能。  
  
## 实现步骤  
  
1.  当用户选择 **完成单词** 从 **IntelliSense** 菜单上， <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 命令发送到语言服务。  
  
2.  <xref:Microsoft.VisualStudio.Package.ViewFilter> 类捕获的命令和调用 <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> 方法，分析原因为 <xref:Microsoft.VisualStudio.Package.ParseReason>。  
  
3.  <xref:Microsoft.VisualStudio.Package.Source> 类然后调用 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法以获取可能的单词完成，然后显示工具提示中的单词列表使用的列表 <xref:Microsoft.VisualStudio.Package.CompletionSet> 类。  
  
     如果只有一个匹配的单词， <xref:Microsoft.VisualStudio.Package.Source> 类完成单词。  
  
 或者，如果扫描仪返回触发器值 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 键入标识符的第一个字符， <xref:Microsoft.VisualStudio.Package.Source> 类检测到此功能，并调用 <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> 方法，分析原因为 <xref:Microsoft.VisualStudio.Package.ParseReason>。 在这种情况下分析程序必须检测成员选择字符的状态，并提供成员的列表。  
  
## 启用了完整的字词的支持  
 若要启用对 word 完成项集合 `CodeSense` 命名参数传递给 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 与语言包相关联的用户属性。 这会将设置 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> 属性 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 类。  
  
 您的分析程序必须返回声明的列表，以响应分析原因值 <xref:Microsoft.VisualStudio.Package.ParseReason>, ，为 word 完成操作。  
  
## 在 ParseSource 方法中实现完成单词  
 为 word 完成 <xref:Microsoft.VisualStudio.Package.Source> 类将调用 <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> 方法 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 类来获取可能的字匹配项的列表。 您必须在派生自的类中实现列表 <xref:Microsoft.VisualStudio.Package.Declarations> 类。 请参阅 <xref:Microsoft.VisualStudio.Package.Declarations> 类必须实现的方法的详细信息。  
  
 如果该列表包含只有单个字词，则 <xref:Microsoft.VisualStudio.Package.Source> 类自动插入该代替的不完整单词的单词。 如果该列表包含多个单词 <xref:Microsoft.VisualStudio.Package.Source> 类显示工具提示列表，用户可以从中选择一个适当的选项。  
  
 此外请查看示例的 <xref:Microsoft.VisualStudio.Package.Declarations> 类中的实现 [在早期语言服务中的成员完成](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)。