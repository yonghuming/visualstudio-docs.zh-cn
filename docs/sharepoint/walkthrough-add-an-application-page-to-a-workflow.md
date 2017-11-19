---
title: "演练： 向工作流添加的应用程序页 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, adding applications page to workflow
- application page [SharePoint development in Visual Studio]
ms.assetid: e4845d07-917b-45cb-a569-4ecdd602fbd9
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bab156bdd1589aaac10a619409b44e50558b9c15
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-add-an-application-page-to-a-workflow"></a>演练：向工作流中添加应用程序页
  本演练演示如何添加显示派生自工作流到工作流项目的数据的应用程序页。 基于本主题所述的项目[演练： 创建带有关联和启动窗体的工作流](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)。  
  
 本演练演示了下列任务：  
  
-   向 SharePoint 工作流项目中添加 ASPX 应用程序页面。  
  
-   从工作流项目中获取数据和操作它。  
  
-   在应用程序页上的表中显示数据。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练：  
  
-   支持的版本的[!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]和 SharePoint。 有关详细信息，请参阅[有关开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
-   你还必须完成本主题中的项目[演练： 创建带有关联和启动窗体的工作流](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)。  
  
## <a name="amending-the-workflow-code"></a>修改工作流代码  
 首先，将某个代码行添加到工作流的费用报表量设置结果列的值。 更高版本在费用报销单汇总计算中使用此值。  
  
#### <a name="to-set-the-value-of-the-outcome-column-in-the-workflow"></a>在工作流中设置结果列的值  
  
1.  加载已完成的项目，从主题[演练： 创建带有关联和启动窗体的工作流](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)到[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  （具体取决于您的编程语言） 打开 Workflow1.cs 或 Workflow1.vb 代码。  
  
3.  到底部`createTask1_MethodInvoking`方法，添加以下代码：  
  
    ```vb  
    createTask1_TaskProperties1.ExtendedProperties("Outcome") =   
      workflowProperties.InitiationData  
    ```  
  
    ```csharp  
    createTask1_TaskProperties1.ExtendedProperties["Outcome"] =   
      workflowProperties.InitiationData;  
    ```  
  
## <a name="creating-an-application-page"></a>创建应用程序页  
 接下来，向项目添加 ASPX 窗体。 此窗体将显示从支出报表工作流项目中获取的数据。 若要执行此操作，将添加的应用程序页。 应用程序页上使用相同的母版页作为其他 SharePoint 页，这意味着它将类似于 SharePoint 站点上的其他页。  
  
#### <a name="to-add-an-application-page-to-the-project"></a>若要向项目中添加的应用程序页  
  
1.  选择 ExpenseReport 项目，然后，在菜单栏上，选择**项目**，**添加新项**。  
  
2.  在**模板**窗格中，选择**应用程序页**模板，使用项目项的默认名称 (**ApplicaitonPage1.aspx**)，然后选择**添加**按钮。  
  
3.  在[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]ApplicationPage1.aspx，替换`PlaceHolderMain`节替换为以下：  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
        <asp:Label ID="Label1" runat="server" Font-Bold="True"   
            Text="Expenses that exceeded allotted amount" Font-Size="Medium"></asp:Label>  
        <br />  
        <asp:Table ID="Table1" runat="server">  
        </asp:Table>  
    </asp:Content>  
    ```  
  
     此代码将表添加到标题以及页。  
  
4.  通过将添加到应用程序页标题`PlaceHolderPageTitleInTitleArea`节替换为以下：  
  
    ```  
    <asp:Content ID="PageTitleInTitleArea" ContentPlaceHolderID="PlaceHolderPageTitleInTitleArea" runat="server" >  
        Expense Report Summary  
    </asp:Content>  
    ```  
  
## <a name="coding-the-application-page"></a>编码的应用程序页  
 接下来，将代码添加到费用报表汇总应用程序页。 当您打开页时，代码将扫描超出分配的支出限制的支出的任务列表中 SharePoint。 该报告列出每个项的支出费用的总和。  
  
#### <a name="to-code-the-application-page"></a>编写应用程序页的代码  
  
1.  选择**ApplicationPage1.aspx**节点，然后在菜单栏上，选择**视图**，**代码**以显示应用程序页背后的代码。  
  
2.  替换**使用**或**导入**语句 （具体取决于您的编程语言） 替换为以下类的顶部：  
  
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
    >  请确保在代码中将"TestServer"替换运行 SharePoint 的有效服务器的名称。  
  
## <a name="testing-the-application-page"></a>测试应用程序页  
 接下来，确定应用程序页上是否正确显示支出数据。  
  
#### <a name="to-test-the-application-page"></a>若要测试应用程序页  
  
1.  选择 F5 键以运行并将项目部署到 SharePoint。  
  
2.  选择**主页**按钮，，然后选择**共享文档**快速启动栏显示在 SharePoint 站点上的共享文档列表上的链接。  
  
3.  若要表示对于此示例的费用报告，某些新将文档上载到文档列表通过选择**文档**链接**报销**页，然后选择顶部的选项卡**将文档上载**工具功能区上的按钮。  
  
4.  通过选择中上载的一些文档后，实例化工作流**库**链接**报销**页并选择顶部的选项卡**库设置**工具功能区上的按钮。  
  
5.  在**文档库设置**页上，选择**工作流设置**中链接**权限和管理**部分。  
  
6.  在**工作流设置**页上，选择**添加工作流**链接。  
  
7.  在**添加工作流**页上，选择**ExpenseReport-Workflow1**工作流中，输入工作流的名称，如**ExpenseTest**，然后选择**下一步**按钮。  
  
     显示工作流关联窗体。 使用它来报告支出限制量。  
  
8.  在关联窗体中，输入**1000年**到**自动批准限制**框中，，然后选择**将关联的工作流**按钮。  
  
9. 选择**主**按钮以返回到 SharePoint 主页。  
  
10. 选择**共享文档**快速启动栏上的链接。  
  
11. 选择一个已上载的文档，以显示一个下拉箭头，选择它，然后选择**工作流**项。  
  
12. 选择以显示工作流启动窗体 ExpenseTest 旁边的映像。  
  
13. 在**支出总**文本框中，输入一个值，大于 1000，，然后选择**启动工作流**按钮。  
  
     当报告的费用超过分配的费用金额时，任务已添加到任务列表中。 一个名为列**ExpenseTest**值**已完成**也将添加到共享文档列表中的支出报表项。  
  
14. 重复步骤 11 13 共享文档列表中的其他文档。 （文档的精确数目并不重要。）  
  
15. 通过在 Web 浏览器中打开以下 URL 显示费用报表汇总应用程序页： **http://***系统名称***/_layouts/ExpenseReport/ApplicationPage1.aspx**.  
  
     支出报表摘要页列出所有超过分配的量的费用报表、 它，超出的金额和所有报表的总金额。  
  
## <a name="next-steps"></a>后续步骤  
 有关 SharePoint 应用程序页的详细信息，请参阅[for SharePoint 创建应用程序页](../sharepoint/creating-application-pages-for-sharepoint.md)。  
  
 你可以了解有关如何通过使用 Visual Studio 中从下面这些主题的可视 Web 设计器设计 SharePoint 页面内容的详细信息：  
  
-   [为 SharePoint 创建 Web 部件](../sharepoint/creating-web-parts-for-sharepoint.md)。  
  
-   [为 Web 部件或应用程序页创建可重用控件](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)。  
  
## <a name="see-also"></a>另请参阅  
 [演练： 创建带有关联和启动窗体的工作流](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [如何： 创建的应用程序页](../sharepoint/how-to-create-an-application-page.md)   
 [为 SharePoint 创建应用程序页](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  