---
title: "演练︰ 创建边缘字形 | Microsoft Docs"
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
  - "编辑器 [Visual Studio SDK]，新增的边距标志符号"
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
caps.latest.revision: 29
caps.handback.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
---
# 演练︰ 创建边缘字形
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可以使用自定义编辑器扩展自定义编辑器的边距的外观。 本演练中放入自定义标志符号的指示器边距时在代码注释将显示"todo"一词。  
  
## 系统必备  
 启动 Visual Studio 2015 中，您并不安装 Visual Studio SDK 从下载中心获得。 它将包括作为 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## 创建 MEF 项目  
  
1.  创建 C\# VSIX 项目。 \(在 **新项目** 对话框中，选择 **Visual C\# \/ 可扩展性**, ，然后 **VSIX 项目**。\) 将解决方案命名 `TodoGlyphTest`。  
  
2.  添加编辑器分类器项目项。 有关详细信息，请参阅[在编辑器中的项模板创建扩展](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  删除现有的类文件。  
  
## 定义标志符号  
 通过实现定义标志符号 <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> 接口。  
  
#### 若要定义标志符号  
  
1.  添加一个类文件并将其命名 `TodoGlyphFactory`。  
  
2.  将以下代码添加使用声明。  
  
     [!code-cs[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]  
  
3.  添加一个名为类 `TodoGlyphFactory` 实现 <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>。  
  
     [!code-cs[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]  
  
4.  添加定义标志符号的维度的私有字段。  
  
     [!code-cs[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]  
  
5.  实现 `GenerateGlyph` 通过定义标志符号的用户界面 \(UI\) 元素。`TodoTag` 定义在此演练的后面。  
  
     [!code-cs[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]  
  
6.  添加一个名为类 `TodoGlyphFactoryProvider` 实现 <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>。 导出此类的 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> 的"TodoGlyph" <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> 的后 VsTextMarker <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 的"代码"和一个 <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> TodoTag。  
  
     [!code-cs[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]  
  
7.  实现 <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> 方法通过实例化 `TodoGlyphFactory`。  
  
     [!code-cs[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]  
  
## 定义 Todo 标记和标记  
 通过创建标记类型和标记，并将其导出使用的标记提供程序定义的上一步骤中定义的用户界面元素和指示器边距之间的关系。  
  
#### 若要定义 todo 标记和标记  
  
1.  将新的类文件添加到项目并将其命名 `TodoTagger`。  
  
2.  添加以下导入。  
  
     [!code-cs[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]  
  
3.  添加一个名为类 `TodoTag`。  
  
     [!code-cs[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]  
  
4.  修改名为的类 `TodoTagger` 实现 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> 类型的 `TodoTag`。  
  
     [!code-cs[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]  
  
5.  到 `TodoTagger` 类中，添加的私有字段 <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> 并且为该分类中查找的文本跨越。  
  
     [!code-cs[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]  
  
6.  添加设置分类器的构造函数。  
  
     [!code-cs[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]  
  
7.  实现 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> 通过查找所有分类的方法跨其名称中包含单词"注释"和其文本包含搜索的文本。 只要找到搜索文本，重新生成一个新 <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> 类型的 `TodoTag`。  
  
     [!code-cs[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]  
  
8.  声明 `TagsChanged` 事件。  
  
     [!code-cs[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]  
  
9. 添加一个名为类 `TodoTaggerProvider` 实现 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, ，并将其与导出 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 的"代码"和一个 <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> TodoTag。  
  
     [!code-cs[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]  
  
10. 导入 <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>。  
  
     [!code-cs[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]  
  
11. 实现 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> 方法通过实例化 `TodoTagger`。  
  
     [!code-cs[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]  
  
## 生成和测试代码  
 若要测试此代码，生成 TodoGlyphTest 解决方案并在实验实例中运行它。  
  
#### 若要生成并测试 TodoGlyphTest 解决方案  
  
1.  生成解决方案。  
  
2.  通过按 F5 运行项目。 Visual Studio 的第二个实例进行实例化。  
  
3.  请确保所显示的指示器边距。 \(在 **工具** 菜单上，单击 **选项**。 在 **文本编辑器** 页上，请确保 **指示器边距** 处于选中状态。\)  
  
4.  打开一个具有注释的代码文件。 将单词"todo"添加到注释部分之一。  
  
5.  代码窗口左侧的指示器边距中应显示一个具有深蓝色的轮廓的浅蓝色圆圈。