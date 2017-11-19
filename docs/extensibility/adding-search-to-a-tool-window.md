---
title: "添加到工具窗口搜索 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
caps.latest.revision: "38"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4f30c28b7255769be97ba6063e7c1ce435dfbe9f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="adding-search-to-a-tool-window"></a>添加到工具窗口搜索
当创建或更新你的扩展中的工具窗口时，可以在 Visual Studio 中添加其他位置出现的相同的搜索功能。 此功能包括以下功能：  
  
-   在工具栏上的自定义区域内始终位于一个搜索框。  
  
-   在搜索框本身叠加进度指示器。  
  
-   能够显示的结果，就会立即输入每个字符 （即时搜索） 或仅后选择 Enter 键 （按需搜索）。  
  
-   一个列表，显示为其已搜索最新的条款。  
  
-   筛选搜索特定字段或搜索目标的方面的能力。  
  
 通过完成本演练，您将学习如何执行以下任务：  
  
1.  创建 VSPackage 项目。  
  
2.  创建工具窗口，其中包含与只读文本框 UserControl。  
  
3.  将一个搜索框添加到工具窗口。  
  
4.  添加搜索实现。  
  
5.  启用即时搜索和显示一个进度栏。  
  
6.  添加**区分大小写**选项。  
  
7.  添加**搜索偶数行仅**筛选器。  
  
## <a name="to-create-a-vsix-project"></a>创建 VSIX 项目  
  
1.  创建一个名为的 VSIX 项目`TestToolWindowSearch`与名为工具窗口**TestSearch**。 如果你需要执行此操作的帮助，请参阅[使用工具窗口创建扩展](../extensibility/creating-an-extension-with-a-tool-window.md)。  
  
## <a name="to-create-a-tool-window"></a>若要创建工具窗口  
  
1.  在`TestToolWindowSearch`项目中，打开 TestSearchControl.xaml 文件。  
  
2.  将现有`<StackPanel>`块以与以下块，将添加一个只读的<xref:System.Windows.Controls.TextBox>到<xref:System.Windows.Controls.UserControl>工具窗口中。  
  
    ```xaml  
    <StackPanel Orientation="Vertical">  
        <TextBox Name="resultsTextBox" Height="800.0"  
            Width="800.0"  
            IsReadOnly="True">  
        </TextBox>  
    </StackPanel>  
    ```  
  
3.  在 TestSearchControl.xaml.cs 文件中，添加以下 using 语句：  
  
    ```csharp  
    using System.Text;  
    ```  
  
4.  删除`button1_Click()`方法。  
  
     在**TestSearchControl**类中，添加下面的代码。  
  
     此代码将添加一个公共<xref:System.Windows.Controls.TextBox>属性名为**SearchResultsTextBox**和名为的公共字符串属性**SearchContent**。 在构造函数中，SearchResultsTextBox 设置文本框中，为和 SearchContent 初始化为一组换行分隔的字符串。 文本框的内容也将初始化为组的字符串。  
  
    ```csharp  
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
  
     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]  
  
5.  生成项目并启动调试。 将显示 Visual Studio 的实验实例。  
  
6.  在菜单栏上，选择**视图**，**其他窗口**， **TestSearch**。  
  
     工具窗口随即出现，但未尚未显示搜索控件。  
  
## <a name="to-add-a-search-box-to-the-tool-window"></a>若要将一个搜索框添加到工具窗口  
  
1.  在 TestSearch.cs 文件中，添加以下代码到`TestSearch`类。 该代码重写<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>属性以便 get 访问器返回`true`。  
  
     若要启用搜索，必须重写<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>属性。 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>类实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch>并提供一个默认实现，不启用搜索。  
  
    ```csharp  
    public override bool SearchEnabled  
    {  
        get { return true; }  
    }  
    ```  
  
2.  生成项目并启动调试。 实验实例中出现。  
  
3.  在 Visual Studio 的实验实例中，打开**TestSearch**。  
  
     在工具窗口的顶部，将显示使用的搜索控件**搜索**水印和放大玻璃图标。 但是，搜索不起作用因为搜索过程尚未实现。  
  
## <a name="to-add-the-search-implementation"></a>添加搜索实现  
 当您在上启用搜索<xref:Microsoft.VisualStudio.Shell.ToolWindowPane>，如前面的过程中，在工具窗口创建搜索主机。 此主机将设置和管理搜索进程，始终在后台线程发生。 因为<xref:Microsoft.VisualStudio.Shell.ToolWindowPane>类管理搜索主机和设置创建向上搜索的只需要创建搜索任务，并提供搜索方法。 搜索过程后台线程，并且对工具窗口控件的调用会在 UI 线程上发生。 因此，你必须使用<xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>方法来管理在与控件的处理中所做的任何调用。  
  
1.  在 TestSearch.cs 文件中，添加以下`using`语句：  
  
    ```csharp  
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
  
2.  在`TestSearch`类中，添加以下代码，执行下列操作：  
  
    -   重写<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A>方法来创建搜索任务。  
  
    -   重写<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A>方法，使还原的文本框中的状态。 当用户取消搜索任务和用户设置或取消设置选项或筛选器时调用此方法。 同时<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A>在 UI 线程上调用程序。 因此，你不需要访问通过文本框<xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>方法。  
  
    -   创建名为的类`TestSearchTask`继承自<xref:Microsoft.VisualStudio.Shell.VsSearchTask>，该属性提供的默认实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>。  
  
         在`TestSearchTask`，构造函数设置引用该工具窗口的私有字段。 若要提供搜索方法，重写<xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>和<xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A>方法。 <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>方法是实现搜索过程的位置。 此过程包括执行搜索，在文本框中显示搜索结果，并调用此方法来报告搜索已完成的基类实现。  
  
    ```csharp  
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
  
3.  通过执行以下步骤测试你搜索的实现：  
  
    1.  重新生成项目并启动调试。  
  
    2.  在 Visual Studio 的实验实例中，再次打开工具窗口，在搜索窗口中，输入一些搜索文本，单击 ENTER。  
  
         应显示正确的结果。  
  
## <a name="to-customize-the-search-behavior"></a>若要自定义搜索行为  
 通过更改搜索设置，可以在搜索控件的显示方式和搜索执行方式进行各种更改。例如，你可以更改水印 （在搜索框中显示的默认文本）、 所需的最低和最大宽度的搜索控件，以及是否显示一个进度栏。 你还可以更改在哪些搜索结果开始显示 （按需或即时搜索），以及是否显示为其你最近搜索的术语的列表的点。 你可以找到中设置的完整列表<xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource>类。  
  
1.  在 TestSearch.cs 文件中，添加以下代码到`TestSearch`类。 此代码使即时搜索而不是按需搜索 （用户无需单击输入的含义）。 该代码重写`ProvideSearchSettings`中的方法`TestSearch`类，该类是需要更改默认设置。  
  
    ```csharp  
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)  
    {  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchStartTypeProperty.Name,   
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}  
    ```  
  
2.  测试新设置重新生成解决方案并重新启动调试器。  
  
     搜索结果将显示每次您的搜索框中输入一个字符。  
  
3.  在`ProvideSearchSettings`方法，添加以下行，允许一个进度栏显示。  
  
    ```csharp  
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
  
     进度栏显示，必须报告进度。 若要报告进度，取消注释下面的代码`OnStartSearch`方法`TestSearchTask`类：  
  
    ```csharp  
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));  
    ```  
  
4.  缓慢处理足够，进度栏可见时，取消注释以下行中的`OnStartSearch`方法`TestSearchTask`类：  
  
    ```csharp  
    System.Threading.Thread.Sleep(100);  
    ```  
  
5.  通过重新生成解决方案并启动到 debugb 测试新的设置。  
  
     进度栏出现在搜索窗口 （作为搜索文本框下面一条蓝线） 每次执行的搜索。  
  
## <a name="to-enable-users-to-refine-their-searches"></a>若要使用户能够优化其搜索  
 你可以允许用户如通过选项来优化其搜索**区分大小写**或**全字匹配**。 选项可将布尔值、 其显示为复选框或显示为按钮的命令。 对于本演练，你将创建一个 boolean 类型的值的选项。  
  
1.  在 TestSearch.cs 文件中，添加以下代码到`TestSearch`类。 该代码重写`SearchOptionsEnum`方法，它允许要检测给定的选项是打开还是关闭的搜索实现。 中的代码`SearchOptionsEnum`中添加一个选项以匹配用例与<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions>枚举器。 匹配大小写的选项都还可作为`MatchCaseOption`属性。  
  
    ```csharp  
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
  
2.  在`TestSearchTask`类，取消注释中的 matchCase 行`OnStartSearch`方法：  
  
    ```csharp  
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
  
3.  测试选项：  
  
    1.  生成项目并启动调试。 实验实例中出现。  
  
    2.  在工具窗口中，选择文本框右侧的向下箭头。  
  
         **区分大小写**显示复选框。  
  
    3.  选择**区分大小写**复选框，以及然后执行某些搜索。  
  
## <a name="to-add-a-search-filter"></a>添加搜索筛选器  
 你可以添加允许用户优化的搜索目标组的搜索筛选器。 例如，你可以按依据其进行了修改最近的日期和其文件扩展名筛选在文件资源管理器中的文件。 在此演练中，你将添加仅偶数行的筛选器。 当用户选择该筛选器时，搜索主机会将你指定的字符串添加到搜索查询。 然后，可以确定这些字符串内搜索方法，并相应地筛选的搜索目标。  
  
1.  在 TestSearch.cs 文件中，添加以下代码到`TestSearch`类。 该代码会实施`SearchFiltersEnum`通过添加<xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter>，指定要筛选搜索结果，以便仅偶数行显示。  
  
    ```csharp  
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
  
     现在搜索控件中显示搜索筛选器`Search even lines only`。 当用户选择的筛选器，该字符串`lines:"even"`出现在搜索框中。 其他搜索条件可以出现在同一时间作为筛选器。 搜索字符串后筛选器，或两个情况下可能出现在筛选器之前,。  
  
2.  在 TestSearch.cs 文件中，添加以下方法`TestSearchTask`类，该类在`TestSearch`类。 这些方法支持`OnStartSearch`方法，你将在下一步，修改。  
  
    ```csharp  
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
  
3.  在`TestSearchTask`类中，更新`OnStartSearch`方法替换为以下代码。 此更改更新代码以支持筛选器。  
  
    ```csharp  
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
  
4.  测试你的代码。  
  
5.  生成项目并启动调试。 在 Visual Studio 的实验实例中，打开工具窗口中，，然后选择搜索控件上的向下箭头。  
  
     **区分大小写**复选框和**搜索偶数行仅**筛选器应显示。  
  
6.  选择筛选器。  
  
     搜索框中包含**行:"甚至"**，并会显示以下结果：  
  
     2 良好  
  
     4 良好  
  
     6 goodbye  
  
7.  删除`lines:"even"`在搜索框中，选择**区分大小写**复选框，，然后输入`g`的搜索框中。  
  
     将显示以下结果：  
  
     1 转  
  
     2 良好  
  
     5 goodbye  
  
8.  选择搜索框右侧的 X。  
  
     搜索被清除，并且原始内容显示。 但是，**区分大小写**复选框仍处于选中状态。