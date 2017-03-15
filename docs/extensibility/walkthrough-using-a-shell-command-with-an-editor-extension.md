---
title: "演练︰ 使用外壳命令与编辑器扩展 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
caps.latest.revision: 46
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 14ac62df46d3edaa93a18d5d2a2e717c7f0ba2de
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-using-a-shell-command-with-an-editor-extension"></a>演练︰ 使用外壳命令与编辑器扩展
从 VSPackage 中，您可以向编辑器中添加功能，如菜单命令。 本演练演示如何将修饰添加到编辑器中的文本视图中，通过调用菜单命令。  
  
 本演练演示如何与 Managed Extensibility Framework (MEF) 组件部件一起作为 VSPackage 的使用。 您必须使用 VSPackage 将菜单命令注册 Visual Studio shell 中，并且可以使用该命令来访问 MEF 组件部分。  
  
## <a name="prerequisites"></a>先决条件  
 启动 Visual Studio 2015 中，您并不安装 Visual Studio SDK 从下载中心获得。 它将包括作为 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-an-extension-with-a-menu-command"></a>使用菜单命令创建扩展  
 创建将名为菜单命令的 VSPackage**添加修饰**上**工具**菜单。  
  
1.  创建一个名为 C# VSIX 项目`MenuCommandTest`，并添加自定义命令项模板名称**AddAdornment**。 有关详细信息，请参阅[使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
2.  打开一个名为 MenuCommandTest 解决方案。 MenuCommandTestPackage 文件具有创建菜单命令，并将其放入的代码**工具**菜单。 此时，该命令只会导致将会显示一个消息框。 后续步骤演示如何更改此设置以显示注释修饰。  
  
3.  在 VSIX 清单编辑器中打开 source.extension.vsixmanifest 文件。 `Assets` Microsoft.VisualStudio.VsPackage 命名 MenuCommandTest 选项卡上应具有一个行。  
  
4.  保存并关闭源 Source.extension.vsixmanifest 文件。  
  
## <a name="adding-a-mef-extension-to-the-command-extension"></a>将 MEF 扩展添加到命令扩展  
  
1.  在**解决方案资源管理器**，用鼠标右键单击解决方案节点，单击**添加**，然后单击**新项目**。 在**添加新项目**对话框中，单击**扩展性**下**Visual C#**，然后**VSIX 项目**。 将项目命名为 `CommentAdornmentTest`。  
  
2.  因为此项目将使用强名称的 VSPackage 程序集进行交互，必须为程序集进行签名。 您可以重用已创建为 VSPackage 的程序集密钥文件。  
  
    1.  打开项目属性，然后选择**签名**选项卡。  
  
    2.  选择**为程序集签名**。  
  
    3.  在下**选择强名称密钥文件**，选择为 MenuCommandTest 程序集生成的 Key.snk 文件。  
  
## <a name="referring-to-the-mef-extension-in-the-vspackage-project"></a>VSPackage 项目中的 MEF 扩展引用  
 由于将 MEF 组件添加到 VSPackage 中，您必须在清单中指定这两种资产。  
  
> [!NOTE]
>  有关 MEF 的详细信息，请参阅[Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)。  
  
#### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>若要引用到 VSPackage 项目中的 MEF 组件  
  
1.  在 MenuCommandTest 项目中，打开 source.extension.vsixmanifest 文件在 VSIX 清单编辑器中。  
  
2.  在**资产**选项卡上，单击**新建**。  
  
3.  在**类型**列表中，选择**Microsoft.VisualStudio.MefComponent**。  
  
4.  在**源**列表中，选择**当前解决方案中的项目**。  
  
5.  在**项目**列表中，选择**CommentAdornmentTest**。  
  
6.  保存并关闭源 source.extension.vsixmanifest 文件。  
  
7.  请确保 MenuCommandTest 项目具有对 CommentAdornmentTest 项目的引用。  
  
8.  在 CommentAdornmentTest 项目中，将项目设置为生成的程序集。 在**解决方案资源管理器**、 选择的项目，并查找**属性**窗口**将生成输出复制到输出目录**属性，并将其设置为**true**。  
  
## <a name="defining-a-comment-adornment"></a>定义注释修饰  
 注释修饰本身组成<xref:Microsoft.VisualStudio.Text.ITrackingSpan>，跟踪所选的文本，以及某些表示作者和文本说明的字符串。</xref:Microsoft.VisualStudio.Text.ITrackingSpan>  
  
#### <a name="to-define-a-comment-adornment"></a>若要定义注释修饰  
  
1.  在 CommentAdornmentTest 项目中，添加一个新类文件并将其命名`CommentAdornment`。  
  
2.  添加以下引用︰  
  
    1.  Microsoft.VisualStudio.CoreUtility  
  
    2.  Microsoft.VisualStudio.Text.Data  
  
    3.  Microsoft.VisualStudio.Text.Logic  
  
    4.  Microsoft.VisualStudio.Text.UI  
  
    5.  Microsoft.VisualStudio.Text.UI.Wpf  
  
    6.  System.ComponentModel.Composition  
  
    7.  PresentationCore  
  
    8.  PresentationFramework  
  
    9. WindowsBase  
  
3.  将以下代码添加`using`语句。  
  
    ```vb  
    using Microsoft.VisualStudio.Text;  
    ```  
  
4.  该文件应包含一个名为类`CommentAdornment`。  
  
    ```  
    internal class CommentAdornment  
    ```  
  
5.  添加三个字段添加到`CommentAdornment`类<xref:Microsoft.VisualStudio.Text.ITrackingSpan>，作者和说明。</xref:Microsoft.VisualStudio.Text.ITrackingSpan>  
  
    ```c#  
    public readonly ITrackingSpan Span;  
    public readonly string Author;  
    public readonly string Text;  
    ```  
  
6.  添加一个构造函数初始化字段。  
  
    ```c#  
    public CommentAdornment(SnapshotSpan span, string author, string text)  
    {  
        this.Span = span.Snapshot.CreateTrackingSpan(span, SpanTrackingMode.EdgeExclusive);  
        this.Author = author;  
        this.Text = text;  
    }  
    ```  
  
## <a name="creating-a-visual-element-for-the-adornment"></a>修饰为创建一个可视元素  
 此外必须为您修饰定义一个可视元素。 对于本演练中，定义从 Windows Presentation Foundation (WPF) 类<xref:System.Windows.Controls.Canvas>。</xref:System.Windows.Controls.Canvas>继承的控件  
  
1.  在 CommentAdornmentTest 项目中，创建一个类并将其命名`CommentBlock`。  
  
2.  添加下面的 `using` 语句。  
  
    ```c#  
    using Microsoft.VisualStudio.Text;  
    using System;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Media;  
    using System.Windows.Shapes;  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Utilities;  
    ```  
  
3.  使`CommentBlock`类继承<xref:System.Windows.Controls.Canvas>。</xref:System.Windows.Controls.Canvas>  
  
    ```c#  
    internal class CommentBlock : Canvas  
    { }  
    ```  
  
4.  添加一些私有字段来定义修饰的可视方面。  
  
    ```c#  
    private Geometry textGeometry;  
    private Grid commentGrid;  
    private static Brush brush;  
    private static Pen solidPen;  
    private static Pen dashPen;  
    ```  
  
5.  添加的构造函数的代码定义注释修饰并添加相应的文本。  
  
    ```c#  
    public CommentBlock(double textRightEdge, double viewRightEdge,   
            Geometry newTextGeometry, string author, string body)  
    {  
        if (brush == null)  
        {  
            brush = new SolidColorBrush(Color.FromArgb(0x20, 0x00, 0xff, 0x00));  
            brush.Freeze();  
            Brush penBrush = new SolidColorBrush(Colors.Green);  
            penBrush.Freeze();  
            solidPen = new Pen(penBrush, 0.5);  
            solidPen.Freeze();  
            dashPen = new Pen(penBrush, 0.5);  
            dashPen.DashStyle = DashStyles.Dash;  
            dashPen.Freeze();  
        }  
  
        this.textGeometry = newTextGeometry;  
  
        TextBlock tb1 = new TextBlock();  
        tb1.Text = author;  
        TextBlock tb2 = new TextBlock();  
        tb2.Text = body;  
  
        const int MarginWidth = 8;  
        this.commentGrid = new Grid();  
        this.commentGrid.RowDefinitions.Add(new RowDefinition());  
        this.commentGrid.RowDefinitions.Add(new RowDefinition());  
        ColumnDefinition cEdge = new ColumnDefinition();  
        cEdge.Width = new GridLength(MarginWidth);  
        ColumnDefinition cEdge2 = new ColumnDefinition();  
        cEdge2.Width = new GridLength(MarginWidth);  
        this.commentGrid.ColumnDefinitions.Add(cEdge);  
        this.commentGrid.ColumnDefinitions.Add(new ColumnDefinition());  
        this.commentGrid.ColumnDefinitions.Add(cEdge2);  
  
        System.Windows.Shapes.Rectangle rect = new System.Windows.Shapes.Rectangle();  
        rect.RadiusX = 6;  
        rect.RadiusY = 3;  
        rect.Fill = brush;  
        rect.Stroke = Brushes.Green;  
  
            Size inf = new Size(double.PositiveInfinity, double.PositiveInfinity);  
            tb1.Measure(inf);  
            tb2.Measure(inf);  
            double middleWidth = Math.Max(tb1.DesiredSize.Width, tb2.DesiredSize.Width);  
            this.commentGrid.Width = middleWidth + 2 * MarginWidth;  
  
        Grid.SetColumn(rect, 0);  
        Grid.SetRow(rect, 0);  
         Grid.SetRowSpan(rect, 2);  
        Grid.SetColumnSpan(rect, 3);  
        Grid.SetRow(tb1, 0);  
        Grid.SetColumn(tb1, 1);  
        Grid.SetRow(tb2, 1);  
        Grid.SetColumn(tb2, 1);  
        this.commentGrid.Children.Add(rect);  
        this.commentGrid.Children.Add(tb1);  
        this.commentGrid.Children.Add(tb2);  
  
        Canvas.SetLeft(this.commentGrid, Math.Max(viewRightEdge - this.commentGrid.Width - 20.0, textRightEdge + 20.0));  
         Canvas.SetTop(this.commentGrid, textGeometry.GetRenderBounds(solidPen).Top);  
  
        this.Children.Add(this.commentGrid);  
    }  
    ```  
  
6.  此外实现<xref:System.Windows.Controls.Panel.OnRender%2A>绘制修饰的事件处理程序。</xref:System.Windows.Controls.Panel.OnRender%2A>  
  
    ```c#  
    protected override void OnRender(DrawingContext dc)  
    {  
        base.OnRender(dc);  
        if (this.textGeometry != null)  
        {  
            dc.DrawGeometry(brush, solidPen, this.textGeometry);  
            Rect textBounds = this.textGeometry.GetRenderBounds(solidPen);  
            Point p1 = new Point(textBounds.Right, textBounds.Bottom);  
            Point p2 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid) - 20.0, p1.X), p1.Y);  
            Point p3 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid), p1.X), (Canvas.GetTop(this.commentGrid) + p1.Y) * 0.5);  
            dc.DrawLine(dashPen, p1, p2);  
            dc.DrawLine(dashPen, p2, p3);  
        }  
    }  
    ```  
  
## <a name="adding-an-iwpftextviewcreationlistener"></a>添加 IWpfTextViewCreationListener  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>是一个 MEF 组件部件，可用于侦听若要查看创建事件。</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>  
  
1.  将类文件添加到 CommentAdornmentTest 项目并将其命名`Connector`。  
  
2.  添加下面的 `using` 语句。  
  
    ```c#  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Utilities;  
    ```  
  
3.  声明的类，实现<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>，并将其导出与<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>"text"和<xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>的<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>。</xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> </xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> </xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> </xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> 内容类型属性指定此类组件适用的内容。 文本类型是所有非二进制文件类型的基类型。 因此，将创建几乎每个文本视图都属于这种类型。 文本查看角色属性指定文本视图组件适用的类型。 文档文本视图角色通常显示线的组合，并存储在文件中的文本。  
  
     [!code-vb[VSSDKMenuCommandTest&#11;](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb) ] 
     [!code-cs [VSSDKMenuCommandTest&#11;](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]  
  
4.  实现<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>方法，以便它调用静态`Create()`事件`CommentAdornmentManager`。</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>  
  
    ```c#  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        CommentAdornmentManager.Create(textView);  
    }  
    ```  
  
5.  添加可用于执行命令的方法。  
  
    ```c#  
    static public void Execute(IWpfTextViewHost host)  
    {  
        IWpfTextView view = host.TextView;  
        //Add a comment on the selected text.   
        if (!view.Selection.IsEmpty)  
        {  
            //Get the provider for the comment adornments in the property bag of the view.  
            CommentAdornmentProvider provider = view.Properties.GetProperty<CommentAdornmentProvider>(typeof(CommentAdornmentProvider));  
  
            //Add some arbitrary author and comment text.   
            string author = System.Security.Principal.WindowsIdentity.GetCurrent().Name;  
            string comment = "Four score....";  
  
            //Add the comment adornment using the provider.  
            provider.Add(view.Selection.SelectedSpans[0], author, comment);  
        }  
    }  
    ```  
  
## <a name="defining-an-adornment-layer"></a>定义修饰层  
 若要添加新修饰，必须定义修饰层。  
  
#### <a name="to-define-an-adornment-layer"></a>若要定义修饰层  
  
1.  在`Connector`类中，声明类型的公共字段<xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>，并将其与导出<xref:Microsoft.VisualStudio.Utilities.NameAttribute>，它指定修饰层的唯一名称和一个<xref:Microsoft.VisualStudio.Utilities.OrderAttribute>修饰该层的 Z 顺序关系定义为其他文本视图层 （文本、 插入符号和所选内容）。</xref:Microsoft.VisualStudio.Utilities.OrderAttribute> </xref:Microsoft.VisualStudio.Utilities.NameAttribute> </xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>  
  
    ```c#  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("CommentAdornmentLayer")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition commentLayerDefinition;  
  
    ```  
  
## <a name="providing-comment-adornments"></a>提供注释修饰  
 当定义修饰时，还实现注释修饰提供程序和注释修饰管理器。 注释修饰服务供应商保留注释修饰的列表，侦听<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>上基础文本缓冲区，并删除注释修饰基础的文本会被删除时的事件。</xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>  
  
1.  将新的类文件添加到 CommentAdornmentTest 项目并将其命名`CommentAdornmentProvider`。  
  
2.  添加下面的 `using` 语句。  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.Collections.ObjectModel;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    ```  
  
3.  添加一个名为类`CommentAdornmentProvider`。  
  
    ```c#  
    internal class CommentAdornmentProvider  
    {  
    }  
    ```  
  
4.  添加文本缓冲区和注释修饰与缓冲区相关的列表的私有字段。  
  
    ```c#  
    private ITextBuffer buffer;  
    private IList<CommentAdornment> comments = new List<CommentAdornment>();  
  
    ```  
  
5.  添加一个构造函数为`CommentAdornmentProvider`。 此构造函数应具有专用访问权限，因为提供程序通过实例化`Create()`方法。 构造函数将添加`OnBufferChanged`事件处理程序<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>事件。</xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>  
  
    ```c#  
    private CommentAdornmentProvider(ITextBuffer buffer)  
    {  
        this.buffer = buffer;  
        //listen to the Changed event so we can react to deletions.   
        this.buffer.Changed += OnBufferChanged;  
    }  
  
    ```  
  
6.  添加 `Create()` 方法。  
  
    ```c#  
    public static CommentAdornmentProvider Create(IWpfTextView view)  
    {  
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentProvider>(delegate { return new CommentAdornmentProvider(view.TextBuffer); });  
    }  
  
    ```  
  
7.  添加 `Detach()` 方法。  
  
    ```c#  
    public void Detach()  
    {  
        if (this.buffer != null)  
        {  
            //remove the Changed listener   
            this.buffer.Changed -= OnBufferChanged;  
            this.buffer = null;  
        }  
    }  
    ```  
  
8.  添加`OnBufferChanged`事件处理程序。  
  
    ```c#  
    private void OnBufferChanged(object sender, TextContentChangedEventArgs e)  
    {  
        //Make a list of all comments that have a span of at least one character after applying the change. There is no need to raise a changed event for the deleted adornments. The adornments are deleted only if a text change would cause the view to reformat the line and discard the adornments.  
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);  
  
        foreach (CommentAdornment comment in this.comments)  
        {  
            Span span = comment.Span.GetSpan(e.After);  
            //if a comment does not span at least one character, its text was deleted.   
            if (span.Length != 0)  
            {  
                keptComments.Add(comment);  
            }  
        }  
  
        this.comments = keptComments;  
    }  
  
    ```  
  
     [!code-cs[VSSDKMenuCommandTest&#21;](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_2.cs) ] 
     [!code-vb [VSSDKMenuCommandTest&#21;](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_2.vb)]  
  
9. 添加的声明的`CommentsChanged`事件。  
  
    ```c#  
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;  
    ```  
  
10. 创建`Add()`方法将添加修饰。  
  
    ```c#  
    public void Add(SnapshotSpan span, string author, string text)  
    {  
        if (span.Length == 0)  
            throw new ArgumentOutOfRangeException("span");  
        if (author == null)  
            throw new ArgumentNullException("author");  
        if (text == null)  
            throw new ArgumentNullException("text");  
  
        //Create a comment adornment given the span, author and text.  
        CommentAdornment comment = new CommentAdornment(span, author, text);  
  
        //Add it to the list of comments.   
        this.comments.Add(comment);  
  
        //Raise the changed event.  
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;  
        if (commentsChanged != null)  
            commentsChanged(this, new CommentsChangedEventArgs(comment, null));  
    }  
  
    ```  
  
11. 添加`RemoveComments()`方法。  
  
    ```c#  
    public void RemoveComments(SnapshotSpan span)  
    {  
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;  
  
        //Get a list of all the comments that are being kept   
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);  
  
        foreach (CommentAdornment comment in this.comments)  
        {  
            //find out if the given span overlaps with the comment text span. If two spans are adjacent, they do not overlap. To consider adjacent spans, use IntersectsWith.   
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))  
            {  
                //Raise the change event to delete this comment.   
                if (commentsChanged != null)  
                    commentsChanged(this, new CommentsChangedEventArgs(null, comment));  
            }  
            else  
                keptComments.Add(comment);  
        }  
  
        this.comments = keptComments;  
    }  
    ```  
  
12. 添加`GetComments()`返回给定的快照范围中的所有批注的方法。  
  
    ```c#  
    public Collection<CommentAdornment> GetComments(SnapshotSpan span)  
    {  
        IList<CommentAdornment> overlappingComments = new List<CommentAdornment>();  
        foreach (CommentAdornment comment in this.comments)  
        {  
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))  
                overlappingComments.Add(comment);  
        }  
  
        return new Collection<CommentAdornment>(overlappingComments);  
    }  
    ```  
  
13. 添加一个名为类`CommentsChangedEventArgs`、，如下所示。  
  
    ```c#  
    internal class CommentsChangedEventArgs : EventArgs  
    {  
        public readonly CommentAdornment CommentAdded;  
  
        public readonly CommentAdornment CommentRemoved;  
  
        public CommentsChangedEventArgs(CommentAdornment added, CommentAdornment removed)  
        {  
            this.CommentAdded = added;  
            this.CommentRemoved = removed;  
        }  
    }  
    ```  
  
## <a name="managing-comment-adornments"></a>管理注释修饰  
 注释修饰 manager 创建修饰，并将其添加到修饰层。 它侦听<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>和<xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed>事件以便它可以移动或删除修饰。</xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> </xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> 它还侦听到`CommentsChanged`时添加或删除注释的注释修饰提供程序引发的事件。  
  
1.  将类文件添加到 CommentAdornmentTest 项目并将其命名`CommentAdornmentManager`。  
  
2.  添加下面的 `using` 语句。  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.Windows.Media;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Formatting;  
    ```  
  
3.  添加一个名为类`CommentAdornmentManager`。  
  
    ```c#  
    internal class CommentAdornmentManager  
        {  
        }  
    ```  
  
4.  添加一些私有字段。  
  
    ```c#  
    private readonly IWpfTextView view;  
    private readonly IAdornmentLayer layer;  
    private readonly CommentAdornmentProvider provider;  
    ```  
  
5.  添加订阅该管理器的构造函数<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>和<xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed>事件，并且还`CommentsChanged`事件。</xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> </xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> 构造函数是私有的因为该管理器实例化的静态`Create()`方法。  
  
    ```c#  
    private CommentAdornmentManager(IWpfTextView view)  
    {  
        this.view = view;  
        this.view.LayoutChanged += OnLayoutChanged;  
        this.view.Closed += OnClosed;  
  
        this.layer = view.GetAdornmentLayer("CommentAdornmentLayer");  
  
        this.provider = CommentAdornmentProvider.Create(view);  
        this.provider.CommentsChanged += OnCommentsChanged;  
    }  
    ```  
  
6.  添加`Create()`方法，获取一个提供程序，或者如果需要创建一个。  
  
    ```c#  
    public static CommentAdornmentManager Create(IWpfTextView view)  
    {  
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });  
    }  
    ```  
  
7.  添加`CommentsChanged`处理程序。  
  
    ```c#  
    private void OnCommentsChanged(object sender, CommentsChangedEventArgs e)  
    {  
        //Remove the comment (when the adornment was added, the comment adornment was used as the tag).   
        if (e.CommentRemoved != null)  
            this.layer.RemoveAdornmentsByTag(e.CommentRemoved);  
  
        //Draw the newly added comment (this will appear immediately: the view does not need to do a layout).   
        if (e.CommentAdded != null)  
            this.DrawComment(e.CommentAdded);  
    }  
    ```  
  
8.  添加<xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed>处理程序。</xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed>  
  
    ```c#  
    private void OnClosed(object sender, EventArgs e)  
    {  
        this.provider.Detach();  
        this.view.LayoutChanged -= OnLayoutChanged;  
        this.view.Closed -= OnClosed;  
    }  
    ```  
  
9. 添加<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>处理程序。</xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>  
  
    ```c#  
    private void OnLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)  
    {  
        //Get all of the comments that intersect any of the new or reformatted lines of text.  
        List<CommentAdornment> newComments = new List<CommentAdornment>();  
  
        //The event args contain a list of modified lines and a NormalizedSpanCollection of the spans of the modified lines.    
        //Use the latter to find the comments that intersect the new or reformatted lines of text.   
        foreach (Span span in e.NewOrReformattedSpans)  
        {  
            newComments.AddRange(this.provider.GetComments(new SnapshotSpan(this.view.TextSnapshot, span)));  
        }  
  
        //It is possible to get duplicates in this list if a comment spanned 3 lines, and the first and last lines were modified but the middle line was not.   
        //Sort the list and skip duplicates.  
        newComments.Sort(delegate(CommentAdornment a, CommentAdornment b) { return a.GetHashCode().CompareTo(b.GetHashCode()); });  
  
        CommentAdornment lastComment = null;  
        foreach (CommentAdornment comment in newComments)  
        {  
            if (comment != lastComment)  
            {  
                lastComment = comment;  
                this.DrawComment(comment);  
            }  
        }  
    }  
    ```  
  
10. 添加绘制注释的私有方法。  
  
     [!code-cs[VSSDKMenuCommandTest&#35;](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_3.cs) ] 
     [!code-vb [VSSDKMenuCommandTest&#35;](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_3.vb)]  
  
## <a name="using-the-menu-command-to-add-the-comment-adornment"></a>使用菜单命令添加注释修饰  
 可以使用菜单命令来创建注释修饰通过实现`MenuItemCallback`VSPackage 的方法。  
  
1.  添加对 MenuCommandTest 项目的以下引用︰  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.Editor  
  
    -   Microsoft.VisualStudio.Text.UI.Wpf  
  
2.  打开 AddAdornment.cs 文件并添加以下`using`语句。  
  
    ```c#  
    using Microsoft.VisualStudio.TextManager.Interop;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Editor;  
    using CommentAdornmentTest;  
    ```  
  
3.  删除 ShowMessageBox() 方法并添加下面的命令处理程序。  
  
    ```c#  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
4.  添加代码以获取当前视图。 你必须获取`SVsTextManager`的 Visual Studio shell 来获取活动`IVsTextView`。  
  
    ```c#  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
        IVsTextManager txtMgr = (IVsTextManager)ServiceProvider.GetService(typeof(SVsTextManager));  
        IVsTextView vTextView = null;  
        int mustHaveFocus = 1;  
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);  
    }  
    ```  
  
5.  如果此文本视图是编辑器文本视图的实例，可以将其转换为<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>接口，然后获得<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>和其相关联的<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>。</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> </xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> 使用<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>调用`Connector.Execute()`方法，它获取注释修饰提供程序，并将修饰。</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> 命令处理程序现在应如下所示︰  
  
    ```c#  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
        IVsTextManager txtMgr = (IVsTextManager)ServiceProvider.GetService(typeof(SVsTextManager));  
        IVsTextView vTextView = null;  
        int mustHaveFocus = 1;  
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);  
        IVsUserData userData = vTextView as IVsUserData;  
         if (userData == null)  
        {  
            Console.WriteLine("No text view is currently open");  
                            return;  
        }  
        IWpfTextViewHost viewHost;  
        object holder;  
        Guid guidViewHost = DefGuidList.guidIWpfTextViewHost;  
        userData.GetData(ref guidViewHost, out holder);  
        viewHost = (IWpfTextViewHost)holder;  
        Connector.Execute(viewHost);  
    }  
    ```  
  
6.  将 AddAdornmentHandler 方法设置为 AddAdornment 构造函数中 AddAdornment 命令的处理程序。  
  
    ```c#  
    private AddAdornment(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
            EventHandler eventHandler = this.AddAdornmentHandler;  
            MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
## <a name="building-and-testing-the-code"></a>生成和测试代码  
  
1.  生成解决方案并启动调试。 应显示的实验实例。  
  
2.  创建文本文件。 键入一些文本，然后选择它。  
  
3.  在**工具**菜单上，单击**调用添加修饰**。 一个提示框应显示文本窗口中，右侧，并应包含类似于以下文本的文本。  
  
     YourUserName  
  
     Fourscore...  
  
## <a name="see-also"></a>另请参阅  
 [演练︰ 将内容类型链接到的文件扩展名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
