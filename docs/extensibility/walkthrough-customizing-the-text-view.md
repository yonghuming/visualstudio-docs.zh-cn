---
title: "演练： 自定义文本视图 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e890145199fe864d2f7b5010495375bfbc6cc094
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-customizing-the-text-view"></a>演练： 自定义文本视图
你可以通过修改其编辑器格式映射中的下列属性的任何自定义文本视图：  
  
-   指示器边距  
  
-   插入插入符号  
  
-   覆盖插入符号  
  
-   选定的文本  
  
-   停用选定的文本 （即，所选文本已失去焦点）  
  
-   可见空白  
  
## <a name="prerequisites"></a>先决条件  
 从 Visual Studio 2015 开始，你并不安装 Visual Studio SDK 从下载中心。 它将包括作为 Visual Studio 安装程序中的可选功能。 你还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-mef-project"></a>创建 MEF 项目  
  
1.  创建 C# VSIX 项目。 (在**新项目**对话框中，选择**Visual C# / 可扩展性**，然后**VSIX 项目**。)将解决方案命名`ViewPropertyTest`。  
  
2.  向项目添加编辑器分类器项模板。 有关详细信息，请参阅[带有编辑器项模板创建扩展](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  删除现有的类文件。  
  
## <a name="defining-the-content-type"></a>定义的内容类型  
  
1.  添加一个类文件并将其命名`ViewPropertyModifier`。  
  
2.  添加以下`using`指令：  
  
     [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
     [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]  
  
3.  声明一个名为类`TestViewCreationListener`继承自<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>。 导出此类具有以下属性：  
  
    -   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>若要指定的内容应用到此侦听器的类型。  
  
    -   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>若要指定该侦听器的角色。  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]  
  
4.  在此类中导入<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>。  
  
     [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
     [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]  
  
## <a name="changing-the-view-properties"></a>更改视图属性  
  
1.  实现<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>方法，以便当打开视图时发生变化的视图属性。 若要进行更改，首先找到<xref:System.Windows.ResourceDictionary>对应于你想要查找的视图的方面。 然后更改资源字典中的相应属性并设置的属性。 批处理调用<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A>方法通过调用<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A>方法之前设置的属性，然后<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A>后设置的属性。  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]  
  
## <a name="building-and-testing-the-code"></a>生成和测试代码  
  
1.  生成解决方案。  
  
     在调试器中运行此项目时，Visual Studio 的第二个实例将进行实例化。  
  
2.  创建一个文本文件并键入一些文本。  
  
    -   插入号应为洋红色，覆盖脱字号应为青绿色。  
  
    -   （文本视图左侧） 的指示器边距应为浅绿色。  
  
3.  选择刚刚键入的文本。 所选文本的颜色应浅色粉红色。  
  
4.  在选定该文本，文本时段外任意位置单击。 所选文本的颜色应深色粉红色。  
  
5.  打开可见空白。 (在**编辑**菜单上，指向**高级**，然后单击**查看空白**)。 键入文本中的某些选项卡。 应显示红色箭头表示选项卡。  
  
## <a name="see-also"></a>另请参阅  
 [语言服务和编辑器扩展点](../extensibility/language-service-and-editor-extension-points.md)