---
title: "创建视图修饰、 命令和设置 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3db7dea958fb3d80a109c021ffb20260f0748bba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-view-adornment-commands-and-settings-column-guides"></a>演练： 创建视图修饰、 命令和设置 （列指南）
你可以扩展 Visual Studio 文本/代码编辑器与命令和视图效果。  本主题演示了如何开始使用一种常用的扩展功能，列参考线。  列参考线是在文本编辑器的视图来帮助你管理你的代码特定列宽上绘制的直观地浅色行。  格式经过特别设计的代码可能很重要的示例包括在文档中，博客文章或 bug 报表。  
  
 在本演练中，你将：  
  
-   创建 VSIX 项目  
  
-   添加编辑器视图修饰  
  
-   添加对保存和到达设置 （其中绘图列参考线和其颜色） 的支持  
  
-   将命令添加 （添加/删除列参考线，更改其颜色）  
  
-   将命令置于编辑菜单和文本文档上下文菜单  
  
-   添加对调用 Visual Studio 命令窗口中的命令的支持  
  
 你还可以尝试使用此 Visual Studio 库列指南功能版本[扩展](https://visualstudiogallery.msdn.microsoft.com/da227a0b-0e31-4a11-8f6b-3a149cf2e459?SRC=Home)。  
  
 **请注意**： 在本演练中你粘贴大量的代码生成的 visual studio 扩展模板的几个文件，但本演练将很快引用与其他扩展示例的 github 上已完成的解决方案。  它而不是使用 generictemplate 图标的实际命令图标，完整的代码是略有不同。  
  
## <a name="getting-started"></a>入门  
 从 Visual Studio 2015 开始，你并不安装 Visual Studio SDK 从下载中心。 它将包括作为 Visual Studio 安装程序中的可选功能。 你还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="setting-up-the-solution"></a>设置该解决方案  
 首先将创建一个 VSIX 项目，添加编辑器视图修饰，并将命令 （其中添加 VSPackage 来拥有该命令）。  基本体系结构如下所示：  
  
-   必须创建一个文本视图创建侦听器`ColumnGuideAdornment`每个视图的对象。  此对象侦听有关视图更改的事件或更改的设置，根据需要更新或重新绘制列的指导。  
  
-   没有`GuidesSettingsManager`用于处理读取和写入从 Visual Studio 设置存储。  设置管理器还具有用于更新支持用户命令的设置的操作 （添加列、 删除列、 更改颜色）。  
  
-   如果你有用户命令是必需的 VSIP 包，但它是只需命令实现对象初始化的样板文件代码。  
  
-   没有`ColumnGuideCommands`.vsct 文件中声明的对象，实现用户命令并挂钩命令的命令处理程序。  
  
 **VSIX**。  使用**文件 &#124;新增功能。。。**命令以创建项目。  在左侧的导航窗格中选择 C# 下的扩展节点并选择**VSIX 项目**右窗格中。  输入 ColumnGuides 的名称，然后选择**确定**以创建该项目。  
  
 **查看修饰**。  在解决方案资源管理器中的项目节点上按右指针按钮。  选择**添加 &#124;新建项...**命令以添加新视图修饰项。  选择**扩展性 &#124;编辑器**左侧的导航窗格中，选择**编辑器视区修饰**右窗格中。  输入名称 ColumnGuideAdornment 作为项目名称，然后选择**添加**以将其添加。  
  
 你可以看到此项模板添加到的项目 （以及引用和等等） 的两个文件： ColumnGuideAdornment.cs 和 ColumnGuideAdornmentTextViewCreationListener.cs。  模板只需在视图上绘制紫色矩形。  下面将更改几个中行的视图创建侦听器，并替换 ColumnGuideAdornment.cs 的内容。  
  
 **命令**。  在解决方案资源管理器中的项目节点上按右指针按钮。  选择**添加 &#124;新建项...**命令以添加新视图修饰项。  选择**扩展性 &#124;VSPackage**左侧的导航窗格中，选择**自定义命令**右窗格中。  输入名称 ColumnGuideCommands 作为项目名称，然后选择**添加**以将其添加。  多个引用，除了添加的命令和包添加 ColumnGuideCommands.cs、 ColumnGuideCommandsPackage.cs 和 ColumnGuideCommandsPackage.vsct。  下面将替换第一个和最后一个文件，以定义和实现命令的内容。  
  
## <a name="setting-up-the-text-view-creation-listener"></a>设置文本视图创建侦听器  
 在编辑器中打开 ColumnGuideAdornmentTextViewCreationListener.cs。  此代码将实现一个处理程序，用于每当 Visual Studio 将创建文本视图。  还有控制当处理程序调用根据视图的特征的特性。  
  
 代码还必须声明一个修饰层。  当编辑器更新视图时，它修饰层获取视图，并于获取修饰元素。  您可以声明你相对于其他具有属性的层的顺序。  将以下行：  
  
```csharp  
[Order(After = PredefinedAdornmentLayers.Caret)]  
```  
  
 替换为以下两个行：  
  
```csharp  
[Order(Before = PredefinedAdornmentLayers.Text)]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
```  
  
 替换的行是组中的声明修饰层的属性。   第一行您更改了列参考线的显示位置的唯一更改。  "之前"视图中的文本意味着它们显示之后或文本下方绘制线条。  第二行声明，列指南修饰适用于文本实体符合你概念是一个文档，但无法声明修饰，例如，仅可编辑文本的工作。  中的详细信息[语言服务和编辑器扩展点](../extensibility/language-service-and-editor-extension-points.md)  
  
## <a name="implementing-the-settings-manager"></a>实现设置管理器  
 GuidesSettingsManager.cs 的内容替换为下面的代码 （如下所述）：  
  
```csharp  
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
  
 大多数的此代码只需创建并分析设置格式:"RGB (\<int >，\<int >，\<int >) \<int >， \<int >，..."。  在结束整数是想列参考线的基于 1 的列。  列的指南扩展捕获其单一设置值字符串中的所有设置。  
  
 有值得突出显示代码的某些部分。  以下代码行获取设置存储的 Visual Studio 托管的包装。  大多数情况下，这将抽离通过 Windows 注册表中，但此 API 是独立于存储机制。  
  
```csharp  
internal static SettingsManager VsManagedSettingsManager =  
    new ShellSettingsManager(ServiceProvider.GlobalProvider);  
```  
  
 Visual Studio 设置存储使用类别标识符和设置标识符来唯一地标识所有设置：  
  
```csharp  
private const string _collectionSettingsName = "Text Editor";  
private const string _settingName = "Guides";  
```  
  
 无需使用`"Text Editor"`作为类别名称，并且你可以选取您喜欢的任何。  
  
 前几个函数是若要更改设置的入口点。  它们检查高级的约束，如指南允许的最大数目。  然后它们调用`WriteSettings`其中撰写设置字符串，并将该属性设置`GuideLinesConfiguration`。  设置此属性将设置值保存到 Visual Studio 设置存储和激发`SettingsChanged`事件以更新所有`ColumnGuideAdornment`对象，每个关联的文本视图。  
  
 有几个入口点函数，如`CanAddGuideline`，用于实现更改设置的命令。  当 Visual Studio 显示菜单时，它将查询命令实现，若要查看是否命令当前启用，则其名称是什么，等等。下面将了解如何以挂钩的命令实现这些入口点。  请参阅[扩展菜单和命令](../extensibility/extending-menus-and-commands.md)有关命令的详细信息。  
  
## <a name="implementing-the-columnguideadornment-class"></a>实现 ColumnGuideAdornment 类  
 `ColumnGuideAdornment`类的实例化时为每个可以有修饰的文本视图。  此类侦听有关视图更改的事件或更改的设置，根据需要更新或重新绘制列的指导。  
  
 ColumnGuideAdornment.cs 的内容替换为下面的代码 （如下所述）：  
  
```csharp  
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
  
 此类的实例保存到关联<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>和列表`Line`视图上绘制的对象。  
  
 构造函数 (从调用`ColumnGuideAdornmentTextViewCreationListener`Visual Studio 创建新视图的时) 创建列指南`Line`对象。  构造函数还将添加处理程序`SettingsChanged`事件 (在中定义`GuidesSettingsManager`) 和查看事件`LayoutChanged`和`Closed`。  
  
 `LayoutChanged`由于几种在视图中，包括在 Visual Studio 将创建视图时更改的事件将触发。  `OnViewLayoutChanged`处理程序调用`AddGuidelinesToAdornmentLayer`执行。  中的代码`OnViewLayoutChanged`确定它是否需要更新基于如字体大小更改、 视图装订线，水平滚动，等的更改的行位置。  中的代码`UpdatePositions`使指南行绘制之间字符或紧随其后的列中的文本行的指定的字符偏移量的文本。  
  
 每当设置更改`SettingsChanged`函数只需重新创建所有`Line`与任何新设置的对象。  在设置后的行位置，代码将删除以前的所有`Line`对象从`ColumnGuideAdornment`修饰层，并将添加新的。  
  
## <a name="defining-the-commands-menus-and-menu-placements"></a>定义命令、 菜单和菜单放置  
 可以有大量声明命令和菜单、 放置在各种其他菜单上的命令或菜单的组和挂接命令处理程序。  本演练中突出显示在此扩展，但更深入信息命令的工作方式，请参阅[扩展菜单和命令](../extensibility/extending-menus-and-commands.md)。  
  
### <a name="introduction-to-the-code"></a>代码简介  
 列参考线扩展会显示声明一组相互关联的命令 （将列添加、 删除列、 更改线条颜色），并在编辑器的上下文菜单的子菜单上将放入该组。  列参考线扩展还将命令添加到 main**编辑**菜单但将保持它们不可见的作为一种常见模式下面所述。  
  
 有三个部分的命令实现： ColumnGuideCommandsPackage.cs、 ColumnGuideCommandsPackage.vsct 和 ColumnGuideCommands.cs。  由模板生成的代码将放入命令**工具**弹出对话框中作为实现的菜单。  你可以查看如何实现在.vsct 和 ColumnGuideCommands.cs 文件因为它是相当简单。  你会将以下这些文件中的代码。  
  
 包代码是样本声明所需的 Visual Studio 以了解扩展能够提供命令和命令的放置位置。  当初始化包时，它将实例命令实现类。  请参阅上面有关与命令相关的包的详细信息的链接的命令。  
  
### <a name="a-common-commands-pattern"></a>一种常见命令模式  
 在列参考线扩展中的命令都非常常用的模式，在 Visual Studio 中的示例。  将相关的命令放在一个组，并将该组在主菜单中，通常与"`<CommandFlag>CommandWellOnly</CommandFlag>`"设置为使该命令不可见。  在主菜单上放置命令 (如**编辑**) 这种方式为他们提供了良好的名称 (如**Edit.AddColumnGuide**) 可用于查找命令，重新分配中的键绑定时**工具选项**并且可用来调用命令时获取完成**命令窗口**。  
  
 然后将命令的组添加到上下文菜单或子的菜单希望用户能够使用命令。  Visual Studio 将对待`CommandWellOnly`作为主菜单仅不可见性标志。  当你将命令的相同组放在上下文菜单或子菜单上时，则命令将可见。  
  
 作为通用模式的一部分，列参考线扩展创建另一个包含单个子菜单的组。  子菜单中又包含四个列指南命令的第一个组。  包含子菜单的第二个组是您将放置在不同的上下文菜单，从而在这些上下文菜单上将子菜单的可重用资产。  
  
### <a name="the-vsct-file"></a>.Vsct 文件  
 .Vsct 文件声明命令，它们从何处，以及图标，依此类推。  .Vsct 文件的内容替换为下面的代码 （如下所述）：  
  
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
  
 **GUID**。  对于 Visual Studio 中查找命令处理程序并调用它们，你需要确保的包 GUID （从项目项模板生成） ColumnGuideCommandsPackage.cs 文件中声明与匹配的 GUID （复制上面的.vsct 文件中声明的包).  如果你重新使用此示例代码，应确保您具有不同的 GUID，以便与其他人可能已复制此代码不冲突。  
  
 ColumnGuideCommandsPackage.cs 中查找以下行并复制介于引号引起来的 GUID:  
  
```csharp  
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";  
```  
  
 将 GUID 粘贴在.vsct 文件中，以便您具有以下行你`Symbols`声明：  
  
```xml  
<GuidSymbol name="guidColumnGuideCommandsPkg"   
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />  
```  
  
 该命令的 Guid 设置并位图图像文件太应是唯一的你的扩展：  
  
```xml  
<GuidSymbol name="guidColumnGuidesCommandSet"   
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">  
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">  
```  
  
 但是，你不需要更改该命令集并位图图像 Guid 在本演练中获取代码才能工作。  设置 GUID 需求以匹配在 ColumnGuideCommands.cs 文件中，声明的命令，但将太; 替换该文件的内容因此，将匹配的 Guid。  
  
 .Vsct 文件中的其他 Guid 标识预先存在的列指南命令将添加到的菜单，因此它们永远不会更改。  
  
 **文件部分**。  .Vsct 具有三个外部部分： 命令、 放置和符号。  命令部分定义命令组、 菜单、 按钮或菜单项和图标的位图。  放置部分用于声明组目的地菜单或其他放置到预先存在的菜单上。  符号部分用于声明在.vsct 文件中，这会使.vsct 代码更具可读性比无处不在具有 Guid 和十六进制数字的其他位置使用的标识符。  
  
 **命令部分、 组定义**。  命令部分首先定义命令组。  命令的组是你使用略灰色的行分隔组看菜单中的命令。  组还可能会填充整个子菜单中，如此示例所示，并且你不会出现灰色的分隔行，在这种情况下。  .Vsct 文件声明两个组， `GuidesMenuItemsGroup` ，有父级到`IDM_VS_MENU_EDIT`(主**编辑**菜单) 与`GuidesContextMenuGroup`，有父级到`IDM_VS_CTXT_CODEWIN`（代码编辑器的上下文菜单）。  
  
 第二个组声明具有`0x0600`优先级：  
  
```xml  
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
             priority="0x0600">  
```  
  
 思路是将列指导我们将子菜单组添加到任何上下文菜单的末尾的子菜单。  但是，你不应假定你非常清楚地知道并强制为始终最后一个通过使用优先级的子菜单`0xFFFF`。  你必须使用此编号，以查看子菜单所在上放置位置的上下文菜单。  在这种情况下`0x0600`足够高，以将其放入菜单末尾就可以看出，但它会为其他人来设计其扩展名，则需要为小于列指南扩展留出空间。  
  
 **命令部分中，菜单定义**。  下一步命令部分定义的子菜单`GuidesSubMenu`，到其父级`GuidesContextMenuGroup`。  `GuidesContextMenuGroup`是我们将添加到所有相关的上下文菜单的组。  在放置部分中，代码放置在此子菜单上四个列指南命令的组。  
  
 **命令部分、 按钮定义**。  命令部分然后定义菜单项或是四个列的按钮指导命令。  `CommandWellOnly`上文所述，意味着的命令都放在主菜单上时不可见。  菜单项的两个按钮声明 （添加参考线和删除指南） 还具有`AllowParams`标志：  
  
```xml  
<CommandFlag>AllowParams</CommandFlag>  
```  
  
 此标志允许，以及使用具有主菜单放置，该命令时 Visual Studio 时，将调用的命令处理程序接收自变量。  如果用户调用命令窗口中的执行命令，那么的参数获取在事件自变量传递给命令处理程序。  
  
 **命令部分、 位图定义**。  最后命令部分用于声明位图或用于命令的图标。  这是一个简单的声明，标识的项目资源并列出使用图标的基于 1 的索引。  .Vsct 文件的符号部分声明作为索引使用的标识符的值。  本演练使用添加到项目中的自定义命令项模板一起提供的位图条。  
  
 **放置部分**。  在命令后部分是放置部分。  第一个参数是该代码添加前面所讨论的第一个组包含四个列指南到子菜单的命令命令的显示位置：  
  
```xml  
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"   
                  priority="0x0100">  
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />  
</CommandPlacement>  
```  
  
 所有其他放置添加`GuidesContextMenuGroup`(其中包含`GuidesSubMenu`) 到其他编辑器上下文菜单。  当代码声明`GuidesContextMenuGroup`，它已成为其父级的代码编辑器的上下文菜单。  这是为什么你看不到代码编辑器的上下文菜单的放置。  
  
 **符号部分**。  如上面所述，符号部分用于声明在.vsct 文件中，这会使.vsct 代码更具可读性比无处不在具有 Guid 和十六进制数字的其他位置使用的标识符。  本部分中的重要点是包 GUID 必须同意在包类中和命令集 GUID 必须同意命令实现类中声明的声明。  
  
## <a name="implementing-the-commands"></a>实现命令  
 ColumnGuideCommands.cs 文件实现命令和挂钩处理程序。  当 Visual Studio 加载包时，并对其进行初始化时，反过来调用包`Initialize`命令实现类上。  命令初始化只需实例化类，并构造函数挂钩所有命令处理程序。  
  
 ColumnGuideCommands.cs 文件的内容替换为下面的代码 （如下所述）：  
  
```csharp  
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
  
 **修复引用**。  将在此时缺少的引用。  在解决方案资源管理器中的引用节点上按右指针按钮。  选择**添加...**命令。  **添加引用**对话框有处于右上角的搜索框。  输入"editor"（不带双引号引起来）。  选择**Microsoft.VisualStudio.Editor** （您必须检查该项目，不只需选择左侧的框项） 的项，然后选择**确定**添加引用。  
  
 **初始化**。  当包类初始化时，它将调用`Initialize`命令实现类上。  `ColumnGuideCommands`初始化实例化类并将类实例及程序包引用保存在类成员。  
  
 让我们看一下命令处理程序挂钩 ups 之一从类构造函数：  
  
```csharp  
_addGuidelineCommand =   
    new OleMenuCommand(AddColumnGuideExecuted, null,  
                       AddColumnGuideBeforeQueryStatus,  
                       new CommandID(ColumnGuideCommands.CommandSet,  
                                     cmdidAddColumnGuide));  
  
```  
  
 你创建`OleMenuCommand`。  Visual Studio 将使用 Microsoft Office 命令系统。  当实例化 OleMenuCommand 是实现该命令的函数的关键参数 (`AddColumnGuideExecuted`)，要在 Visual Studio 将显示带命令的菜单时调用的函数 (`AddColumnGuideBeforeQueryStatus`)，和命令 id。  Visual studio 菜单上显示命令，以便该命令不可见或为特定的菜单显示灰色可以使本身前调用查询状态函数 (例如，禁用**复制**如果未选择任何内容)，更改其图标，或甚至更改其名称 （例如，从将添加一些为删除的内容），依次类推。  命令 ID 必须匹配在.vsct 文件中声明的命令 ID。  该命令的字符串设置，以及列指南添加命令必须匹配.vsct 文件和 ColumnGuideCommands.cs 之间。  
  
 在用户调用该命令通过命令窗口 （如下所述） 时，以下行提供协助：  
  
```csharp  
_addGuidelineCommand.ParametersDescription = "<column>";  
```  
  
 **查询状态**。  查询状态函数`AddColumnGuideBeforeQueryStatus`和`RemoveColumnGuideBeforeQueryStatus`检查某些设置 （例如指南或最大的列的最大数量） 或如果没有要删除的列指南。  如果条件合适，它们启用这些命令。  查询状态函数需要是非常高效，因为每次 Visual Studio 将显示在菜单上的每个命令的菜单，它们运行。  
  
 **AddColumnGuideExecuted 函数**。  添加一条参考线的有趣部分找出当前的编辑器视图和脱字号位置中。  此函数首先调用`GetApplicableColumn`它会检查是否命令处理程序的事件自变量，在没有用户提供的自变量，如果不存在，然后函数检查编辑器的视图：  
  
```csharp  
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
  
 `GetCurrentEditorColumn`必须更深入地介绍若要获取一个小<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>代码视图。  如果通过跟踪`GetActiveTextView`， `GetActiveView`，和`GetTextViewFromVsTextView`，你可以看到如何执行该操作。  下面是相关的代码抽象化，从当前所选内容，然后获取所选内容的帧，然后获取作为帧的 DocView <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>，然后获取<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>IVsTextView，然后获取大量视图和最后 IWpfTextView:  
  
```csharp  
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
  
 IWpfTextView 之后，你可以获取插入符号所在的位置的列：  
  
```csharp  
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
  
 与当前列在手动在用户单击，该代码只需调用设置管理器添加或删除列。  设置管理器，将引发此事件写入所有`ColumnGuideAdornment`对象侦听。  当触发事件时，这些对象使用新的列指南设置更新与其关联的文本视图。  
  
## <a name="invoking-command-from-the-command-window"></a>调用命令从命令窗口  
 列指南示例使用户能够为窗体的扩展性调用两个命令从命令窗口。  如果你使用**视图 &#124;其他 Windows &#124;命令窗口**命令时，你可以看到命令窗口。  可以通过输入"编辑"交互与命令窗口并使用命令名称完成和提供的自变量 120，你具备以下：  
  
```  
> Edit.AddColumnGuide 120  
>  
```  
  
 启用在.vsct 文件声明中，有的示例部分`ColumnGuideCommands`时挂钩命令处理程序，并检查事件自变量的命令处理程序实现的类构造函数。  
  
 你看到"`<CommandFlag>CommandWellOnly</CommandFlag>`"在.vsct 文件以及在编辑主菜单中放置即使我们不再显示中的命令**编辑**菜单 UI。  将它们放在主编辑菜单将为它们提供类似名称**Edit.AddColumnGuide**。  命令组包含的四个命令放置组在编辑菜单上直接的声明：  
  
```xml  
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"  
             priority="0xB801">  
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />  
      </Group>  
  
```  
  
 按钮部分更高版本声明命令`CommandWellOnly`以使它们的主菜单上不可见的并且声明它们与`AllowParams`:  
  
```xml  
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"   
        priority="0x0100" type="Button">  
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
  <Icon guid="guidImages" id="bmpPicAddGuide" />  
  <CommandFlag>CommandWellOnly</CommandFlag>  
  <CommandFlag>AllowParams</CommandFlag>  
  
```  
  
 你看到挂钩中代码的命令处理程序`ColumnGuideCommands`类构造函数提供允许的参数的说明：  
  
```csharp  
_addGuidelineCommand.ParametersDescription = "<column>";  
  
```  
  
 你看到`GetApplicableColumn`函数检查`OleMenuCmdEventArgs`再进行检查当前的列的编辑器的视图的值：  
  
```csharp  
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
  
## <a name="trying-your-extension"></a>尝试你的扩展  
 现在，你可以按**F5**执行你列参考线的扩展。  打开一个文本文件，并使用编辑器的上下文菜单添加参考线，删除它们，并将其颜色设置。  您需要单击文本中 （不空白传入行的末尾） 添加列指南中或编辑器将其添加到在行上的最后一列。  如果你使用命令窗口，并调用具有参数的命令，你可以添加列参考线任何位置。  
  
 如果你想要尝试不同的命令放置、 更改名称、 更改图标和等等，并且具有 Visual Studio 菜单中显示的最新的代码中的任何问题，你可以重置正在调试的实验性配置单元。  弹出**Windows 开始菜单**并键入"重置"。  查找并调用该命令**重置下一步的 Visual Studio 实验实例**。  这会清理所有扩展组件的实验性注册表配置单元。  不清除扩展从组件的设置，因此你必须关闭 Visual Studio 的实验性配置单元时任何参考线仍在那里时你的代码读取存储在下一次启动中的设置。  
  
## <a name="finished-code-project"></a>完成的代码项目  
 即将推出 Visual Studio 扩展性示例的 github 项目和已完成的项目会在那里。  我们将更新本主题那里点，在这种情况。  已完成的示例项目可能具有不同的 guid，并且将有不同的位图条命令图标。  
  
 你还可以尝试使用此 Visual Studio 库列指南功能版本[扩展](https://visualstudiogallery.msdn.microsoft.com/da227a0b-0e31-4a11-8f6b-3a149cf2e459?SRC=Home)。  
  
## <a name="see-also"></a>另请参阅  
 [在编辑器内](../extensibility/inside-the-editor.md)   
 [扩展编辑器和语言服务](../extensibility/extending-the-editor-and-language-services.md)   
 [语言服务和编辑器扩展点](../extensibility/language-service-and-editor-extension-points.md)   
 [扩展菜单和命令](../extensibility/extending-menus-and-commands.md)   
 [将子菜单添加到菜单](../extensibility/adding-a-submenu-to-a-menu.md)   
 [使用编辑器项模板创建扩展](../extensibility/creating-an-extension-with-an-editor-item-template.md)