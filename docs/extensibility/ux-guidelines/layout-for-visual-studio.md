---
title: "Visual Studio 的布局 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
caps.latest.revision: 2
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 2
---
# Visual Studio 的布局
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio 对话框的大多数都是 [实用程序对话框布局](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout), ，哪些是 unthemed 对话框该遵循标准 [Windows 桌面对话框布局原则](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx)。 随着 Visual Studio 若要刷新其 UI，一些更加醒目的对话框具有新的设计，用于确定它们为产品定义体验。 这些 [主题对话框布局](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) 有主题的外观。  
  
##  <a name="BKMK_UtilityDialogLayout"></a> 实用程序对话框布局  
  
-   实用程序对话框中的所有控件应该从顶部\/左侧开始，向下流动。  
  
-   永远不会在一个对话框，以填充较大的区域上居中对齐控件。  
  
-   使用环境字体的所有对话框文本。 在编写 visual 规范时，指定环境字体而不是选择特定字体和大小。 请参阅 [环境字体](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)。  
  
-   使用一致的控件间距和放置目标支持耕耘所得到的质量。  
  
-   对话框可能会变得更大数量的控件和 \/ 或控件，唯一 juxtaposition 更复杂。 对于这些复杂的情况，留有足够空间之间控件分组，以便用户能够在逻辑上顺畅进行分析。  
  
### 实用程序对话框布局示例  
 以像素为单位表示的所有维度。  
  
 ![Dialog spacing for labels above controls](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801\-a\_UtilitySpacingAbove")  
  
 **图 a: 08.01 间距指导原则与控件上方标签的实用程序对话框**  
  
 ![Dialog spacing for labels to the left of controls](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801\-b\_UtilitySpacingLeft")  
  
 **图 b: 08.01 间距指导原则与控件左侧标签的实用程序对话框**  
  
### 布局的详细信息  
  
#### 边距  
  
-   所有对话都应有 12 像素的边框环绕所有边缘。  
  
-   为组内的边距应为从框架边缘的 9 个像素。  
  
-   在选项卡控件中的边距应为 6 个像素从选项卡控件的边缘。  
  
#### 命令按钮  
  
-   在内容的对话框框架上运行的命令按钮。 它们应被放置在底部右侧，并应具有更高版本才能将按钮设置明显分离足够变量空间。  
  
-   如果可以在对话框中运行的水平按钮，替代命令按钮配置是在右上角的垂直堆栈。 请参阅 [内部命令按钮](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) 下面。  
  
-   命令按钮 \(低左\/中心对话框的\) 的左边空白区域被视为"带区"对话框操作控件的一部分。 唯一应起、 强行进入该空间是与整个任务或对话框的帮助链接。  
  
-   命令按钮应为 75 x 23 像素。  
  
-   命令按钮应相隔的 6 个像素。  
  
 ![Basic button alignment](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801\-c\_ButtonAlign")  
  
 **图 c: 08.01 基本按钮对齐方式**  
  
#### 标签  
  
-   左对齐所有标签。  
  
-   对于位于以下位置: 控件的上方的标签，它们应该左对齐精确地与它下面的控件和标签的底部应为 5 像素上方的另一个控件 \(例如，组合框\)。  
  
-   对于位于以下位置: 控件左侧标签，标签和输入的控件之间的最小宽度为 10 像素。 应该用于对文本框、 文本框、 组合框或其他控件对齐建立隐式的第二列。  
  
-   标签是句子大小写形式，并跟一个冒号。 请参阅 [文本样式](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)。  
  
#### 控件之间的距离  
 合理地放置控件。 堆积控件之间的间距的没有绝对相关准则。 在控件之间拟合度可能对话框之间稍有变化。 建议的间距是垂直的控件\/标签对 20 像素和 9 个像素水平控件\/标签对。 水平对的最小控制间距是 6 个像素。  
  
 ![Recommended distance between controls](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801\-d\_ControlDistance")  
  
 **控件之间的距离的图 d: 08.01 建议**  
  
#### 控制缩进  
 当嵌套的控件时，将与上面的控件，通常的标签的左边缘的水平的内部控件对齐。  
  
 ![Nested control alignment](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801\-e\_ControlAlign")  
  
 **图 e: 08.01 嵌套控件对齐方式**  
  
#### 控件宽度  
 应不超过该字段的平均输入文本框中或其他类似的控件的宽度。 平均英语单词是五个字符。 例如，文本框中，需要一个长路径名称应为只要允许水平布局，而下拉列表中，为平台名称只应允许的最长的项的长度。  
  
#### 帮助器文本  
  
-   一个对话框，可以显示提供了有关用途的对话框的详细信息的帮助文本。 这通常位于顶部，并且可以是 1\-2 句子。  
  
-   行长度应该是用户可以分析和读取一个舒适宽度。 中等对话框应不超过 550 像素宽。  
  
####  <a name="BKMK_InteriorCommandButtons"></a> 内部命令按钮  
 在更复杂的对话框中，内部控制可能具有其自己相关的按钮，这可能会影响对话框中的提交按钮的位置。  
  
-   使用内部垂直对齐方式 \(列\) 按钮时 **确定**\/**取消** 水平方向在右下角中。  
  
-   使用内部的水平对齐 \(行\) 按钮时 **确定**\/**取消** 在右上角垂直方向。 这种情况下并不常见。  
  
-   内部按钮的大小应为目标匹配的大小的 75 x 23 像素的标准按钮大小 **确定**\/**取消** 按钮在可能的情况。 如果按钮标签超出标准按钮大小按钮，在该集中其他按钮应与该更广的大小保持一致。  
  
 ![Horizontal OK and Cancel buttons](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801\-f\_HorizOKCan")  
  
 **图 f: 08.01 垂直内部水平确定 \/ 取消按钮**  
  
 ![Vertical OK and Cancel buttons](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801\-g\_VertOKCan")  
  
 **图 g: 08.01 水平内部按钮显示垂直确定 \/ 取消**  
  
#### \[浏览...\] 按钮  
 **\[浏览...\]** 按照文本框中的按钮应拼写成"浏览 …" 完全，包括省略号。 如果空间紧密或有多个 **\[浏览...\]** 在屏幕上，按钮的按钮可以减少到只需省略号。  
  
##  <a name="BKMK_ThemedDialogLayout"></a> 主题对话框布局  
 在 Visual Studio 中的主题对话框具有较浅的外观，并提供了更多的空白空间。 版式提供更强调和感兴趣，它提供了更加开放行距和字体大小和重量的变体。 如有可能，chrome 和标题栏已减少或移除。 这些对话框的布局也应遵循此基本模式:  
  
1.  对话框的背景为白色。  
  
2.  中间值显示为灰色没有 1 像素规则边框。  
  
3.  对话框标题不再位于标题栏中，但提供了视觉效果和强调更大的点大小。 \(请参阅字体大小部分中的 [文本样式](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)。\)  
  
4.  应结合了附加的文本，如描述，标签 **环境字体 \+ 粗体**。  
  
5.  内部的列分隔由 1 个像素宽规则以浅灰色。  
  
6.  默认链接都有没有下划线。 悬停和按下的状态已更改颜色以及下划线。  
  
7.  提交按钮 \(如 **确定**\/**取消**\) 位于右下角。  
  
### 主题对话框布局示例  
 ![Themed dialog layout](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801\-h\_ThemedDialog")  
  
 **图 h: 08.01 主题对话框**  
  
 ![Themed dialog dimensions](~/docs/extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801\-i\_ThemedDialogDimensions")  
  
 **图 i: 08.01 主题对话框 – 维度**  
  
 ![Themed dialog fonts](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801\-j\_ThemedDialogFonts")  
  
 **图 j: 08.01 主题对话框 – 字体**  
  
 ![Themed dialog colors](~/docs/extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801\-k\_ThemedDialogColors")  
  
 **图 k: 08.01 主题对话框 – 颜色**  
  
## 请参阅  
 [Visual Studio 的应用程序模式](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)   
 [控件 \(Windows\)](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx)   
 [对话框 \(Windows\)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx)