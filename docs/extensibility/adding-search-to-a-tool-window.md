---
title: "将搜索添加到工具窗口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
caps.latest.revision: 38
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
ms.sourcegitcommit: bca8c87d4f7d89d491fab13e1a511febce81d3d8
ms.openlocfilehash: 845bbc5c34280f7ceafcaa3d763065f6d73388fe
ms.lasthandoff: 02/22/2017

---
# <a name="adding-search-to-a-tool-window"></a>添加到工具窗口搜索
当创建或更新您的扩展中的一个工具窗口时，可以在 Visual Studio 中添加相同的搜索功能在其他位置出现。 此功能包括以下功能︰  
  
-   在工具栏上的自定义区域始终位于一个搜索框。  
  
-   在搜索框本身叠加一个进度指示器。  
  
-   只要输入每个字符 （即时搜索），或者只有在选择 Enter 键 （按需搜索） 后，才显示结果的功能。  
  
-   显示为其已搜索到的最新的术语列表。  
  
-   筛选搜索的特定字段或搜索目标的各个方面的能力。  
  
 通过遵循本演练，您将学习如何执行以下任务︰  
  
1.  创建 VSPackage 项目。  
  
2.  创建一个包含与只读文本框 UserControl 的工具窗口。  
  
3.  将搜索框添加到工具窗口中。  
  
4.  添加搜索实现。  
  
5.  启用即时搜索和显示一个进度栏。  
  
6.  添加**区分大小写**选项。  
  
7.  添加**搜索偶数行仅**筛选器。  
  
## <a name="to-create-a-vsix-project"></a>创建 VSIX 项目  
  
1.  创建一个名为的 VSIX 项目`TestToolWindowSearch`与名为工具窗口**TestSearch**。 如果您需要执行此操作的帮助，请参阅[使用一个工具窗口创建扩展](../extensibility/creating-an-extension-with-a-tool-window.md)。  
  
## <a name="to-create-a-tool-window"></a>若要创建一个工具窗口  
  
1.  在`TestToolWindowSearch`项目中，打开 TestSearchControl.xaml 文件。  
  
2.  替换现有`<StackPanel>`块以与下面的块，也就是添加一个只读的<xref:System.Windows.Controls.TextBox>到<xref:System.Windows.Controls.UserControl>工具窗口中。</xref:System.Windows.Controls.UserControl> </xref:System.Windows.Controls.TextBox>  
  
    ```xaml  
    <StackPanel Orientation="Vertical">  
        <TextBox Name="resultsTextBox" Height="800.0"  
            Width="800.0"  
            IsReadOnly="True">  
        </TextBox>  
    </StackPanel>  
    ```  
  
3.  在 TestSearchControl.xaml.cs 文件中，添加以下 using 语句︰  
  
    ```c#  
    using System.Text;  
    ```  
  
4.  删除`button1_Click()`方法。  
  
     在**TestSearchControl**类中，添加下面的代码。  
  
     此代码将添加一个公共<xref:System.Windows.Controls.TextBox>属性名为**SearchResultsTextBox**和一个名为的公共字符串属性**SearchContent**。</xref:System.Windows.Controls.TextBox> 在构造函数中，SearchResultsTextBox 设置为文本框中，同时 SearchContent 初始化到一组换行分隔的字符串。 文本框中的内容也将初始化为字符串集。  
  
    ```c#  
    public partial class TestSearchControl : UserControl  
    {  
        public TextBox SearchResultsTextBox { get; set; }  
        public string SearchContent { get; set; }  
  
        public TestSearchControl()  
        {  
            InitializeComponent();  
  
            this.SearchResultsTextBox = resultsTextBox;  
            this.SearchContent = BuildContent();  
  
            this.SearchResultsTextBox.Text = this.SearchContent;  
        }  
  
        private string BuildContent()  
        {  
            StringBuilder sb = new StringBuilder();  
            sb.AppendLine("1 go");  
            sb.AppendLine("2 good");  
            sb.AppendLine("3 Go");  
            sb.AppendLine("4 Good");  
            sb.AppendLine("5 goodbye");  
            sb.AppendLine("6 Goodbye");  
  
            return sb.ToString();  
        }  
    }  
    ```  
  
     [!code-cs[ToolWindowSearch&#1;](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs) ] 
     [!code-vb [ToolWindowSearch&#1;](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]  
  
5.  生成项目并启动调试。 将显示 Visual Studio 的实验实例。  
  
6.  在菜单栏上依次选择**视图**，**其他窗口**， **TestSearch**。  
  
     工具窗口中显示，但搜索控件不显示。  
  
## <a name="to-add-a-search-box-to-the-tool-window"></a>若要将搜索框添加到工具窗口  
  
1.  在 TestSearch.cs 文件中，添加以下代码到`TestSearch`类。 该代码重写<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>属性，以便 get 访问器返回`true`。</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>  
  
     若要启用搜索，必须重写<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>属性。</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>类实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch>，并提供一个默认实现，不能通过搜索。</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> </xref:Microsoft.VisualStudio.Shell.ToolWindowPane>  
  
    ```c#  
    public override bool SearchEnabled  
    {  
        get { return true; }  
    }  
    ```  
  
2.  生成项目并启动调试。 将显示的实验实例。  
  
3.  在 Visual Studio 的实验实例中，打开**TestSearch**。  
  
     在工具窗口的顶部，将出现与的搜索控件**搜索**水印和放大玻璃图标。 但是，搜索不工作，还因为尚未实现对搜索过程。  
  
## <a name="to-add-the-search-implementation"></a>若要添加的搜索实现  
 如果在启用搜索<xref:Microsoft.VisualStudio.Shell.ToolWindowPane>，如在上一过程中，工具窗口创建搜索主机。</xref:Microsoft.VisualStudio.Shell.ToolWindowPane> 该主机将设置和管理搜索过程，始终在后台线程发生。 因为<xref:Microsoft.VisualStudio.Shell.ToolWindowPane>类管理搜索主机和设置创建向上搜索的只需要创建搜索任务，然后提供搜索方法。</xref:Microsoft.VisualStudio.Shell.ToolWindowPane> 搜索过程发生在后台线程，并在 UI 线程上发生了对工具窗口控件调用。 因此，必须使用<xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>方法来管理在该控件处理中所做的任何调用。</xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>  
  
1.  在 TestSearch.cs 文件中，添加以下`using`语句︰  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.Runtime.InteropServices;  
    using System.Text;  
    using System.Windows.Controls;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.PlatformUI;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
2.  在`TestSearch`类中，添加下面的代码执行下列操作︰  
  
    -   重写<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch>方法来创建搜索任务。</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch>  
  
    -   重写<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A>方法，以还原文本框中的状态。</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> 当用户取消搜索任务和用户设置或取消设置选项或筛选器时，调用此方法。 同时<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A>在 UI 线程上调用。</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> 因此，您不需要访问通过文本框<xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>方法。</xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>  
  
    -   创建一个类的名为`TestSearchTask`继承自<xref:Microsoft.VisualStudio.Shell.VsSearchTask>该属性提供<xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>。</xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>的默认实现，</xref:Microsoft.VisualStudio.Shell.VsSearchTask>  
  
         在`TestSearchTask`，该构造函数设置引用工具窗口中的私有字段。 若要提供的搜索方法，重写<xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>和<xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A>方法。</xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> </xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>方法就是其中实现了搜索进程。</xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> 此过程包括执行搜索，在文本框中显示搜索结果以及调用此方法以报告完成搜索后的基类实现。  
  
    ```c#  
    public override IVsSearchTask CreateSearch(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback)  
    {  
        if (pSearchQuery == null || pSearchCallback == null)  
            return null;  
         return new TestSearchTask(dwCookie, pSearchQuery, pSearchCallback, this);  
    }  
  
    public override void ClearSearch()  
    {  
        TestSearchControl control = (TestSearchControl)this.Content;  
        control.SearchResultsTextBox.Text = control.SearchContent;  
    }  
  
    internal class TestSearchTask : VsSearchTask  
    {  
        private TestSearch m_toolWindow;  
  
        public TestSearchTask(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback, TestSearch toolwindow)  
            : base(dwCookie, pSearchQuery, pSearchCallback)  
        {  
            m_toolWindow = toolwindow;  
        }  
  
        protected override void OnStartSearch()  
        {  
            // Use the original content of the text box as the target of the search.   
            var separator = new string[] { Environment.NewLine };  
            TestSearchControl control = (TestSearchControl)m_toolWindow.Content;  
            string[] contentArr = control.SearchContent.Split(separator, StringSplitOptions.None);  
  
            // Get the search option.   
            bool matchCase = false;  
            // matchCase = m_toolWindow.MatchCaseOption.Value;   
  
                // Set variables that are used in the finally block.  
                StringBuilder sb = new StringBuilder("");  
                uint resultCount = 0;  
                this.ErrorCode = VSConstants.S_OK;  
  
                try  
                {  
                    string searchString = this.SearchQuery.SearchString;  
  
                    // Determine the results.   
                    uint progress = 0;  
                    foreach (string line in contentArr)  
                    {  
                        if (matchCase == true)  
                        {  
                            if (line.Contains(searchString))  
                            {  
                                sb.AppendLine(line);  
                                resultCount++;  
                            }  
                        }  
                        else  
                            {  
                                if (line.ToLower().Contains(searchString.ToLower()))  
                                {  
                                    sb.AppendLine(line);  
                                    resultCount++;  
                                }  
                            }  
  
                            // SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));   
  
                            // Uncomment the following line to demonstrate the progress bar.   
                            // System.Threading.Thread.Sleep(100);  
                        }  
                    }  
                    catch (Exception e)  
                    {  
                        this.ErrorCode = VSConstants.E_FAIL;  
                    }  
                    finally  
                    {  
                        ThreadHelper.Generic.Invoke(() =>  
                        { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });  
  
                        this.SearchResults = resultCount;  
                    }  
  
            // Call the implementation of this method in the base class.   
            // This sets the task status to complete and reports task completion.   
            base.OnStartSearch();  
        }  
  
        protected override void OnStopSearch()  
        {  
            this.SearchResults = 0;  
        }  
    }  
    ```  
  
3.  通过执行以下步骤来测试您搜索的实现︰  
  
    1.  重新生成项目并启动调试。  
  
    2.  在 Visual Studio 的实验实例中，再次打开工具窗口、 搜索窗口中输入一些搜索文本和单击 ENTER。  
  
         应显示正确的结果。  
  
## <a name="to-customize-the-search-behavior"></a>若要自定义搜索行为  
 通过更改搜索设置，可以在搜索控件的显示方式和搜索执行方式进行各种更改。 例如，可以更改水印 （在搜索框中显示的默认文本）、 所需的最低和最大宽度的搜索控件，以及是否显示一个进度栏。 此外可以更改的点开始 （按需或即时搜索中） 显示的搜索结果以及是否显示为其最近搜索到的术语列表。 可以在<xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource>类</xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource>中找到设置的完整的列表  
  
1.  在 TestSearch.cs 文件中，添加以下代码到`TestSearch`类。 此代码启用即时搜索而不是按需搜索 （用户无需单击输入的含义）。 该代码重写`ProvideSearchSettings`中的方法`TestSearch`类，该类是需要更改默认设置。  
  
    ```c#  
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)  
    {  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchStartTypeProperty.Name,   
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}  
    ```  
  
2.  测试新设置重新生成解决方案并重新启动调试器。  
  
     搜索结果将显示每次您在搜索框中输入一个字符。  
  
3.  在`ProvideSearchSettings`方法中，添加以下行，可以显示一个进度栏。  
  
    ```c#  
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)  
    {  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchStartTypeProperty.Name,   
             (uint)VSSEARCHSTARTTYPE.SST_INSTANT);  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchProgressTypeProperty.Name,   
             (uint)VSSEARCHPROGRESSTYPE.SPT_DETERMINATE);  
    }  
    ```  
  
     若要显示的进度条，必须报告进度。 若要报告进度，请取消注释下面的代码`OnStartSearch`方法`TestSearchTask`类︰  
  
    ```c#  
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));  
    ```  
  
4.  缓慢足够的处理进度条是否可见，请取消注释中的以下行将`OnStartSearch`方法`TestSearchTask`类︰  
  
    ```c#  
    System.Threading.Thread.Sleep(100);  
    ```  
  
5.  通过重新生成解决方案并启动到 debugb 测试新的设置。  
  
     进度栏出现在搜索窗口 （作为一条蓝线下方的搜索文本框） 每次执行搜索。  
  
## <a name="to-enable-users-to-refine-their-searches"></a>若要使用户能够改进其搜索  
 您可以允许用户以如通过选项来优化其搜索**区分大小写**或**全字匹配**。 选项可以是布尔值，它显示为复选框或显示为按钮的命令。 对于本演练，你将创建一个布尔值的选项。  
  
1.  在 TestSearch.cs 文件中，添加以下代码到`TestSearch`类。 该代码重写`SearchOptionsEnum`方法，它允许搜索实现来检测到给定的选项是开还是关。 中的代码`SearchOptionsEnum`中添加一个选项以匹配用例与<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions>枚举器。</xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> 区分大小写的选项都还可作为`MatchCaseOption`属性。  
  
    ```c#  
    private IVsEnumWindowSearchOptions m_optionsEnum;  
    public override IVsEnumWindowSearchOptions SearchOptionsEnum  
    {  
        get  
        {  
            if (m_optionsEnum == null)  
            {  
                List<IVsWindowSearchOption> list = new List<IVsWindowSearchOption>();  
  
                list.Add(this.MatchCaseOption);  
  
                m_optionsEnum = new WindowSearchOptionEnumerator(list) as IVsEnumWindowSearchOptions;  
            }  
            return m_optionsEnum;  
        }  
    }  
  
    private WindowSearchBooleanOption m_matchCaseOption;  
    public WindowSearchBooleanOption MatchCaseOption  
    {  
        get  
        {  
            if (m_matchCaseOption == null)  
            {  
                m_matchCaseOption = new WindowSearchBooleanOption("Match case", "Match case", false);  
            }  
            return m_matchCaseOption;  
        }  
    }  
    ```  
  
2.  在`TestSearchTask`类中，取消注释中的 matchCase 行`OnStartSearch`方法︰  
  
    ```c#  
    private IVsEnumWindowSearchOptions m_optionsEnum;  
    public override IVsEnumWindowSearchOptions SearchOptionsEnum  
    {  
        get  
        {  
            if (m_optionsEnum == null)  
            {  
                List<IVsWindowSearchOption> list = new List<IVsWindowSearchOption>();  
  
                list.Add(this.MatchCaseOption);  
  
                m_optionsEnum = new WindowSearchOptionEnumerator(list) as IVsEnumWindowSearchOptions;  
            }  
            return m_optionsEnum;  
        }  
    }  
  
    private WindowSearchBooleanOption m_matchCaseOption;  
    public WindowSearchBooleanOption MatchCaseOption  
    {  
        get  
         {  
            if (m_matchCaseOption == null)  
            {  
                m_matchCaseOption = new WindowSearchBooleanOption("Match case", "Match case", false);  
            }  
            return m_matchCaseOption;  
        }  
    }  
    ```  
  
3.  测试选项︰  
  
    1.  生成项目并启动调试。 将显示的实验实例。  
  
    2.  在工具窗口中，选择文本框右侧的向下箭头。  
  
         **区分大小写**显示复选框。  
  
    3.  选择**区分大小写**复选框，然后再执行某些搜索。  
  
## <a name="to-add-a-search-filter"></a>若要添加的搜索筛选器  
 您可以添加允许用户优化的搜索目标组的搜索筛选器。 例如，您可以按依据其进行了修改最新的日期和各个文件扩展名筛选文件资源管理器中的文件。 在本演练中，您将添加甚至只为行筛选器。 当用户选择该筛选器时，搜索主机会将您指定的字符串添加到搜索查询。 然后可以识别这些字符串内搜索方法，并相应地进行筛选的搜索目标。  
  
1.  在 TestSearch.cs 文件中，添加以下代码到`TestSearch`类。 该代码会实施`SearchFiltersEnum`通过添加<xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter>，指定要筛选搜索结果，以便只偶数行显示。</xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter>  
  
    ```c#  
    public override IVsEnumWindowSearchFilters SearchFiltersEnum  
    {  
        get  
        {  
            List<IVsWindowSearchFilter> list = new List<IVsWindowSearchFilter>();  
            list.Add(new WindowSearchSimpleFilter("Search even lines only", "Search even lines only", "lines", "even"));  
            return new WindowSearchFilterEnumerator(list) as IVsEnumWindowSearchFilters;  
        }  
    }  
  
    ```  
  
     现在，搜索控件显示的搜索筛选器`Search even lines only`。 当用户选择的筛选器，该字符串`lines:"even"`出现在搜索框。 其他搜索条件可以出现在同一时间作为筛选器。 搜索字符串后和 / 或筛选器中，情况下可能出现在筛选器中之前,。  
  
2.  在 TestSearch.cs 文件中，添加以下方法向`TestSearchTask`类，该类是在`TestSearch`类。 这些方法还支持`OnStartSearch`方法，您将在下一步，修改。  
  
    ```c#  
    private string RemoveFromString(string origString, string stringToRemove)  
    {  
        int index = origString.IndexOf(stringToRemove);  
        if (index == -1)  
            return origString;  
        else   
             return (origString.Substring(0, index) + origString.Substring(index + stringToRemove.Length)).Trim();  
    }  
  
    private string[] GetEvenItems(string[] contentArr)  
    {  
        int length = contentArr.Length / 2;  
        string[] evenContentArr = new string[length];  
  
        int indexB = 0;  
        for (int index = 1; index < contentArr.Length; index += 2)  
        {  
            evenContentArr[indexB] = contentArr[index];  
            indexB++;  
        }  
  
        return evenContentArr;  
    }  
    ```  
  
3.  在`TestSearchTask`类中，更新`OnStartSearch`方法替换为以下代码。 这一更改更新代码以支持该筛选器。  
  
    ```c#  
    protected override void OnStartSearch()  
    {  
        // Use the original content of the text box as the target of the search.   
        var separator = new string[] { Environment.NewLine };  
        string[] contentArr = ((TestSearchControl)m_toolWindow.Content).SearchContent.Split(separator, StringSplitOptions.None);  
  
        // Get the search option.   
        bool matchCase = false;  
        matchCase = m_toolWindow.MatchCaseOption.Value;  
  
        // Set variables that are used in the finally block.  
        StringBuilder sb = new StringBuilder("");  
        uint resultCount = 0;  
        this.ErrorCode = VSConstants.S_OK;  
  
        try  
        {  
            string searchString = this.SearchQuery.SearchString;  
  
            // If the search string contains the filter string, filter the content array.   
            string filterString = "lines:\"even\"";  
  
            if (this.SearchQuery.SearchString.Contains(filterString))  
            {  
                // Retain only the even items in the array.  
                contentArr = GetEvenItems(contentArr);  
  
                // Remove 'lines:"even"' from the search string.  
                searchString = RemoveFromString(searchString, filterString);  
            }  
  
            // Determine the results.   
            uint progress = 0;  
            foreach (string line in contentArr)  
            {  
                if (matchCase == true)  
                {  
                    if (line.Contains(searchString))  
                    {  
                        sb.AppendLine(line);  
                        resultCount++;  
                    }  
                }  
                else  
                {  
                    if (line.ToLower().Contains(searchString.ToLower()))  
                    {  
                        sb.AppendLine(line);  
                        resultCount++;  
                    }  
                }  
  
                SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));  
  
                // Uncomment the following line to demonstrate the progress bar.   
                // System.Threading.Thread.Sleep(100);  
            }  
        }  
        catch (Exception e)  
        {  
            this.ErrorCode = VSConstants.E_FAIL;  
        }  
        finally  
        {  
            ThreadHelper.Generic.Invoke(() =>  
            { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });  
  
            this.SearchResults = resultCount;  
        }  
  
        // Call the implementation of this method in the base class.   
        // This sets the task status to complete and reports task completion.   
        base.OnStartSearch();  
    }  
    ```  
  
4.  测试您的代码。  
  
5.  生成项目并启动调试。 在 Visual Studio 的实验实例中，打开工具窗口，然后选择搜索控件上的向下箭头。  
  
     **区分大小写**复选框和**搜索偶数行仅**筛选器应显示。  
  
6.  选择筛选器。  
  
     搜索框包含**行:"偶数"**，并且显示以下结果︰  
  
     2 工作正常  
  
     4 良好  
  
     6 再见  
  
7.  删除`lines:"even"`从搜索框中，选择**区分大小写**复选框，然后再输入`g`搜索框中。  
  
     显示以下结果︰  
  
     1 转到  
  
     2 工作正常  
  
     5 再见  
  
8.  选择搜索框右侧的 X。  
  
     清除搜索，并显示原始内容。 但是，**区分大小写**复选框仍处于选中状态。
