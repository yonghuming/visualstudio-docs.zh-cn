---
title: "演练︰ 自定义文本视图 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e40368ed6aaf68b747f19cffe4e378a89ff6c0b5
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-customizing-the-text-view"></a>演练︰ 自定义文本视图
您可以通过修改其编辑器格式映射中的下列属性的任何自定义文本视图︰  
  
-   指示器边距  
  
-   插入号  
  
-   覆盖插入符号  
  
-   选定的文本  
  
-   非活动状态的所选的文本 （也就是说，所选文本已失去焦点）  
  
-   可见空白  
  
## <a name="prerequisites"></a>先决条件  
 启动 Visual Studio 2015 中，您并不安装 Visual Studio SDK 从下载中心获得。 它将包括作为 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-mef-project"></a>创建 MEF 项目  
  
1.  创建 C# VSIX 项目。 (在**新项目**对话框中，选择**Visual C# / 可扩展性**，然后**VSIX 项目**。)将解决方案命名`ViewPropertyTest`。  
  
2.  向项目添加编辑器分类器项模板。 有关详细信息，请参阅[带有编辑器项模板创建扩展](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  删除现有的类文件。  
  
## <a name="defining-the-content-type"></a>将内容类型定义  
  
1.  添加一个类文件并将其命名`ViewPropertyModifier`。  
  
2.  将以下代码添加`using`指令︰  
  
     [!code-cs[VSSDKViewPropertyTest&#1;](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs) ] 
     [!code-vb [VSSDKViewPropertyTest&#1;](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]  
  
3.  声明一个名为类`TestViewCreationListener`继承自<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>。</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> 导出此类具有以下属性︰  
  
    -   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>若要指定的内容应用到此侦听器的类型。</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>  
  
    -   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>若要指定该侦听器的角色。</xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>  
  
     [!code-cs[VSSDKViewPropertyTest&#2;](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest&#2;](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]  
  
4.  在此类中，导入<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>。</xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>  
  
     [!code-cs[VSSDKViewPropertyTest&#3;](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs) ] 
     [!code-vb [VSSDKViewPropertyTest&#3;](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]  
  
## <a name="changing-the-view-properties"></a>更改视图属性  
  
1.  实现<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>方法以便打开该视图时都更改查看属性。</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> 若要进行更改，请首先找到<xref:System.Windows.ResourceDictionary>对应于您想要查找的视图的方面。</xref:System.Windows.ResourceDictionary> 资源字典中的相应属性和更改设置的属性。 批处理调用<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A>方法通过调用<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A>方法之前设置的属性，然后<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A>设置属性后。</xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> </xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> </xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A>  
  
     [!code-cs[VSSDKViewPropertyTest&#4;](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs) ] 
     [!code-vb [VSSDKViewPropertyTest&#4;](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]  
  
## <a name="building-and-testing-the-code"></a>生成和测试代码  
  
1.  生成解决方案。  
  
     在调试器中运行此项目时，Visual Studio 的第二个实例将进行实例化。  
  
2.  创建一个文本文件并键入一些文本。  
  
    -   插入号应是洋红色并且覆盖插入符号应青绿色。  
  
    -   （左侧的文本视图） 的指示器边距应为浅绿色。  
  
3.  选择刚刚键入的文本。 将所选文本的颜色应为 light 粉红色。  
  
4.  在选定文本，文本窗口外任意位置单击。 将所选文本的颜色应为深粉红色。  
  
5.  打开可见空白。 (在**编辑**菜单上，指向**高级**，然后单击**查看空白**)。 键入的文本中的某些选项卡。 此时应该显示红色箭头表示选项卡。  
  
## <a name="see-also"></a>另请参阅  
 [语言服务和编辑器扩展点](../extensibility/language-service-and-editor-extension-points.md)
