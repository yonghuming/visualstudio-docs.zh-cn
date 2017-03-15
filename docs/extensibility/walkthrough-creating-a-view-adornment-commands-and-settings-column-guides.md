---
title: "创建视图修饰、 命令和设置 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
caps.latest.revision: 7
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
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: f37f2f8243a49f4f85b0f4177f2f33a7a724f08b
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-creating-a-view-adornment-commands-and-settings-column-guides"></a>演练︰ 创建视图修饰、 命令和设置 （列指南）
您可以扩展 Visual Studio 文本/代码编辑器中使用的命令和查看效果。  本主题演示了如何开始使用一种常用的扩展功能，列参考线。  列参考线是以可视方式浅色文本编辑器的视图来帮助你管理你的代码与特定列的宽度上绘制的直线。  格式经过特别设计的代码可能很重要的示例包括在文档中，博客文章或 bug 报告。  
  
 在本演练中，你将︰  
  
-   创建一个 VSIX 项目  
  
-   添加编辑器视图修饰  
  
-   添加对保存和攀上设置 （其中绘图列参考线和它们的颜色） 的支持  
  
-   添加命令 （添加/删除列参考线，将其颜色设置）  
  
-   将在编辑菜单和文本文档上下文菜单上的命令  
  
-   添加对调用 Visual Studio 命令窗口中的命令的支持  
  
 您可以试用版列指南功能与此 Visual Studio 库[扩展](https://visualstudiogallery.msdn.microsoft.com/da227a0b-0e31-4a11-8f6b-3a149cf2e459?SRC=Home)。  
  
 **请注意**︰ 在本演练中你粘贴大量的代码生成的 visual studio 扩展模板的几个文件，但很快就本演练中将引用与其他扩展插件示例的 github 上已完成的解决方案。  完整的代码的略有不同，在于它具有真正的命令图标而不是使用 generictemplate 图标。  
  
## <a name="getting-started"></a>入门  
 启动 Visual Studio 2015 中，您并不安装 Visual Studio SDK 从下载中心获得。 它将包括作为 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="setting-up-the-solution"></a>设置该解决方案  
 首先将创建一个 VSIX 项目、 添加编辑器视图修饰，并将一个命令 （其中添加拥有该命令的 VSPackage）。  是的如下所示的基本体系结构︰  
  
-   必须创建一个文本视图创建侦听器`ColumnGuideAdornment`每个视图的对象。  此对象侦听有关视图的更改的事件或更改设置，根据需要更新或重新绘制列的指导。  
  
-   没有`GuidesSettingsManager`处理读取和写入操作从 Visual Studio 设置存储区。  设置管理器还具有用于更新支持的用户命令的设置的操作 （将列添加、 删除列、 更改颜色）。  
  
-   VSIP 包，如果您有用户命令是必需的但它是仅初始化命令实现对象的样板代码。  
  
-   没有`ColumnGuideCommands`.vsct 文件中声明对象，该实现语音命令，并挂接命令的命令处理程序对象。  
  
 **VSIX**。  使用**文件 |新增功能。。。** 若要创建一个项目的命令。  在左侧的导航窗格中选择在 C# 扩展性节点并选择**VSIX 项目**在右窗格中。  输入名称 ColumnGuides 并选择**确定**创建项目。  
  
 **查看修饰**。  在解决方案资源管理器中的项目节点，请按右指针按钮。  选择**添加 |新建项...** 若要添加的新视图修饰项的命令。  选择**扩展性 |编辑器**左的导航窗格中，然后选择**编辑器视区修饰**在右窗格中。  输入名称 ColumnGuideAdornment 作为项目名称，并选择**添加**以将其添加。  
  
 您可以看到这个项模板添加到项目 （以及引用等） 的两个文件︰ ColumnGuideAdornment.cs 和 ColumnGuideAdornmentTextViewCreationListener.cs。  这些模板只是在视图上绘制一个紫色矩形。  下面将更改数视图创建侦听器中的行，并替换 ColumnGuideAdornment.cs 的内容。  
  
 **命令**。  在解决方案资源管理器中的项目节点，请按右指针按钮。  选择**添加 |新建项...** 若要添加的新视图修饰项的命令。  选择**扩展性 |VSPackage**左的导航窗格中，然后选择**自定义命令**在右窗格中。  输入名称 ColumnGuideCommands 作为项目名称，并选择**添加**以将其添加。  除了了若干引用添加命令和包添加 ColumnGuideCommands.cs、 ColumnGuideCommandsPackage.cs 和 ColumnGuideCommandsPackage.vsct。  下面将替换第一个和最后一个文件来定义和实现命令的内容。  
  
## <a name="setting-up-the-text-view-creation-listener"></a>设置文本视图创建侦听器  
 在编辑器中打开 ColumnGuideAdornmentTextViewCreationListener.cs。  For Visual Studio 创建文本视图时，此代码将实现一个处理程序。  有一些控制何时该处理程序调用根据视图的特征的属性。  
  
 该代码还必须声明一个修饰层。  当编辑器更新视图时，视图获取修饰图层，并从中获取修饰元素。  您可以声明您相对于其他具有属性的层的顺序。  将以下行︰  
  
```c#  
[Order(After = PredefinedAdornmentLayers.Caret)]  
```  
  
 替换为以下两行︰  
  
```c#  
[Order(Before = PredefinedAdornmentLayers.Text)]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
```  
  
 替换的行是一组声明修饰层的属性中。   第一行您更改了列参考线的显示位置的唯一更改。  "之前"视图中的文本表示它们显示之后或文本下方绘制线条。  第二行声明列指南修饰都适用于适合您的文档中，概念的文本实体，但无法声明修饰，例如，仅可用于可编辑的文本。  中的详细信息[语言服务和编辑器扩展点](../extensibility/language-service-and-editor-extension-points.md)  
  
## <a name="implementing-the-settings-manager"></a>实现的设置管理器  
 GuidesSettingsManager.cs 的内容替换为下面的代码 （如下所述）︰  
  
```c#  
using Microsoft.VisualStudio.Settings;  
using Microsoft.VisualStudio.Shell;  
using Microsoft.VisualStudio.Shell.Settings;  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Windows.Media;  
  
namespace ColumnGuides  
{  
    internal static class GuidesSettingsManager  
    {  
        // Because my code is always called from the UI thred, this succeeds.  
        internal static SettingsManager VsManagedSettingsManager =  
            new ShellSettingsManager(ServiceProvider.GlobalProvider);  
  
        private const int _maxGuides = 5;  
        private const string _collectionSettingsName = "Text Editor";  
        private const string _settingName = "Guides";  
        // 1000 seems reasonable since primary scenario is long lines of code  
        private const int _maxColumn = 1000;   
  
        static internal bool AddGuideline(int column)  
        {  
            if (! IsValidColumn(column))  
                throw new ArgumentOutOfRangeException(  
                    "column",  
                    "The paramenter must be between 1 and " + _maxGuides.ToString());  
            var offsets = GuidesSettingsManager.GetColumnOffsets();  
            if (offsets.Count() >= _maxGuides)  
                return false;  
            // Check for duplicates  
            if (offsets.Contains(column))  
                return false;  
            offsets.Add(column);  
            WriteSettings(GuidesSettingsManager.GuidelinesColor, offsets);  
            return true;  
        }  
  
        static internal bool RemoveGuideline(int column)  
        {  
            if (!IsValidColumn(column))  
                throw new ArgumentOutOfRangeException(  
                    "column", "The paramenter must be between 1 and 10,000");  
            var columns = GuidesSettingsManager.GetColumnOffsets();  
            if (! columns.Remove(column))  
            {  
                // Not present.  Allow user to remove the last column   
                // even if they're not on the right column.  
                if (columns.Count != 1)  
                    return false;  
  
                columns.Clear();  
            }  
            WriteSettings(GuidesSettingsManager.GuidelinesColor, columns);  
            return true;  
        }  
  
        static internal bool CanAddGuideline(int column)  
        {  
            if (!IsValidColumn(column))  
                return false;  
            var offsets = GetColumnOffsets();  
            if (offsets.Count >= _maxGuides)  
                return false;  
            return ! offsets.Contains(column);  
        }  
  
        static internal bool CanRemoveGuideline(int column)  
        {  
            if (! IsValidColumn(column))  
                return false;  
            // Allow user to remove the last guideline regardless of the column.  
            // Okay to call count, we limit the number of guides.  
            var offsets = GuidesSettingsManager.GetColumnOffsets();  
            return offsets.Contains(column) || offsets.Count() == 1;  
        }  
  
        static internal void RemoveAllGuidelines()  
        {  
            WriteSettings(GuidesSettingsManager.GuidelinesColor, new int[0]);  
        }  
  
        private static bool IsValidColumn(int column)  
        {  
            // zero is allowed (per user request)  
            return 0 <= column && column <= _maxColumn;  
        }  
  
        // This has format "RGB(<int>, <int>, <int>) <int> <int>...".  
        // There can be any number of ints following the RGB part,   
        // and each int is a column (char offset into line) where to draw.  
        static private string _guidelinesConfiguration;  
        static private string GuidelinesConfiguration  
        {  
            get  
            {  
                if (_guidelinesConfiguration == null)  
                {  
                    _guidelinesConfiguration =   
                        GetUserSettingsString(  
                            GuidesSettingsManager._collectionSettingsName,  
                            GuidesSettingsManager._settingName)  
                        .Trim();  
                }  
                return _guidelinesConfiguration;  
            }  
  
            set  
            {  
                if (value != _guidelinesConfiguration)  
                {  
                    _guidelinesConfiguration = value;  
                    WriteUserSettingsString(  
                        GuidesSettingsManager._collectionSettingsName,  
                        GuidesSettingsManager._settingName, value);  
                    // Notify ColumnGuideAdornments to update adornments in views.  
                    var handler = GuidesSettingsManager.SettingsChanged;  
                    if (handler != null)  
                        handler();  
                }  
            }  
        }  
  
        internal static string GetUserSettingsString(string collection, string setting)  
        {  
            var store = GuidesSettingsManager  
                            .VsManagedSettingsManager  
                            .GetReadOnlySettingsStore(SettingsScope.UserSettings);  
            return store.GetString(collection, setting, "RGB(255,0,0) 80");  
        }  
  
        internal static void WriteUserSettingsString(string key, string propertyName,  
                                                     string value)  
        {  
            var store = GuidesSettingsManager  
                            .VsManagedSettingsManager  
                            .GetWritableSettingsStore(SettingsScope.UserSettings);  
            store.CreateCollection(key);  
            store.SetString(key, propertyName, value);  
        }  
  
        // Persists settings and sets property with side effect of signaling  
        // ColumnGuideAdornments to update.  
        static private void WriteSettings(Color color, IEnumerable<int> columns)  
        {  
            string value = ComposeSettingsString(color, columns);  
            GuidelinesConfiguration = value;  
        }  
  
        private static string ComposeSettingsString(Color color,  
                                                    IEnumerable<int> columns)  
        {  
            StringBuilder sb = new StringBuilder();  
            sb.AppendFormat("RGB({0},{1},{2})", color.R, color.G, color.B);  
            IEnumerator<int> columnsEnumerator = columns.GetEnumerator();  
            if (columnsEnumerator.MoveNext())  
            {  
                sb.AppendFormat(" {0}", columnsEnumerator.Current);  
                while (columnsEnumerator.MoveNext())  
                {  
                    sb.AppendFormat(", {0}", columnsEnumerator.Current);  
                }  
            }  
            return sb.ToString();  
        }  
  
        // Parse a color out of a string that begins like "RGB(255,0,0)"  
        static internal Color GuidelinesColor  
        {  
            get  
            {  
                string config = GuidelinesConfiguration;  
                if (!String.IsNullOrEmpty(config) && config.StartsWith("RGB("))  
                {  
                    int lastParen = config.IndexOf(')');  
                    if (lastParen > 4)  
                    {  
                        string[] rgbs = config.Substring(4, lastParen - 4).Split(',');  
  
                        if (rgbs.Length >= 3)  
                        {  
                            byte r, g, b;  
                            if (byte.TryParse(rgbs[0], out r) &&  
                                byte.TryParse(rgbs[1], out g) &&  
                                byte.TryParse(rgbs[2], out b))  
                            {  
                                return Color.FromRgb(r, g, b);  
                            }  
                        }  
                    }  
                }  
                return Colors.DarkRed;  
            }  
  
            set  
            {  
                WriteSettings(value, GetColumnOffsets());  
            }  
        }  
  
        // Parse a list of integer values out of a string that looks like  
        // "RGB(255,0,0) 1, 5, 10, 80"  
        static internal List<int> GetColumnOffsets()  
        {  
            var result = new List<int>();  
            string settings = GuidesSettingsManager.GuidelinesConfiguration;  
            if (String.IsNullOrEmpty(settings))  
                return new List<int>();  
  
            if (!settings.StartsWith("RGB("))  
                return new List<int>();  
  
            int lastParen = settings.IndexOf(')');  
            if (lastParen <= 4)  
                return new List<int>();  
  
            string[] columns = settings.Substring(lastParen + 1).Split(',');  
  
            int columnCount = 0;  
            foreach (string columnText in columns)  
            {  
                int column = -1;  
                // VS 2008 gallery extension didn't allow zero, so per user request ...  
                if (int.TryParse(columnText, out column) && column >= 0)  
                {  
                    columnCount++;  
                    result.Add(column);  
                    if (columnCount >= _maxGuides)  
                        break;  
                }  
            }  
            return result;  
        }  
  
        // Delegate and Event to fire when settings change so that ColumnGuideAdornments   
        // can update.  We need nothing special in this event since the settings manager   
        // is statically available.  
        //  
        internal delegate void SettingsChangedHandler();  
        static internal event SettingsChangedHandler SettingsChanged;  
  
    }  
}  
  
```  
  
 此代码的大部分只是创建和分析设置格式:"RGB (\<int&1;>，\<int&1;>，\<int&1;>) \<int&1;>， \<int&1;>，..."。  在结束整数都是所需列参考线的位置的基于&1; 的列。  列指南扩展捕获单个设置值字符串中的所有设置。  
  
 有需要强调代码的某些部分。  下面的代码行获取为设置存储的 Visual Studio 托管的包装。  大多数情况下，这通过 Windows 注册表中提取，但此 API 都是独立的存储机制。  
  
```c#  
internal static SettingsManager VsManagedSettingsManager =  
    new ShellSettingsManager(ServiceProvider.GlobalProvider);  
```  
  
 Visual Studio 设置存储使用类别标识符和设置标识符来唯一标识的所有设置︰  
  
```c#  
private const string _collectionSettingsName = "Text Editor";  
private const string _settingName = "Guides";  
```  
  
 不需要使用`“Text Editor”`作为类别名称，并且您可以选择您喜欢的任何。  
  
 第一少数几个函数是入口点，若要更改设置。  这些检查高级约束类似的参考线允许的最大值。  然后它们调用`WriteSettings`其中撰写设置字符串，并将该属性设置`GuideLinesConfiguration`。  设置此属性将设置值保存到 Visual Studio 设置存储并触发`SettingsChanged`事件来更新所有`ColumnGuideAdornment`对象时，每个关联的文本的视图。  
  
 有几个入口点函数，如`CanAddGuideline`，，用于实现更改设置的命令。  当 Visual Studio 显示菜单时，它将查询命令实现方式以查看如果当前启用命令，其名称是什么，等等。下面将看到如何挂接命令实现这些入口点。  请参阅[扩展菜单和命令](../extensibility/extending-menus-and-commands.md)有关命令的详细信息。  
  
## <a name="implementing-the-columnguideadornment-class"></a>实现 ColumnGuideAdornment 类  
 `ColumnGuideAdornment`为可以有修饰每个文本视图实例化类。  此类侦听有关视图的更改的事件或更改设置，根据需要更新或重新绘制列的指导。  
  
 ColumnGuideAdornment.cs 的内容替换为下面的代码 （如下所述）︰  
  
```c#  
using System;  
using System.Windows.Media;  
using Microsoft.VisualStudio.Text.Editor;  
using System.Collections.Generic;  
using System.Windows.Shapes;  
using Microsoft.VisualStudio.Text.Formatting;  
using System.Windows;  
  
namespace ColumnGuides  
{  
    /// <summary>  
    /// Adornment class, one instance per text view that draws a guides on the viewport  
    /// </summary>  
    internal sealed class ColumnGuideAdornment  
    {  
        private const double _lineThickness = 1.0;  
        private IList<Line> _guidelines;  
        private IWpfTextView _view;  
        private double _baseIndentation;  
        private double _columnWidth;  
  
        /// <summary>  
        /// Creates editor column guidelines  
        /// </summary>  
        /// <param name="view">The <see cref="IWpfTextView"/> upon   
        /// which the adornment will be drawn</param>  
        public ColumnGuideAdornment(IWpfTextView view)  
        {  
            _view = view;  
            _guidelines = CreateGuidelines();  
            GuidesSettingsManager.SettingsChanged +=   
                new GuidesSettingsManager.SettingsChangedHandler(SettingsChanged);  
            view.LayoutChanged +=   
                new EventHandler<TextViewLayoutChangedEventArgs>(OnViewLayoutChanged);  
            _view.Closed += new EventHandler(OnViewClosed);  
        }  
  
        void SettingsChanged()  
        {  
            _guidelines = CreateGuidelines();  
            UpdatePositions();  
            AddGuidelinesToAdornmentLayer();  
        }  
  
        void OnViewClosed(object sender, EventArgs e)  
        {  
            _view.LayoutChanged -= OnViewLayoutChanged;  
            _view.Closed -= OnViewClosed;  
            GuidesSettingsManager.SettingsChanged -= SettingsChanged;  
        }  
  
        private bool _firstLayoutDone;  
  
        void OnViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)  
        {  
            bool fUpdatePositions = false;  
  
            IFormattedLineSource lineSource = _view.FormattedLineSource;  
            if (lineSource == null)  
            {  
                return;  
            }  
            if (_columnWidth != lineSource.ColumnWidth)  
            {  
                _columnWidth = lineSource.ColumnWidth;  
                fUpdatePositions = true;  
            }  
            if (_baseIndentation != lineSource.BaseIndentation)  
            {  
                _baseIndentation = lineSource.BaseIndentation;  
                fUpdatePositions = true;  
            }  
            if (fUpdatePositions ||  
                e.VerticalTranslation ||  
                e.NewViewState.ViewportTop != e.OldViewState.ViewportTop ||  
                e.NewViewState.ViewportBottom != e.OldViewState.ViewportBottom)  
            {  
                UpdatePositions();  
            }  
            if (!_firstLayoutDone)  
            {  
                AddGuidelinesToAdornmentLayer();  
                _firstLayoutDone = true;  
            }  
        }  
  
        private static IList<Line> CreateGuidelines()  
        {  
            Brush lineBrush = new SolidColorBrush(GuidesSettingsManager.GuidelinesColor);  
            DoubleCollection dashArray = new DoubleCollection(new double[] { 1.0, 3.0 });  
            IList<Line> result = new List<Line>();  
            foreach (int column in GuidesSettingsManager.GetColumnOffsets())  
            {  
                Line line = new Line()  
                {  
                    // Use the DataContext slot as a cookie to hold the column  
                    DataContext = column,  
                    Stroke = lineBrush,  
                    StrokeThickness = _lineThickness,  
                    StrokeDashArray = dashArray  
                };  
                result.Add(line);  
            }  
            return result;  
        }  
  
        void UpdatePositions()  
        {  
            foreach (Line line in _guidelines)  
            {  
                int column = (int)line.DataContext;  
                line.X2 = _baseIndentation + 0.5 + column * _columnWidth;  
                line.X1 = line.X2;  
                line.Y1 = _view.ViewportTop;  
                line.Y2 = _view.ViewportBottom;  
            }  
        }  
  
        void AddGuidelinesToAdornmentLayer()  
        {  
            // Grab a reference to the adornment layer that this adornment   
            // should be added to  
            // Must match exported name in ColumnGuideAdornmentTextViewCreationListener  
            IAdornmentLayer adornmentLayer =   
                _view.GetAdornmentLayer("ColumnGuideAdornment");  
            if (adornmentLayer == null)  
                return;  
            adornmentLayer.RemoveAllAdornments();  
            // Add the guidelines to the adornment layer and make them relative   
            // to the viewport  
            foreach (UIElement element in _guidelines)  
                adornmentLayer.AddAdornment(AdornmentPositioningBehavior.OwnerControlled,  
                                            null, null, element, null);  
        }  
    }  
  
}  
```  
  
 此类的实例保存到关联<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>和列表`Line`绘制在视图上的对象。</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>  
  
 构造函数 (从调用`ColumnGuideAdornmentTextViewCreationListener`Visual Studio 创建新的视图时) 创建列指南`Line`对象。  构造函数还将添加处理程序`SettingsChanged`事件 (在中定义`GuidesSettingsManager`) 并查看事件`LayoutChanged`和`Closed`。  
  
 `LayoutChanged`由于几种在视图中，包括在 Visual Studio 将创建视图时更改的事件触发。  `OnViewLayoutChanged`处理程序调用`AddGuidelinesToAdornmentLayer`来执行。  中的代码`OnViewLayoutChanged`确定它是否需要更新根据更改等字体大小的变化，视图装订线，水平滚动的行位置。  中的代码`UpdatePositions`导致绘制个字符之间或紧随其后的是文本行中指定的字符偏移量中的文本列的参考线。  
  
 只要设置更改`SettingsChanged`函数只是重新创建所有`Line`具有任何新设置的对象。  设置后的行位置，代码将删除所有以前`Line`对象从`ColumnGuideAdornment`修饰层，并添加新的。  
  
## <a name="defining-the-commands-menus-and-menu-placements"></a>定义命令、 菜单和菜单放置  
 可能有大量声明命令和菜单、 命令或菜单组置于各种其他菜单和挂接命令处理程序。  本演练中突出显示命令如何工作中这种扩展，但对于更深入信息，请参阅[扩展菜单和命令](../extensibility/extending-menus-and-commands.md)。  
  
### <a name="introduction-to-the-code"></a>该代码简介  
 列参考线扩展演示如何声明一组相互关联的命令 （将列添加、 删除列、 更改线条颜色），然后将该组放在子菜单的编辑器的上下文菜单上。  列参考线扩展还会将命令添加到 main**编辑**菜单但将保持它们不可见的作为一种常见模式下面讨论。  
  
 有三个部分的命令实现︰ ColumnGuideCommandsPackage.cs、 ColumnGuideCommandsPackage.vsct 和 ColumnGuideCommands.cs。  由模板生成的代码放入命令**工具**菜单弹出对话框中的实现。  您可以查看程序中如何实现.vsct 和 ColumnGuideCommands.cs 文件由于它是相当简单。  将替换下面这些文件中的代码。  
  
 包代码是样板声明所需的 Visual Studio 来发现该扩展，提供了命令和命令的放置位置。  包初始化时，它实例化命令的实现类。  请参阅以上链接了解有关与命令相关的包的详细信息的命令。  
  
### <a name="a-common-commands-pattern"></a>一种常见命令模式  
 在列参考线扩展中的命令都举例说明如何在 Visual Studio 中的常用模式。  将相关的命令放在一个组，然后输入该组主菜单中，通常与"`<CommandFlag>CommandWellOnly</CommandFlag>`"设置以使该命令不可见。  将命令放在主菜单上 (如**编辑**) 这种方式将为它们提供很好的名称 (如**Edit.AddColumnGuide**) 可用于查找命令时将重新分配中的键绑定**工具选项**并且可用来调用命令时获取完成**命令窗口**。  
  
 然后向上下文菜单添加命令的组或子的菜单预期用户可以使用命令的位置。  Visual Studio 将其`CommandWellOnly`为仅在主菜单不可见性标志。  当你将命令的同一个组放在上下文菜单或子菜单上时，则命令将可见。  
  
 作为通用模式的一部分，列参考线扩展创建包含单个子菜单的另一个组。  反过来，子菜单包含具有由四列指南命令的第一个组。  包含子菜单的第二个组是对您放在不同的上下文菜单，从而在这些上下文菜单上将子菜单的可重用资产。  
  
### <a name="the-vsct-file"></a>.Vsct 文件  
 .Vsct 文件声明的命令，其中它们随同，图标，依此类推。  .Vsct 文件的内容替换为下面的代码 （如下所述）︰  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
  <!--  This is the file that defines the actual layout and type of the commands.  
        It is divided in different sections (e.g. command definition, command  
        placement, ...), with each defining a specific set of properties.  
        See the comment before each section for more details about how to  
        use it. -->  
  
  <!--  The VSCT compiler (the tool that translates this file into the binary  
        format that VisualStudio will consume) has the ability to run a preprocessor  
        on the vsct file; this preprocessor is (usually) the C++ preprocessor, so  
        it is possible to define includes and macros with the same syntax used  
        in C++ files. Using this ability of the compiler here, we include some files  
        defining some of the constants that we will use inside the file. -->  
  
  <!--This is the file that defines the IDs for all the commands exposed by   
      VisualStudio. -->  
  <Extern href="stdidcmd.h"/>  
  
  <!--This header contains the command ids for the menus provided by the shell. -->  
  <Extern href="vsshlids.h"/>  
  
  <!--The Commands section is where commands, menus, and menu groups are defined.  
      This section uses a Guid to identify the package that provides the command   
      defined inside it. -->  
  <Commands package="guidColumnGuideCommandsPkg">  
    <!-- Inside this section we have different sub-sections: one for the menus, another    
    for the menu groups, one for the buttons (the actual commands), one for the combos   
    and the last one for the bitmaps used. Each element is identified by a command id  
    that is a unique pair of guid and numeric identifier; the guid part of the identifier  
    is usually called "command set" and is used to group different command inside a  
    logically related group; your package should define its own command set in order to  
    avoid collisions with command ids defined by other packages. -->  
  
    <!-- In this section you can define new menu groups. A menu group is a container for   
         other menus or buttons (commands); from a visual point of view you can see the   
         group as the part of a menu contained between two lines. The parent of a group   
         must be a menu. -->  
    <Groups>  
  
      <!-- The main group is parented to the edit menu. All the buttons within the group  
           have the "CommandWellOnly" flag, so they're actually invisible, but it means  
           they get canonical names that begin with "Edit". Using placements, the group  
           is also placed in the GuidesSubMenu group. -->  
      <!-- The priority 0xB801 is chosen so it goes just after   
           IDG_VS_EDIT_COMMANDWELL -->  
      <Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"  
             priority="0xB801">  
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />  
      </Group>  
  
      <!-- Group for holding the "Guidelines" sub-menu anchor (the item on the menu that  
           drops the sub menu). The group is parented to  
           the context menu for code windows. That takes care of most editors, but it's  
           also placed in a couple of other windows using Placements -->  
      <Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
             priority="0x0600">  
        <Parent guid="guidSHLMainMenu" id="IDM_VS_CTXT_CODEWIN" />  
      </Group>  
  
    </Groups>  
  
    <Menus>  
      <Menu guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" priority="0x1000"  
            type="Menu">  
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup" />  
        <Strings>  
          <ButtonText>&Column Guides</ButtonText>  
        </Strings>  
      </Menu>  
    </Menus>  
  
    <!--Buttons section. -->  
    <!--This section defines the elements the user can interact with, like a menu command or a button   
        or combo box in a toolbar. -->  
    <Buttons>  
      <!--To define a menu group you have to specify its ID, the parent menu and its   
          display priority.   
          The command is visible and enabled by default. If you need to change the   
          visibility, status, etc, you can use the CommandFlag node.  
          You can add more than one CommandFlag node e.g.:  
              <CommandFlag>DefaultInvisible</CommandFlag>  
              <CommandFlag>DynamicVisibility</CommandFlag>  
          If you do not want an image next to your command, remove the Icon node or   
          set it to <Icon guid="guidOfficeIcon" id="msotcidNoIcon" /> -->  
  
      <Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"   
              priority="0x0100" type="Button">  
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
        <Icon guid="guidImages" id="bmpPicAddGuide" />  
        <CommandFlag>CommandWellOnly</CommandFlag>  
        <CommandFlag>AllowParams</CommandFlag>  
        <Strings>  
          <ButtonText>&Add Column Guide</ButtonText>  
        </Strings>  
      </Button>  
  
      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveColumnGuide"   
              priority="0x0101" type="Button">  
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
        <Icon guid="guidImages" id="bmpPicRemoveGuide" />  
        <CommandFlag>CommandWellOnly</CommandFlag>  
        <CommandFlag>AllowParams</CommandFlag>  
        <Strings>  
          <ButtonText>&Remove Column Guide</ButtonText>  
        </Strings>  
      </Button>  
  
      <Button guid="guidColumnGuidesCommandSet" id="cmdidChooseGuideColor"   
              priority="0x0103" type="Button">  
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
        <Icon guid="guidImages" id="bmpPicChooseColor" />  
        <CommandFlag>CommandWellOnly</CommandFlag>  
        <Strings>  
          <ButtonText>Column Guide &Color...</ButtonText>  
        </Strings>  
      </Button>  
  
      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveAllColumnGuides"   
              priority="0x0102" type="Button">  
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
        <CommandFlag>CommandWellOnly</CommandFlag>  
        <Strings>  
          <ButtonText>Remove A&ll Columns</ButtonText>  
        </Strings>  
      </Button>  
    </Buttons>  
  
    <!--The bitmaps section is used to define the bitmaps that are used for the  
        commands.-->  
    <Bitmaps>  
      <!--  The bitmap id is defined in a way that is a little bit different from the  
            others:   
            the declaration starts with a guid for the bitmap strip, then there is the  
            resource id of the bitmap strip containing the bitmaps and then there are   
            the numeric ids of the elements used inside a button definition. An important  
            aspect of this declaration is that the element id   
            must be the actual index (1-based) of the bitmap inside the bitmap strip. -->  
      <Bitmap guid="guidImages" href="Resources\ColumnGuideCommands.png"   
              usedList="bmpPicAddGuide, bmpPicRemoveGuide, bmpPicChooseColor" />  
    </Bitmaps>  
  
  </Commands>  
  
  <CommandPlacements>  
  
    <!-- Define secondary placements for our groups -->  
  
    <!-- Place the group containing the three commands in the sub-menu -->  
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"   
                      priority="0x0100">  
      <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />  
    </CommandPlacement>  
  
    <!-- The HTML editor context menu, for some reason, redefines its own groups  
         so we need to place a copy of our context menu there too. -->  
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
                      priority="0x1001">  
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_HTML" />  
    </CommandPlacement>  
  
    <!-- The HTML context menu in Dev12 changed. -->  
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
                      priority="0x1001">  
      <Parent guid="CMDSETID_HtmEdGrp_Dev12" id="IDMX_HTM_SOURCE_HTML_Dev12" />  
    </CommandPlacement>  
  
    <!-- Similarly for Script -->  
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"  
                      priority="0x1001">  
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_SCRIPT" />  
    </CommandPlacement>  
  
    <!-- Similarly for ASPX  -->  
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
                      priority="0x1001">  
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_ASPX" />  
    </CommandPlacement>  
  
    <!-- Similarly for the XAML editor context menu -->  
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"  
                      priority="0x0600">  
      <Parent guid="guidXamlUiCmds" id="IDM_XAML_EDITOR" />  
    </CommandPlacement>  
  
  </CommandPlacements>  
  
  <!-- This defines the identifiers and their values used above to index resources  
       and specify commands. -->  
  <Symbols>  
    <!-- This is the package guid. -->  
    <GuidSymbol name="guidColumnGuideCommandsPkg"   
                value="{e914e5de-0851-4904-b361-1a3a9d449704}" />  
  
    <!-- This is the guid used to group the menu commands together -->  
    <GuidSymbol name="guidColumnGuidesCommandSet"   
                value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">  
      <IDSymbol name="GuidesContextMenuGroup" value="0x1020" />  
      <IDSymbol name="GuidesMenuItemsGroup" value="0x1021" />  
      <IDSymbol name="GuidesSubMenu" value="0x1022" />  
      <IDSymbol name="cmdidAddColumnGuide" value="0x0100" />  
      <IDSymbol name="cmdidRemoveColumnGuide" value="0x0101" />  
      <IDSymbol name="cmdidChooseGuideColor" value="0x0102" />  
      <IDSymbol name="cmdidRemoveAllColumnGuides" value="0x0103" />  
    </GuidSymbol>  
  
    <GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">  
      <IDSymbol name="bmpPicAddGuide" value="1" />  
      <IDSymbol name="bmpPicRemoveGuide" value="2" />  
      <IDSymbol name="bmpPicChooseColor" value="3" />  
    </GuidSymbol>  
  
    <GuidSymbol name="CMDSETID_HtmEdGrp_Dev12"   
                value="{78F03954-2FB8-4087-8CE7-59D71710B3BB}">  
      <IDSymbol name="IDMX_HTM_SOURCE_HTML_Dev12" value="0x1" />  
    </GuidSymbol>  
  
    <GuidSymbol name="CMDSETID_HtmEdGrp" value="{d7e8c5e1-bdb8-11d0-9c88-0000f8040a53}">  
      <IDSymbol name="IDMX_HTM_SOURCE_HTML" value="0x33" />  
      <IDSymbol name="IDMX_HTM_SOURCE_SCRIPT" value="0x34" />  
      <IDSymbol name="IDMX_HTM_SOURCE_ASPX" value="0x35" />  
    </GuidSymbol>  
  
    <GuidSymbol name="guidXamlUiCmds" value="{4c87b692-1202-46aa-b64c-ef01faec53da}">  
      <IDSymbol name="IDM_XAML_EDITOR" value="0x103" />  
    </GuidSymbol>  
  </Symbols>  
  
</CommandTable>  
  
```  
  
 **GUID**。  若要查找命令处理程序并调用它们的 Visual studio，您需要确保的包 ColumnGuideCommandsPackage.cs 文件 （从项目项模板生成） 中声明的 GUID 匹配 GUID 在.vsct 文件 （复制从上面） 中声明的包。  如果重复使用此示例代码，则应确保你有不同的 GUID，以便与其他人可能已复制此代码不冲突。  
  
 在 ColumnGuideCommandsPackage.cs 中查找以下行并将复制介于引号引起来的 GUID:  
  
```c#  
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";  
```  
  
 将 GUID 粘贴在.vsct 文件中，以便具有以下行您`Symbols`声明︰  
  
```xml  
<GuidSymbol name="guidColumnGuideCommandsPkg"   
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />  
```  
  
 该命令的 Guid 设置和位图图像文件太应该是唯一的您的扩展︰  
  
```xml  
<GuidSymbol name="guidColumnGuidesCommandSet"   
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">  
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">  
```  
  
 但是，您不需要更改该命令集和位图图像在本演练中的 Guid 来获取代码才能工作。  设置 GUID 需求以匹配 ColumnGuideCommands.cs 文件中的声明的命令，但您将替换该文件的内容有点不同︰因此，将匹配 Guid。  
  
 .Vsct 文件中的其他 Guid 标识预先存在的列指南命令会添加到其中的菜单，因此它们永远不会更改。  
  
 **文件部分**。  .Vsct 有三个外部部分︰ 命令、 放置和符号。  命令部分定义命令组、 菜单、 按钮或菜单项和图标的位图。  放置节声明组向何处寻求菜单或到预先存在的菜单上的其他位置上。  符号部分声明在.vsct 文件中，这会使.vsct 代码比无处不在具有 Guid 和十六进制数字更易读的其他位置使用的标识符。  
  
 **命令节、 组定义**。  命令部分首先定义命令组。  组的命令是菜单中看到与轻微的灰线分隔这些组命令。  一组可能还会填充整个子菜单中的，如本示例中所示，您看不到这种情况下分隔行灰色。  .Vsct 文件声明两个组， `GuidesMenuItemsGroup` ，成为的父级`IDM_VS_MENU_EDIT`(主**编辑**菜单) 与`GuidesContextMenuGroup`，成为的父级`IDM_VS_CTXT_CODEWIN`（代码编辑器的上下文菜单）。  
  
 第二个组声明具有`0x0600`优先级︰  
  
```xml  
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
             priority="0x0600">  
```  
  
 其理念是将列将引导我们将添加到的任何上下文菜单的子菜单组末尾的子菜单。  但是，您不应假定您非常清楚地知道并强制子菜单始终是通过使用的优先级的最后一个`0xFFFF`。  您必须摆弄此号码，请参阅子菜单所在上放置位置的上下文菜单。  在这种情况下`0x0600`很高，足以将其放在菜单末尾据我们所看到的但它会为其他人来设计其扩展名为小于列指南扩展，如果需要留出空间。  
  
 **命令部分中，菜单定义**。  接下来将命令部分定义子菜单`GuidesSubMenu`，到其父级`GuidesContextMenuGroup`。  `GuidesContextMenuGroup`是我们将添加到所有相关的上下文菜单的组。  在放置部分中，代码将使用由四列指南命令组放在此子菜单上。  
  
 **命令节、 按钮定义**。  然后，命令部分定义的菜单项或四个列的按钮指南命令。  `CommandWellOnly`上文所述，意味着这些命令是放在主菜单上时不可见。  菜单项的两个按钮声明 （添加参考线和删除指南） 还具有`AllowParams`标志︰  
  
```xml  
<CommandFlag>AllowParams</CommandFlag>  
```  
  
 此标志启用，以及具有主菜单放置，该命令时 Visual Studio 时，将调用命令处理程序接收参数。  如果用户调用命令窗口中的命令，那么参数获取在事件参数传递到命令处理程序。  
  
 **命令部分，位图定义**。  最后的命令部分声明位图或使用的命令的图标。  这是一个简单的声明，标识项目资源，并列出使用图标的基于&1; 的索引。  .Vsct 文件的 symbols 部分声明作为索引使用的标识符的值。  本演练使用带有自定义命令项模板添加到项目中提供的位图条。  
  
 **放置部分**。  命令之后部分是放置部分。  第一个参数是该代码添加上面所讨论的第一个组包含四个列指南命令绑定到子菜单命令的显示位置︰  
  
```xml  
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"   
                  priority="0x0100">  
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />  
</CommandPlacement>  
```  
  
 所有其他位置添加`GuidesContextMenuGroup`(其中包含`GuidesSubMenu`) 到其他编辑器上下文菜单。  当该代码声明`GuidesContextMenuGroup`，它已成为其父级的代码编辑器的上下文菜单。  这是为什么你看不到代码编辑器的上下文菜单上的放置。  
  
 **符号部分**。  如上面所述，符号部分声明在.vsct 文件中，这会使.vsct 代码比无处不在具有 Guid 和十六进制数字更易读的其他位置使用的标识符。  本部分中的要点是包 GUID 必须同意包类，而和命令组 GUID 必须同意命令实现类中声明的声明。  
  
## <a name="implementing-the-commands"></a>实现命令  
 ColumnGuideCommands.cs 文件实现的命令，并挂接的处理程序。  包后，Visual Studio 加载包时对其进行初始化，反过来调用`Initialize`命令实现类上。  命令初始化只需实例化类，并构造函数将所有命令处理程序都挂钩。  
  
 ColumnGuideCommands.cs 文件的内容替换为下面的代码 （如下所述）︰  
  
```c#  
using System;  
using System.ComponentModel.Design;  
using System.Globalization;  
using Microsoft.VisualStudio.Shell;  
using Microsoft.VisualStudio.Shell.Interop;  
using Microsoft.VisualStudio.TextManager.Interop;  
using Microsoft.VisualStudio.Text.Editor;  
using Microsoft.VisualStudio;  
  
namespace ColumnGuides  
{  
    /// <summary>  
    /// Command handler  
    /// </summary>  
    internal sealed class ColumnGuideCommands  
    {  
  
        const int cmdidAddColumnGuide = 0x0100;  
        const int cmdidRemoveColumnGuide = 0x0101;  
        const int cmdidChooseGuideColor = 0x0102;  
        const int cmdidRemoveAllColumnGuides = 0x0103;  
  
        /// <summary>  
        /// Command menu group (command set GUID).  
        /// </summary>  
        static readonly Guid CommandSet =   
            new Guid("c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e");  
  
        /// <summary>  
        /// VS Package that provides this command, not null.  
        /// </summary>  
        private readonly Package package;  
  
        OleMenuCommand _addGuidelineCommand;  
        OleMenuCommand _removeGuidelineCommand;  
  
        /// <summary>  
        /// Initializes the singleton instance of the command.  
        /// </summary>  
        /// <param name="package">Owner package, not null.</param>  
        public static void Initialize(Package package)  
        {  
            Instance = new ColumnGuideCommands(package);  
        }  
  
        /// <summary>  
        /// Gets the instance of the command.  
        /// </summary>  
        public static ColumnGuideCommands Instance  
        {  
            get;  
            private set;  
        }  
  
        /// <summary>  
        /// Initializes a new instance of the <see cref="ColumnGuideCommands"/> class.  
        /// Adds our command handlers for menu (commands must exist in the command   
        /// table file)  
        /// </summary>  
        /// <param name="package">Owner package, not null.</param>  
        private ColumnGuideCommands(Package package)  
        {  
            if (package == null)  
            {  
                throw new ArgumentNullException("package");  
            }  
  
            this.package = package;  
  
            // Add our command handlers for menu (commands must exist in the .vsct file)  
  
            OleMenuCommandService commandService =  
                this.ServiceProvider.GetService(typeof(IMenuCommandService))  
                    as OleMenuCommandService;  
            if (commandService != null)  
            {  
                // Add guide  
                _addGuidelineCommand =   
                    new OleMenuCommand(AddColumnGuideExecuted, null,  
                                       AddColumnGuideBeforeQueryStatus,  
                                       new CommandID(ColumnGuideCommands.CommandSet,  
                                                     cmdidAddColumnGuide));  
                _addGuidelineCommand.ParametersDescription = "<column>";  
                commandService.AddCommand(_addGuidelineCommand);  
                // Remove guide  
                _removeGuidelineCommand =  
                    new OleMenuCommand(RemoveColumnGuideExecuted, null,  
                                       RemoveColumnGuideBeforeQueryStatus,  
                                       new CommandID(ColumnGuideCommands.CommandSet,  
                                                     cmdidRemoveColumnGuide));  
                _removeGuidelineCommand.ParametersDescription = "<column>";  
                commandService.AddCommand(_removeGuidelineCommand);  
                // Choose color  
                commandService.AddCommand(  
                    new MenuCommand(ChooseGuideColorExecuted,  
                                    new CommandID(ColumnGuideCommands.CommandSet,  
                                                  cmdidChooseGuideColor)));  
                // Remove all  
                commandService.AddCommand(  
                    new MenuCommand(RemoveAllGuidelinesExecuted,  
                                    new CommandID(ColumnGuideCommands.CommandSet,  
                                                  cmdidRemoveAllColumnGuides)));  
            }  
        }  
  
        /// <summary>  
        /// Gets the service provider from the owner package.  
        /// </summary>  
        private IServiceProvider ServiceProvider  
        {  
            get  
            {  
                return this.package;  
            }  
        }  
  
        private void AddColumnGuideBeforeQueryStatus(object sender, EventArgs e)  
        {  
            int currentColumn = GetCurrentEditorColumn();  
            _addGuidelineCommand.Enabled =  
                GuidesSettingsManager.CanAddGuideline(currentColumn);  
        }  
  
        private void RemoveColumnGuideBeforeQueryStatus(object sender, EventArgs e)  
        {  
            int currentColumn = GetCurrentEditorColumn();  
            _removeGuidelineCommand.Enabled =  
                GuidesSettingsManager.CanRemoveGuideline(currentColumn);  
        }  
  
        private int GetCurrentEditorColumn()  
        {  
            IVsTextView view = GetActiveTextView();  
            if (view == null)  
            {  
                return -1;  
            }  
  
            try  
            {  
                IWpfTextView textView = GetTextViewFromVsTextView(view);  
                int column = GetCaretColumn(textView);  
  
                // Note: GetCaretColumn returns 0-based positions. Guidelines are 1-based  
                // positions.  
                // However, do not subtract one here since the caret is positioned to the  
                // left of  
                // the given column and the guidelines are positioned to the right. We  
                // want the  
                // guideline to line up with the current caret position. e.g. When the  
                // caret is  
                // at position 1 (zero-based), the status bar says column 2. We want to  
                // add a  
                // guideline for column 1 since that will place the guideline where the  
                // caret is.  
                return column;  
            }  
            catch (InvalidOperationException)  
            {  
                return -1;  
            }  
        }  
  
        /// <summary>  
        /// Find the active text view (if any) in the active document.  
        /// </summary>  
        /// <returns>The IVsTextView of the active view, or null if there is no active  
        /// document or the  
        /// active view in the active document is not a text view.</returns>  
        private IVsTextView GetActiveTextView()  
        {  
            IVsMonitorSelection selection =  
                this.ServiceProvider.GetService(typeof(IVsMonitorSelection))  
                                                    as IVsMonitorSelection;  
            object frameObj = null;  
            ErrorHandler.ThrowOnFailure(  
                selection.GetCurrentElementValue(  
                    (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame, out frameObj));  
  
            IVsWindowFrame frame = frameObj as IVsWindowFrame;  
            if (frame == null)  
            {  
                return null;  
            }  
  
            return GetActiveView(frame);  
        }  
  
        private static IVsTextView GetActiveView(IVsWindowFrame windowFrame)  
        {  
            if (windowFrame == null)  
            {  
                throw new ArgumentException("windowFrame");  
            }  
  
            object pvar;  
            ErrorHandler.ThrowOnFailure(  
                windowFrame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView, out pvar));  
  
            IVsTextView textView = pvar as IVsTextView;  
            if (textView == null)  
            {  
                IVsCodeWindow codeWin = pvar as IVsCodeWindow;  
                if (codeWin != null)  
                {  
                    ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));  
                }  
            }  
            return textView;  
        }  
  
        private static IWpfTextView GetTextViewFromVsTextView(IVsTextView view)  
        {  
  
            if (view == null)  
            {  
                throw new ArgumentNullException("view");  
            }  
  
            IVsUserData userData = view as IVsUserData;  
            if (userData == null)  
            {  
                throw new InvalidOperationException();  
            }  
  
            object objTextViewHost;  
            if (VSConstants.S_OK  
                   != userData.GetData(Microsoft.VisualStudio  
                                                .Editor  
                                                .DefGuidList.guidIWpfTextViewHost,  
                                       out objTextViewHost))  
            {  
                throw new InvalidOperationException();  
            }  
  
            IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;  
            if (textViewHost == null)  
            {  
                throw new InvalidOperationException();  
            }  
  
            return textViewHost.TextView;  
        }  
  
        /// <summary>  
        /// Given an IWpfTextView, find the position of the caret and report its column  
        /// number. The column number is 0-based  
        /// </summary>  
        /// <param name="textView">The text view containing the caret</param>  
        /// <returns>The column number of the caret's position. When the caret is at the  
        /// leftmost column, the return value is zero.</returns>  
        private static int GetCaretColumn(IWpfTextView textView)  
        {  
            // This is the code the editor uses to populate the status bar.  
            Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =  
                textView.Caret.ContainingTextViewLine;  
            double columnWidth = textView.FormattedLineSource.ColumnWidth;  
            return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)  
                                       / columnWidth));  
        }  
  
        /// <summary>  
        /// Determine the applicable column number for an add or remove command.  
        /// The column is parsed from command arguments, if present. Otherwise  
        /// the current position of the caret is used to determine the column.  
        /// </summary>  
        /// <param name="e">Event args passed to the command handler.</param>  
        /// <returns>The column number. May be negative to indicate the column number is  
        /// unavailable.</returns>  
        /// <exception cref="ArgumentException">The column number parsed from event args  
        /// was not a valid integer.</exception>  
        private int GetApplicableColumn(EventArgs e)  
        {  
            var inValue = ((OleMenuCmdEventArgs)e).InValue as string;  
            if (!string.IsNullOrEmpty(inValue))  
            {  
                int column;  
                if (!int.TryParse(inValue, out column) || column < 0)  
                    throw new ArgumentException("Invalid column");  
                return column;  
            }  
  
            return GetCurrentEditorColumn();  
        }  
  
        /// <summary>  
        /// This function is the callback used to execute a command when the a menu item  
        /// is clicked. See the Initialize method to see how the menu item is associated  
        /// to this function using the OleMenuCommandService service and the MenuCommand  
        /// class.  
        /// </summary>  
        private void AddColumnGuideExecuted(object sender, EventArgs e)  
        {  
            int column = GetApplicableColumn(e);  
            if (column >= 0)  
            {  
                GuidesSettingsManager.AddGuideline(column);  
            }  
        }  
  
        private void RemoveColumnGuideExecuted(object sender, EventArgs e)  
        {  
            int column = GetApplicableColumn(e);  
            if (column >= 0)  
            {  
                GuidesSettingsManager.RemoveGuideline(column);  
            }  
        }  
  
        private void RemoveAllGuidelinesExecuted(object sender, EventArgs e)  
        {  
            GuidesSettingsManager.RemoveAllGuidelines();  
        }  
  
        private void ChooseGuideColorExecuted(object sender, EventArgs e)  
        {  
            System.Windows.Media.Color color = GuidesSettingsManager.GuidelinesColor;  
  
            using (System.Windows.Forms.ColorDialog picker =   
                new System.Windows.Forms.ColorDialog())  
            {  
                picker.Color = System.Drawing.Color.FromArgb(255, color.R, color.G,  
                                                             color.B);  
                if (picker.ShowDialog() == System.Windows.Forms.DialogResult.OK)  
                {  
                    GuidesSettingsManager.GuidelinesColor =   
                        System.Windows.Media.Color.FromRgb(picker.Color.R,  
                                                           picker.Color.G,   
                                                           picker.Color.B);  
                }  
            }  
        }  
  
    }  
}  
  
```  
  
 **修复引用**。  将在此时缺少的引用。  在解决方案资源管理器中引用节点上按右指针按钮。  选择**添加...** 命令。  **添加引用** 对话框具有处于右上角的搜索框。  输入"编辑器"（不带双引号引起来）。  选择**Microsoft.VisualStudio.Editor** （您必须检查项目中，不只是选择左侧的框项） 的项，然后选择**确定**将引用添加。  
  
 **初始化**。  当包在类初始化时，它将调用`Initialize`命令实现类上。  `ColumnGuideCommands`初始化实例化类，并将类实例及包引用保存在类成员。  
  
 让我们看一个命令处理程序挂钩 ups 从类构造函数︰  
  
```c#  
_addGuidelineCommand =   
    new OleMenuCommand(AddColumnGuideExecuted, null,  
                       AddColumnGuideBeforeQueryStatus,  
                       new CommandID(ColumnGuideCommands.CommandSet,  
                                     cmdidAddColumnGuide));  
  
```  
  
 您创建`OleMenuCommand`。  Visual Studio 将使用 Microsoft Office 命令系统。  Key 参数实例化 OleMenuCommand 时实现的命令的函数 (`AddColumnGuideExecuted`)，用于在 Visual Studio 将显示带有该命令的菜单时调用的函数 (`AddColumnGuideBeforeQueryStatus`)，和命令 id。  Visual studio 会在一个命令显示在菜单上，这样，该命令不可见或灰色菜单上的特定显示可进行自身之前调用查询状态函数 (例如，禁用**副本**如果未选择任何内容)、 更改它的图标，或甚至更改它的名称 （例如，从添加的某些对象为删除的内容），等等。  命令 ID 必须匹配在.vsct 文件中声明的命令 ID。  该命令的字符串设置并列参考线添加命令必须匹配在.vsct 文件和 ColumnGuideCommands.cs 之间。  
  
 在用户调用命令通过命令窗口中 （如下所述） 时，以下行提供协助︰  
  
```c#  
_addGuidelineCommand.ParametersDescription = "<column>";  
```  
  
 **查询状态**。  查询状态函数`AddColumnGuideBeforeQueryStatus`和`RemoveColumnGuideBeforeQueryStatus`检查某些设置 （如指南或最大的列的最大数量） 或如果没有要删除的列指南。  如果条件合适，它们启用这些命令。  查询状态函数需要是非常高效，因为它们在每次运行 Visual Studio 将显示在菜单上的每个命令的菜单。  
  
 **AddColumnGuideExecuted 函数**。  添加一个指南的有趣部分确定出当前的编辑器视图和插入符号位置。  此函数首先调用`GetApplicableColumn`它会检查是否有用户提供的参数在命令处理程序的事件参数中并不存在，如果该函数检查编辑器的视图︰  
  
```c#  
private int GetApplicableColumn(EventArgs e)  
{  
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;  
    if (!string.IsNullOrEmpty(inValue))  
    {  
        int column;  
        if (!int.TryParse(inValue, out column) || column < 0)  
            throw new ArgumentException("Invalid column");  
        return column;  
    }  
  
    return GetCurrentEditorColumn();  
}  
  
```  
  
 `GetCurrentEditorColumn`具有要更深入地介绍一下获取<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>代码的视图。</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>  如果您通过跟踪`GetActiveTextView`， `GetActiveView`，和`GetTextViewFromVsTextView`，您可以看到如何做到这一点。  以下是相关代码抽象出来，从当前所选内容，然后获取所选内容的框架，然后获取作为框架的 DocView <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>，然后获取<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>从 IVsTextView，然后获取视图中的主机，并最后 IWpfTextView:</xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>  
  
```c#  
   IVsMonitorSelection selection =  
       this.ServiceProvider.GetService(typeof(IVsMonitorSelection))   
           as IVsMonitorSelection;  
   object frameObj = null;  
  
ErrorHandler.ThrowOnFailure(selection.GetCurrentElementValue(  
                                (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame,  
                                out frameObj));  
  
   IVsWindowFrame frame = frameObj as IVsWindowFrame;  
   if (frame == null)  
       <<do nothing>>;  
  
...  
   object pvar;  
   ErrorHandler.ThrowOnFailure(frame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView,  
                                                  out pvar));  
  
   IVsTextView textView = pvar as IVsTextView;  
   if (textView == null)  
   {  
       IVsCodeWindow codeWin = pvar as IVsCodeWindow;  
       if (codeWin != null)  
       {  
           ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));  
       }  
   }  
  
...  
   if (textView == null)  
       <<do nothing>>  
  
   IVsUserData userData = textView as IVsUserData;  
   if (userData == null)  
       <<do nothing>>  
  
   object objTextViewHost;  
   if (VSConstants.S_OK   
           != userData.GetData(Microsoft.VisualStudio.Editor.DefGuidList  
                                                            .guidIWpfTextViewHost,  
                                out objTextViewHost))  
   {  
       <<do nothing>>  
   }  
  
   IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;  
   if (textViewHost == null)  
       <<do nothing>>  
  
   IWpfTextView textView = textViewHost.TextView;  
  
```  
  
 IWpfTextView 后，你可以获取插入符号的位置的列︰  
  
```c#  
private static int GetCaretColumn(IWpfTextView textView)  
{  
    // This is the code the editor uses to populate the status bar.  
    Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =  
        textView.Caret.ContainingTextViewLine;  
    double columnWidth = textView.FormattedLineSource.ColumnWidth;  
    return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)  
                                / columnWidth));  
}  
  
```  
  
 与当前列手里在用户单击了，该代码只需调用上设置管理器来添加或删除列。  设置管理器会触发所有的事件`ColumnGuideAdornment`对象侦听。  当触发事件时，这些对象的新列指南设置更新与其关联的文本视图。  
  
## <a name="invoking-command-from-the-command-window"></a>从命令窗口调用命令  
 列指南示例使用户能够调用作为一种形式的可扩展性的两个命令从命令窗口。  如果您使用**视图 |其他窗口 |命令窗口**命令时，您可以看到命令窗口中。  通过输入"编辑"交互使用命令窗口和命令名称完成并提供参数 120，您拥有以下︰  
  
```  
> Edit.AddColumnGuide 120  
>  
```  
  
 启用在.vsct 文件声明中，这是此示例的各个部分`ColumnGuideCommands`时它挂接命令处理程序，以及检查事件参数的命令处理程序实现的类构造函数。  
  
 您所看到的"`<CommandFlag>CommandWellOnly</CommandFlag>`"在.vsct 文件以及在编辑主菜单中的放置即使我们不再显示中的命令**编辑**菜单 UI。  将它们放在主编辑菜单将为它们提供类似的名称**Edit.AddColumnGuide**。  命令组包含四个命令置于组编辑菜单直接的声明︰  
  
```xml  
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"  
             priority="0xB801">  
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />  
      </Group>  
  
```  
  
 按钮部分更高版本声明命令`CommandWellOnly`以使它们在主菜单上不可见的并且声明它们与`AllowParams`:  
  
```xml  
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"   
        priority="0x0100" type="Button">  
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
  <Icon guid="guidImages" id="bmpPicAddGuide" />  
  <CommandFlag>CommandWellOnly</CommandFlag>  
  <CommandFlag>AllowParams</CommandFlag>  
  
```  
  
 您所看到的命令处理程序挂钩代码`ColumnGuideCommands`类构造函数提供允许的参数的说明︰  
  
```c#  
_addGuidelineCommand.ParametersDescription = "<column>";  
  
```  
  
 您所看到的`GetApplicableColumn`函数检查`OleMenuCmdEventArgs`之前检查当前列的编辑器的视图的值︰  
  
```c#  
private int GetApplicableColumn(EventArgs e)  
{  
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;  
    if (!string.IsNullOrEmpty(inValue))  
    {  
        int column;  
        if (!int.TryParse(inValue, out column) || column < 0)  
            throw new ArgumentException("Invalid column");  
        return column;  
    }  
  
```  
  
## <a name="trying-your-extension"></a>尝试您的扩展  
 现在，可以按**F5**执行列参考线扩展。  打开一个文本文件，并使用编辑器的上下文菜单上添加参考线，删除它们，并更改其颜色。  您需要单击以文本 （没有空白传递行的末尾） 添加一个列指南中或编辑器将其添加到最后一列的行上。  如果您使用命令窗口，并调用带有参数的命令，可以添加任意位置列参考线。  
  
 如果您想要尝试不同的命令放置、 更改名称、 更改图标，依此类推，并且具有 Visual Studio 菜单中显示的最新代码中的任何问题，您可以重置正在调试的实验性配置单元。  调出**Windows 开始菜单**并键入"重置"。  查找并调用该命令**重置下一步的 Visual Studio 实验实例**。  这样将清除所有的扩展组件的实验性的注册表配置单元。  不是全新扩展从组件的设置，因此任何参考线，您必须关闭 Visual Studio 的实验性 hive 时仍在那里当您的代码中读取设置存储在下一次启动时。  
  
## <a name="finished-code-project"></a>完成的代码项目  
 很快将 Visual Studio 扩展性示例，一个 github 项目和已完成的项目都将会出现。  我们将更新此主题以点处在这种情况。  已完成的示例项目可能具有不同的 guid，并且将有不同的位图条命令图标。  
  
 您可以试用版列指南功能与此 Visual Studio 库[扩展](https://visualstudiogallery.msdn.microsoft.com/da227a0b-0e31-4a11-8f6b-3a149cf2e459?SRC=Home)。  
  
## <a name="see-also"></a>另请参阅  
 [在编辑器内](../extensibility/inside-the-editor.md)   
 [扩展编辑器和语言服务](../extensibility/extending-the-editor-and-language-services.md)   
 [语言服务和编辑器扩展点](../extensibility/language-service-and-editor-extension-points.md)   
 [扩展的菜单和命令](../extensibility/extending-menus-and-commands.md)   
 [将子菜单添加到菜单](../extensibility/adding-a-submenu-to-a-menu.md)   
 [在编辑器中的项模板创建扩展](../extensibility/creating-an-extension-with-an-editor-item-template.md)
