---
title: "演练： 大纲显示 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: "30"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f503d9e8b0ef125fdb72ea60a9928f308b900993
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-outlining"></a>演练： 大纲显示
你可以实现基于语言的功能，例如通过定义类型的文本区域，你想要展开或折叠大纲显示。 你可以定义区域语言服务上下文中或可以定义你自己的文件名称扩展和内容类型，还可以将区域定义应用于仅该类型，或可以将区域定义应用于现有内容类型 （如"text")。 本演练演示如何定义和显示大纲区域。  
  
## <a name="prerequisites"></a>先决条件  
 从 Visual Studio 2015 开始，你并不安装 Visual Studio SDK 从下载中心。 它将包括作为 Visual Studio 安装程序中的可选功能。 你还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>创建 Managed Extensibility Framework (MEF) 项目  
  
#### <a name="to-create-a-mef-project"></a>创建 MEF 项目  
  
1.  创建一个 VSIX 项目。 将解决方案命名`OutlineRegionTest`。  
  
2.  向项目添加编辑器分类器项模板。 有关详细信息，请参阅[带有编辑器项模板创建扩展](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  删除现有的类文件。  
  
## <a name="implementing-an-outlining-tagger"></a>实现大纲显示的标记器  
 大纲区域，标记的一种类型的标记 (<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>)。 此标记提供标准大纲显示行为。 可以展开或折叠的大纲的区域。 如果它将展开，并展开的区域方式通过一条竖线来划分，如果它处于折叠状态加号或减号标记轮廓包围的区域。  
  
 下面的步骤演示如何定义创建由分隔的各个区域的大纲显示区域的标记器"["和"]"。  
  
#### <a name="to-implement-an-outlining-tagger"></a>若要实现大纲显示的标记器  
  
1.  添加一个类文件并将其命名`OutliningTagger`。  
  
2.  导入以下命名空间。  
  
     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]  
  
3.  创建一个名为类`OutliningTagger`，并将其实现<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:  
  
     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]  
  
4.  添加一些字段跟踪的文本缓冲区和快照，并累积的应标记为大纲区域的行集。 此代码包括区域表示对象 （用于更高版本定义） 大纲区域的列表。  
  
     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]  
  
5.  添加一个字段，初始化的标记器构造函数分析缓冲区，并添加到事件处理程序<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>事件。  
  
     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]  
  
6.  实现<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>方法，该实例化标记方法跨越。 此示例假定中的范围<xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection>传入到方法中都是连续的但这可能不始终是这种情况。 此方法将为每个大纲区域实例化新的标记范围。  
  
     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]  
  
7.  声明`TagsChanged`事件处理程序。  
  
     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]  
  
8.  添加`BufferChanged`响应的事件处理程序<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>事件通过分析文本缓冲区。  
  
     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]  
  
9. 添加一个方法，用以分析缓冲区。 此处提供的示例是仅用于说明目的。 以同步方式分析缓冲区到嵌套大纲区域。  
  
     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]  
  
10. 下面的 helper 方法获取一个整数，表示的大纲显示、 级别，这样的： 1 的最左侧的大括号对。  
  
     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]  
  
11. 下面的 helper 方法将转换 SnapshotSpan （稍后在本主题中定义） 的区域。  
  
     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]  
  
12. 下面的代码是仅用于说明目的。 它定义一个包含行号和偏移量开始的大纲区域，以及对父区域 （如果有） 的引用的 PartialRegion 类。 这使分析器设置嵌套大纲区域。 派生的区域类包含的末尾的大纲显示区域的行号的引用。  
  
     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]  
  
## <a name="implementing-a-tagger-provider"></a>实现标记器提供程序  
 你必须为你的标记器导出标记器提供程序。 标记器提供程序创建`OutliningTagger`"text"内容类型或其他返回的缓冲区`OutliningTagger`如果缓冲区中已有一个。  
  
#### <a name="to-implement-a-tagger-provider"></a>若要实现标记器提供程序  
  
1.  创建一个名为类`OutliningTaggerProvider`实现<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>，并将其导出的 ContentType 和 TagType 属性使用。  
  
     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]  
  
2.  实现<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A>方法通过添加`OutliningTagger`属性的缓冲区。  
  
     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]  
  
## <a name="building-and-testing-the-code"></a>生成和测试代码  
 若要测试此代码，生成 OutlineRegionTest 解决方案并在实验实例中运行它。  
  
#### <a name="to-build-and-test-the-outlineregiontest-solution"></a>若要生成和测试 OutlineRegionTest 解决方案  
  
1.  生成解决方案。  
  
2.  在调试器中运行此项目时，Visual Studio 的第二个实例将进行实例化。  
  
3.  创建文本文件。 键入一些文本，其中包括左大括号和右大括号。  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4.  应包括这两个大括号的大纲区域。 应该可以通过单击左侧的左大括号负号，若要折叠的大纲区域。 当区域处于折叠状态，省略号 （...） 应该显示折叠的地区和弹出项包含文本的左侧**将鼠标悬停文本**将指针移省略号时应显示。  
  
## <a name="see-also"></a>另请参阅  
 [演练：将内容类型链接到文件扩展名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)