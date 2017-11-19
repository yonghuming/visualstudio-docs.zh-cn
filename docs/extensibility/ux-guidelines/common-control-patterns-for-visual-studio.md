---
title: "Visual Studio 的常见控件模式 |Microsoft 文档"
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3e06a3e89b69b2b69a97c4deb2d68d98913f6e03
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="common-control-patterns-for-visual-studio"></a>Visual Studio 的常见控件模式
##  <a name="BKMK_CommonControls"></a>公共控件  
  
### <a name="overview"></a>概述  
公共控件构成了 Visual Studio 中的用户界面的大部分。 在 Visual Studio 界面中使用的最常见的控件应遵循[Windows 桌面交互准则](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx)。 本主题是特定于 Visual Studio，并介绍了特殊的情况下或增加这些 Windows 准则的详细信息。  
  
#### <a name="common-controls-in-this-topic"></a>本主题中的公共控件  
  
-   [滚动条](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)  
  
-   [输入的字段](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)  
  
-   [组合框和下拉列表](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)  
  
-   [复选框](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)  
  
-   [单选按钮](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)  
  
-   [组框架](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)  
  
-   [文本控件](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
-   [按钮和超链接](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
-   [树视图](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)  
  
#### <a name="visual-style"></a>视觉样式  
样式控件时要考虑的第一件事是是否在主题 UI 中使用的控件。 为非主题 UI 中的标准 UI 控件，并必须遵循[正常的 Windows 桌面样式](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742399\(v=vs.85\).aspx)，这意味着它们不是重新模板化，应出现在其默认控件外观。  
  
-   **标准 （实用工具） 对话框：**没有主题。 不重新创建模板。 使用基本控件样式默认值。  
  
-   **工具窗口、 文档编辑器，设计图面和主题的对话框：**使用使用颜色服务的专门主题的外观。  
  
###  <a name="BKMK_Scrollbars"></a>滚动条  
 滚动条应遵循[常见的交互模式适用于 Windows 滚动条](https://msdn.microsoft.com/en-us/library/windows/desktop/bb787527\(v=vs.85\).aspx)除非它们扩充内容信息，如在代码编辑器中。  
  
###  <a name="BKMK_InputFields"></a>输入的字段  
 对于典型交互行为，请按照[文本框中的 Windows 桌面准则](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742442\(v=vs.85\).aspx)。  
  
#### <a name="visual-style"></a>视觉样式  
  
-   输入的字段不应风格实用程序对话框中。 使用固有的控件的基本形式。  
  
-   主题的输入的字段应仅用于主题的对话框和工具窗口中。  
  
#### <a name="specialized-interactions"></a>专用的交互  
  
-   只读字段将具有灰色 （禁用） 背景但 （活动） 的默认前景色。  
  
-   所需字段应具有**\<所需 >**一样水印其中。 不应更改除中极少数情况下的背景的颜色。  
  
-   验证错误： 请参阅[通知和 Visual Studio 的进度](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)  
  
-   输入的字段应调整大小以适应内容不适用于在其中显示它们，窗口的宽度也任意匹配长的字段，例如，路径的长度。 长度可能向用户表示的字段中允许多少个字符限制。  
  
     ![不正确的输入的字段长度： 不太可能的名称将为这么长。] (../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707年 01_IncorrectInputFieldControl")<br />不正确的输入的字段长度： 不太可能的名称将为这么长。
  
     ![更正输入的字段长度： 输入的字段是合理预期的内容宽度。] (../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707年 02_CorrectInputFieldControl")<br />更正输入的字段长度： 输入的字段是合理预期的内容宽度。
  
###  <a name="BKMK_ComboBoxesAndDropDowns"></a>组合框和下拉列表  
对于典型交互行为，请按照[下拉列表和组合框的 Windows 桌面准则](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742404\(v=vs.85\).aspx)。  
  
#### <a name="visual-style"></a>视觉样式  
  
-   在实用工具对话框中，不重新创建模板控件。 使用固有的控件的基本形式。  
  
-   在主题 UI 中组合框和下拉列表遵循标准主题的控件。  
  
#### <a name="layout"></a>布局  
组合框和下拉列表的大小以适合内容不适用于在其中显示它们，窗口的宽度也任意匹配长的字段，例如，路径的长度。  
  
![不正确： 下拉宽度为太长，将显示的内容。] (../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707年 03_IncorrectDropDownLayout")<br />不正确： 下拉宽度为太长，将显示的内容。
  
![正确： 下拉列表的大小以允许翻译增长，但不是会不必要地长。] (../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707年 04_CorrectDropDownLayout")<br />正确： 下拉列表的大小以允许翻译增长，但不是会不必要地长。 
  
###  <a name="BKMK_CheckBoxes"></a>复选框  
对于典型交互行为，请按照[复选框的 Windows 桌面准则](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742401\(v=vs.85\).aspx)。  
  
#### <a name="visual-style"></a>视觉样式  
  
-   在实用工具对话框中，不重新创建模板控件。 使用固有的控件的基本形式。  
  
-   在主题 UI 中的复选框按照标准主题的控件。  
  
#### <a name="specialized-interactions"></a>专用的交互  
  
-   带一个复选框的交互必须永远不会弹出一个对话框，或导航到另一个区域。  
  
-   对齐文本的第一行的基线的复选框。  
  
     ![不正确： 复选框处于居中位置的文本。] (../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707年 05_IncorrectCheckBoxAlign")<br />不正确： 复选框处于居中位置的文本。
  
     ![正确： 复选框对齐文本的第一行。] (../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707年 06_CorrectCheckBoxAlign")<br />正确： 复选框对齐文本的第一行。
  
###  <a name="BKMK_RadioButtons"></a>单选按钮  
对于典型交互行为，请按照[单选按钮的 Windows 桌面准则](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742436\(v=vs.85\).aspx)。  
  
#### <a name="visual-style"></a>视觉样式  
在实用工具对话框中，执行操作不样式单选按钮。 使用固有的控件的基本形式。  
  
#### <a name="specialized-interactions"></a>专用的交互  
不需要使用组框架括起单选选择，除非你需要维护组紧密布局中的差异。  
  
###  <a name="BKMK_GroupFrames"></a>组框架  
对于典型交互行为，请按照[组框架的 Windows 桌面准则](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742405\(v=vs.85\).aspx)。  
  
#### <a name="visual-style"></a>视觉样式  
在实用工具对话框中，不设置的样式组框架。 使用固有的控件的基本形式。  
  
#### <a name="layout"></a>布局  
  
-   不需要使用组框架括起单选选择，除非你需要维护组紧密布局中的差异。  
  
-   永远不会用组框架来实现单个控件。  
  
-   因此，有时可接受使用水平规则而不是组框架容器。  
  
##  <a name="BKMK_TextControls"></a>文本控件

### <a name="static-text-fields"></a>静态文本字段

静态文本字段不能由用户选择，和显示只读信息。 应避免使用它的任何文本，用户可能想要复制到剪贴板。 但是，只读的静态文本可以更改以反映状态的更改。 在下面，输出名称下的信息组更改以反映到它上面的根 Namespace 文本框所做的任何更改的静态文本的示例。

有两种方法，以显示静态文本的信息。

静态文本可以是在其自己在对话框中，而无需任何包含没有分组冲突。 决定是否真正必要的额外行的一个框。 一个示例是目录路径组行中，所创建部分下的显示，如下所示：  

![文本控件中的静态文本信息](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "DisplayingStaticText.png")<br />文本控件中的静态文本的信息

在对话框中存在其他分组的区域，其中包含的信息可帮助提高可读性，和当部分可以显示或隐藏 (如**属性窗口**说明窗格) 或者你想要与类似 UI 中，保持一致放置在一个框静态文本。 此分组框应为单个规则和带有`ButtonShadow`:

![在属性窗口中的静态文本](../../extensibility/ux-guidelines/media/PropertiesWindow.png "PropertiesWindow.png")<br />在属性窗口中的静态文本

### <a name="read-only-text-box"></a>只读文本框

这允许用户选择字段内的文本，但不是能编辑它。 通过使用常用的三维方形界定这些文本框`ButtonShadow`填充。

文本框可以变为活动状态 （编辑） 时用户更改关联的控件，例如检查/取消选中复选框，或选择/取消选择一个单选按钮。 例如，在**工具&gt;选项**页所示，**主页**文本框将成为活动时**使用默认值**复选框处于未选中状态。

![只读文本框中，显示非活动和活动状态](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />只读文本框中，显示非活动和活动状态

### <a name="using-text-in-dialogs"></a>在对话框中使用文本

对话框中的文本的重要原则：

-   文本框、 列表框和 unthemed 对话框中的帧的标签以谓词开头，对第一个字，首字母大写和以冒号结束。

    > 主题对话框中的文本控件将遵循[Windows 桌面 UX 准则](https://msdn.microsoft.com/library/windows/desktop/dn742479.aspx)且不会结束标点，除了问号中帮助链接。

-   对于复选框和选项按钮标签开头谓词，在第一个字，首字母大写和有未结束标点。

-   按钮、 菜单、 菜单项和选项卡的标签对 （词首字母大写） 的每个单词的首字母大写。

-   标签术语应与其他对话框中的类似标签一致。

-   如果可能，具有写入或之前它将转到开发人员可以实现针对审批文本编写器/编辑器。

-   所有控件都应有标签除外的特殊情况下在哪些按 tab 键就足够了。
使用帮助程序文本在适当的时候。

### <a name="helper-text"></a>帮助程序文本

包含在对话框以帮助用户了解对话框的目的，或以指示要采取的操作。 帮助程序文本应使用仅在需要时以避免干扰简单对话框。 帮助器文本的两种变化是对话框和水印。

按照帮助器文本的常见位置，并可选择性中引入新区域。 帮助器文本的常见方案是：

-   在对话框中，提供有关如何与复杂对话框进行交互的其他方向的帮助程序文本。

-   中的空工具窗口或对话框，以解释为什么没有内容是可见的水印文本。

-   说明窗格中，如在底部**属性窗口**。

-   水印空编辑器，以解释用户若要开始所应采取什么操作中的文本。
  
### <a name="dialog-helper-text"></a>对话框帮助程序文本

用户体验设计器可帮助确定帮助程序文本适合。 设计器可以定义帮助程序文本以及其常规内容的显示位置。 用户协助可以写入/编辑实际文本。

### <a name="watermarks"></a>水印

对话框受益于略有不同的水印准则。 由于出现一个对话框，可以正忙，有许多 UI 元素 （标签、 提示文本、 按钮和其他容器控件中的与文本），尤其是当那些出现在黑色，水印突出以深灰色的好 (VSColor: `ButtonShadow`)。 水印通常在类似具有白色背景的列表框控件中显示 (VSColor: `Window`)。

-   文本显示在深灰色 (VSColor: `ButtonShadow`)。 但是，如果水印出现在中型灰色或其他颜色 (VSColor: `ButtonFace`) 后台并没有其可读性感到担忧，请转底黑字 (VSColor: `WindowText`)。

-   水印可以居中或两端对齐。 将标准设计规则的应用进行对齐方式的决策时。 水印不能选择背景上。

![水印文本示例](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />水印文本示例

### <a name="context-specific-dynamic-text"></a>特定于上下文 （动态） 文本

动态文本可以是使用的一种在对话框或无模式的用户界面中的两种方式： 或动态标签作为动态内容。

-   动态标签： 动态文本的一个常见用途是提供详细信息所选项目，如在一个对话框，其中包含的元素和属性右侧的网格中显示这些元素的列表中的描述性面板中。 属性网格的标签可能是动态的以便在左侧选择项目时，右侧的网格显示为该特定项的信息。

-   动态文本： 可以在其中你需要在这种方式，显示的特定信息和不是一般信息，但应格外小心地不要过度使用的实例。

如果你希望用户能够复制信息的能力，动态文本应为只读的文本字段中。
  
##  <a name="BKMK_ButtonsAndHyperlinks"></a>按钮和超链接  
  
### <a name="overview"></a>概述  
按钮和链接控件 （的超链接） 应遵循[的超链接的基本 Windows 桌面指南](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742406\(v=vs.85\).aspx)对于用法，词语、 调整大小，和间距。  
  
### <a name="choosing-between-buttons-and-links"></a>按钮和链接之间进行选择  
传统上，操作使用按钮和超链接已保留导航。 按钮可在所有情况下，但已得到扩展 Visual Studio 中的链接的角色，以便按钮和链接是在某些情况下更可互换。  
  
何时使用命令按钮：  
  
-   主命令  
  
-   显示用于收集输入的 windows 或进行选择，即使它们是辅助命令  
  
-   破坏性或不可逆的操作  
  
-   向导和页流内的承诺按钮  
  
避免工具窗口中的命令按钮或如果标签需要两个以上的词。 链接可以具有更长的标签。  
  
 何时使用链接：  
  
-   导航到另一个窗口、 文档或网页  
  
-   情况下，需要更长的标签或短句子来描述操作的目的  
  
-   其中一个按钮将占用大量的 UI，前提是操作不破坏性或不可逆的紧密空间  
  
-   取消加重辅助命令的情况下在其中有很多命令  
  
#### <a name="examples"></a>示例  
![命令后面的状态消息的信息栏中使用链接](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703 01_CommandLinkInfobar")<br />使用以下状态消息的信息栏中的命令链接
  
![CodeLens 弹出中使用链接](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703 02_LinksInCodeLens")<br />CodeLens 弹出中使用的链接
  
![链接辅助命令的用于其中按钮会引起过多关注](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703 03_LinksAsSecondaryCommands")<br />用于辅助命令按钮将在其中吸引过多关注的链接
  
### <a name="common-buttons"></a>常见的按钮  
  
#### <a name="text"></a>Text  
请按照中的写入准则[UI 文本和术语](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)。  
  
#### <a name="visual-style"></a>视觉样式  
  
##### <a name="standard-unthemed"></a>标准 (unthemed)  
Visual Studio 中的大多数按钮将显示实用程序对话框中，并且不应风格。 所指示的操作系统，它们应反映标准按钮的外观。  
  
##### <a name="themed"></a>主题  
在某些情况下，可能在应用了样式的用户界面中使用按钮和必须适当地设置样式这些按钮。 请参阅[对话框](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)有关主题的控件的信息。  
  
### <a name="special-buttons"></a>特殊的按钮  
  
#### <a name="browse-buttons"></a>浏览...按钮  
**[浏览...]**按钮使用网格、 对话框和工具窗口和其他无模式的 UI 元素。 它们显示了选取器，可帮助用户成为控件填充一个值。 有两种变体此按钮，长和短。  
  
![长 [浏览...] 按钮](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703 04_BrowseLong")<br />长 [浏览...] 按钮
  
![短仅省略号 [...] 按钮](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703 05_BrowseShort")<br />短仅省略号 [...] 按钮
  
何时使用仅省略号短按钮：  
  
-   如果有多个一个长**[浏览...]**在对话框中，如多个字段时可用来浏览按钮。 使用短**[…]**按钮以删除以避免通过这种情况下创建的令人困惑的访问密钥 (**（& a) 浏览**和**（&) 浏览**在同一对话框)。  
  
-   在紧密对话框中，或在没有任何合理的地方安置长按钮时。  
  
-   如果该按钮将显示一个网格控件中。  
  
有关使用按钮的指导原则：  
  
-   不要使用访问密钥。 若要访问它使用键盘，用户必须使用 tab 键从相邻的控件。 确保 tab 键顺序以便立即后将填充的字段位于任何浏览按钮。 绝不要使用下面的第一个期间下划线。  
  
-   设置 Microsoft Active 可访问性 (MSAA)**名称**属性**浏览...** （包括省略号） 以便，屏幕读取器将读取它作为"浏览"并不是"点点点"或"段的段的期。" 对于托管的控件，这意味着设置**AccessibleName**属性。  
  
-   永远不会使用省略号**[…]**浏览操作之外的按钮。 例如，如果你需要**[新建...]**按钮，但没有足够的空间的文本，则需要重新设计的对话框。  
  
##### <a name="sizing-and-spacing"></a>大小和间距  
![大小调整 [浏览...] 按钮： 标准版本为 75 x 23 像素，简短版本为 26 x 23 像素](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703 06_BrowseSizing")<br />调整[浏览...]按钮大小
  
![间距 [浏览...] 按钮： 间距相关的控件和标准的浏览按钮 7 像素之间，相关的控件和短浏览之间的间距按钮 5 个像素](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703 07_BrowseSpacing")<br />设置[浏览...]按钮间距
  
#### <a name="graphical-buttons"></a>图形按钮  
一些按钮应始终使用数据的图形图像，永远不会包含文本，以节省空间并避免本地化问题。 这些通常用于字段选取和其他可排序的列表中。  
  
> **注意：**用户必须向这些按钮 （没有任何访问密钥） 选项卡上，因此将其放在合理的顺序。 映射`name`以便屏幕读取器正确解释此按钮的操作所需的操作的按钮属性。  
  
| 函数 | Button |  
| --- | --- |  
| 添加 | ![图形"添加"按钮](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703 08_ButtonAdd") |
| 删除 | ![图形"删除"按钮](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703 09_ButtonRemove") |
| 添加所有 | ![图形"全部添加"按钮](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703 10_ButtonAddAll") |
| 删除所有 | ![图形"全部删除"按钮](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703 11_ButtonRemoveAll") |
| 上移 | ![图形"上移"按钮](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703 12_ButtonMoveUp") |
| 下移 | ![图形"下移"按钮](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703 13_ButtonMoveDown") |
| 删除 | ![图形"删除"按钮](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703 14_ButtonDelete") |
  
##### <a name="sizing-and-spacing"></a>大小和间距  
大小调整图形按钮为与的较短形式相同**[浏览...]**按钮 （26 x 23 像素为单位）：  
  
![图形上使用和不使用透明颜色显示的按钮图像外观](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703 15_GraphicalButtonSpacing")<br />使用和不使用透明颜色显示的按钮上的图形映像的外观
  
### <a name="hyperlinks"></a>超链接  
超链接非常适合于基于导航的操作，如打开帮助主题、 模式对话框或向导。 如果超链接用于命令，它应始终显示到 UI 的可见和明显更改。 一般情况下，提交的操作 （例如，保存，取消，并删除） 的操作来更好地传递使用按钮。  
  
#### <a name="writing-style"></a>书写样式  
请按照[用户界面文本的 Windows 桌面指南](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx)。 不要使用"了解更多关于，""告诉我详细关于，"或"获取帮助与此"分段。 相反，短语在主要的帮助内容由回答的问题方面的帮助链接文本。 例如，"**如何将服务器添加到服务器资源管理器？**"  
  
#### <a name="visual-style"></a>视觉样式  
  
-   应始终使用超链接[VSColor 服务](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)。 如果超链接样式不正确，则它将闪烁红色活动时或显示后要访问的另一种颜色。  
  
-   不包含在控件停留在线状态，除非链接是一个完整的句子中的句子片段如水印中的下划线。  
  
-   悬停时，不应显示下划线。 相反，向用户链接处于活动状态的反馈是略颜色更改和相应的链接光标。  
  
##  <a name="BKMK_TreeViews"></a>树视图  
  
树视图提供一种组织复杂方式列出到父-子组。 用户可以展开或折叠父组，以显示或隐藏基础子项目。 可以选择的树视图中每个项，以提供进一步的操作。  
  
###  <a name="BKMK_TreeViewVisualStyle"></a>树视图视觉样式  
  
#### <a name="expanders"></a>扩展器  
使用 Windows 和 Visual Studio 的扩展器设计应符合树视图控件。 每个节点使用的扩展器控件来显示或隐藏基础项。 使用扩展器控件的用户可能会遇到 Windows 和 Visual Studio 中的不同的树视图中提供一致性。  
  
![正确： 使用扩展器控件的树视图节点的正确样式](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705 1_TreeViewCorrect")<br />使用扩展器控件的树视图节点的正确： 正确样式
  
![不正确： 不正确的样式的树视图节点](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705 2_TreeViewIncorrect1")<br />不正确： 不正确的样式的树视图节点
  
#### <a name="selection"></a>选择  
当在树视图中选择一个节点时，突出显示应扩展到整个树视图控件的宽度。 这有助于用户清楚地标识他们选择的项。 选择颜色应反映当前的 Visual Studio 主题。  
  
![正确： 突出显示所选节点的适合树视图控件的整个宽度。] (../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705 1_TreeViewCorrect")<br />正确： 突出显示所选节点的适合树视图控件的整个宽度。
  
![不正确： 突出显示所选节点的不符合树视图控件的整个的宽度。] (../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705 3_TreeViewIncorrect2")<br />不正确： 突出显示所选节点的不符合树视图控件的整个的宽度。
  
#### <a name="icons"></a>图标  
图标仅应使用树视图控件中，如果它们帮助直观地确定项之间的差异。 一般情况下，应仅在异类列表中的图标的执行信息来区分类型的元素中使用的图标。 在同类列表程序使用图标可以经常被视为干扰，应当避免。 在这种情况下 （父） 中的组图标，可以提供其中的项的类型。 如果图标是动态的并且可用来指示状态将是此规则的例外。  
  
#### <a name="scroll-bars"></a>滚动条  
如果内容适合在树视图控件，应始终隐藏滚动条。 它是可接受的滚动条在可滚动的窗口中是隐藏的或不完全透明和显示包含的树视图窗口拥有焦点时或在树的悬停时查看本身。  
  
![因为内容已经超出了树视图控件的限制，则会显示这两个垂直和水平滚动条。] (../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705 4_Scrollbars")<br />因为内容已经超出了树视图控件的限制，则会显示这两个垂直和水平滚动条。
  
###  <a name="BKMK_TreeViewInteractions"></a>树视图交互  
  
#### <a name="context-menus"></a>上下文菜单  
树视图节点可能会显示上下文菜单中的子菜单选项。 通常，用户已用鼠标右键单击某个项或使用选择的项的 Windows 键盘上按下菜单键时出现此情况。 很重要，该节点获得焦点，并选择。 这有助于用户确定哪一项所属的子菜单。  
  
![已选择具有生成通知用户的上下文菜单提升焦点的项的项。] (../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705 5_ContextMenu")<br />已选择具有生成通知用户的上下文菜单提升焦点的项的项。
  
#### <a name="keyboard"></a>键盘  
树视图应提供用于选择项并展开/折叠节点上使用键盘功能。 这可确保导航满足我们的可访问性要求。  
  
##### <a name="tree-view-control"></a>树视图控件  
Visual Studio 树控件应遵循常见键盘导航：  
  
-   **向上箭头：**选定的树中向上移动项目  
  
-   **向下箭头：**通过树向下移动选择项  
  
-   **右箭头：**展开树中的节点  
  
-   **向左键：**折叠树中的节点  
  
-   **输入密钥：**启动，加载、 执行所选的项  
  
##### <a name="trid-tree-view-and-grid-view"></a>Trid （树视图和网格视图）  
Trid 控件是包含在网格中的树视图的复杂控件。 展开、 折叠，和导航树应遵循相同的键盘命令作为树视图中，并添加以下内容：  
  
-   **右箭头：**展开节点。 展开节点后，它应继续导航到右侧最接近的列。 导航应在行的结尾处停止。  
  
-   **选项卡：**到最接近的单元格右侧的导航。  在行的末尾，导航继续到下一行。  
  
-   **按 shift + Tab:**到最接近的单元格左侧的导航。  在行的开头，导航到前一行中的最右边的单元格将继续。  
  
![Visual Studio 中的 trid 控件](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705 6_Trid")<br />Visual Studio 中的 trid 控件