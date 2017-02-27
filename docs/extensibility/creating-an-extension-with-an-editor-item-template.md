---
title: "在编辑器中的项模板创建扩展 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，新的扩展"
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# 在编辑器中的项模板创建扩展
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可以使用 Visual Studio SDK 来创建基本编辑器扩展插件添加到编辑器中的分类器、 修饰和边距中包含的项模板。 编辑器项模板是适用于 Visual C\# 或 Visual Basic VSIX 项目。  
  
## 先决条件  
 启动 Visual Studio 2015 中，您并不安装 Visual Studio SDK 从下载中心获得。 它将包括作为 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## 创建分类器扩展  
 编辑器分类器项目模板将创建一个相应的文本的颜色的编辑器分类器 \(在这种情况下，所有内容\) 的任何文本文件中。  
  
1.  在 **新项目** 对话框框中，展开 **Visual C\#** 或 **Visual Basic** ，然后单击 **扩展性**。 在 **模板** 窗格中，选择 **VSIX 项目**。 在 **名称** 框中，键入 `TestClassifier`。 单击“确定”。  
  
2.  在 **解决方案资源管理器**, ，用鼠标右键单击项目节点并选择 **添加 \/ 新项**。 转到 Visual C\# **扩展性** 节点，然后选择 **编辑器分类器**。 保留默认的文件名 \(EditorClassifier1.cs\)。  
  
3.  有三个代码文件，如下所示:  
  
    -   EditorClassifier1.cs 包含 `EditorClassifier1` 类。  
  
    -   EditorClassifier1ClassificationDefinition.cs 包含 `OEditorClassifier1ClassificationDefinition` 类。  
  
    -   EditorClassifier1Format.cs 包含 `EditorClassifier1Format`  类。  
  
    -   EditorClassifier1Provider.cs 包含 `EditorClassifier1Provider` 类。  
  
4.  生成项目并启动调试。 将显示 Visual Studio 的实验实例。  
  
     如果您打开一个文本文件，所有文本具有都下划线紫色背景。  
  
## 创建相对于文本的修饰扩展  
 编辑器文本修饰模板创建修饰的文本字符的所有实例相对于文本的修饰 'a' 使用都有一个红色的框和蓝色背景的框。 它是相对于文本的由于框中始终覆盖层的 a 字符，即使它们被移动或重新格式化。  
  
1.  在 **新项目** 对话框框中，展开 **Visual C\#** 或 **Visual Basic** ，然后单击 **扩展性**。 在 **模板** 窗格中，选择 **VSIX 项目**。 在 **名称** 框中，键入 `TestAdornment`。 单击“确定”。  
  
2.  在 **解决方案资源管理器**, ，用鼠标右键单击项目节点并选择 **添加 \/ 新项**。 转到 Visual C\# **扩展性** 节点，然后选择 **编辑器文本修饰**。 保留默认的文件名 \(TextAdornment1.cs\/vb\)。  
  
3.  有两个代码文件，如下所示:  
  
    -   TextAdornment1.cs 包含 `TextAdornment1` 类。  
  
    -   extAdornment1TextViewCreationListener.cs 包含 `TextAdornment1TextViewCreationListener` 类。  
  
4.  生成项目并启动调试。 将显示的实验实例。 如果您打开一个文本文件，在文本中的所有 a 字符轮廓以蓝色背景的红色。  
  
## 创建相对于视区的修饰扩展  
 编辑器视区修饰模板将创建将添加一个具有红色的轮廓线到视区的右上角的紫色框相对于视区的修饰。  
  
> [!NOTE]
>  *视区* 是当前显示的文本视图的区域。  
  
#### 若要通过使用编辑器视区修饰模板创建一个视区修饰扩展  
  
1.  在 **新项目** 对话框框中，展开 **Visual C\#** 或 **Visual Basic** ，然后单击 **扩展性**。 在 **模板** 窗格中，选择 **VSIX 项目**。 在 **名称** 框中，键入 `ViewportAdornment`。 单击“确定”。  
  
2.  在 **解决方案资源管理器**, ，用鼠标右键单击项目节点并选择 **添加 \/ 新项**。 转到 Visual C\# **扩展性** 节点，然后选择 **编辑器视区修饰**。 保留默认的文件名 \(ViewportAdornment1.cs\/vb\)。  
  
3.  有两个代码文件，如下所示:  
  
    -   ViewportAdornment1.cs 包含 `ViewportAdornment1` 类。  
  
    -   ViewportAdornment1TextViewCreationListener.cs 包含 `ViewportAdornment1TextViewCreationListener` 类  
  
4.  生成项目并启动调试。 将显示的实验实例。 如果创建新的文本文件，都有一个红色的框的紫色框被显示在视区的右上角。  
  
## 创建扩展名为边距  
 该编辑器的边缘模板将创建与单词"Hello world\!"一起显示的绿色边距 下面的水平滚动条。  
  
#### 使用编辑器的边缘模板创建扩展名为边距  
  
1.  在 **新项目** 对话框框中，展开 **Visual C\#** 或 **Visual Basic** ，然后单击 **扩展性**。 在 **模板** 窗格中，选择 **VSIX 项目**。 在 **名称** 框中，键入 `MarginExtension`。 单击“确定”。  
  
2.  在 **解决方案资源管理器**, ，用鼠标右键单击项目节点并选择 **添加 \/ 新项**。 转到 Visual C\# **扩展性** 节点，然后选择 **编辑器视区修饰**。 保留默认的文件名 \(EditorMargin1.cs\/vb\)。  
  
3.  有两个代码文件，如下所示:  
  
    -   EditorMargin1.cs 包含 `EditorMargin1` 类。  
  
    -   EditorMargin1Factory.cs 包含 `EditorMargin1Factory` 类。  
  
4.  生成此项目并启动调试。 将显示的实验实例。 如果您打开一个文本文件，绿色边距中的某些词语"Hello EditorMargin1"，如下所示的水平滚动条。  
  
## 请参阅  
 [语言服务和编辑器扩展点](../extensibility/language-service-and-editor-extension-points.md)