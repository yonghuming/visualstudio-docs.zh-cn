---
title: "字体和格式设置为 Visual Studio |Microsoft 文档"
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
caps.latest.revision: 5
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9524ecc3cadef58821fba857de8e82e59eea9b43
ms.openlocfilehash: c55c135034f5b3b2dd09ccf94e22e56e8f04797e
ms.contentlocale: zh-cn
ms.lasthandoff: 05/04/2017

---
# <a name="fonts-and-formatting-for-visual-studio"></a>字体和 Visual Studio 的格式设置
##  <a name="BKMK_TheEnvironmentFont"></a>环境字体  
 必须针对自定义向用户公开 Visual Studio 中的所有字体。 这主要通过**字体和颜色**页面**工具 > 选项**对话框。 字体设置的三个主要类别包括︰  
  
-   **环境字体**-IDE （集成的开发环境），用于所有界面元素，包括对话框、 菜单、 工具窗口和文档窗口的主字体。 默认情况下，环境字体将关联到显示为 9 pt Segoe UI 在当前版本的 Windows 系统字体。 一种字体用于所有界面元素，可帮助确保整个 IDE 具有一致的字体的外观。  
  
-   **文本编辑器**— 在页上，在代码以及其他图面基于文本的编辑器可以自定义在文本编辑器中的元素**工具 > 选项**。  
  
-   **特定集合**-提供其接口元素的用户自定义可能会公开特定于它们的设计的字体的设计器窗口图面自己设置页中**工具 > 选项**。  
  
### <a name="editor-font-customization-and-resizing"></a>编辑器字体自定义和调整大小  
 用户通常将放大或缩放大小和/或根据其首选项，独立于常规用户界面编辑器中文本的颜色。 环境字体可能会出现在或自定义编辑器/设计器的一部分的元素上使用，因为它务必要注意的预期的行为，这些字体分类之一发生更改时。  
  
 在编辑器但不是属于中创建显示的 UI 元素时*内容*，务必使用环境字体和不将文本字体，这样可预测的方式调整元素的大小。  
  
1.  代码中的文本编辑器，与代码文本字体设置调整大小并响应编辑器文本的缩放级别。  
  
2.  接口的所有其他元素应绑定到环境字体设置，并对环境的任何全局更改做出响应。 这包括 （但不限于）︰  
  
    -   上下文菜单中的文本  
  
    -   中文编辑器修饰，像灯泡菜单文本，快速查找编辑器窗格中，并导航到窗格  
  
    -   标签文本在对话框中，如**在文件中查找**或**重构**  
  
### <a name="accessing-the-environment-font"></a>访问环境字体  
 在本机或 WinForms 代码中，可以通过调用方法访问环境字体`IUIHostLocale::GetDialogFont`后查询从接口`SID_SUIHostLocale`服务。  
  
 有关 Windows Presentation Foundation (WPF) 中，从 shell 的派生对话框窗口类`DialogWindow`类而不是 WPF 的`Window`类。  
  
 在 XAML 中，代码如下所示︰  
  
```  
<ui:DialogWindow  
    x:Class"MyNameSpace.MyWindow"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:s="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:ui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"  
    ShowInTaskbar="False"  
    WindowStartupLocation="CenterOwner"  
    Title="My Dialog">  
</ui:DialogWindow>  
  
code behind:  
  
internal partial class WebConfigModificationWindow : DialogWindow  
{  
}  
```  
  
 (替换`Microsoft.VisualStudio.Shell.11.0`MPF dll 的当前版本。)  
  
 若要显示的对话框，请调用"`ShowModal()`"通过类`ShowDialog()`。 `ShowModal()`在外壳程序中设置正确的模式状态，可以确保对话框能够位于父窗口中，依次类推。  
  
 代码如下所示:  
  
```  
MyWindow window = new MyWindow();  
window.ShowModal()  
```  
  
 `ShowModal`返回一个布尔值？ （可以为 null 的布尔值） 与`DialogResult`，如果需要可使用它。 返回值为 true，如果对话框中，已关闭**确定**。  
  
 如果你需要在自己显示一些 WPF UI，以不是一个对话框，并且承载`HwndSource`，如弹出窗口或 Win32/WinForms 父窗口窗口的 WPF 子窗口，你将需要设置`FontFamily`和`FontSize`的 WPF 元素的根元素上。 (命令行界面在主窗口中，设置的属性，但它们不继承过去`HWND`)。 Shell 提供的资源的属性可以绑定到，如下︰  
  
```  
<Setter property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />  
<Setter property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />  
```  
  
###  <a name="BKMK_Formatting"></a>格式设置 （缩放/粗） 引用  
 一些对话框需要要以粗体显示的特定文本或以外环境字体的大小。 以前，大于环境字体的字体编码为"`environment font +2`"或类似。 使用提供的代码片段将支持高 DPI 监视器，并确保显示文本始终出现在正确的大小和 （如 Light 或 Semilight） 权重。  
  
> **注意︰ 你应用格式设置之前，请确保你是遵循在中找到的指导原则[文本样式](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)。**  
  
 若要缩放环境字体，请设置的样式的 TextBlock 或所述的标签。 每个正确使用这些代码段将生成正确的字体，包括适当的大小和权重变体。  
  
 其中"`vsui`"是对命名空间的引用`Microsoft.VisualStudio.Shell`:  
  
```  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0" 
```  
  
#### <a name="375-environment-font--light"></a>375%环境字体 + Light  
 **显示为︰** 34 pt Segoe UI Light  
 **用于︰** （罕见） 唯一品牌 UI 中，如在启动页

 **过程代码︰**其中`textBlock`是以前定义的 TextBlock 和`label`是以前定义的标签︰  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);  
```  
  
 **XAML:**设置的 TextBlock 或标签的样式，如所示。  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>  
```  
  
#### <a name="310-environment-font--light"></a>310%环境字体 + Light  
 **显示为︰** 28 pt Segoe UI Light   
 **用于︰**大型签名对话框标题，主报表中标题  
  
 **过程代码︰**其中`textBlock`是以前定义的 TextBlock 和`label`是以前定义的标签︰  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);    
```  
  
 **XAML:**设置的 TextBlock 或标签的样式，如所示。  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>     
```  
  
#### <a name="200-environment-font--semilight"></a>200%环境字体 + Semilight  
 **显示为︰** 18 pt Segoe UI Semilight    
 **用于︰**副标题、 小型和中型对话框中的标题  
  
 **过程代码︰**其中`textBlock`是以前定义的 TextBlock 和`label`是以前定义的标签︰ 
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);    
```  
  
 **XAML:**设置的 TextBlock 或标签的样式，如所示︰  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>    
```  
  
#### <a name="155-environment-font"></a>155%环境字体  
 **显示为︰** 14 pt Segoe UI    
 **用于︰** UI 或报表，很好地在文档中的部分标题  
  
 **过程代码︰**其中`textBlock`是以前定义的 TextBlock 和`label`是以前定义的标签︰  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);    
```  
  
 **XAML:**设置的 TextBlock 或标签的样式，如所示︰  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>  
```  
  
#### <a name="133-environment-font"></a>133%环境字体  
 **显示为︰** 12 pt Segoe UI    
 **用于︰**签名对话框和文档中的较小副标题很好地 UI  
  
 **过程代码︰**其中`textBlock`是以前定义的 TextBlock 和`label`是以前定义的标签︰  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);    
```  
  
 **XAML:**设置的 TextBlock 或标签的样式，如所示︰  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>    
```  
  
#### <a name="122-environment-font"></a>122%环境字体  
 **显示为︰** 11 pt Segoe UI    
 **用于︰**部分签名对话框中的标题、 排名靠前的节点在树视图中，垂直选项卡导航  
  
 **过程代码︰**其中`textBlock`是以前定义的 TextBlock 和`label`是以前定义的标签︰  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);    
```  
  
 **XAML:**设置的 TextBlock 或标签的样式，如所示︰  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>    
```  
  
#### <a name="environment-font--bold"></a>环境字体 + 粗体  
 **显示为︰**粗体 9 pt Segoe UI    
 **用于︰**标签和小标题中签名对话框、 报表和文档井中 UI  
  
 **过程代码︰**其中`textBlock`是以前定义的 TextBlock 和`label`是以前定义的标签︰  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironmentBoldStyleKey);    
```  
  
 **XAML:**设置的 TextBlock 或标签的样式，如所示︰  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>    
```  
  
### <a name="localizable-styles"></a>可本地化的样式  
 在某些情况下，本地化人员将需要修改为不同的区域设置，如粗移除东亚语言的文本的字体样式。 若要使本地化的字体样式成为可能，这些样式必须是.resx 文件中。 若要实现此目的和仍编辑 Visual Studio 窗体设计器中的字体样式的最佳方法是在设计时显式设置字体样式。 尽管此创建一个完整 font 对象，而且可能似乎违背了父字体的继承，只有元素都属性用于设置的字体。  
  
 该解决方案旨在挂钩对话框窗体的`FontChanged`事件。 在`FontChanged`事件，审核所有控件，然后检查是否设置了其字体。 如果设置，请将其更改为基于窗体的字体和控件的上一个字体样式新字体。 此代码中的一个示例是︰  
  
```  
private void Form1_FontChanged(object sender, System.EventArgs e)  
{  
          SetFontStyles();  
}  
  
/// <summary>  
/// SetFontStyles - This function will iterate all controls on a page  
/// and recreate their font with the desired fontstyle.  
/// It should be called in the OnFontChanged handler (and also in the constructor  
/// in case the IUIService is not available so OnFontChange doesn't fire).  
/// This way, when the VS shell font is given to us the controls that have  
/// a different style for the font (bolded for example) will recreate their font  
/// and use the VS shell font but with a style variation (bolded ...).  
/// </summary>   
protected void SetFontStyles()  
{  
     SetFontStyles(this, this, this.Font);  
}  
  
protected static void SetFontStyles(Control topControl, Control parent, Font referenceFont)  
{  
     foreach(Control c in parent.Controls)  
     {  
          if (c.Controls != null && c.Controls.Count > 0) {  
               SetFontStyles(topControl, c, referenceFont);  
          }  
          if (c.Font != topControl.Font) {  
               c.Font = new Font(referenceFont, c.Font.Style);  
          }  
     }  
}  
```  
  
 使用此代码可保证，窗体的字体更新时，控件的字体将更新以及。 应该调用此方法还可从窗体的构造函数，因为对话框可能会失败，若要获取其实例`IUIService`和`FontChanged`将永远不会触发事件。 挂接`FontChanged`将允许以动态拾取新字体，即使对话框已打开的对话框。  
  
### <a name="testing-the-environment-font"></a>测试环境字体  
 若要确保你的 UI 使用环境字体，且会保留大小设置，请打开**工具 > 选项 > 环境 > 字体和颜色**，在下面选择"环境字体""显示其设置:"下拉列表菜单。  
  
 ![在工具的字体和颜色设置&gt;选项对话框](~/docs/extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201-a_OptionsFonts")<br />在工具的字体和颜色设置&gt;选项对话框
  
 设置为更非常不同于默认字体。 若要更加明显的 UI 不会更新，请选择带衬线 （例如"Times New Roman") 字体并设置非常大的大小。 然后测试你的 UI，以确保它遵循环境。 下面是一个示例使用许可证对话框︰  
  
 ![不遵从环境字体的 UI 文本的示例](~/docs/extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201-b_WrongFontDialog")<br />不遵从环境字体的 UI 文本的示例
  
 "用户信息"和"产品信息"不在此情况下，遵从字体。 在某些情况下，这可能是一个明确的设计选择，但它可以是 bug 的显式字体未指定为红线规范的一部分。  
  
 若要重置该字体，请单击"使用默认值"下**工具 > 选项 > 环境 > 字体和颜色**。  
  
##  <a name="BKMK_TextStyle"></a>文本样式  
 文本样式引用字体大小、 宽度和大小写。 实现指南，请参阅[环境字体](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)。  
  
### <a name="text-casing"></a>文本大小写  
  
#### <a name="all-caps"></a>全部大写  
 未为标题或 Visual Studio 中的标签使用全部大写。  
  
#### <a name="all-lowercase"></a>所有小写  
 不要使用全部采用小写形式的标题或 Visual Studio 中的标签。  
  
#### <a name="sentence-and-title-case"></a>句子和标题的用例  
 词首字母大写或句子大小写，具体取决于这种情况，应使用 Visual Studio 中的文本。  
  
|有关使用词首字母大写︰|使用句子大小写为︰|  
|-------------------------|----------------------------|  
|对话框标题|标签|  
|分组框|复选框|  
|菜单项|单选按钮|  
|上下文菜单项|列表框项|  
|按钮|状态栏|  
|表标签||  
|列标题||  
|工具提示||  
  
##### <a name="title-case"></a>词首字母大写  
 词首字母大写是一种样式在其中的大部分或全部短语内的单词的第一个字母都大写。 在 Visual Studio 中，词首字母大写用于多个项，包括︰  
  
-   **工具提示。** 示例:"预览选择的项"  
  
-   **列标题。** 示例:"系统响应"  
  
-   **菜单项。** 示例:"全部保存"  
  
 当使用词首字母大写，这些是何时以使其大写单词以及何时将其保留为小写的准则︰  
  
|大写|注释和示例|  
|---------------|---------------------------|  
|所有名词||  
|所有谓词|包括"Is"和其他形式的"要"|  
|所有副词|包括"不是"和"时"|  
|所有形容词|包括"This"和"，"|  
|所有代词|包括所有格"其"以及"它，"代词的缩写式"它"和谓词"是"|  
|第一个和最后一个单词，而不考虑词类||  
|介词属于谓词短语|"所有 Windows 正在关闭"或者"关闭系统"|  
|首字母缩写词的所有字母|HTML、 XML、 URL、 IDE、 RGB|  
|如果它是名词或专有形容词，或如果字具有相等的权重，第二个 word 中的组合词|交叉引用，预 Microsoft 软件，读/写访问权限，运行时|  
  
|小写|示例|  
|---------------|--------------|  
|如果它是另一个的词性或修改的第一个单词分词的组合词中的第二个单词|操作指南、 采用关闭|  
|文章，除非有标题中的第一个单词|a、 an、 the|  
|协调连词|并且，但，且未，或|  
|介词词的动词短语之外的四个或更少字母|到，到，作为为 out 的在最前面的|  
|"到"时在无穷短语中使用|"如何格式化硬盘磁盘"|  
  
##### <a name="sentence-case"></a>句子大小写  
 句子大小写是编写在只有第一个词的句子大小写，以及任何专有名词和代词的标准大小写方法"I"。 通常情况下，句子大小写是为全球客户若要读取，尤其是当内容将被转换一台计算机更容易。 使用句子大小写为︰  
  
1.  **状态栏消息。** 这些很简单，简单地说，并只提供状态信息。 示例:"加载项目文件"  
  
2.  **所有其他 UI 元素**，其中包括标签、 复选框、 单选按钮和列表框项。 示例:"所有项在列表中选择"  
  
### <a name="text-formatting"></a>文本格式  
 由控制在 Visual Studio 2013 中设置格式的默认文本[环境字体](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)。 此服务可帮助确保整个 IDE （集成的开发环境），具有一致的字体的外观，并且必须使用它来为你的用户保证一致的体验。  
  
 Visual Studio 字体服务使用的默认大小来自 Windows，而显示为 9 pt。  
  
 你可以应用到环境字体格式。 本主题介绍如何以及在何处使用样式。 有关实现信息，请参阅[环境字体](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)。  
  
#### <a name="bold-text"></a>显示为粗体文本  
 显示为粗体文本在 Visual Studio 中尽量少使用，并应为保留︰  
  
-   在向导中的问题标签  
  
-   指定活动项目在解决方案资源管理器  
  
-   重写属性工具窗口中的值  
  
-   Visual Basic 编辑器下拉列表中的某些事件  
  
-   服务器生成文档大纲的网页中的内容  
  
-   复杂的对话框或设计器 UI 中的部分标头  
  
#### <a name="italics"></a>斜体  
 Visual Studio 不使用粗体或斜体斜体文本。  
  
#### <a name="color"></a>颜色  
  
-   蓝色是保留的超链接 （导航和命令） 和永远不会用于方向。  
  
-   可以显示针对这些目的为更大的标题 （环境字体 x 155%或更高版本）︰  
  
    -   若要提供与 Visual Studio UI 的签名的视觉效果  
  
    -   若要调用的特定区域的关注  
  
    -   提供从标准暗灰色/黑色环境文本颜色的起伏  
  
-   在标题中的颜色应利用现有 Visual Studio 的品牌颜色，主要主要紫色 #FF68217A。  
  
-   在标题中使用颜色，你必须遵守[Windows 颜色准则](https://msdn.microsoft.com/en-us/library/dn742482.aspx)，包括对比度和其他可访问性注意事项。  
  
### <a name="font-size"></a>字体大小  
 Visual Studio UI 设计功能具有更多的空白空间较浅外观。 如果可能，具有已减少 chrome 和标题栏或将其删除。 尽管信息密度是 Visual Studio 中的要求，版式仍然是重要的是，主要侧重于更加开放的行距和变化的字体大小和权重。  
  
 下表包括设计详细信息和使用在 Visual Studio 中的显示字体的可视化示例。 一些显示字体变体具有的大小和权重，如 Semilight 或 Light，编码到它们的外观。  
  
 在找不到所有显示字体的实现代码段[格式设置 （缩放/粗） 引用](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting)。  
  
#### <a name="375-environment-font--light"></a>375%环境字体 + Light  
  
|||  
|-|-|  
|**用法︰**少见。 唯一经过品牌打造的 UI 仅。<br /><br /> **执行操作︰**<br /><br /> -使用句子大小写<br />-始终使用轻型<br /><br /> **不要：**<br /><br /> 使用 ui 以外签名如起始页的 UI<br />-粗体、 斜体或加粗斜体<br />-用于正文文本<br />-使用工具窗口中|**显示为︰** 34 pt Segoe UI Light<br /><br /> **Visual 示例︰**<br /><br /> *当前未使用。可能在启动页中使用。*|  
  
#### <a name="310-environment-font--light"></a>310%环境字体 + Light  
  
|||  
|-|-|  
|**用法︰**<br /><br /> 签名对话框中的更大标题<br />-主报表标题<br /><br /> **执行操作︰**<br /><br /> -使用句子大小写<br />-始终使用轻型<br /><br /> **不要：**<br /><br /> 使用 ui 以外签名如起始页的 UI<br />-粗体、 斜体或加粗斜体<br />-用于正文文本<br />-使用工具窗口中|**显示为︰** 28 pt Segoe UI Light<br /><br /> **Visual 示例︰**<br /><br /> ![310%环境字体 &#43; 的示例Light 标题](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|  
  
#### <a name="200-environment-font--semilight"></a>200%环境字体 + Semilight  
  
|||  
|-|-|  
|**用法︰**<br /><br /> -标题<br />的小型和中型对话框中标题<br /><br /> **执行操作︰**<br /><br /> -使用句子大小写<br />-始终使用 Semilight 权重<br /><br /> **不要：**<br /><br /> -粗体、 斜体或加粗斜体<br />-用于正文文本<br />-使用工具窗口中|**显示为︰** 18 pt Segoe UI Semillight<br /><br /> **Visual 示例︰**<br /><br /> ![200%环境字体 &#43; 的示例Semilight](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202-b_EF200")|  
  
#### <a name="155-environment-font"></a>155%环境字体  
  
|||  
|-|-|  
|**用法︰**<br /><br /> 在文档中的节标题很好地 UI<br />-报表<br /><br /> **执行︰**使用句子大小写<br /><br /> **不要：**<br /><br /> -粗体、 斜体或加粗斜体<br />-用于正文文本<br />-使用标准 Visual Studio 控件中<br />-使用工具窗口中|**显示为︰** 14 pt Segoe UI<br /><br /> **Visual 示例︰**<br /><br /> ![155%环境字体标题的示例](~/docs/extensibility/ux-guidelines/media/0202-c_ef155.png "0202-c_EF155")|  
  
#### <a name="133-environment-font"></a>133%环境字体  
  
|||  
|-|-|  
|**用法︰**<br /><br /> 的签名对话框中较小副标题<br />的在文档中较小副标题很好地 UI<br /><br /> **执行︰**使用句子大小写<br /><br /> **不要：**<br /><br /> -粗体、 斜体或加粗斜体<br />-用于正文文本<br />-使用标准 Visual Studio 控件中<br />-使用工具窗口中|**显示为︰** 12 pt Segoe UI<br /><br /> **Visual 示例︰**<br /><br /> ![133%环境字体标题的示例](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202-d_EF133")|  
  
#### <a name="122-environment-font"></a>122%环境字体  
  
|||  
|-|-|  
|**用法︰**<br /><br /> 签名对话框中的节标题<br />的在树视图中顶级节点<br />-垂直制表符导航<br /><br /> **执行︰**使用句子大小写<br /><br /> **不要：**<br /><br /> -粗体、 斜体或加粗斜体<br />-用于正文文本<br />-使用标准 Visual Studio 控件中<br />-使用工具窗口中|**显示为︰** 11 pt Segoe UI<br /><br /> **Visual 示例︰**<br /><br /> ![122%环境字体标题的示例](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202-e_EF122")|  
  
#### <a name="environment-font--bold"></a>环境字体 + 粗体  
  
|||  
|-|-|  
|**用法︰**<br /><br /> -标签和小标题签名对话框中<br />-标签和小标题在报表中<br />-标签和文档中的副标题 UI<br /><br /> **执行操作︰**<br /><br /> -使用句子大小写<br />-使用加粗的权重<br /><br /> **不要：**<br /><br /> -斜体或加粗斜体<br />-用于正文文本<br />-使用标准 Visual Studio 控件中<br />-使用工具窗口中|**显示为︰**粗体 9 pt Segoe UI<br /><br /> **Visual 示例︰**<br /><br /> ![环境字体 &#43; 的示例加粗的标题](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202-f_EFB")|  
  
#### <a name="environment-font"></a>环境字体  
  
|||  
|-|-|  
|**用法︰**所有其他文本<br /><br /> **执行︰**使用句子大小写<br /><br /> **不︰**斜体或加粗倾斜|**显示为︰** 9 pt Segoe UI<br /><br /> **Visual 示例︰**<br /><br /> ![环境字体的示例](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202-g_EF")|  
  
### <a name="padding-and-spacing"></a>边距和间距  
 标题需要为他们提供适当的重点周围的空间。 此空间各不相同，具体取决于点大小和哪些其他内容即将标题，如水平的规则或环境字体中的文本行。  
  
-   单独一个标题的理想填充应为 90%的资本字符高度空间。 例如，一个 28 pt Segoe UI Light 标题的 26 pt cap 高度和填充大约应 23 pt 或大约 31 的像素为单位。  
  
-   一个标题周围的最小空间应为 50%的资本字符高度。 一个标题伴随规则或其他紧密调整元素时，可能使用较少的空间。  
  
-   以粗体显示环境字体文本应遵循默认行高度间距和填充。  
  
## <a name="see-also"></a>另请参阅  
 [MSDN︰ 字体 (Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742483\(v=vs.85\).aspx)   
 [MSDN︰ 用户界面文本 (Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx)
