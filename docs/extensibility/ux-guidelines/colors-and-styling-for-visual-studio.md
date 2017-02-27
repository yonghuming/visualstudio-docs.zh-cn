---
title: "颜色和样式对 Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# 颜色和样式对 Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

## 使用 Visual Studio 中的颜色  
 在 Visual Studio 中，颜色是主要用作一种通信工具，而不仅仅是作为修饰。 按最小方式使用的颜色和保留的情况下，您希望对:  
  
-   含义或隶属关系 \(例如，平台或语言修饰符\) 通信  
  
-   吸引注意力 \(例如，指示状态更改\)  
  
-   提高可读性，并为导航用户界面提供界标  
  
-   提高性能  
  
 存在多个选项将颜色分配给在 Visual Studio 中的用户界面元素。 有时可能很难进行图的选项，您就应该使用，或如何正确使用。 本主题将帮助您:  
  
1.  了解不同的服务和系统用于在 Visual Studio 中定义的颜色。  
  
2.  选择正确的给定元素的选项。  
  
3.  正确地使用您选择的选项。  
  
 **重要提示:** 永远不会进行硬编码十六进制、 RGB 或到 UI 元素的系统颜色。 使用本服务允许在优化色调的灵活性。 此外，没有服务，您将不能充分利用的主题交换功能 [VSColor 服务](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)。  
  
### 用于向 Visual Studio 界面元素分配颜色的方法  
 选择最适合于您的用户界面元素的方法。  
  
|您的 UI|方法|它们是什么?|  
|-----------|--------|------------|  
|有嵌入或独立的对话框。|**系统颜色**|系统允许操作系统定义的颜色和外观的 UI 元素，如通用对话框控件的名称。|  
|您有自定义你想要与整体的 VS 环境保持一致的用户界面，具有匹配的类别和语义含义的共享令牌的用户界面元素。|**常用共享的颜色**|已有的预定义的颜色的特定 UI 元素的标记名称|  
|具有一个单独的功能组并且没有类似的元素没有共享的颜色。|**自定义颜色**|颜色令牌名称是特定于区域，不应将与其他 UI，共享|  
|你想要允许最终用户以进行自定义用户界面或内容 \(例如，文本编辑器或专用设计器窗口\)。|**最终用户自定义**<br /><br /> **\(工具 \> 选项对话框\)**|定义的"字体和颜色"页中设置 **工具 \> 选项** 对话框或特定于一个用户界面功能的专用的页面。|  
|您必须在 HTML 中编写的用户界面。|**Daytona**|允许用户界面用来访问该颜色和字体的服务的 HTML 编写的。|  
  
### Visual Studio 主题  
 Visual Studio 提供了三种不同的颜色主题: 光源、 暗、 和蓝色。 此外可以检测出高对比度模式，这是可访问性为设计整个系统的颜色主题。  
  
 用户会提示您在其首次使用 Visual Studio 的过程中选择一个主题，并能够通过转到更高版本切换主题 **工具 \> 选项 \> 环境 \> 常规** ，然后从"颜色主题"下拉菜单中选择新的主题。  
  
 用户还可以使用控制面板其整个系统切换到多个高对比度主题之一。 如果用户选择一个高对比度主题，然后 Visual Studio 的颜色主题选择器不会再影响到颜色在 Visual Studio 中，虽然主题中的任何更改都保存，以便在用户退出高对比度模式。 高对比度模式的详细信息，请参阅 [选择高对比度颜色](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors)。  
  
### VSColor 服务  
 Visual Studio 提供了称为 VSColor 服务，以便您可以将 UI 元素的颜色值绑定到包含每个 Visual Studio 主题的颜色值的已命名项的环境颜色服务。 这可确保您的颜色将自动更改，以反映当前用户所选主题或系统高对比度模式。 此服务的使用意味着在一个位置，处理所有与主题相关的颜色更改的实现，如果使用的从服务的常用共享的颜色，UI 会自动反映在 Visual Studio 的未来版本中的新主题。  
  
### 实现  
 Visual Studio 源代码包括多个包定义文件，包含令牌的名称和每个主题的相应的颜色值的列表。 颜色服务读取 VSColors 在这些包定义文件中定义。 这些颜色是在 XAML 标记中或在代码中引用，然后通过加载 **IVsUIShell5.GetThemedColor** 方法或 DynamicResource 映射。  
  
### 系统颜色  
 公共控件引用默认系统颜色。 如果您希望您的 UI 使用系统颜色，如当您创建未嵌入或作为独立的对话框，您不需要执行任何操作。  
  
### VSColor 服务中的常用共享的颜色  
 界面元素应反映整体的 Visual Studio 环境。 通过重新使用适合于您正在设计的用户界面组件的公共共享的颜色，可以确保您的界面与其他 Visual Studio 接口，一致，并且，当您的颜色主题是添加或更新时，将自动更新。  
  
 在使用之前常用共享的颜色，请确保您了解如何正确使用它们。 常用共享颜色的使用不当可能会导致不一致的、 令人沮丧的或混乱的用户体验。  
  
### 用户可自定义颜色  
 请参阅: [为最终用户公开颜色](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)  
  
 有时，想要允许最终用户若要自定义 UI，例如在创建代码编辑器中或设计图面。 可自定义 UI 组件都位于 **字体和颜色** 部分 **工具 \> 选项** 对话框中，用户可以选择要更改的前景色和 \/ 或背景色。  
  
 ![Tools &#62; Options dialog in Visual Studio](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301\-a\_ToolsOptionsDialog")  
  
 **工具 \> 选项对话框**  
  
### Web UI 颜色  
 它变得越来越普遍适用于使用 HTML，以便可以在 Visual Studio Online 和 Visual Studio 中使用它们的创作用户界面组件。 Visual Studio 环境内运行时，UI 用 HTML 编写仍须使用 VSColor 服务。 有关 Daytona 以及如何使用它的信息，请参阅 [Daytona 和 web 用户界面](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_DaytonaAndWebUI)。  
  
##  <a name="BKMK_TheVSColorService"></a> VSColor 服务  
 Visual Studio 提供了一种环境颜色服务，也称为 VSColor 服务或命令行程序颜色服务。 此服务允许您将 UI 元素的颜色值绑定到名称值的颜色集，其中包含每个主题颜色。 必须为所有 UI 元素，使用 VSColor 服务，以便颜色自动发生更改以反映当前用户所选主题设置，并以使 UI 绑定到的环境颜色服务将与集成新的主题在将来版本的 Visual Studio。  
  
### 服务的工作方式  
 环境颜色服务读取 VSColors UI 组件.pkgdef 中定义。 这些 VSColors 然后在 XAML 标记或代码中引用并将其加载通过 **IVsUIShell5.GetThemedColor** 或 DynamicResource 映射。  
  
 ![Environment color service architecture](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302\-a\_EnvironmentColorServiceArchitecture")  
  
 **环境颜色服务体系结构**  
  
### 访问服务  
 有多种不同的方式访问使用 VSColor 服务，具体取决于哪种颜色标记您和您具有哪种代码。  
  
#### 预定义的环境颜色  
  
##### 从本机代码  
 外壳中提供的颜色的 COLORREF 使访问的服务。 服务接口是:  
  
```  
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)  
```  
  
 文件 VSShell80.idl，枚举中 **\_\_VSSYSCOLOREX** 具有 shell 颜色常数。 若要使用它，请在作为索引值记录在 MSDN 枚举 \_\_VSSYSCOLOREX 中的值之一，或将常规索引号 Windows 系统 API，传递 **GetSysColor**, ，接受。 执行此操作将获取应在第二个参数中使用的颜色的 RGB 值。  
  
 如果存储钢笔或画笔用新的颜色，必须 AdviseBroadcastMessages \(从 Visual Studio shell\)，并侦听 WM\_SYSCOLORCHANGE 和 WM\_THEMECHANGED 消息。  
  
```  
// To access the color service in native code, you'll make a call that resembles this: pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);  
  
```  
  
 **注意:** 返回 COLORREF 值 **GetVSSysColorEx\(\)** 包含只是 R、 G、 B 组件的主题颜色。 如果主题条目使用透明胶片，阿尔法通道值将被丢弃之前返回。 因此，如果感兴趣的环境颜色需要使用在透明度通道是重要的地方，建议您使用 IVsUIShell5.GetThemedColor 而不是 IVsUIShell2::GetVSSysColorEx，如本主题后面所述。  
  
##### 从托管代码  
 通过本机代码访问 VSColor 服务其实非常简单。 如果您正在调试托管代码，但是，如何确定并使用该服务可能比较棘手。 这一点，下面是 C\# 代码段演示此过程:  
  
```  
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e) { //getIVSUIShell2 IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2; Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2"); if (uiShell2 != null) { //get the COLORREF structure uint win32Color; uiShell.GetVSSysColorEx(VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color); //translate it to a managed Color structure Color myColor = ColorTranslator.FromWin32((int)win32Color); //use it e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100); } }  
```  
  
 如果您正在 Visual Basic 中，使用:  
  
```  
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)  
```  
  
##### 从 WPF UI  
 您可以绑定到 Visual Studio 通过导出到应用程序的 ResourceDictionary 的值的颜色。 下面是举例说明如何使用颜色表中的资源，以及绑定到 XAML 中的环境字体数据。  
  
```  
<Style TargetType="{x:Type Button}"> <Setter Property="TextBlock.FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" /> <Setter Property="TextBlock.FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" /> <Setter Property="Background" Value="{DynamicResource VsBrush.EnvironmentBackgroundGradient}" /> </Style>  
```  
  
#### 助手类和托管代码的方法  
 对于托管代码，shell 的管理包框架库 \(Microsoft.VisualStudio.Shell.12.0.dll\) 包含几个帮助器类促进使用主题颜色。  
  
 中的帮助器方法 **Microsoft.VisualStudio.Shell.VsColors** 多功能进纸器中的类包括 **GetThemedGDIColor\(\)** 和 **GetThemedWPFColor\(\)**。 这些帮助器方法返回主题项作为 System.Drawing.Color 或 System.Windows.Media.Color，WinForms 或 WPF 用户界面中使用的颜色值。  
  
```  
IVsUIShell5 shell5; Button button = new Button(); button.BackColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemBrushKey); button.ForeColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemTextBrushKey); /// <summary> /// Gets a System.Drawing.Color value from the current theme for the given color key. /// </summary> /// <param name="vsUIShell">The IVsUIShell5 service, used to get the color's value.</param> /// <param name="themeResourceKey">The key to find the color for.</param> /// <returns>The current theme's value of the named color.</returns> public static System.Drawing.Color GetThemedGDIColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey) { Validate.IsNotNull(vsUIShell, "vsUIShell"); Validate.IsNotNull(themeResourceKey, "themeResourceKey"); byte[] colorComponents = GetThemedColorRgba(vsUIShell, themeResourceKey); // Note: The Win32 color we get back from IVsUIShell5.GetThemedColor is ABGR return System.Drawing.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]); } private static byte[] GetThemedColorRgba(IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey) { Guid category = themeResourceKey.Category; __THEMEDCOLORTYPE colorType = __THEMEDCOLORTYPE.TCT_Foreground if (themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundColor || themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundBrush) { colorType = __THEMEDCOLORTYPE.TCT_Background; } // This call will throw an exception if the color is not found uint rgbaColor = vsUIShell.GetThemedColor(ref category, themeResourceKey.Name, (uint)colorType); return BitConverter.GetBytes(rgbaColor); } public static System.Windows.Media.Color GetThemedWPFColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey) { Validate.IsNotNull(vsUIShell, "vsUIShell"); Validate.IsNotNull(themeResourceKey, "themeResourceKey"); byte[] colorComponents = GetThemedColorComponents(vsUIShell, themeResourceKey); return System.Windows.Media.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]); }  
  
```  
  
 此外可以使用类以获得给定的 WPF 颜色资源键，VSCOLOR 标识符，反之亦然。  
  
```  
public static string GetColorBaseKey(int vsSysColor); public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);  
```  
  
 方法 **VsColors** 类查询 VSColor 服务以返回每次调用它们的颜色值。 若要获取颜色值是 **System.Drawing.Color**, ，性能更好的替代方法是以转而使用的方法 **Microsoft.VisualStudio.PlatformUI.VSThemeColor** 类，该类将缓存从 VSColor 服务中获取的颜色值。 此类订阅内部 shell 广播的消息事件并发生主题更改事件时将放弃缓存的值。 此外，该类提供。要订阅的主题发生更改的 NET 友好事件。 使用 **ThemeChanged** 事件来添加新的处理程序，并使用 **GetThemedColor\(\)** 方法来获取颜色值 **ThemeResourceKeys** 感兴趣。 示例代码可能如下所示:  
  
```  
public MyWindowPanel() { InitializeComponent(); // Subscribe to theme changes events so we can refresh the colors VSColorTheme.ThemeChanged += VSColorTheme_ThemeChanged; RefreshColors(); } private void VSColorTheme_ThemeChanged(ThemeChangedEventArgs e) { RefreshColors(); // Also post a message to all the children so they can apply the current theme appropriately foreach (System.Windows.Forms.Control child in this.Controls) { NativeMethods.SendMessage(child.Handle, e.Message, IntPtr.Zero, IntPtr.Zero); } } private void RefreshColors() { this.BackColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowBackgroundColorKey); this.ForeColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowTextColorKey); } protected override void Dispose(bool disposing) { if (disposing) { VSColorTheme.ThemeChanged -= this.VSColorTheme_ThemeChanged; base.Dispose(disposing);} }  
```  
  
##  <a name="BKMK_ChoosingHighContrastColors"></a> 选择高对比度颜色  
  
### 概述  
 Windows 使用几个提高文本、 背景和图像的色彩对比度的高对比度系统级别主题使元素显示在屏幕上更为明显。 出于可访问性原因，很重要，Visual Studio 界面元素时正确响应用户切换到高对比度主题。  
  
 只有较少量的系统颜色可以用于高对比度主题。 在选择您的系统颜色名称时，请记住以下提示:  
  
1.  **选择具有相同的语义含义的系统颜色** 为您更改颜色的元素。 例如，如果选择的时间段内的文本的高对比度颜色时，使用 WindowText 和不 ControlText。  
  
2.  **选择前景\/背景对** 在一起或不会相信您的颜色选择将在所有的高对比度主题中工作。  
  
3.  **确定您的 UI 的哪些部分是最重要，并确保内容区域将脱颖而出。**您将丢失大量的详细信息，通常会区分颜色色调细微的差异，因此强边框颜色的使用是常见的定义的内容区域，因为出现了不同的内容区域没有颜色变体。  
  
### 系统颜色集  
 在表 [WPF 团队博客: SystemColors 引用](http://blogs.msdn.com/b/wpf/archive/2010/11/30/systemcolors-reference.aspx) 指示组完整的系统颜色名称和相应的色调显示在每个主题。  
  
 如果将应用此限制的一组颜色到你的 UI， *预期，将会丢失的"正常"主题中已存在的细节*。 下面是用户界面的示例，用于区分工具窗口内的相应区域的细微灰颜色。 在配合时使用高对比度模式中显示的同一窗口，您可以看到，所有背景都是相同的色调，由单独的边框指示的那些区域的边框:  
  
 ![Properties window](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303\-a\_PropertiesWindow")  
  
 **如何细微的详细信息的示例都将丢失在高对比度**  
  
#### 在编辑器中选择文本颜色  
 在编辑器中或设计图面上使用彩色的文本，以指示含义，如允许更容易地识别相似项的组。 高对比度主题中，但是，您没有能够区分这两个以上三种文本颜色。 WindowText、 GrayText 和 HotTrackText 是 WindowBackground 曲面上可用的唯一颜色。 因为不能使用三个以上的颜色，请仔细选择你想要在高对比度模式中显示的最重要差异。  
  
 对于每个令牌的名称在每个高对比度主题中的显示在编辑器表面上允许的色调:  
  
 ![High Contrast editor comparison](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303\-b\_HCEditorComparison")  
  
 **高对比度编辑器比较**  
  
 编辑器表面蓝色主题中的示例:  
  
 ![Editor in Blue theme](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303\-c\_EditorBlue")  
  
 **蓝色主题中的编辑器**  
  
 ![Editor in High Contrast theme](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303\-d\_EditorHC1")  
  
 **高对比度 \#1 主题中的编辑器**  
  
### 使用模式  
 许多常用的 UI 元素已定义的高对比度颜色。 您可以引用这些使用情况模式选择您自己的系统颜色名称时，以使 UI 元素与类似的组件保持一致。  
  
|系统颜色|用法|  
|----------|--------|  
|ActiveCaption|-   活动的 IDE 和 rafted 的窗口按钮上悬停时，按标志符号<br />-   IDE 和 rafted 的窗口的标题栏背景<br />-   默认状态栏背景|  
|ActiveCaptionText|-   活动的 IDE 和 rafted 的窗口标题栏前台 \(文本和标志符号\)<br />-   背景和活动窗口上悬停和按下的按钮的边框|  
|控件|-   组合框、 下拉列表中和搜索控制默认和已禁用的背景信息，包括下拉按钮<br />-   停靠目标按钮背景<br />-   命令状态栏背景<br />-   工具窗口背景|  
|ControlDark|-   IDE 背景<br />-   菜单和命令栏分隔符<br />-   命令栏边框<br />-   菜单阴影<br />-   工具窗口选项卡上默认值并将其悬停边框和分隔符<br />-   文档也溢出按钮背景<br />-   停靠目标标志符号边框|  
|ControlDarkDark|-   失去焦点的、 所选的文档选项卡窗口|  
|ControlLight|-   自动隐藏选项卡边框<br />-   组合框和下拉列表边框<br />-   停靠目标背景和边框|  
|ControlLightLight|-   所选、 集中式临时边框|  
|ControlText|-   组合框和下拉列表中列出了标志符号<br />-   工具窗口中取消选择选项卡文本|  
|GrayText|-   组合框和下拉列表中禁用边框、 下拉列表中的标志符号、 文本和菜单项文本<br />-   禁用的菜单文本<br />-   搜索控件 ' 搜索选项标头文本<br />-   搜索控制部分分隔符|  
|突出显示|-   所有将鼠标指针悬停和按下的背景和边框，除组合框下拉按钮背景和文档也溢出按钮边框<br />-   选定的项的背景|  
|HighlightText|-   所有悬停和按下的前景色 \(文本和标志符号\)<br />-   为主的工具窗口和文档选项卡窗口控件的前景<br />-   为主的工具窗口标题栏边框<br />-   具有焦点，所选的临时选项卡前景色<br />-   文档也溢出按钮边框上悬停或按<br />-   选定的图标的边框|  
|HotTrack|-   滚动条滚动块背景和按下时的边框<br />-   在按下的滚动条箭头标志符号|  
|InactiveCaption|-   非活动状态的 IDE 和 rafted 的窗口按钮上悬停时的标志符号<br />-   IDE 和 rafted 的窗口的标题栏背景<br />-   已禁用的搜索控件背景|  
|InactiveCaptionText|-   非活动状态的 IDE 和 rafted 的窗口标题栏前台 \(文本和标志符号\)<br />-   活动窗口按钮背景和上悬停时的边框<br />-   失去焦点的工具窗口按钮背景和边框<br />-   已禁用的搜索控件的前景|  
|菜单|-   下拉列表菜单背景<br />-   Checked 和已禁用的复选标记背景|  
|MenuText|-   下拉列表菜单边框<br />-   选中标记检查<br />-   菜单上的标志符号<br />-   下拉列表菜单文本<br />-   选定的图标的边框|  
|滚动条|-   滚动条和滚动条箭头背景，所有状态|  
|窗口|-   自动隐藏选项卡背景<br />-   菜单栏和命令架背景<br />-   失去焦点或未选定的文档窗口选项卡的背景和文档边框，用于打开和临时选项卡<br />-   失去焦点的工具窗口标题栏背景<br />-   工具窗口选项卡的背景，同时选中和取消选中|  
|WindowFrame|-   IDE 边框|  
|WindowText|-   自动隐藏选项卡上的前景色<br />-   所选的工具窗口选项卡上的前景色<br />-   失去焦点的文档窗口选项卡上，将失去焦点或未选定的临时选项卡前景色<br />-   树视图默认前景色和将鼠标悬停在选定标志符号<br />-   工具窗口选定的选项卡边框<br />-   滚动条滚动块背景、 边框和标志符号|  
  
##  <a name="BKMK_ExposingColorsForEndUsers"></a> 为最终用户公开颜色  
  
### 概述  
 有时想要允许最终用户若要自定义 UI，例如在创建代码编辑器中或设计图面。 若要这样做的最常见方法是使用 **工具 \> 选项** 对话框。 除非您拥有高度专业化需要特殊的控件的 UI，呈现自定义项的最简单方式是通过 **字体和颜色** 页内 **环境** 对话框的一节。 对于公开为自定义每个元素，用户可以选择要更改的前景色和 \/ 或背景色。  
  
### 构建可自定义颜色的 VSPackage  
 VSPackage 可以控制的字体和通过自定义类别的颜色和字体和颜色属性页上显示的项。 当使用此机制，必须实现 Vspackage [IVsFontAndColorDefaultsProvider](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.aspx) 接口和其关联的接口。  
  
 从原理上讲，此机制可以用于修改所有现有的显示项和包含它们的类别。 但是，它不应修改文本编辑器类别或其显示项。 文本编辑器类别的详细信息，请参阅 [字体和颜色概述](https://msdn.microsoft.com/en-us/library/bb165065.aspx)。  
  
 若要实现自定义类别或显示项，VSPackage 必须:  
  
-   **创建或标识注册表中的类别。**IDE 的实现 **字体和颜色** 属性页使用此信息来正确地查询支持给定的类别中的服务。  
  
-   **创建或标识注册表 \(可选\) 中的组。**它可能会定义一个组，表示两个或多个类别的并集很有用。 如果定义一个组，则 IDE 将自动合并子类别，并分发显示该组中的项目。  
  
-   **实现 IDE 的支持。**  
  
-   **处理字体和颜色的更改。**  
  
#### 若要创建或标识类别  
 构造一个特殊类型的类别下 \[HKLM\\SOFTWARE\\Microsoft \\Visual Studio\\ \< Visual Studio 版本 \> \\FontAndColors\\ \< 类别 \>\] 的注册表项。 \< 类别 \> 是类别的非本地化名称。  
  
 填充注册表具有两个值:  
  
|名称|类型|数据|描述|  
|--------|--------|--------|--------|  
|类别|REG\_SZ|GUID|创建 GUID 来标识类别|  
|package|REG\_SZ|GUID|支持类别 VSPackage 服务的 GUID|  
  
 在注册表中指定的服务必须提供实现 [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) 为相应的类别。  
  
#### 若要创建或标识一组  
 构造一个特殊类型的类别下 \[HKLM\\SOFTWARE\\Microsoft \\Visual Studio\\ \< Visual Studio 版本 \> \\FontAndColors\\ \< 组 \>\] 的注册表项。 \< 组 \> 是组的非本地化名称。  
  
 填充注册表具有两个值:  
  
|名称|类型|数据|描述|  
|--------|--------|--------|--------|  
|类别|REG\_SZ|GUID|创建 GUID 来标识类别|  
|package|REG\_SZ|GUID|支持类别 VSPackage 服务的 GUID|  
  
 在注册表中指定的服务必须提供实现 **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** 为相应的组。  
  
 ![IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304\-a\_FontAndColorGroup")  
  
### 若要实现 IDE 支持  
 实现 [GetObject](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject.aspx), ，它返回 [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) 接口或 **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** 接口适用于每个类别的 IDE 或组提供的 GUID。  
  
 对于每个类别，它支持，VSPackage 实现的单独实例 [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) 接口。  
  
 通过实现方法 [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) 必须提供具有的 IDE:  
  
-   类别中的显示项的列表  
  
-   显示项的可本地化名称  
  
-   显示该类别的每个成员的信息  
  
 **注意:** 每个类别必须包含至少一个显示项。  
  
 IDE 将使用 **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** 接口来定义几个类别的并集。  
  
 其实现提供了 IDE:  
  
-   构成了一组给定的类别列表  
  
-   实例的访问 [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) 支持组内的每个类别  
  
-   可本地化的组名称  
  
#### 更新 IDE  
 IDE 将缓存有关字体和颜色设置的信息。 因此，任何修改后的 IDE 字体和颜色的配置，确保缓存最新的是一种最佳做法。  
  
 更新缓存通过 [IvsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) 接口，并在可执行全局或仅在所选的项。  
  
### 处理字体和颜色的更改  
 若要正确地支持 VSPackage 显示的文本的颜色设置，支持 VSPackage 的颜色设置服务必须响应通过字体和颜色属性页所做的用户启动的更改。  
  
 若要执行此操作，VSPackage 必须:  
  
-   **处理 IDE 生成的事件** 通过实现 [IVsFontAndColorEvents](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.aspx) 接口。 IDE 将调用相应方法后面的字体和颜色页上的用户修改。 例如，它调用 [OnFontChanged](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged.aspx) 如果选择新字体的方法。  
  
 **或**  
  
-   **轮询更改 IDE**。 这可以通过系统实现 [IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) 接口。 主要用于支持的持久性，尽管 [GetItem](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem.aspx) 方法可以获取字体和颜色显示项的信息。 字体和颜色设置的详细信息，请参阅 MSDN 文章 [访问存储的字体和颜色设置](https://msdn.microsoft.com/en-us/library/bb166382.aspx)。  
  
 **注意:** 若要确保轮询结果是否正确，请使用 [IVsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) 接口，以确定是否缓存刷新和更新之前调用的检索方法所需 [IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) 接口。  
  
#### 注册自定义字体和颜色类别，而无需实现接口  
 下面的代码示例演示如何注册自定义字体和颜色而无需实现接口的类别:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window] "Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}" "Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}" "ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}" "NameID"=dword:00000064  
```  
  
 **注意:**  
  
-   "NameID"\= 在包中的本地化的类别名称的资源 ID  
  
-   "ToolWindowPackage"\= 包 GUID  
  
-   "Category"\="{9FF46859\-A47E\-47bf\-8AC5\-EC3DBE69D1FE}"只是一个示例和实际值可以是由实现者提供一个新的 GUID。  
  
### 设置字体和颜色的属性类别 GUID  
 下面的代码示例演示如何设置类别的 Guid。  
  
```  
// m_pView is your IVsTextView IVsTextEditorPropertyCategoryContainer spPropCatContainer = (IVsTextEditorPropertyCategoryContainer)m_pView; if (spPropCatContainer != null) { IVsTextEditorPropertyContainer spPropContainer; Guid GUID_EditPropCategory_View_MasterSettings = new Guid("{D1756E7C-B7FD-49a8-B48E-87B14A55655A}"); hr = spPropCatContainer.GetPropertyCategory( ref GUID_EditPropCategory_View_MasterSettings, out spPropContainer); if(hr == 0) { hr = spPropContainer.SetProperty( VSEDITPROPID.VSEDITPROPID_ViewGeneral_FontCategory, catGUID); hr = spPropContainer.SetProperty( VSEDITPROPID.VSEDITPROPID_ViewGeneral_ColorCategory, catGUID); } }  
```  
  
##  <a name="BKMK_DaytonaAndWebUI"></a> Daytona 和 web 用户界面  
  
### 概述  
 "Daytona"是一套 Api、 工具和服务，使用户能够使用 HTML、 CSS 和 JavaScript，可在多种主机，如 Visual Studio 或 f12 键创建插件。 插件是可移植的组件，它们编写在 HTML、 CSS 和 JavaScript 和可选的特定于宿主的组件组成。 每个 Daytona 主机可以有其自己的 UI 约定，隐式或显式的插件必须符合才能显示其环境的本机集。 某些主机，如 Visual Studio 中，允许最终用户可以更改默认"主题"，以便在创作样式表时，宿主的可视方面不能成为静态目标。 这是一个棘手的开发人员构建可移植的插件。 本主题说明如何编写 web 用户界面在 Visual Studio 中正确地支持主题和高对比度的方式使用 Daytona 主机。  
  
### Daytona 主题机制  
 Daytona 运行时提供了一套抽象化 UI 约定的服务和主题功能的主机。 这些服务可确保插件自动符合 visual 根据的环境中托管的用户的期望。 此行为提供的三个主要功能:  
  
1.  运行时注入样式表 \(plugin.css\) 以透明方式将一组 CSS 规则应用于插件的用户界面并设置样式的 HTML 控件 \(例如，HTMLInputElement 和 HTMLButtonElement 一组默认的  
  
2.  一组主机提供可用于样式用户界面元素使用的是基于主题的而不是硬编码值的标记  
  
    1.  用于访问使用 CSS 这些令牌的声明性语法  
  
    2.  一个 API 用于以编程方式从 JavaScript 访问主题令牌  
  
3.  主题更改通知  
  
#### 运行时注入样式表  
 与主机来注入样式的 Daytona 运行时坐标自动表主题插件的标准用户界面元素。 这包括以下概念的样式:  
  
-   环境字体  
  
-   背景色  
  
-   超链接  
  
-   窗体控件 \(例如: \< 选择 \>，\< 输入 \>，\< 按钮 \>  
  
-   表  
  
-   标题  
  
-   滚动条  
  
 这意味着，如果您的 UI 完全由组成的标准 HTML UI 控件，则任何额外工作应需要能够正确响应主题发生更改并支持高对比度。  
  
#### 自定义用户界面  
 在几乎每个重要的情况下，的标准 HTML UI 控件将为不足，无法为某个插件提供完整的体验并必须引入自定义用户界面。 为了支持适当的字体选择和颜色的用法， **主题令牌** CSS 中以声明方式或通过下面所述的 JavaScript API 以强制方式应使用。 Daytona 运行库将负责更新在插件负载以及主题更改使用这些标记的样式表。  
  
##### 主题令牌  
 这两个标准和特定于宿主的主题令牌是可用的。 标准的令牌是主机注入并始终可用。 使用标准标记，只要有可能是更可取的方法。 保证标准标记都由所有 Daytona 主机，并使用它们使你的插件本质上是更易于移植。 尽管应添加唯一的新令牌，应删除任何可能的一套标准标记会发生变化。 如下所述的 Visual Studio 2013 版本:  
  
|标记名称|描述|  
|----------|--------|  
|插件背景色|该插件的默认背景色|  
|插件颜色|该插件的默认前景色|  
|插件 contextmenu 活动颜色|默认选择前景色的上下文菜单在它们不再活动 \(具有焦点\)|  
|插件 contextmenu 背景色|上下文菜单默认背景色|  
|插件 contextmenu 边框颜色|上下文菜单默认边框颜色|  
|插件 contextmenu 颜色|默认前景色的上下文菜单|  
|插件 contextmenu 悬停颜色|上下文菜单默认悬停背景色|  
|插件 contextmenu 的悬停时的文本颜色|默认悬停前景色的上下文菜单|  
|插件 contextmenu\-图标复选框|上下文菜单将默认复选框图标颜色|  
|插件 contextmenu\-非活动状态的文本颜色|默认选择前景色的非活动状态时的上下文菜单|  
|插件 contextmenu 分隔符颜色|上下文菜单的的默认分隔符颜色|  
|插件字体系列|默认字体系列要用于该插件|  
  
 在 Visual Studio 中，以下插件字体令牌基于环境字体设置:  
  
-   插件字体大小  
  
-   插件字体粗细  
  
-   插件突出显示的背景色  
  
-   插件突出显示颜色  
  
-   插件处于非活动状态颜色  
  
 以下插件链接令牌用于样式 HTMLElements \(的超链接\):  
  
-   插件链接颜色  
  
-   插件链接活动颜色  
  
-   插件链接悬停颜色  
  
 Plugin.css 样式滚动条默认情况下使用更好地支持以下令牌 \(尤其是，Visual Studio\) 的各个主机中的主题:  
  
-   插件滚动条箭头颜色  
  
-   插件滚动条的背景色  
  
-   插件滚动条表面颜色  
  
 以下插件选择令牌用于样式 HTMLSelectElement \(组合框下拉列表\):  
  
-   插件的选择的选项的背景色  
  
-   插件选择选项颜色  
  
-   plugin\-select\-option\-checked\-background\-color  
  
-   plugin\-select\-option\-checked\-border\-color  
  
-   plugin\-select\-option\-checked\-foreground\-color  
  
-   plugin\-select\-option\-hover\-background\-color  
  
-   plugin\-select\-option\-hover\-border\-color  
  
-   plugin\-select\-option\-hover\-foreground\-color  
  
-   插件选择边框颜色  
  
-   插件选择背景色  
  
-   插件选择的前景颜色  
  
-   插件的选择的悬停时的背景色  
  
-   插件的选择的悬停时的边框颜色  
  
-   插件的选择的悬停时的前景色  
  
-   插件表边框颜色  
  
-   插件\-表\-标头的背景色  
  
-   插件表标题颜色  
  
-   插件文本框边框颜色  
  
-   插件文本框的背景色  
  
-   文本框中的插件颜色  
  
-   插件的文本框中的已禁用的背景色  
  
-   插件的文本框中的已禁用的边框颜色  
  
-   插件文本框中已禁用颜色  
  
 这些标记应该用于 *所有* 树视图和表，因为它们具有正确设置在各个主机，以便支持的主题和高对比度的默认设置:  
  
-   插件的树视图的内容的背景色  
  
-   插件 treeview 内容颜色  
  
-   plugin\-treeview\-content\-inactive\-selected\-color  
  
-   plugin\-treeview\-content\-mouseover\-background\-color  
  
-   插件的树视图的内容的鼠标悬停的颜色  
  
-   plugin\-treeview\-content\-inactive\-selected\-color  
  
-   plugin\-treeview\-content\-selected\-background\-color  
  
-   plugin\-treeview\-content\-selected\-border\-color  
  
-   插件的树视图的内容\-选择的颜色  
  
##### 特定于宿主的令牌  
 除了支持令牌的标准集，主机还可以提供非标准的令牌。 Visual Studio 主机会通过允许插件在清单的 Visual Studio 特定部分中指定主题令牌别名。 例如:  
  
```  
"vs": { "theme_token_aliases": { "diagnostics-host-border": { "category": "f8a8b2a5-dd35-43f6-a382-fd6a61325c22", "key_type": "BackgroundColor", "name": "Border" }, ... } }  
  
```  
  
 此示例中引入了一个主题令牌，名为"诊断\-主机的边框，"可以以相同的方式被引用到上述标准标记。 使用类别、 key\_type 和名称解析通过颜色 **IVsFontAndColorStorage** 接口。 在许多情况下，就可以在位于 vscommon\\themes 中的 XML 文件中查找适当的颜色 \(以及类别、 key\_type 和名称信息\)。 如果您的包引入了新的可配置颜色，则使用此相同的机制: 类别、 key\_type 和为想要使用的颜色的名称匹配。 插件作者应尝试使用尽可能的标准标记，并仅使用特定于宿主的令牌在绝对必要时。  
  
##### 在 CSS 中使用主题令牌  
 通过格式经过特别设计的注释语法称为主题令牌。 标记分析规则:  
  
1.  注释表达式必须括在方括号内 \(**\[\]**\)。  
  
2.  在注释内，但表达式中，外部的所有空白将被都忽略。  
  
3.  注释表达式直接必须遵循它将替换的属性。  
  
4.  在表达式中任何前导或尾随空格将进行修整。  
  
5.  在表达式中的每个令牌名称必须括在大括号内 \(例如， **{字体系列}** 和 **{按钮悬停颜色}**\)。 否则，它将作为一个文本值处理。  
  
 下面是示例的标记的分析器将如何替换 CSS 值，前提假设 **插件背景色** 令牌包含的值的 \#000 和 **插件字体系列** 令牌具有"Verdana。"的值  
  
|编写的 CSS|已分析的 CSS|备注|  
|-------------|--------------|--------|  
|`background-color: #fff; /*[{plugin-background-color}]*/`|`background-color: #000;`|默认值替换为动态的特定于宿主的值。|  
|`background-color: #fff; /*   [{plugin-background-color}]   */`|`background-color: #000;`|表达式外部的空白将被忽略。|  
|`background-color: #fff; /*[   {plugin-background-color}   ]*/`|`background-color: #000;`|在表达式中的尾部，前导空白进行修整。|  
|`background-color: #fff; /*{plugin-background-color}*/`|`background-color: #fff;`|表达式不括在方括号内，并因此忽略注释。|  
|`background-color: #fff; /*[plugin-background-color]*/`|`background-color: plugin-background-color;`|该令牌不括在大括号中且因此视为文字值。|  
|`/*[{plugin-background-color}]*/ background-color: #fff;`|`background-color: #fff;`|该注释不遵循该属性值，并因此将被忽略。|  
|`background-color: #fff; /*[{plugin-background-color}]*/`|`background-color: #fff;`|*与上面相同*|  
|`/*[{plugin-background-color}]*/ background-color: #fff;`|`background-color: #fff;`|*与上面相同*|  
|`font-family: Arial, sans-serif; /*[{plugin-font-family}, sans-serif]*/`|`font-family: Verdana, sans-serif;`|替换为令牌并维护文本内容。|  
|`background-image: linear-gradient(0% #000, 100% #ccc); /*[linear-gradient(0% #000, 100% {plugin-background-color})]*/`|`background-image: linear-gradient(0% #000, 100% #000);`|*与上面相同*|  
  
 如果一个 CSS 文件中包含主题的链接元素的 HTML 文件中的数据插件主题属性必须标记的令牌。 例如:  
  
```  
<link href="default.css" rel="stylesheet" data-plugin-theme="true" />  
```  
  
##### 使用 JavaScript 提供的主题令牌  
 尽管自定义 UI 应尽可能通过 CSS 主题，有一些方案时的主题值令牌需要以编程方式访问。 例如，如果不从 CSS，继承样式 CanvasElement 到当要绘制自定义用户界面或 UI 元素正在动态创建而不是引用样式表。 这些方案启用通过 Daytona API **Plugin.Theme.getValue**。 此函数返回在给定的标记名称的主机提供的主题值。  
  
|没有主题|应用了主题|  
|----------|-----------|  
|`var surface = document.getElementById("surface").getContext("2d"); surface.fillStyle = "#ccc"; surface.fillRect(0, 0, 200, 200);`|`var surface = document.getElementById("surface").getContext("2d"); surface.fillStyle = ("plugin-background-color"); surface.fillRect(0, 0, 200, 200);`|  
|`var el = document.createElement("div"); el.style.backgroundColor = "#ccc";`|`var el = document.createElement("div"); el.style.backgroundColor = Plugin.Theme.getValue("plugin-background-color");`|  
  
 如果从 JavaScript 使用令牌**, ，必须处理主题更改事件以响应更新**。 这是在 CSS 中以声明方式使用主题标记为不必要的因为 Daytona 运行时将对其负责为插件。 可以按以下方式处理主题事件:  
  
|成员 \(单个处理程序\)|DOM 事件 \(多个处理程序\)|  
|-------------------|-----------------------|  
|`Plugin.Theme.onchange = function () { // re-draw dynamic UI here }`|`Plugin.Theme.addEventListener("change", function () { // re-draw dynamic UI here });`|  
  
 在这种情况下，将会极为普遍重新调用 **Plugin.Theme.getValue** 中这些处理程序，当主题发生更改时，更改主题令牌可能的值。  
  
##### 标准的令牌映射  
 标准标记映射到的环境和 Shell 的颜色。 下面的列表提供了风格的这些映射。  
  
|标记名称|VS 映射 \(EnvironmentColors\)|  
|----------|---------------------------------|  
|插件颜色|ToolWindowTextColorKey|  
|插件背景色|ToolWindowBackgroundColorKey|  
|插件链接颜色|ControlLinkTextColorKey|  
|插件链接悬停颜色|ControlLinkTextHoverColorKey|  
|插件链接活动颜色|ControlLinkTextPressedColorKey|  
|插件突出显示颜色|HighlightTextColorKey|  
|插件突出显示的背景色|HighlightColorKey|  
|插件\-表\-标头的背景色|GridHeadingBackgroundColorKey|  
|插件表标题颜色|GridHeadingTextColorKey|  
|插件表边框颜色|GridLineColorKey|  
|插件按钮的背景色|ButtonFaceColorKey|  
|插件的按钮的悬停时的背景色|ButtonHighlightColorKey|  
|按钮的插件颜色|ButtonTextColorKey|  
|插件按钮的边框颜色|ButtonBorderColorKey|  
  
##### 主题更改  
 Visual Studio 主机触发器插件主题更改时最终用户将与以下设置做出更改:  
  
 **颜色主题:**  
  
 ![Color theme changes](../../extensibility/ux-guidelines/media/0305-a_colortheme.png "0305\-a\_ColorTheme")  
  
 **环境主题:**  
  
 ![Environment theme changes](../../extensibility/ux-guidelines/media/0305-b_environmenttheme.png "0305\-b\_EnvironmentTheme")  
  
 **操作系统主题** \(仅在将更改与高对比度\):  
  
 ![OS theme changes](../../extensibility/ux-guidelines/media/0305-c_ostheme.png "0305\-c\_OSTheme")