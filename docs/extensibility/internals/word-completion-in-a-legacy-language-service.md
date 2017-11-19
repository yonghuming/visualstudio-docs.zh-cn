---
title: "在旧语言服务 word 完成 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c24765450d0bf8ffdab479bb28c822602892b595
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="word-completion-in-a-legacy-language-service"></a>在旧语言服务中的单词完成
单词完成填写上部分键入的单词的缺少字符。 如果只有一个可能的完成，完成字符输入时完成单词。 如果部分单词与匹配多个可能性，显示可能的完成列表。 完成字符可以是任何不用于标识符的字符。  
  
 旧语言服务实现的 VSPackage，一部分但实现语言服务功能的新方法是使用 MEF 扩展。 若要了解详细信息，请参阅[扩展编辑器和语言服务](../../extensibility/extending-the-editor-and-language-services.md)。  
  
> [!NOTE]
>  我们建议你开始使用新的编辑器 API 越早越好。 这将改善语言服务的性能，并让您充分利用新的编辑器功能。  
  
## <a name="implementation-steps"></a>实现步骤  
  
1.  当用户选择**完成单词**从**IntelliSense**菜单上，<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>命令发送到语言服务。  
  
2.  <xref:Microsoft.VisualStudio.Package.ViewFilter>类捕获的命令和调用<xref:Microsoft.VisualStudio.Package.Source.Completion%2A>方法分析原因为<xref:Microsoft.VisualStudio.Package.ParseReason>。  
  
3.  <xref:Microsoft.VisualStudio.Package.Source>然后类调用<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法以获取可能的单词完成和显示工具提示中的单词列表使用列表<xref:Microsoft.VisualStudio.Package.CompletionSet>类。  
  
     如果只有一个匹配的单词，<xref:Microsoft.VisualStudio.Package.Source>类完成单词。  
  
 或者，如果扫描仪返回触发器值<xref:Microsoft.VisualStudio.Package.TokenTriggers>如果类型标识符的第一个字符，<xref:Microsoft.VisualStudio.Package.Source>检测到此类，并调用<xref:Microsoft.VisualStudio.Package.Source.Completion%2A>方法分析原因为<xref:Microsoft.VisualStudio.Package.ParseReason>。 在这种情况下分析器必须检测成员选择字符的状态，并提供成员的列表。  
  
## <a name="enabling-support-for-the-complete-word"></a>启用对完成单词的支持  
 若要启用对 word 完成项集合`CodeSense`命名参数传递给<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>语言包与关联的用户属性。 这将设置<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A>属性<xref:Microsoft.VisualStudio.Package.LanguagePreferences>类。  
  
 你的分析程序必须在分析的原因值到响应中返回的声明列表<xref:Microsoft.VisualStudio.Package.ParseReason>，为单词完成运行。  
  
## <a name="implementing-complete-word-in-the-parsesource-method"></a>在 ParseSource 方法中实现完成单词  
 为单词完成<xref:Microsoft.VisualStudio.Package.Source>类调用<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>方法<xref:Microsoft.VisualStudio.Package.AuthoringScope>类来获取可能的单词匹配结果列表。 你必须派生自的类中实现列表<xref:Microsoft.VisualStudio.Package.Declarations>类。 请参阅<xref:Microsoft.VisualStudio.Package.Declarations>类必须实现的方法的详细信息。  
  
 如果列表包含仅单个单词，则<xref:Microsoft.VisualStudio.Package.Source>类自动插入该代替部分单词的单词。 如果列表包含多个单词，<xref:Microsoft.VisualStudio.Package.Source>类显示工具提示列表，用户可以从中选择的合适选择。  
  
 此外看的示例<xref:Microsoft.VisualStudio.Package.Declarations>中的类实现[旧语言服务中的成员自动补全](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)。