---
title: "演练： 显示匹配的大括号 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c4a7d122f19e21eebbe5bd598272fb7cb9f52b27
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-displaying-matching-braces"></a>演练： 显示匹配的大括号
你可以实现的基于语言的功能，如按定义你想要匹配，大的括号，然后将文本标记标记添加到匹配的大括号，当脱字号上一个大括号匹配的大括号。 你可以定义一种语言的上下文中的大括号或可以定义你自己的文件名称扩展和内容类型，并将标记应用到只是该类型，或您可以将标记应用到现有的内容类型 （例如"text")。 下面的演练演示如何应用标记为"text"内容类型匹配的大括号。  
  
## <a name="prerequisites"></a>先决条件  
 从 Visual Studio 2015 开始，你并不安装 Visual Studio SDK 从下载中心。 它将包括作为 Visual Studio 安装程序中的可选功能。 你还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>创建 Managed Extensibility Framework (MEF) 项目  
  
#### <a name="to-create-a-mef-project"></a>创建 MEF 项目  
  
1.  创建编辑器分类器项目。 将解决方案命名`BraceMatchingTest`。  
  
2.  向项目添加编辑器分类器项模板。 有关详细信息，请参阅[带有编辑器项模板创建扩展](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  删除现有的类文件。  
  
## <a name="implementing-a-brace-matching-tagger"></a>实现大括号匹配标记器  
 若要获取大括号突出显示与用于 Visual Studio 中的一个示例类似的效果，则可以实现的类型的标记器<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>。 下面的代码演示如何定义任何级别的嵌套的大括号对标记器。 在此示例中，大括号对 []。 []，和中标记器构造函数中，定义了 {}，但是在完整的语言的实现将语言规范中定义的相关的大括号对。  
  
#### <a name="to-implement-a-brace-matching-tagger"></a>若要实现大括号匹配标记器  
  
1.  添加一个类文件并将其命名 BraceMatching。  
  
2.  导入以下命名空间。  
  
     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]  
  
3.  定义一个类`BraceMatchingTagger`继承自<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>类型的<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>。  
  
     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]  
  
4.  添加用于文本视图、 源缓冲区和当前的快照点，并作为一组大括号对的属性。  
  
     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]  
  
5.  标记器构造函数中，在设置的属性和订阅以查看更改的事件<xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged>和<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>。 在此示例中，供说明用途，匹配对还定义构造函数中。  
  
     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]  
  
6.  作为的一部分<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>实现中，声明 TagsChanged 事件。  
  
     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]  
  
7.  事件处理程序更新的当前插入符号位置`CurrentChar`属性和引发 TagsChanged 事件。  
  
     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]  
  
8.  实现<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>方法可以进行匹配大括号或者左大括号或前一个字符时关闭的大括号，如下所示 Visual Studio 的当前字符时。 当找到匹配项时，此方法实例化两个标记，则左大括号和右大括号。  
  
     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]  
  
9. 以下私有方法查找匹配的任何级别的嵌套的大括号。 第一种方法查找匹配的打开的字符的关闭字符：  
  
     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]  
  
10. 下面的 helper 方法查找匹配关闭字符的打开字符：  
  
     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]  
  
## <a name="implementing-a-brace-matching-tagger-provider"></a>实现大括号匹配标记器提供程序  
 除了实现的标记器，你必须实现，并且导出标记器提供程序中。 在这种情况下，提供程序的内容类型为"text"。 这意味着大括号匹配将显示在所有类型的文本文件，但更完整的实现将会应用只与特定的内容类型相匹配的大括号。  
  
#### <a name="to-implement-a-brace-matching-tagger-provider"></a>实现大括号匹配标记器提供程序  
  
1.  声明的标记器提供程序继承自<xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>、 将其命名为 BraceMatchingTaggerProvider，并将其与导出<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>"text"和<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>的<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>。  
  
     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]  
  
2.  实现<xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>方法可实例化 BraceMatchingTagger。  
  
     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]  
  
## <a name="building-and-testing-the-code"></a>生成和测试代码  
 若要测试此代码，生成 BraceMatchingTest 解决方案并在实验实例中运行它。  
  
#### <a name="to-build-and-test-bracematchingtest-solution"></a>若要生成和测试 BraceMatchingTest 解决方案  
  
1.  生成解决方案。  
  
2.  在调试器中运行此项目时，Visual Studio 的第二个实例将进行实例化。  
  
3.  创建一个文本文件，并键入一些文本，其中包括匹配的大括号。  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4.  当将插入符号之前的左大括号上时，该大括号和匹配的括号应突出显示。 当你将光标的位置关闭大括号之后时，该大括号和匹配的左大括号应突出显示。  
  
## <a name="see-also"></a>另请参阅  
 [演练：将内容类型链接到文件扩展名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)