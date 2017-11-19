---
title: "演练： 创建边距标志符号 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 94c4b602b29bb86acaf1b910075913abcfc79ac0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-margin-glyph"></a>演练： 创建边距标志符号
你可以使用自定义编辑器扩展自定义编辑器边距的外观。 本演练将自定义标志符号置于上指示器边距，只要代码注释中显示单词"todo"。  
  
## <a name="prerequisites"></a>先决条件  
 从 Visual Studio 2015 开始，你并不安装 Visual Studio SDK 从下载中心。 它将包括作为 Visual Studio 安装程序中的可选功能。 你还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-mef-project"></a>创建 MEF 项目  
  
1.  创建 C# VSIX 项目。 (在**新项目**对话框中，选择**Visual C# / 可扩展性**，然后**VSIX 项目**。)将解决方案命名`TodoGlyphTest`。  
  
2.  添加编辑器分类器项目项。 有关详细信息，请参阅[带有编辑器项模板创建扩展](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  删除现有的类文件。  
  
## <a name="defining-the-glyph"></a>定义标志符号  
 通过实现定义标志符号<xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>接口。  
  
#### <a name="to-define-the-glyph"></a>若要定义标志符号  
  
1.  添加一个类文件并将其命名`TodoGlyphFactory`。  
  
2.  添加以下使用声明。  
  
     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]  
  
3.  添加一个名为类`TodoGlyphFactory`实现<xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>。  
  
     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]  
  
4.  添加定义标志符号的维度的私有字段。  
  
     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]  
  
5.  实现`GenerateGlyph`通过定义标志符号用户界面 (UI) 元素。 `TodoTag`稍后在本演练定义。  
  
     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]  
  
6.  添加一个名为类`TodoGlyphFactoryProvider`实现<xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>。 导出此类的<xref:Microsoft.VisualStudio.Utilities.NameAttribute>的"TodoGlyph"<xref:Microsoft.VisualStudio.Utilities.OrderAttribute>的后 VsTextMarker<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>的"代码"和<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>TodoTag。  
  
     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]  
  
7.  实现<xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A>方法是实例化的方法`TodoGlyphFactory`。  
  
     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]  
  
## <a name="defining-a-todo-tag-and-tagger"></a>定义 Todo 标记和标记器  
 通过创建标记类型和标记器，并将其导出使用的标记器提供程序定义的上一步骤中定义的用户界面元素和指示器边距之间的关系。  
  
#### <a name="to-define-a-todo-tag-and-tagger"></a>若要定义 todo 标记和标记器  
  
1.  向项目添加新的类文件并将其命名`TodoTagger`。  
  
2.  添加以下导入。  
  
     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]  
  
3.  添加一个名为类`TodoTag`。  
  
     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]  
  
4.  修改名为的类`TodoTagger`实现<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>类型的`TodoTag`。  
  
     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]  
  
5.  到`TodoTagger`类，将为私有字段添加<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>和文本，以在分类中找到跨越。  
  
     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]  
  
6.  添加设置分类器的构造函数。  
  
     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]  
  
7.  实现<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>通过查找所有分类的方法跨其名称中包含单词"注释"和其文本包括搜索文本。 只要找到搜索文本，重新生成一个新<xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601>类型的`TodoTag`。  
  
     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]  
  
8.  声明`TagsChanged`事件。  
  
     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]  
  
9. 添加一个名为类`TodoTaggerProvider`实现<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>，并将其与导出<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>的"代码"和<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>TodoTag。  
  
     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]  
  
10. 导入<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>。  
  
     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]  
  
11. 实现<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A>方法是实例化的方法`TodoTagger`。  
  
     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]  
  
## <a name="building-and-testing-the-code"></a>生成和测试代码  
 若要测试此代码，生成 TodoGlyphTest 解决方案并在实验实例中运行它。  
  
#### <a name="to-build-and-test-the-todoglyphtest-solution"></a>若要生成和测试 TodoGlyphTest 解决方案  
  
1.  生成解决方案。  
  
2.  按 F5 运行项目。 Visual Studio 的第二个实例是实例化。  
  
3.  请确保显示的指示器边距。 (在**工具**菜单上，单击**选项**。 在**文本编辑器**页上，请确保**指示器边距**选择。)  
  
4.  打开具有注释的代码文件。 将单词"todo"添加到注释部分之一。  
  
5.  具有深蓝色的轮廓的浅蓝色圆形应出现在代码窗口左侧的指示器边距。