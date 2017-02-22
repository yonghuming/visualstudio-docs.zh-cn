---
title: "演练︰ 显示匹配的大括号 | Microsoft Docs"
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
  - "编辑器 [Visual Studio SDK]，新的大括号匹配"
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
caps.latest.revision: 27
caps.handback.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
---
# 演练︰ 显示匹配的大括号
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以实现基于语言的功能，如大括号匹配通过定义您希望匹配，括在括号的内，然后将文本标记添加到匹配的大括号，插入符号移动上一个大括号时。 你可以定义大括号中的一种语言，上下文可以定义你自己的文件名称扩展和内容类型并将标记应用于只是该类型，或将标记应用到现有的内容类型 （如"text"\)。 下面的演练演示如何将应用标记为"text"内容类型匹配的大括号。  
  
## 系统必备  
 启动 Visual Studio 2015 中，您并不安装 Visual Studio SDK 从下载中心获得。 它将包括作为 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## 创建 Managed Extensibility Framework \(MEF\) 项目  
  
#### 创建 MEF 项目  
  
1.  创建编辑器分类器项目。 将解决方案命名 `BraceMatchingTest`。  
  
2.  向项目添加编辑器分类器项模板。 有关详细信息，请参阅[在编辑器中的项模板创建扩展](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  删除现有的类文件。  
  
## 实现大括号匹配标记  
 若要获取大括号突出显示与 Visual Studio 中使用的一个示例相似的效果，可以实现类型的标记 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>。 下面的代码演示如何定义的任何级别的嵌套的大括号对标记。 在此示例中，大括号对 \[\]。 \[\]、 和中标记器构造函数中，定义了 {}，但是在完整的语言实现将语言规范中定义的相关的大括号对。  
  
#### 若要实现大括号匹配标记  
  
1.  添加一个类文件并将其命名括号匹配。  
  
2.  导入以下命名空间。  
  
     [!code-cs[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]  
  
3.  定义一个类 `BraceMatchingTagger` ，该类继承自 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> 类型的 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>。  
  
     [!code-cs[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]  
  
4.  为文本视图、 源缓冲区和当前快照点，以及一组大括号对添加属性。  
  
     [!code-cs[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]  
  
5.  标记器构造函数中，在设置的属性和订阅视图更改事件 <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> 和 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>。 在此示例中，出于说明目的，配对也定义构造函数中。  
  
     [!code-cs[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]  
  
6.  作为的一部分 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> 实现中，声明 TagsChanged 事件。  
  
     [!code-cs[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]  
  
7.  事件处理程序更新的当前插入符号位置 `CurrentChar` 属性并引发 TagsChanged 事件。  
  
     [!code-cs[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]  
  
8.  实现 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> 方法相匹配大括号内的任何一个时当前字符是左大括号或前一个字符时关闭的大括号，如 Visual Studio 中所示。 当找到匹配项时，此方法实例化，这两个标记、 左大括号和右大括号。  
  
     [!code-cs[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]  
  
9. 下面的私有方法查找匹配的任何级别的嵌套的大括号。 第一种方法查找匹配的打开的字符的结束字符︰  
  
     [!code-cs[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]  
  
10. 下面的 helper 方法查找打开与关闭字符相匹配的字符︰  
  
     [!code-cs[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]  
  
## 实现大括号匹配标记提供程序  
 除了实现标记，还必须实现并导出标记提供程序。 在这种情况下，该提供程序的内容类型为"text"。 这意味着大括号匹配所有类型的文本文件，将出现，但更完整的实现将应用只与特定的内容类型相匹配的大括号。  
  
#### 若要实现大括号匹配标记的提供程序  
  
1.  声明的标记提供程序继承自 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>, 、 将其命名 BraceMatchingTaggerProvider，并将其与导出 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 的"text"和一个 <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> 的 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>。  
  
     [!code-cs[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]  
  
2.  实现 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> 方法来实例化 BraceMatchingTagger。  
  
     [!code-cs[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]  
  
## 生成和测试代码  
 若要测试此代码，生成 BraceMatchingTest 解决方案并在实验实例中运行它。  
  
#### 若要生成并测试 BraceMatchingTest 解决方案  
  
1.  生成解决方案。  
  
2.  在调试器中运行此项目时，Visual Studio 的第二个实例将进行实例化。  
  
3.  创建一个文本文件，并键入一些文本，其中包括成对的大括号。  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4.  当放置在左大括号之前插入符号时，该大括号和匹配的括号应该突出显示。 当恰好在右花括号后放置光标时，该大括号和匹配的左大括号应该突出显示。  
  
## 请参阅  
 [演练: 将内容类型链接到的文件扩展名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)