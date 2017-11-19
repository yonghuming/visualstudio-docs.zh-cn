---
title: "Visual Studio 布局 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
caps.latest.revision: "2"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0ebb82c49820bdd664324984bd7d3bb88a5bb5fd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="layout-for-visual-studio"></a>Visual Studio 的布局
Visual Studio 对话框的大部分[实用工具对话框布局](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout)，这是 unthemed 对话框该按照标准[Windows 桌面对话框布局原则](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx)。 Visual Studio 移动，以便刷新其 UI，一部分变得较为突出对话框必须建立它们为产品定义体验的新设计。 这些[主题对话框布局](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout)具有主题的外观。  
  
##  <a name="BKMK_UtilityDialogLayout"></a>实用程序对话框布局  
  
-   实用工具对话框内的所有控件应开始顶部/左侧，向下流动。  
  
-   永远不会在一个对话框，以填充大型区域上居中对齐控件。  
  
-   使用环境字体的所有对话框文本。 当编写 visual 规范时，指定环境字体而不是选择特定的字体和大小。 请参阅[环境字体](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)。  
  
-   使用统一的控制间距和放置目标支持为在编程工作的质量。  
  
-   对话框可能变得更多的控件和 / 或控件的唯一 juxtaposition 从更复杂。 对于这些复杂的情况，允许控制分组，可以向用户授予在逻辑上顺畅分析之间有足够的空间。  
  
### <a name="utility-dialog-layout-examples"></a>实用程序对话框布局示例  
 以像素为单位表示的所有维度。  
  
 ![控件上方标签的对话框间距](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801 a_UtilitySpacingAbove")  
  
 **与控件上方标签的实用程序对话框图答： 08.01 间距准则**  
  
 ![控件左侧标签的对话框间距](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801 b_UtilitySpacingLeft")  
  
 **图 b: 08.01 间距带有控件左侧标签的实用程序对话框的准则**  
  
### <a name="layout-details"></a>布局详细信息  
  
#### <a name="margins"></a>边距  
  
-   所有对话应都具有所有边缘 12 像素边框。  
  
-   在组范围内的边距应为 9 像素从框架边缘。  
  
-   选项卡控件内的边距应为从选项卡控件的边缘的 6 个像素。  
  
#### <a name="command-buttons"></a>命令按钮  
  
-   在不在内容的对话框框架上运行命令按钮。 它们应将放置在底部右侧，且应具有更高版本以设置按钮的方式很明确单独足够变量空间。  
  
-   如果有运行在对话框内的水平按钮，备用命令按钮配置是在右上角的垂直堆栈。 请参阅[内部命令按钮](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons)下面。  
  
-   命令按钮 （底部左侧/中央对话框） 左侧的空间视为对话框操作控件的"带"的一部分。 该空间应入侵的唯一操作是与整个任务或对话框相关的帮助链接。  
  
-   命令按钮应为 75 x 23 像素。  
  
-   命令按钮应相隔的 6 个像素。  
  
 ![基本按钮对齐方式](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801 c_ButtonAlign")  
  
 **图 c: 08.01 基本按钮对齐方式**  
  
#### <a name="labels"></a>标签  
  
-   左对齐所有标签。  
  
-   对于位于控件上方的标签，它们应左对齐精确地与它下面的控件和标签底部应该是上面的其他控件 （例如，组合框） 的顶部的 5 个像素。  
  
-   对于位于以下位置： 控件左侧标签，标签的输入的控件之间的最小宽度为 10 像素。 应为对齐的文本框、 组合框或其他控件建立隐含的第二个列。  
  
-   标签是句子大小写形式后, 跟一个冒号。 请参阅[文本样式](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)。  
  
#### <a name="distance-between-controls"></a>控件之间的距离  
 规范的合理堆栈控件。 没有任何绝对指导来堆积控件之间的间距。 在控件之间拟合度之间对话框可能略有不同。 建议的间距是垂直的控件标签对 20 像素和水平的控件标签对 9 个像素。 水平对的最小控件间距是 6 个像素。  
  
 ![建议控件之间的距离](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801 d_ControlDistance")  
  
 **控件之间的距离的图 d: 08.01 建议**  
  
#### <a name="control-indentation"></a>控件缩进  
 当嵌套控件时，将上面的控件，通常的标签的左边缘与水平的内部控件对齐。  
  
 ![嵌套的控件对齐效果](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801 e_ControlAlign")  
  
 **图 08.01 e： 嵌套控件对齐效果**  
  
#### <a name="control-width"></a>控件宽度  
 应不超过字段的平均输入的文本框中或其他相似的控件的宽度。 平均的英语断为五个字符。 例如，文本框中，需要长路径名称应为只要允许水平布局，尽管下拉列表中平台名称只应允许的最长的项的长度。  
  
#### <a name="helper-text"></a>帮助程序文本  
  
-   一个对话框可以显示提供了有关用途的对话框的详细信息的帮助程序文本。 这通常位于顶部，并且可以是 1-2 句子。  
  
-   行长度应该是用户可以分析和读取适应宽度。 中等规模对话框应不超过 550 像素宽。  
  
####  <a name="BKMK_InteriorCommandButtons"></a>内部命令按钮  
 在更复杂的对话框中，内部控件可能具有其自己的相关的按钮，这可能会影响对话框的提交按钮的位置。  
  
-   使用内部垂直对齐方式 （列） 按钮时**确定**/**取消**在右下角的水平方向。  
  
-   使用内部水平对齐方式 （行） 按钮时**确定**/**取消**在右上角的垂直方向。 这种情况下并不常见。  
  
-   内部按钮大小应为目标的 75 x 23 像素，匹配的大小的标准按钮大小**确定**/**取消**按钮在可能的情况。 如果按钮标签进行超过了标准按钮大小的按钮，在该集中其他按钮应与该更宽的大小保持一致。  
  
 ![水平确定和取消按钮](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801 f_HorizOKCan")  
  
 **水平确定 / 取消与图 f: 08.01 垂直内部按钮**  
  
 ![垂直确定和取消按钮](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801 g_VertOKCan")  
  
 **带垂直确定 / 取消的图 08.01 g： 水平内部按钮**  
  
#### <a name="browse-button"></a>[浏览...]按钮  
 **[浏览...]**出"浏览 …"，请按照文本框中的按钮应拼写以完整、 包括省略号。 如果空间紧密或有多个**[浏览...]**在屏幕上，该按钮的按钮可以减少到仅省略号。  
  
##  <a name="BKMK_ThemedDialogLayout"></a>主题对话框布局  
 Visual Studio 中的主题对话框具有更轻的外观，并提供更多的空白区域。 版式提供更多强调和感兴趣，它提供了更加开放的行距和变化的字体大小和权重。 如果可能，具有已减少 chrome 和标题栏或将其删除。 这些对话框的布局应遵循此基本模式：  
  
1.  对话框的背景为白色。  
  
2.  中间值显示为灰色没有 1 像素规则边框。  
  
3.  对话框的标题不再位于标题栏中，但提供视觉效果和更大的点大小的强调。 (请参阅中的字体大小部分[文本样式](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)。)  
  
4.  应与其他文本，如描述，结合使用的标签**环境字体 + 粗体**。  
  
5.  内部列由浅灰色中的 1 个像素宽规则分隔开。  
  
6.  默认的链接有不带任何下划线。 悬停和已按下的状态具有颜色更改加下划线。  
  
7.  提交按钮 (如**确定**/**取消**) 位于右下角。  
  
### <a name="themed-dialog-layout-examples"></a>主题对话框布局示例  
 ![主题对话框布局](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801 h_ThemedDialog")  
  
 **图 08.01-h： 主题对话框**  
  
 ![主题对话框尺寸](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801 i_ThemedDialogDimensions")  
  
 **图 08.01-i： 主题对话框尺寸**  
  
 ![主题对话框字体](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801 j_ThemedDialogFonts")  
  
 **图 j: 08.01 主题对话框字体**  
  
 ![主题对话框颜色](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801 k_ThemedDialogColors")  
  
 **图 k: 08.01 主题对话框颜色**  
  
## <a name="see-also"></a>另请参阅  
 [Visual Studio 的应用程序模式](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)   
 [控件 (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx)   
 [对话框 (Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx)