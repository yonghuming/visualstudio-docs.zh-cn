---
title: "演练: 大纲显示 | Microsoft Docs"
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
  - "编辑器 [Visual Studio SDK]，新的大纲显示"
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: 30
caps.handback.revision: 30
ms.author: "gregvanl"
manager: "ghogen"
---
# 演练: 大纲显示
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以实现基于语言的功能，如大纲显示通过定义您想要展开或折叠的文本区域的类型。 您可以定义区域的语言服务上下文中可以定义你自己的文件名称扩展和内容类型并将区域定义应用于只是该类型，或可以将区域定义应用于现有的内容类型 \(如"text"\)。 本演练演示如何定义，并且显示大纲区域。  
  
## 系统必备  
 启动 Visual Studio 2015 中，您并不安装 Visual Studio SDK 从下载中心获得。 它将包括作为 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## 创建 Managed Extensibility Framework \(MEF\) 项目  
  
#### 创建 MEF 项目  
  
1.  创建一个 VSIX 项目。 将解决方案命名 `OutlineRegionTest`。  
  
2.  向项目添加编辑器分类器项模板。 有关更多信息，请参见[在编辑器中的项模板创建扩展](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  删除现有的类文件。  
  
## 实现大纲显示标记  
 大纲区域标记的类型的标记 \(<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>\)。 此标记提供标准大纲显示行为。 可以展开或折叠以大纲方式显示的区域。 如果它将展开，并且方式通过一条竖线来划分展开的区域，由如果它处于折叠状态加号或减号标记以大纲方式显示的区域。  
  
 下面的步骤演示如何定义将创建由分隔的所有区域的大纲区域标记"\["和"\]"。  
  
#### 若要实现大纲显示标记  
  
1.  添加一个类文件并将其命名 `OutliningTagger`。  
  
2.  导入以下命名空间。  
  
     [!code-cs[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]  
  
3.  创建一个名为类 `OutliningTagger`, ，并让其实现 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:  
  
     [!code-cs[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]  
  
4.  添加一些字段来跟踪文本缓冲区和快照，以及要累计的应标记为大纲显示区域的行集。 此代码包括区域表示对象 \(若要稍后定义\) 的大纲区域的列表。  
  
     [!code-cs[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]  
  
5.  添加一个标记器构造函数初始化字段，分析缓冲区，并添加到一个事件处理程序 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> 事件。  
  
     [!code-cs[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]  
  
6.  实现 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> 方法，它会实例化标记跨越。 此示例假定在范围 <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> 中传递给该方法是连续的尽管这不一定总是这种情况。 此方法实例化新的标记范围，为每个大纲区域。  
  
     [!code-cs[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]  
  
7.  声明 `TagsChanged` 事件处理程序。  
  
     [!code-cs[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]  
  
8.  添加 `BufferChanged` 响应的事件处理程序 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> 通过分析文本缓冲区的事件。  
  
     [!code-cs[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]  
  
9. 添加对缓冲区进行分析的方法。 此处给出的示例是仅用于说明目的。 以同步方式将缓冲区分析为嵌套大纲区域。  
  
     [!code-cs[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]  
  
10. 下面的 helper 方法获取一个整数，以便 1 是最左边的大括号对表示的大纲显示、 级别。  
  
     [!code-cs[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]  
  
11. 下面的 helper 方法将转换 SnapshotSpan \(更高版本在本主题中定义\) 的区域。  
  
     [!code-cs[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]  
  
12. 下面的代码是仅用于说明目的。 它定义一个 PartialRegion 类，包含的行号和偏移量开始的大纲区域，以及对父区域 \(如果有\) 的引用。 这样，分析器将设置嵌套大纲区域。 派生的 Region 类包含对大纲区域结尾的行号的引用。  
  
     [!code-cs[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]  
  
## 实现标记提供程序  
 必须将标记提供程序导出为您的标记。 标记提供程序会创建 `OutliningTagger` 为"text"内容类型或其他返回的缓冲区 `OutliningTagger` 如果缓冲区已经有了一个。  
  
#### 若要实现标记提供程序  
  
1.  创建一个名为类 `OutliningTaggerProvider` 实现 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, ，并将其导出使用 ContentType 和 TagType 属性。  
  
     [!code-cs[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]  
  
2.  实现 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> 方法通过添加 `OutliningTagger` 到缓冲区的属性。  
  
     [!code-cs[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]  
  
## 生成和测试代码  
 若要测试此代码，生成 OutlineRegionTest 解决方案并在实验实例中运行它。  
  
#### 若要生成并测试 OutlineRegionTest 解决方案  
  
1.  生成解决方案。  
  
2.  在调试器中运行此项目时，Visual Studio 的第二个实例将进行实例化。  
  
3.  创建文本文件。 键入一些文本，其中包括左大括号和右大括号。  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4.  应包含这两个大括号的大纲区域。 您应可以通过单击左侧的左大括号负号，若要折叠的大纲区域。 当区域处于折叠状态，省略号 \(...\) 应该显示折叠的地区和弹出项包含文本的左侧 **将鼠标指针悬停文本** 时将指针移到省略号应显示。  
  
## 请参阅  
 [演练: 将内容类型链接到的文件扩展名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)