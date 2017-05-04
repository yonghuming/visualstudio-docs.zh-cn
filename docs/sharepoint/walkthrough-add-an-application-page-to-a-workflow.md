---
title: "演练：向工作流中添加应用程序页 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "应用程序页 [Visual Studio 中的 SharePoint 开发]"
  - "Visual Studio 中的 SharePoint 开发, 向工作流添加应用程序页"
ms.assetid: e4845d07-917b-45cb-a569-4ecdd602fbd9
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# 演练：向工作流中添加应用程序页
  本演练演示如何将显示派生自工作流的数据的应用程序页添加到工作流项目中。  本演练是基于[演练：创建带有关联窗体和启动窗体的工作流](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)主题中描述的项目构建的。  
  
 本演练将演示以下任务：  
  
-   将 ASPX 应用程序页添加到 SharePoint 工作流项目中。  
  
-   从工作流项目中获取数据并操作数据。  
  
-   在应用程序页上的表中显示数据。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 系统必备  
 你需要以下组件来完成本演练：  
  
-   支持的 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] 和 SharePoint 版本。  有关详细信息，请参阅[开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
-   还必须完成[演练：创建带有关联窗体和启动窗体的工作流](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)主题中的项目。  
  
## 修改工作流代码  
 首先，向工作流中添加一行代码，以将“Outcome”（结果）列的值设置为零用金报销单上显示的金额。  以后会在零用金报销单汇总计算中用到此值。  
  
#### 设置工作流中的“Outcome”（结果）列的值  
  
1.  将在[演练：创建带有关联窗体和启动窗体的工作流](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)主题中完成的项目加载到 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  打开 Workflow1.cs 代码或 Workflow1.vb 代码（具体取决于您的编程语言）。  
  
3.  将以下代码添加到 `createTask1_MethodInvoking` 方法的底部：  
  
    ```vb  
    createTask1_TaskProperties1.ExtendedProperties("Outcome") =   
      workflowProperties.InitiationData  
    ```  
  
    ```csharp  
    createTask1_TaskProperties1.ExtendedProperties["Outcome"] =   
      workflowProperties.InitiationData;  
    ```  
  
## 创建应用程序页  
 接下来，向项目中添加 ASPX 窗体。  此窗体将显示从零用金报销单工作流项目中获取的数据。  为此，将添加一个应用程序页。  应用程序页使用与其他 SharePoint 页相同的母版页，这意味着应用程序页将与 SharePoint 网站上的其他页类似。  
  
#### 向项目中添加应用程序页  
  
1.  选择 ExpenseReport 项目，然后在菜单栏上，选择 “项目”，“添加新项”。  
  
2.  在 **模板** 窗格中，选择 **应用程序页** 模板，为项目项 \(**ApplicaitonPage1.aspx**\)使用默认名称，然后选择 **添加** 按钮。  
  
3.  在 ApplicationPage1.aspx 的 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 中，用以下代码替换 `PlaceHolderMain` 部分：  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
        <asp:Label ID="Label1" runat="server" Font-Bold="True"   
            Text="Expenses that exceeded allotted amount" Font-Size="Medium"></asp:Label>  
        <br />  
        <asp:Table ID="Table1" runat="server">  
        </asp:Table>  
    </asp:Content>  
    ```  
  
     此代码将表和标题一起添加到页面中。  
  
4.  通过用以下代码替换 `PlaceHolderPageTitleInTitleArea` 部分，将标题添加到应用程序页中：  
  
    ```  
    <asp:Content ID="PageTitleInTitleArea" ContentPlaceHolderID="PlaceHolderPageTitleInTitleArea" runat="server" >  
        Expense Report Summary  
    </asp:Content>  
    ```  
  
## 编写应用程序页代码  
 接下来，向零用金报销单汇总应用程序页中添加代码。  当打开该页时，代码将扫描 SharePoint 中的任务列表，以找出超出分配的开支限制的零用金。  报表将每一项与零用金总计一起列出。  
  
#### 编写应用程序页代码  
  
1.  选择**“ApplicationPage1.aspx”**节点，在菜单上选择**“视图”“代码”**，以显示应用程序页背后的代码。  
  
2.  用以下代码替换类顶部的 **using** 或 **Import** 语句（具体取决于您的编程语言）：  
  
    ```vb  
    Imports System  
    Imports Microsoft.SharePoint  
    Imports Microsoft.SharePoint.WebControls  
    Imports System.Collections  
    Imports System.Data  
    Imports System.Web.UI  
    Imports System.Web.UI.WebControls  
    Imports System.Web.UI.WebControls.WebParts  
    Imports System.Drawing  
    Imports Microsoft.SharePoint.Navigation  
    ```  
  
    ```csharp  
    using System;  
    using Microsoft.SharePoint;  
    using Microsoft.SharePoint.WebControls;  
    using System.Collections;  
    using System.Data;  
    using System.Web.UI;  
    using System.Web.UI.WebControls;  
    using System.Web.UI.WebControls.WebParts;  
    using System.Drawing;  
    using Microsoft.SharePoint.Navigation;  
    ```  
  
3.  将以下代码添加到 `Page_Load` 方法中：  
  
    ```vb  
    Try  
        ' Reference the Tasks list on the SharePoint site.  
        ' Replace "TestServer" with a valid SharePoint server name.  
        Dim site As SPSite = New SPSite("http://TestServer")  
        Dim list As SPList = site.AllWebs(0).Lists("Tasks")  
        ' string text = "";  
        Dim sum As Integer = 0  
        Table1.Rows.Clear()  
        ' Add table headers.  
        Dim hr As TableHeaderRow = New TableHeaderRow  
        hr.BackColor = Color.LightBlue  
        Dim hc1 As TableHeaderCell = New TableHeaderCell  
        Dim hc2 As TableHeaderCell = New TableHeaderCell  
        hc1.Text = "Expense Report Name"  
        hc2.Text = "Amount Exceeded"  
        hr.Cells.Add(hc1)  
        hr.Cells.Add(hc2)  
        ' Add the TableHeaderRow as the first item   
        ' in the Rows collection of the table.  
        Table1.Rows.AddAt(0, hr)  
        ' Iterate through the tasks in the Task list and collect those    
        ' that have values in the "Related Content" and "Outcome" fields   
        ' - the fields written to when expense approval is required.  
        For Each item As SPListItem In list.Items  
            Dim s_relContent As String = ""  
            Dim s_outcome As String = ""  
            Try  
                ' Task has the fields - treat as expense report.  
                s_relContent = item.GetFormattedValue("Related Content")  
                s_outcome = item.GetFormattedValue("Outcome")  
            Catch erx As System.Exception  
                ' Task does not have fields - skip it.  
                Continue For  
            End Try  
            ' Convert amount to an int and keep a running total.  
            If (Not String.IsNullOrEmpty(s_relContent) And Not   
              String.IsNullOrEmpty(s_outcome)) Then  
                sum = (sum + Convert.ToInt32(s_outcome))  
                Dim relContent As TableCell = New TableCell  
                relContent.Text = s_relContent  
                Dim outcome As TableCell = New TableCell  
                outcome.Text = ("$" + s_outcome)  
                Dim dataRow2 As TableRow = New TableRow  
                dataRow2.Cells.Add(relContent)  
                dataRow2.Cells.Add(outcome)  
                Table1.Rows.Add(dataRow2)  
            End If  
        Next  
        ' Report the sum of the reports in the table footer.  
        Dim tfr As TableFooterRow = New TableFooterRow  
        tfr.BackColor = Color.LightGreen  
        ' Create a TableCell object to contain the   
        ' text for the footer.  
        Dim ftc1 As TableCell = New TableCell  
        Dim ftc2 As TableCell = New TableCell  
        ftc1.Text = "TOTAL: "  
        ftc2.Text = ("$" + Convert.ToString(sum))  
        ' Add the TableCell object to the Cells  
        ' collection of the TableFooterRow.  
        tfr.Cells.Add(ftc1)  
        tfr.Cells.Add(ftc2)  
        ' Add the TableFooterRow to the Rows  
        ' collection of the table.  
        Table1.Rows.Add(tfr)  
    Catch errx As Exception  
        System.Diagnostics.Debug.WriteLine(("Error: " + errx.ToString))  
    End Try  
    ```  
  
    ```csharp  
    try  
    {  
        // Reference the Tasks list on the SharePoint site.  
        // Replace "TestServer" with a valid SharePoint server name.  
        SPSite site = new SPSite("http://TestServer");  
        SPList list = site.AllWebs[0].Lists["Tasks"];  
  
        // string text = "";  
        int sum = 0;  
  
        Table1.Rows.Clear();  
  
        // Add table headers.  
        TableHeaderRow hr = new TableHeaderRow();  
        hr.BackColor = Color.LightBlue;  
        TableHeaderCell hc1 = new TableHeaderCell();  
        TableHeaderCell hc2 = new TableHeaderCell();  
        hc1.Text = "Expense Report Name";  
        hc2.Text = "Amount Exceeded";  
        hr.Cells.Add(hc1);  
        hr.Cells.Add(hc2);  
        // Add the TableHeaderRow as the first item   
        // in the Rows collection of the table.  
        Table1.Rows.AddAt(0, hr);  
  
        // Iterate through the tasks in the Task list and collect those   
        // that have values in the "Related Content" and "Outcome"   
        // fields - the fields written to when expense approval is   
        // required.  
        foreach (SPListItem item in list.Items)  
        {  
            string s_relContent = "";  
            string s_outcome = "";  
  
            try  
            {  
                // Task has the fields - treat as expense report.  
                s_relContent = item.GetFormattedValue("Related   
                  Content");  
                s_outcome = item.GetFormattedValue("Outcome");  
            }  
            catch  
            {  
                // Task does not have fields - skip it.  
                continue;  
            }  
  
            if (!String.IsNullOrEmpty(s_relContent) &&   
              !String.IsNullOrEmpty(s_outcome))  
            {  
                // Convert amount to an int and keep a running total.  
                sum += Convert.ToInt32(s_outcome);  
                TableCell relContent = new TableCell();  
                relContent.Text = s_relContent;  
                TableCell outcome = new TableCell();  
                outcome.Text = "$" + s_outcome;  
                TableRow dataRow2 = new TableRow();  
                dataRow2.Cells.Add(relContent);  
                dataRow2.Cells.Add(outcome);  
                Table1.Rows.Add(dataRow2);  
            }  
        }  
  
        // Report the sum of the reports in the table footer.  
           TableFooterRow tfr = new TableFooterRow();  
        tfr.BackColor = Color.LightGreen;  
  
        // Create a TableCell object to contain the   
        // text for the footer.  
        TableCell ftc1 = new TableCell();  
        TableCell ftc2 = new TableCell();  
        ftc1.Text = "TOTAL: ";  
        ftc2.Text = "$" + Convert.ToString(sum);  
  
        // Add the TableCell object to the Cells  
        // collection of the TableFooterRow.  
        tfr.Cells.Add(ftc1);  
        tfr.Cells.Add(ftc2);  
  
        // Add the TableFooterRow to the Rows  
        // collection of the table.  
        Table1.Rows.Add(tfr);  
    }  
  
    catch (Exception errx)  
    {  
        System.Diagnostics.Debug.WriteLine("Error: " + errx.ToString());  
    }  
    ```  
  
    > [!WARNING]  
    >  确保用运行 SharePoint 有效的服务器名称替换“TestServer”代码。  
  
## 测试应用程序页  
 接下来，确定应用程序页是否正确显示零用金数据。  
  
#### 测试应用程序页  
  
1.  选择 F5 运行项目，并将项目部署到 SharePoint。  
  
2.  选择**“主页”**按钮，然后通过选择快速启动栏上的**“共享文档”**链接来显示 SharePoint 网站上的“共享文档”列表。  
  
3.  若要表示此示例的零用金报销单，请通过选择页面顶部**“库工具”**的选项卡上的**“文档”**链接，然后选择工具功能区上的**“上载文档”**按钮，将一些新文档上载到文档列表中。  
  
4.  在上载一些文档之后，通过选择页顶部的**库工具** 选项卡的 **库** 链接，然后选择 **库设置** 按钮在工具功能区实例化工作流。  
  
5.  在**“文档库设置”**页上，选择**“权限和管理”**部分中的**“工作流设置”**链接。  
  
6.  在**“工作流设置”**页中，选择**“添加工作流”**链接。  
  
7.  在**“添加工作流”**页中，选择**“ExpenseReport \- Workflow1”**工作流，为该工作流输入名称（例如“ExpenseTest”），然后选择**“下一步”**按钮。  
  
     将显示工作流的关联窗体。  将使用此窗体来报告零用金限制金额。  
  
8.  在关联窗体中，输入 **1000**到**自动审批限制** 框中，然后选择 **关联工作流** 按钮。  
  
9. 选择**“主页”**按钮返回到 SharePoint 主页。  
  
10. 选择快速启动栏上的**“共享文档”**链接。  
  
11. 选择某个已上载的文档以显示下拉箭头，选择该文件，然后选择 **工作流** 项。  
  
12. 选择 ExpenseTest 旁边的图像以显示工作流启动窗体。  
  
13. 在**“Expense Total”（零用金总计）**文本框中，输入一个大于 1000 的值，然后选择**“Start Workflow”（启动工作流）**按钮。  
  
     如果报告的费用超过分配的零用金，则将向任务列表中添加任务。  具有**“已完成”**值的名为**“ExpenseTest”**的列也将添加到“共享文档”列表中的零用金报销单项中。  
  
14. 对于“共享文档”列表中的其他文档，重复步骤 11 至步骤 13。（文档的具体数目无关紧要。）  
  
15. 通过在 Web 浏览器中打开以下 URL 来显示零用金报销单汇总应用程序页：**http:\/\/***系统名称SystemName***\/\_layouts\/ExpenseReport\/ApplicationPage1.aspx**。  
  
     零用金报销单汇总页将列出超过分配的金额的所有零用金报销单、报销单超出的金额以及所有报销单的总金额。  
  
## 后续步骤  
 有关 SharePoint 应用程序页的更多信息，请参见[为 SharePoint 创建应用程序页](../sharepoint/creating-application-pages-for-sharepoint.md)。  
  
 通过按照以下主题的说明在 Visual Studio 中使用 Visual Web Designer，可以了解有关如何设计 SharePoint 页面内容的更多信息：  
  
-   [为 SharePoint 创建 Web 部件](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
-   [为 Web 部件或应用程序页创建可重用控件](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
## 请参阅  
 [演练：创建带有关联窗体和启动窗体的工作流](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [如何：创建应用程序页](../sharepoint/how-to-create-an-application-page.md)   
 [为 SharePoint 创建应用程序页](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  