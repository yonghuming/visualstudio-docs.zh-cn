---
title: "演练： 显示灯泡建议 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 46a20e68874db1bc94dda4227c062174e0b72b01
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-displaying-light-bulb-suggestions"></a>演练： 显示灯泡建议
电灯泡是 Visual Studio 编辑器中使用的图标会展开以显示一组操作，例如修补通过内置的代码分析器或重构代码标识的问题。  
  
 在 Visual C# 和 Visual Basic 编辑器中，你可以还使用.NET Compiler Platform ("Roslyn") 编写并打包你自己的代码分析器操作的自动显示电灯泡。 有关详细信息，请参见:  
  
-   [如何： 编写 C# 诊断和代码修复](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)  
  
-   [如何： 编写 Visual Basic 诊断和代码修复](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)  
  
 C + + 等其他语言还提供一些快速操作，如创建该函数的存根 （stub） 实现的建议电灯泡。  
  
 下面是一个灯泡如下所示。 在 Visual Basic 或 Visual C# 项目中，红色波形曲线将出现下变量名时无效。 当你将鼠标移无效的标识符时，灯泡会显示在光标附近。  
  
 ![灯泡](../extensibility/media/lightbulb.png "LightBulb")  
  
 如果通过电灯泡单击向下箭头，被显示一组建议的操作，以及所选操作的预览。 在这种情况下，它显示如果执行此操作将对你的代码进行的更改。  
  
 ![灯泡预览](../extensibility/media/lightbulbpreview.png "LightBulbPreview")  
  
 电灯泡可用于提供你自己建议的操作。 例如，你可以提供操作来移动打开到新行的大括号或将它们移到前面的行的末尾。 下面的演练演示如何创建出现一个灯泡在当前单词上并且具有两个建议操作：**将转换为大写形式**和**转换为小写**。  
  
## <a name="prerequisites"></a>先决条件  
 从 Visual Studio 2015 开始，你并不安装 Visual Studio SDK 从下载中心。 它将包括作为 Visual Studio 安装程序中的可选功能。 你还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>创建 Managed Extensibility Framework (MEF) 项目  
  
1.  创建 C# VSIX 项目。 (在**新项目**对话框中，选择**Visual C# / 可扩展性**，然后**VSIX 项目**。)将解决方案命名`LightBulbTest`。  
  
2.  添加**编辑器分类器**到项目的项模板。 有关详细信息，请参阅[带有编辑器项模板创建扩展](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  删除现有的类文件。  
  
4.  添加以下引用到项目中，并设置**Copy Local**到`False`:  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
5.  添加新的类文件并将其命名**LightBulbTest**。  
  
6.  添加以下 using 语句：  
  
    ```csharp  
    using System;  
    using System.Linq;  
    using System.Collections.Generic;  
    using System.Threading.Tasks;  
    using Microsoft.VisualStudio.Language.Intellisense;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Operations;  
    using Microsoft.VisualStudio.Utilities;  
    using System.ComponentModel.Composition;  
    using System.Threading;  
  
    ```  
  
## <a name="implementing-the-light-bulb-source-provider"></a>实现灯泡源提供程序  
  
1.  在 LightBulbTest.cs 类文件中，删除 LightBulbTest 类。 添加一个名为类**TestSuggestedActionsSourceProvider**实现<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>。 使用的名称将其导出**测试建议操作**和<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>"text"。  
  
    ```csharp  
    [Export(typeof(ISuggestedActionsSourceProvider))]  
    [Name("Test Suggested Actions")]  
    [ContentType("text")]  
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider  
    ```  
  
2.  在源提供程序类中，导入<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>并将其添加为属性。  
  
    ```csharp  
    [Import(typeof(ITextStructureNavigatorSelectorService))]  
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }  
    ```  
  
3.  实现<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A>方法以返回<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>对象。 我们将讨论下一步部分中的源。  
  
    ```csharp  
    public ISuggestedActionsSource CreateSuggestedActionsSource(ITextView textView, ITextBuffer textBuffer)  
    {  
        if (textBuffer == null && textView == null)  
        {  
            return null;  
        }  
        return new TestSuggestedActionsSource(this, textView, textBuffer);  
    }  
    ```  
  
## <a name="implementing-the-isuggestedactionsource"></a>实现 ISuggestedActionSource  
 建议的操作源负责收集的建议的操作集并将其添加正确的上下文中。 在这种情况下的上下文是当前的单词和建议的操作是**UpperCaseSuggestedAction**和**LowerCaseSuggestedAction**，其下一节中，我们将讨论。  
  
1.  添加类**TestSuggestedActionsSource**实现<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>。  
  
    ```csharp  
    internal class TestSuggestedActionsSource : ISuggestedActionsSource  
    ```  
  
2.  建议的操作源提供程序、 文本缓冲区和文本视图添加私有的只读字段。  
  
    ```csharp  
    private readonly TestSuggestedActionsSourceProvider m_factory;  
    private readonly ITextBuffer m_textBuffer;  
    private readonly ITextView m_textView;  
    ```  
  
3.  添加设置私有字段的构造函数。  
  
    ```csharp  
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)  
    {  
        m_factory = testSuggestedActionsSourceProvider;  
        m_textBuffer = textBuffer;  
        m_textView = textView;  
    }  
    ```  
  
4.  添加返回单词的目前光标下的一个私有方法。 以下方法查看光标的当前位置，并要求提供的字范围的文本结构导航器。 如果光标在字词<xref:Microsoft.VisualStudio.Text.Operations.TextExtent>out 参数中返回; 否则为`out`参数是`null`并且该方法返回`false`。  
  
    ```csharp  
    private bool TryGetWordUnderCaret(out TextExtent wordExtent)  
    {  
        ITextCaret caret = m_textView.Caret;  
        SnapshotPoint point;  
  
        if (caret.Position.BufferPosition > 0)  
        {  
            point = caret.Position.BufferPosition - 1;  
        }  
        else  
        {  
            wordExtent = default(TextExtent);  
            return false;  
        }  
  
        ITextStructureNavigator navigator = m_factory.NavigatorService.GetTextStructureNavigator(m_textBuffer);  
  
        wordExtent = navigator.GetExtentOfWord(point);  
        return true;  
    }  
    ```  
  
5.  实现 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A> 方法。 编辑器中调用此方法以找出是否显示电灯泡。 进行此调用常常，例如只要将光标从一个行移动到另一个，或者当鼠标悬停在错误波形曲线。 它是异步以便允许在处理此方法时，对执行其他 UI 操作。 在大多数情况下，此方法需要执行一些分析和分析的当前行，因此处理可能需要一些时间。  
  
     在我们实现它以异步方式获取<xref:Microsoft.VisualStudio.Text.Operations.TextExtent>并确定范围是否有效，即它是否有一些文本，而不是空格。  
  
    ```csharp  
    public Task<bool> HasSuggestedActionsAsync(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)  
    {  
        return Task.Factory.StartNew(() =>  
        {  
            TextExtent extent;  
            if (TryGetWordUnderCaret(out extent))  
            {  
                // don't display the action if the extent has whitespace  
                return extent.IsSignificant;  
              }  
            return false;  
        });  
    }  
    ```  
  
6.  实现<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A>方法，返回的数组<xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet>包含不同的对象<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>对象。 展开电灯泡时，调用此方法。  
  
    > [!WARNING]
    >  应确保的实现`HasSuggestedActionsAsync()`和`GetSuggestedActions()`是否一致; 即，如果`HasSuggestedActionsAsync()`返回`true`，然后`GetSuggestedActions()`应具有要显示的某些操作。 在许多情况下`HasSuggestedActionsAsync()`之前调用`GetSuggestedActions()`，但并不总是这种情况。 例如，如果用户通过按调用灯泡操作 (CTRL +。) 仅`GetSuggestedActions()`调用。  
  
    ```csharp  
    public IEnumerable<SuggestedActionSet> GetSuggestedActions(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)  
    {  
        TextExtent extent;  
        if (TryGetWordUnderCaret(out extent) && extent.IsSignificant)  
        {  
            ITrackingSpan trackingSpan = range.Snapshot.CreateTrackingSpan(extent.Span, SpanTrackingMode.EdgeInclusive);  
            var upperAction = new UpperCaseSuggestedAction(trackingSpan);  
            var lowerAction = new LowerCaseSuggestedAction(trackingSpan);  
            return new SuggestedActionSet[] { new SuggestedActionSet(new ISuggestedAction[] { upperAction, lowerAction }) };  
        }  
        return Enumerable.Empty<SuggestedActionSet>();  
    }   
    ```  
  
7.  定义`SuggestedActionsChanged`事件。  
  
    ```csharp  
    public event EventHandler<EventArgs> SuggestedActionsChanged;  
    ```  
  
8.  若要完成实现，添加实现`Dispose()`和`TryGetTelemetryId()`方法。 我们不希望为遥测，所以只需，则返回 false 然后设置为空的 GUID。  
  
    ```csharp  
    public void Dispose()  
    {  
    }  
  
    public bool TryGetTelemetryId(out Guid telemetryId)  
    {  
        // This is a sample provider and doesn't participate in LightBulb telemetry  
        telemetryId = Guid.Empty;  
        return false;  
    }  
    ```  
  
## <a name="implementing-light-bulb-actions"></a>实现灯泡操作  
  
1.  在项目中，添加到 Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll 和集的引用**Copy Local**到`False`。  
  
2.  创建两个类，第一个名为`UpperCaseSuggestedAction`和第二个名为`LowerCaseSuggestedAction`。 两个类都实现 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>。  
  
    ```csharp  
    internal class UpperCaseSuggestedAction : ISuggestedAction   
    internal class LowerCaseSuggestedAction : ISuggestedAction  
    ```  
  
     两个类都相似，只不过其中一个调用<xref:System.String.ToUpper%2A>和其他调用<xref:System.String.ToLower%2A>。 以下步骤仅说明大写操作类，但你必须实现这两个类。 将实现大写操作的步骤用作实现小写操作的模式。  
  
3.  添加以下 using 语句，这些类：  
  
    ```csharp  
    using Microsoft.VisualStudio.Imaging.Interop;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Documents;  
    using System.Windows.Media;  
  
    ```  
  
4.  声明一组私有字段。  
  
    ```csharp  
    private ITrackingSpan m_span;  
    private string m_upper;  
    private string m_display;  
    private ITextSnapshot m_snapshot;  
    ```  
  
5.  添加设置该字段的构造函数。  
  
    ```csharp  
    public UpperCaseSuggestedAction(ITrackingSpan span)  
    {  
        m_span = span;  
        m_snapshot = span.TextBuffer.CurrentSnapshot;  
        m_upper = span.GetText(m_snapshot).ToUpper();  
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));  
    }  
    ```  
  
6.  实现<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A>方法，以便它显示操作预览。  
  
    ```csharp  
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)  
    {  
        var textBlock = new TextBlock();  
        textBlock.Padding = new Thickness(5);  
        textBlock.Inlines.Add(new Run() { Text = m_upper });  
        return Task.FromResult<object>(textBlock);  
    }  
    ```  
  
7.  实现<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A>方法，以便它返回一个空<xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet>枚举。  
  
    ```csharp  
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)  
    {  
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);  
    }  
    ```  
  
8.  如下所示实现属性。  
  
    ```csharp  
    public bool HasActionSets  
    {  
        get { return false; }  
    }  
    public string DisplayText  
    {  
        get { return m_display; }  
    }  
    public ImageMoniker IconMoniker  
    {  
       get { return default(ImageMoniker); }  
    }  
    public string IconAutomationText  
    {  
        get  
        {  
            return null;  
        }  
    }  
    public string InputGestureText  
    {  
        get  
        {  
            return null;  
        }  
    }  
    public bool HasPreview  
    {  
        get { return true; }  
    }  
    ```  
  
9. 实现<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A>方法通过将范围中的文本替换为其大写等效项。  
  
    ```csharp  
    public void Invoke(CancellationToken cancellationToken)  
    {  
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);  
    }  
    ```  
  
    > [!WARNING]
    >  灯泡操作**Invoke**方法不应显示 UI。  如果你的操作未显示新的用户界面 （例如预览或选择对话框），不会显示直接内从 UI **Invoke**方法但改为计划从返回后显示你的 UI **Invoke**.  
  
10. 若要完成实现，添加`Dispose()`和`TryGetTelemetryId()`方法。  
  
    ```csharp  
    public void Dispose()  
    {  
    }  
  
    public bool TryGetTelemetryId(out Guid telemetryId)  
    {  
        // This is a sample action and doesn't participate in LightBulb telemetry  
        telemetryId = Guid.Empty;  
        return false;  
    }  
    ```  
  
11. 不要忘记将执行相同的操作`LowerCaseSuggestedAction`将显示文本更改为"转换"{0}"为小写"并调用<xref:System.String.ToUpper%2A>到<xref:System.String.ToLower%2A>。  
  
## <a name="building-and-testing-the-code"></a>生成和测试代码  
 若要测试此代码，生成 LightBulbTest 解决方案并在实验实例中运行它。  
  
1.  生成解决方案。  
  
2.  在调试器中运行此项目时，Visual Studio 的第二个实例将进行实例化。  
  
3.  创建一个文本文件并键入一些文本。 你应看到电灯泡左侧的文本。  
  
     ![测试灯泡](../extensibility/media/testlightbulb.png "TestLIghtBulb")  
  
4.  指向电灯泡。 你应看到向下箭头。  
  
5.  当你单击电灯泡时，两个建议的操作应显示，以及预览选定的操作。  
  
     ![测试灯泡，已展开](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")  
  
6.  如果单击第一个操作，则当前单词中的所有文本都将转换为大写。 如果单击第二个操作，则所有文本都将转换为小写。  
  