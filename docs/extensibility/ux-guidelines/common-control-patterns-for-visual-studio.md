---
title: "用于 Visual Studio 的常用控件模式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# 用于 Visual Studio 的常用控件模式
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

##  <a name="BKMK_CommonControls"></a> 公共控件  
  
### 概述  
 公共控件构成了 Visual Studio 中的用户界面的大部分。 在 Visual Studio 界面中使用的最常见控件应遵循 [Windows 桌面的交互准则](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx)。 本文档是特定于 Visual Studio，并介绍了特殊的情况下或扩充这些 Windows 准则的详细信息。  
  
#### 本主题中的公共控件  
  
-   [滚动条](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)  
  
-   [输入的字段](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)  
  
-   [组合框和下拉列表](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)  
  
-   [复选框](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)  
  
-   [单选按钮](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)  
  
-   [组帧](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)  
  
-   [文本控件](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
-   [按钮和超链接](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
-   [树视图](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)  
  
#### 视觉样式  
 首先要考虑样式控件时是否应用了主题 UI 中使用的控件。 标准用户界面中的控件是为主题的 UI，而且必须遵循 [正常的 Windows 桌面样式](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742399\(v=vs.85\).aspx), ，这意味着它们不是 re 模板化，应出现在它们的默认控件外观。  
  
-   **标准 \(实用工具\) 对话框:** 没有主题。 执行没有 re 模板。 使用基本的控件样式默认值。  
  
-   **工具窗口、 文档编辑器、 设计图面和主题的对话:** 使用专用主题外观，可以使用颜色服务。  
  
###  <a name="BKMK_Scrollbars"></a> 滚动条  
 滚动条应遵循 [Windows 滚动条的常见交互模式](https://msdn.microsoft.com/en-us/library/windows/desktop/bb787527\(v=vs.85\).aspx) 除非它们增加内容的信息，如在代码编辑器中。  
  
###  <a name="BKMK_InputFields"></a> 输入的字段  
 对于典型交互行为，请按照 [文本框中的 Windows 桌面准则](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742442\(v=vs.85\).aspx)。  
  
#### 视觉样式  
  
-   没有要输入的字段实用程序的对话框中设置样式。 使用内置于控件的基本样式。  
  
-   只应在应用了主题的对话框和工具窗口中主题的输入的字段。  
  
#### 专用的交互  
  
-   只读字段都但 \(活动\) 的默认前景色背景为灰色 \(禁用\)。  
  
-   所需字段应将 **\< 需要 \>** 作为其中要水印。 不应更改除中极少数情况下的背景的颜色。  
  
-   验证错误: 请参阅 [通知和 Visual Studio 的进度](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)  
  
-   输入的字段应将其调整为适合内容不适用于在其中会显示它们，窗口的宽度也任意长的字段中，如路径长度相匹配。 长度可能向用户指示的字段中允许的字符数限制。  
  
     ![Incorrect input field control width](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707\-01\_IncorrectInputFieldControl")   
     **不正确的输入的字段长度: 不太可能的名称将为这长。**  
  
     ![Correct input field control width](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707\-02\_CorrectInputFieldControl")   
     **更正输入的字段长度: 输入字段是合理的预期内容宽度。**  
  
###  <a name="BKMK_ComboBoxesAndDropDowns"></a> 组合框和下拉列表  
 对于典型交互行为，请按照 [下拉列表和组合框的 Windows 桌面准则](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742404\(v=vs.85\).aspx)。  
  
#### 视觉样式  
  
-   在实用程序对话框中，执行不 re 模板控件。 使用内置于控件的基本样式。  
  
-   在主题 UI、 组合框和下拉列表中，按照标准主题的控件。  
  
#### 布局  
 组合框和下拉列表应将其调整为适合内容不适用于在其中会显示它们，窗口的宽度也任意长的字段中，如路径长度相匹配。  
  
 ![Incorrect drop&#45;down layout](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707\-03\_IncorrectDropDownLayout")  
  
 **下拉列表控件的不正确的字段长度**  
  
 ![Correct drop&#45;down layout](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707\-04\_CorrectDropDownLayout")  
  
 **下拉列表控件的正确的字段长度**  
  
###  <a name="BKMK_CheckBoxes"></a> 复选框  
 对于典型交互行为，请按照 [复选框的 Windows 桌面准则](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742401\(v=vs.85\).aspx)。  
  
#### 视觉样式  
  
-   在实用程序对话框中，执行不 re 模板控件。 使用内置于控件的基本样式。  
  
-   在主题 UI 中的复选框按照标准主题的控件。  
  
#### 专用的交互  
  
-   有一个复选框的交互必须永远不会弹出一个对话框，或导航到另一个区域。  
  
-   使复选框与文本的第一行的基线对齐。  
  
     ![Incorrect check box alignment](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707\-05\_IncorrectCheckBoxAlign")   
     **不正确的复选框对齐方式: 文本上居中显示复选框。**  
  
     ![Correct check box alignment](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707\-06\_CorrectCheckBoxAlign")   
     **更正复选框对齐方式: 的第一行文本基线对齐复选框。**  
  
###  <a name="BKMK_RadioButtons"></a> 单选按钮  
 对于典型交互行为，请按照 [单选按钮的 Windows 桌面准则](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742436\(v=vs.85\).aspx)。  
  
#### 视觉样式  
 在实用程序对话框中，执行操作样式的单选按钮。 使用内置于控件的基本样式。  
  
#### 专用的交互  
 不需要使用一个组框括起单选选项。  
  
###  <a name="BKMK_GroupFrames"></a> 组帧  
 对于典型交互行为，请按照 [组帧的 Windows 桌面准则](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742405\(v=vs.85\).aspx)。  
  
#### 视觉样式  
 在实用程序对话框中，请执行不样式组帧。 使用内置于控件的基本样式。  
  
#### 布局  
  
-   不需要使用一个组框以便包含单选选项，除非您需要保持紧密布局中的一组区别。  
  
-   永远不会将一个组框用于单个控件。  
  
-   有时是可以接受而不是组帧容器使用水平标尺。  
  
##  <a name="BKMK_TextControls"></a> 文本控件  
  
### 标签  
  
#### 活动标签状态  
  
##### 实用程序 \(标准\) 对话框\)  
  
-   一般情况下，按照控件标签的 Windows 桌面指导。  
  
-   在实用程序对话框中，标签应显示非加粗，在标准环境字体和文本颜色。 请参阅 [字体和格式对 Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)。  
  
-   省略号应始终遵循标签。  
  
##### 签名 \(主题\) 对话框\)  
 Label 控件可能显示为粗体或浅灰色。  
  
#### 禁用的标签状态  
 标签应反映与之关联的控件的外观。 例如，如果禁用了关联的控件，然后标签应显示为灰色并已禁用。 这通常由操作系统处理，并且需要任何特殊处理。  
  
#### 动态标签  
 将根据当前所选内容动态标签发生变化。 只要有可能，使用母版\/详细信息为布局中动态标签来帮助用户了解所显示的信息是相关到特定的所选内容并不是一般的信息。  
  
 ![Dynamic label used with dynamic content](../../extensibility/ux-guidelines/media/070702-01_dynamiclabel.png "070702\-01\_DynamicLabel")  
  
 **与动态内容一起使用的动态标签示例**  
  
#### 说明文本  
 某些界面元素受益于以帮助用户了解 UI 目的或以指示应采取的操作的说明文本。  
  
-   说明文本顶部的对话框中，最常见的是，但可以出现在其他区域，以便为复杂控件分组的指令。  
  
-   说明文本非交互式的但可能包含指向帮助主题的超链接。  
  
-   使用说明性文本，并谨慎地仅在需要时。  
  
##### 格式化  
 说明文本应环境字体，标准 \(非主题\) 的控件文本。 请参阅 [字体和格式对 Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)。  
  
 有关编写说明文字的详细信息，请参阅 [UI text and terminology](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)。  
  
 ![Instructional text formatting](../../extensibility/ux-guidelines/media/070702-02_instructionaltextformatting.png "070702\-02\_InstructionalTextFormatting")  
  
 **Visual Studio 对话框中的说明文本**  
  
#### 信息性文本  
 信息性文本是为提供的用户的其他信息的文本。 它可以是静态或动态的或使用作为通知。 始终是只读的但如果它可用于使用者能够将信息复制，应动态文本置于如只读文本字段的控件容器。  
  
##### 动态 \(特定于上下文的\) 文本  
 动态信息文本根据上下文，如当用户将焦点切换会更改。 通常，但并非总是与动态标签配对动态内容。  
  
 ![Dynamic information text](../../extensibility/ux-guidelines/media/070702-03_informationaldynamictext.png "070702\-03\_InformationalDynamicText")  
  
 **动态信息文本更改取决于上下文。**  
  
##### 格式化  
 有两种方法来显示只读文本字段: 直接在 UI 上的任何一个图面 \(参阅上文\) 或包含在另一个控件，如组框架或文本框。 任何一个是正确的根据具体情况。 负责功能设计器，以确定如何显示只读信息。  
  
 文本可以是只读的文本框内。 这通常表示内容，可以选择并复制，尽管不能对其进行编辑。  
  
 ![Informational text formatting for read&#45;only fields](../../extensibility/ux-guidelines/media/070702-04_informationalformatting.png "070702\-04\_InformationalFormatting")  
  
 **只读字段的信息性文本格式设置**  
  
#### 水印  
 虽然用词可能相同，水印和说明性文本之间的区别是，水印会用替换内容时该控件\/窗口不为空，而且始终说明性文本保持可见。  
  
 窗口或控件为空时，应使用水印。 它们指示了什么都不用做以便填充区域，并可能包括操作链接以打开相关的窗口，例如作为拖动源。  
  
##### 视觉样式  
  
-   水印应在窗口中水平居中。  
  
-   水印应该居中对齐，不是左对齐。  
  
-   水印可能垂直居中或定位在区域的顶部附近。 如果位于顶部附近的区域，必须有足够的空间更高版本，以便突出显示水印。  
  
-   使用 `Environment.GrayText` 的令牌和标准环境字体颜色。 超链接应使用标准的超链接共享令牌: `Environment.PanelHyperlink`, ，`Environment.PanelHyperlinkHover`, ，`Environment.PanelHyperlinkPressed`, ，和 `Environment.PanelHyperlinkDisabled`。  
  
-   水印不能选择在背景上  
  
-   如果可能，包括链接中的水印，以帮助用户入门。  
  
 ![Watermark text in a designer window](../../extensibility/ux-guidelines/media/070702-05_watermark1.png "070702\-05\_Watermark1")  
  
 ![Watermark text in a tool window](../../extensibility/ux-guidelines/media/070702-06_watermark2.png "070702\-06\_Watermark2")  
  
 **在 Visual Studio 中的水印文本的示例**  
  
##  <a name="BKMK_ButtonsAndHyperlinks"></a> 按钮和超链接  
  
### 概述  
 按钮和链接控件 \(的超链接\) 应遵循 [超链接的基本 Windows 桌面指导](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742406\(v=vs.85\).aspx) 使用率、 措词、 调整以及间距。  
  
### 按钮和链接之间进行选择  
 过去，按钮已用于操作，并且已保留用于导航的超链接。 按钮可能会使用在所有情况下，但链接的角色扩展 Visual Studio 中，以便按钮和链接是更可互换的一些条件。  
  
 何时使用的命令按钮:  
  
-   主要命令  
  
-   显示用来收集输入的 windows 或做出的选择，即使它们是辅助命令  
  
-   破坏性的或不可逆的操作  
  
-   向导和页面流内的提交按钮  
  
 避免工具窗口中的命令按钮或如果标签需要两个以上的单词。 链接可以具有较长的标签。  
  
 何时使用链接:  
  
-   导航到另一个窗口、 文档或网页  
  
-   需要更长的标签或短句子来描述操作目的的情况  
  
-   其中一个按钮将严重影响用户界面，假设的操作不破坏性的或不可逆的紧密空格  
  
-   取消加重辅助命令的情况下，因为有许多命令  
  
#### 示例  
 ![Infobar command links following a status message](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703\-01\_CommandLinkInfobar")  
  
 **使用后跟状态消息的信息栏命令链接**  
  
 ![Links used in the CodeLens popup](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703\-02\_LinksInCodeLens")  
  
 **CodeLens 弹出中使用的链接**  
  
 ![Links used as secondary commands](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703\-03\_LinksAsSecondaryCommands")  
  
 **用于辅助命令按钮会吸引投入大量精力的位置的链接**  
  
### 常见按钮  
  
#### Text  
 请按照中的写入指导原则 [UI text and terminology](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)。  
  
#### 视觉样式  
  
##### 标准对话框  
 在 Visual Studio 中的大多数按钮将出现在标准对话框，并且不应设置样式。 所指示的操作系统，它们应反映按钮的标准外观。  
  
##### 应用了主题  
 在某些情况下，可能会在应用了样式的用户界面中使用按钮，这些按钮必须适当地设置样式。 请参阅 [对话框](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) 有关主题控件的信息。  
  
### 特殊按钮  
  
#### 浏览... 按钮  
 **\[浏览...\]** 按钮使用网格、 对话框和工具窗口以及其他无模式的用户界面元素。 它们将显示可以帮助用户在控件中填充值的选取器。 有两种变体此按钮，长和短。  
  
 ![Long &#91;Browse...&#93; button](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703\-04\_BrowseLong")  
  
 **长 \[浏览...\] 按钮**  
  
 ![Short ellipsis&#45;only &#91;Browse...&#93; button](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703\-05\_BrowseShort")  
  
 **短仅省略号 \[...\] 按钮**  
  
 何时使用仅省略号短按钮:  
  
-   如果有多个长 **\[浏览...\]** 在对话框中，如当多个字段可用来浏览按钮。 使用短期 **\[...\]** 按钮以删除以避免这种情况下所创建的令人困惑的访问密钥 \(**\(& a\) 浏览** 和 **B & 浏览** 在同一对话框中\)。  
  
-   在紧密的对话框中，或没有合理的地方安置长按钮时。  
  
-   如果该按钮将显示在网格控件。  
  
 使用按钮的准则:  
  
-   不要使用访问密钥。 若要访问它使用键盘，用户必须按 tab 键从相邻的控件。 确保 tab 键顺序，以便将填充的字段后立即处在任何浏览按钮。 永远不会使用下面的第一个期间下划线。  
  
-   设置 Microsoft Active Accessibility \(MSAA\) **名称** 属性设置为 **浏览 …** \(包括省略号\) 这样的屏幕读取器将读取它为"浏览"并不是"圆点点点"或"期间期期间。" 对于托管控件，这意味着设置 **AccessibleName** 属性。  
  
-   永远不会使用省略号 **\[...\]** 浏览操作之外的按钮。 例如，如果您需要 **\[新建...\]** 按钮，但没有足够的空间存放该文本，则需要进行重新设计，对话框。  
  
##### 大小调整和间距  
 ![Sizing &#91;Browse...&#93; buttons](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703\-06\_BrowseSizing")  
  
 **大小调整 \[浏览...\] 按钮**  
  
 ![Spacing &#91;Browse...&#93; buttons](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703\-07\_BrowseSpacing")  
  
 **间距 \[浏览...\] 按钮**  
  
#### 图形按钮  
 某些按钮应始终使用数据的图形图像，并且永远不会包含文本，为了节省空间和避免本地化问题。 这些通常用于字段选取器和其他可排序列表中。  
  
> [!NOTE]
>  用户必须对这些按钮 \(没有任何访问密钥\) 选项卡上，因此将它们放在合理的顺序。 将按钮的 name 属性映射到以使屏幕读取器正确解释此按钮的操作所需的操作。  
  
|||  
|-|-|  
|添加|![Graphical "Add" button](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703\-08\_ButtonAdd")|  
|删除|![Graphical "Remove" button](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703\-09\_ButtonRemove")|  
|全部添加|![Graphical "Add All" button](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703\-10\_ButtonAddAll")|  
|删除所有|![Graphical "Remove All" button](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703\-11\_ButtonRemoveAll")|  
|上移|![Graphical "Move Up" button](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703\-12\_ButtonMoveUp")|  
|下移|![Graphical "Move Down" button](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703\-13\_ButtonMoveDown")|  
|删除|![Graphical "Delete" button](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703\-14\_ButtonDelete")|  
  
##### 大小调整和间距  
 调整图形按钮为与的缩略版相同 **\[浏览...\]** 按钮 \(26 x 23 像素为单位\):  
  
 ![Button with and without transparent color showing](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703\-15\_GraphicalButtonSpacing")  
  
 **在使用和不使用透明颜色显示的按钮图形图像的外观**  
  
### 超链接  
 超链接非常适合于基于导航的操作，例如，打开帮助主题、 模式对话框或向导。 如果命令使用超链接，则它应始终对 UI 显示可见和明显的更改。 一般情况下，提交到的操作 \(如取消，保存和删除\) 的操作是更好地传达使用按钮。  
  
#### 写作风格  
 请按照 [用户界面文本的 Windows 桌面指南](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx)。 不要使用"了解更多关于，""告诉我更多关于，"或"获取帮助与此"分段。 相反，短语在回答的帮助内容的主要问题方面的帮助链接文本。 例如，"**如何将服务器添加到服务器资源管理器?**"  
  
#### 视觉样式  
  
-   应始终使用超链接 [VSColor 服务](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)。 如果超链接的样式设置不正确，它会闪烁的红色活动时或显示被访问后的另一种颜色。  
  
-   不包含在控件停留在线状态，除非的链接有一个完整的句子中的句子片段如水印的下划线。  
  
-   悬停时的情况下不应出现下划线。 相反，向用户链接处于活动状态的反馈是轻微颜色变化和相应的链接游标。  
  
##  <a name="BKMK_TreeViews"></a> 树视图  
  
### 概述  
 树视图提供了一种组织复杂方法中列出了父\-子组。 用户可以展开或折叠父组，以显示或隐藏底层的子项目。 在树视图中的每个项，可以选择要将提供更多操作。  
  
 本主题介绍可接受的使用、 正确设计和功能的树视图。  
  
#### 主题内容  
  
-   [视觉样式](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewVisualStyle)  
  
-   [交互](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewInteractions)  
  
###  <a name="BKMK_TreeViewVisualStyle"></a> 视觉样式  
  
#### 扩展器  
 使用 Windows 和 Visual Studio 的扩展器设计应符合树视图控件。 每个节点使用 expander 控件来显示或隐藏基础项。 使用扩展器控件的用户可能会遇到 Windows 和 Visual Studio 中的其他树视图提供一致性。  
  
 ![Correct tree view control](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705\-1\_TreeViewCorrect")  
  
 **使用 expander 控件的树视图节点的正确: 正确样式**  
  
 ![Incorrect tree view nodes](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705\-2\_TreeViewIncorrect1")  
  
 **错误: 不正确的样式的树视图节点**  
  
#### 选择  
 当在树视图中选择某节点时，突出显示应扩展到整个树视图控件的宽度。 这有助于用户清楚地标识所选的项。 选择颜色应反映当前的 Visual Studio 主题。  
  
 ![Correct tree view control](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705\-1\_TreeViewCorrect")  
  
 **正确: 突出显示所选节点的适合树视图控件的整个宽度。**  
  
 ![Incorrect tree view highlighting](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705\-3\_TreeViewIncorrect2")  
  
 **不正确: 突出显示所选节点的不符合树视图控件的整个的宽度。**  
  
#### 图标  
 如果他们帮助直观地识别项之间的差异，则只应在树视图控件中使用图标。 一般情况下，应仅在图标中的执行信息元素的类型进行区分的异类列表中使用的图标。 同构的列表中，使用图标可频繁地将其视为干扰因此应当避免。 在这种情况下 \(父\) 中的组图标可传达其中的项的类型。 如果该图标是动态的用于指示状态是此规则的例外。  
  
#### 滚动条  
 如果内容适合在树视图控件中，应始终隐藏滚动条。 它是可接受的滚动条可滚动的窗口中处于隐藏或半透明和显示在包含树视图窗口具有焦点，或在悬停时的树视图自身中。  
  
 ![Tree view with scroll bars](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705\-4\_Scrollbars")  
  
 **因为内容已经超出了树视图控件的限制，则会显示这两个垂直和水平滚动条。**  
  
###  <a name="BKMK_TreeViewInteractions"></a> 交互  
  
#### 上下文菜单  
 树视图节点可以显示在上下文菜单中的子菜单选项。 通常，用户已用鼠标右键单击某项或在选定的项与 Windows 键盘上按菜单键时出现此情况。 很重要的节点获得焦点和选择。 这可帮助用户识别为子菜单属于哪个项。  
  
 ![Selected tree node and context menu](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705\-5\_ContextMenu")  
  
 **尚未选择已生成以通知用户的上下文菜单提升焦点哪一项的项。**  
  
#### 键盘  
 树视图中应提供能够选择项，然后展开\/折叠节点上使用键盘。 这可以确保导航满足我们的可访问性要求。  
  
##### 树视图控件  
 Visual Studio 树控件应该遵循通用的键盘导航:  
  
-   **向上键:** 选择项目的树中向上移动  
  
-   **的向下箭头:** 树向下移动来选择项  
  
-   **向右箭头:** 展开树中的节点  
  
-   **向左箭头键:** 折叠树中的节点  
  
-   **Enter 键:** 启动，请加载、 执行选定的项  
  
##### Trid \(树视图和网格视图\)  
 Trid 控件是一个复杂的控件，它包含在网格中的树视图。 展开、 折叠，和导航树应遵守相同的键盘命令，以树视图，但增加了以下步骤:  
  
-   **向右箭头:** 展开节点。 展开该节点后，它应继续导航到右边最接近的列。 导航应在行末尾处停止。  
  
-   **选项卡:** 导航到右侧的最接近的单元格。  在行末尾，导航到下一行将继续。  
  
-   **Shift \+ 选项卡上:** 导航到左侧的最接近的单元格。  在行的开头，导航到前一行中最右边的单元格将继续。  
  
 ![Trid control in Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705\-6\_Trid")  
  
 **在 Visual Studio 中的 trid 控件**