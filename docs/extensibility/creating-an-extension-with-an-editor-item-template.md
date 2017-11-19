---
title: "使用编辑器项模板创建扩展 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ebfb54a289fe085f00c40df34256cfb2174f98fc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="creating-an-extension-with-an-editor-item-template"></a>使用编辑器项模板创建扩展
你可以使用 Visual Studio SDK，以创建基本的编辑器扩展添加到编辑器中的分类器、 修饰和边距中包含的项模板。 编辑器项模板是适用于 Visual C# 或 Visual Basic VSIX 项目。  
  
## <a name="prerequisites"></a>先决条件  
 从 Visual Studio 2015 开始，你并不安装 Visual Studio SDK 从下载中心。 它将包括作为 Visual Studio 安装程序中的可选功能。 你还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-classifier-extension"></a>创建分类器扩展  
 编辑器分类器项模板创建颜色的相应文本编辑器分类器 (在这种情况下，所有内容) 任何文本文件中。  
  
1.  在**新项目**对话框框中，展开**Visual C#**或**Visual Basic** ，然后单击**扩展性**。 在**模板**窗格中，选择**VSIX 项目**。 在“名称”框中键入 `TestClassifier`。 单击“确定”。  
  
2.  在**解决方案资源管理器**，右键单击项目节点并选择**添加 / 新项**。 转到 Visual C#**扩展性**节点，然后选择**编辑器分类器**。 保留默认文件名称 (EditorClassifier1.cs)。  
  
3.  有三个代码文件，如下所示：  
  
    -   EditorClassifier1.cs 包含`EditorClassifier1`类。  
  
    -   EditorClassifier1ClassificationDefinition.cs 包含`OEditorClassifier1ClassificationDefinition`类。  
  
    -   EditorClassifier1Format.cs 包含`EditorClassifier1Format`类。  
  
    -   EditorClassifier1Provider.cs 包含`EditorClassifier1Provider`类。  
  
4.  生成项目并启动调试。 将显示 Visual Studio 的实验实例。  
  
     如果你打开一个文本文件，针对紫色背景中带下划线的所有文本。  
  
## <a name="creating-a-text-relative-adornment-extension"></a>创建文本相对修饰扩展  
 编辑器文本修饰模板创建修饰的文本字符的所有实例相对于文本的修饰 'a' 通过使用具有红色边框和背景为蓝色的框。 它是相对于文本的因为框始终叠加的 a 字符，即使它们已移动或重新格式化。  
  
1.  在**新项目**对话框框中，展开**Visual C#**或**Visual Basic** ，然后单击**扩展性**。 在**模板**窗格中，选择**VSIX 项目**。 在“名称”框中键入 `TestAdornment`。 单击“确定”。  
  
2.  在**解决方案资源管理器**，右键单击项目节点并选择**添加 / 新项**。 转到 Visual C#**扩展性**节点，然后选择**编辑器文本修饰**。 保留默认文件名称 (TextAdornment1.cs/vb)。  
  
3.  有两个代码文件，如下所示：  
  
    -   TextAdornment1.cs 包含`TextAdornment1`类。  
  
    -   extAdornment1TextViewCreationListener.cs 包含`TextAdornment1TextViewCreationListener`类。  
  
4.  生成项目并启动调试。 实验实例中出现。 如果你打开一个文本文件，在文本中的所有 a 字符所述针对蓝色背景的红色。  
  
## <a name="creating-a-viewport-relative-adornment-extension"></a>创建相对于视区的修饰扩展  
 编辑器视区修饰模板创建将添加具有到视区的右上角红色轮廓线的紫色框相对于视区的修饰。  
  
> [!NOTE]
>  *视区*是当前显示的文本视图的区域。  
  
#### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>使用编辑器视区修饰模板创建的视区修饰扩展  
  
1.  在**新项目**对话框框中，展开**Visual C#**或**Visual Basic** ，然后单击**扩展性**。 在**模板**窗格中，选择**VSIX 项目**。 在“名称”框中键入 `ViewportAdornment`。 单击“确定”。  
  
2.  在**解决方案资源管理器**，右键单击项目节点并选择**添加 / 新项**。 转到 Visual C#**扩展性**节点，然后选择**编辑器视区修饰**。 保留默认文件名称 (ViewportAdornment1.cs/vb)。  
  
3.  有两个代码文件，如下所示：  
  
    -   ViewportAdornment1.cs 包含`ViewportAdornment1`类。  
  
    -   ViewportAdornment1TextViewCreationListener.cs 包含`ViewportAdornment1TextViewCreationListener`类  
  
4.  生成项目并启动调试。 实验实例中出现。 如果你创建新的文本文件，都有一个红色的框的紫色框所示的视区的右上角。  
  
## <a name="creating-a-margin-extension"></a>创建边距扩展  
 该编辑器边距模板将创建与单词"Hello world ！"一起显示的绿色边距 下面的水平滚动条。  
  
#### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>使用编辑器边距模板创建的边距扩展  
  
1.  在**新项目**对话框框中，展开**Visual C#**或**Visual Basic** ，然后单击**扩展性**。 在**模板**窗格中，选择**VSIX 项目**。 在“名称”框中键入 `MarginExtension`。 单击“确定”。  
  
2.  在**解决方案资源管理器**，右键单击项目节点并选择**添加 / 新项**。 转到 Visual C#**扩展性**节点，然后选择**编辑器视区修饰**。 保留默认文件名称 (EditorMargin1.cs/vb)。  
  
3.  有两个代码文件，如下所示：  
  
    -   EditorMargin1.cs 包含`EditorMargin1`类。  
  
    -   EditorMargin1Factory.cs 包含`EditorMargin1Factory`类。  
  
4.  生成此项目并启动调试。 实验实例中出现。 如果你打开一个文本文件，水平滚动条下面是否显示绿色边距有单词"Hello EditorMargin1"。  
  
## <a name="see-also"></a>另请参阅  
 [语言服务和编辑器扩展点](../extensibility/language-service-and-editor-extension-points.md)