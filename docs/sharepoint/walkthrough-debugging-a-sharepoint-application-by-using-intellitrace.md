---
title: "演练： 使用 IntelliTrace 调试 SharePoint 应用程序 |Microsoft 文档"
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
helpviewer_keywords:
- IntelliTrace [SharePoint development in Visual Studio]
- standalone data collector
- SharePoint development in Visual Studio, IntelliTrace
- data collector
- IntelliTrace
ms.assetid: 4bd80d2f-f680-4bf4-81c3-f14e8185f6a4
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a020b82dccd1491e0381bee8ff104b944d5cf7b0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-debugging-a-sharepoint-application-by-using-intellitrace"></a>演练：使用 IntelliTrace 调试 SharePoint 应用程序
  通过使用 IntelliTrace，你可以更轻松地调试 SharePoint 解决方案。 传统的调试器使你只有解决方案的快照在当前时间点。 但是，你可以使用 IntelliTrace 查看过去发生在事件，你的解决方案和它们发生，导航到的代码的上下文。  
  
 本演练演示如何使用 Microsoft Monitoring Agent 以从已部署应用程序收集 IntelliTrace 数据调试在 Visual Studio Ultimate 中的 SharePoint 2010 或 SharePoint 2013 项目。 若要分析该数据，必须使用 Visual Studio 旗舰版。 此项目包含功能接收器，其中，当激活此功能，则将任务添加到任务列表和公告列表到公告。 停用该功能后，将任务标记为已完成，和公告列表添加第二个通知。 但是，该过程包含一个逻辑错误，阻止项目正常运行。 通过使用 IntelliTrace，你将找到并更正错误。  
  
 **适用于：**本主题中的信息适用于 Visual Studio 中创建的 SharePoint 2010 和 SharePoint 2013 解决方案。  
  
 本演练阐释了以下任务：  
  
-   [创建功能接收器](#BKMK_CreateReceiver)  
  
-   [向功能接收器中添加代码](#BKMK_AddCode)  
  
-   [测试项目](#BKMK_Test1)  
  
-   [使用 Microsoft Monitoring Agent 收集 IntelliTrace 数据](#BKMK_CollectDiagnosticData)  
  
-   [调试并修复 SharePoint 解决方案](#BKMK_DebugSolution)  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练：  
  
-   受支持的 Windows 和 SharePoint 的版本。 请参阅[开发 SharePoint 解决方案的需求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio 旗舰版。  
  
##  <a name="BKMK_CreateReceiver"></a>创建功能接收器  
 首先，你创建的空 SharePoint 项目具有功能接收器。  
  
#### <a name="to-create-a-feature-receiver"></a>若要创建功能接收器  
  
1.  创建 SharePoint 2010 或 SharePoint 2013 解决方案项目，并将其命名**IntelliTraceTest**。  
  
     **SharePoint 自定义向导**出现时，你的项目和解决方案的信任级别可以在其中指定 SharePoint 站点。  
  
2.  选择**部署为场解决方案**选项按钮，，然后选择**完成**按钮。  
  
     IntelliTrace 仅仅作用于场解决方案。  
  
3.  在**解决方案资源管理器**，打开快捷菜单**功能**节点，然后选择**添加功能**。  
  
     Feature1.feature 显示。  
  
4.  为 Feature1.feature，打开快捷菜单，然后选择**添加事件接收器**将代码模块添加到功能。  
  
##  <a name="BKMK_AddCode"></a>向功能接收器中添加代码  
 接下来，将代码添加到功能接收器中的两个方法：`FeatureActivated`和`FeatureDeactivating`。 激活或停用在 SharePoint 中，分别功能时，将触发这些方法。  
  
#### <a name="to-add-code-to-the-feature-receiver"></a>若要将代码添加到功能接收器  
  
1.  在顶部`Feature1EventReceiver`类中，添加以下代码，其中声明指定 SharePoint 站点和子站点的变量：  
  
    ```vb  
    ' SharePoint site and subsite.  
    Private siteUrl As String = "http://localhost"  
    Private webUrl As String = "/"  
    ```  
  
    ```csharp  
    // SharePoint site and subsite.  
    private string siteUrl = "http://localhost";  
    private string webUrl = "/";  
    ```  
  
2.  将 `FeatureActivated` 方法替换为以下代码：  
  
    ```vb  
    Public Overrides Sub FeatureActivated(ByVal properties As SPFeatureReceiverProperties)  
        Try  
            Using site As New SPSite(siteUrl)  
                Using web As SPWeb = site.OpenWeb(webUrl)  
                    ' Reference the lists.  
                    Dim announcementsList As SPList = web.Lists("Announcements")  
                    Dim taskList As SPList = web.Lists("Tasks")  
  
                    ' Add an announcement to the Announcements list.  
                    Dim listItem As SPListItem = announcementsList.Items.Add()  
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)  
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()  
                    listItem.Update()  
  
                    ' Add a task to the Task list.  
                    Dim newTask As SPListItem = taskList.Items.Add()  
                    newTask("Title") = "Deactivate feature: " & Convert.ToString(properties.Definition.DisplayName)  
                    newTask.Update()  
                End Using  
            End Using  
  
        Catch e As Exception  
            Console.WriteLine("Error: " & e.ToString())  
        End Try  
  
    End Sub  
    ```  
  
    ```csharp  
    public override void FeatureActivated(SPFeatureReceiverProperties properties)  
    {  
        try  
        {  
            using (SPSite site = new SPSite(siteUrl))  
            {  
                using (SPWeb web = site.OpenWeb(webUrl))  
                {  
                    // Reference the lists.  
                    SPList announcementsList = web.Lists["Announcements"];  
                    SPList taskList = web.Lists["Tasks"];  
  
                    // Add an announcement to the Announcements list.  
                    SPListItem listItem = announcementsList.Items.Add();  
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;  
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " + DateTime.Now.ToString();  
                    listItem.Update();  
  
                    // Add a task to the Task list.  
                    SPListItem newTask = taskList.Items.Add();  
                    newTask["Title"] = "Deactivate feature: " + properties.Definition.DisplayName;  
                    newTask.Update();  
                }  
            }  
        }  
  
        catch (Exception e)  
        {  
            Console.WriteLine("Error: " + e.ToString());  
        }  
  
    }  
    ```  
  
3.  将 `FeatureDeactivating` 方法替换为以下代码：  
  
    ```vb  
    Public Overrides Sub FeatureDeactivating(ByVal properties As SPFeatureReceiverProperties)  
        ' The following line induces an error to demonstrate debugging.  
        ' Remove this line later for proper operation.  
        Throw New System.InvalidOperationException("Serious error occurred!")  
        Try  
            Using site As New SPSite(siteUrl)  
                Using web As SPWeb = site.OpenWeb(webUrl)  
                    ' Reference the lists.  
                    Dim taskList As SPList = web.Lists("Tasks")  
                    Dim announcementsList As SPList = web.Lists("Announcements")  
  
                    ' Add an announcement that the feature was deactivated.  
                    Dim listItem As SPListItem = announcementsList.Items.Add()  
                    listItem("Title") = "Deactivated Feature: " & Convert.ToString(properties.Definition.DisplayName)  
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was deactivated on: " & DateTime.Now.ToString()  
                    listItem.Update()  
  
                    ' Find the task that the feature receiver added to the Task list when the  
                    ' feature was activated.  
                    Dim qry As New SPQuery()  
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>"  
                    Dim taskItems As SPListItemCollection = taskList.GetItems(qry)  
  
                    For Each taskItem As SPListItem In taskItems  
                        ' Mark the task as complete.  
                        taskItem("PercentComplete") = 1  
                        taskItem("Status") = "Completed"  
                        taskItem.Update()  
                    Next  
                End Using  
  
            End Using  
  
        Catch e As Exception  
            Console.WriteLine("Error: " & e.ToString())  
        End Try  
  
    End Sub  
    ```  
  
    ```csharp  
    public override void FeatureDeactivating(SPFeatureReceiverProperties properties)  
    {  
        // The following line induces an error to demonstrate debugging.  
        // Remove this line later for proper operation.  
        throw new System.InvalidOperationException("A serious error occurred!");   
        try  
        {  
            using (SPSite site = new SPSite(siteUrl))  
            {  
                using (SPWeb web = site.OpenWeb(webUrl))  
                {  
                    // Reference the lists.  
                    SPList taskList = web.Lists["Tasks"];  
                    SPList announcementsList = web.Lists["Announcements"];  
  
                    // Add an announcement that the feature was deactivated.  
                    SPListItem listItem = announcementsList.Items.Add();  
                    listItem["Title"] = "Deactivated Feature: " + properties.Definition.DisplayName;  
                    listItem["Body"] = properties.Definition.DisplayName + " was deactivated on: " + DateTime.Now.ToString();  
                    listItem.Update();  
  
                    // Find the task that the feature receiver added to the Task list when the  
                    // feature was activated.  
                    SPQuery qry = new SPQuery();  
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>";  
                    SPListItemCollection taskItems = taskList.GetItems(qry);  
  
                    foreach (SPListItem taskItem in taskItems)  
                    {  
                        // Mark the task as complete.  
                        taskItem["PercentComplete"] = 1;  
                        taskItem["Status"] = "Completed";  
                        taskItem.Update();  
                    }  
                }  
            }  
  
        }  
  
        catch (Exception e)  
        {  
            Console.WriteLine("Error: " + e.ToString());  
        }  
    }  
    ```  
  
##  <a name="BKMK_Test1"></a>测试项目  
 现在，不会向功能接收器中添加代码，数据收集器正在运行，部署并运行 SharePoint 解决方案以测试是否它能否正常工作。  
  
> [!IMPORTANT]  
>  对于本例，请在 FeatureDeactivating 事件处理程序引发错误。 稍后在本演练中，你通过使用数据收集器创建的.iTrace 文件中找到此错误。  
  
#### <a name="to-test-the-project"></a>测试项目  
  
1.  将解决方案部署到 SharePoint，然后在浏览器中打开 SharePoint 站点。  
  
     该功能会自动激活，从而导致其功能接收器中添加公告和任务。  
  
2.  显示公告和任务列表的内容。  
  
     公告列表应具有名为的新通告**已激活功能： IntelliTraceTest_Feature1**，和任务列表应该具有一个名为的新任务**停用功能： IntelliTraceTest_Feature1**。 如果缺少任一这些项时，请验证是否已激活该功能。 如果它未激活，则将其激活。  
  
3.  停用该功能，执行以下步骤：  
  
    1.  上**站点操作**在 SharePoint 中，菜单中，选择**站点设置**。  
  
    2.  下**站点操作**，选择**管理站点功能**链接。  
  
    3.  旁边**IntelliTraceTest Feature1**，选择**停用**按钮。  
  
    4.  在警告页上，选择**停用此功能**链接。  
  
     FeatureDeactivating() 事件处理程序引发错误。  
  
##  <a name="BKMK_CollectDiagnosticData"></a>使用 Microsoft Monitoring Agent 收集 IntelliTrace 数据  
 如果运行 SharePoint 的系统上安装 Microsoft Monitoring Agent，您可以通过使用 IntelliTrace 返回的泛型信息比更具体的数据来调试 SharePoint 解决方案。 代理会在 Visual Studio 之外工作方式是使用 PowerShell cmdlet 以捕获你的 SharePoint 解决方案运行时的调试信息。  
  
> [!NOTE]  
>  本部分中的配置信息是特定于此示例。 有关其他配置选项的详细信息，请参阅[使用 IntelliTrace 独立收集器](/visualstudio/debugger/using-the-intellitrace-stand-alone-collector)。  
  
1.  正在运行 SharePoint 的计算机上[设置 Microsoft 监视代理并开始监视你的解决方案](/visualstudio/debugger/using-the-intellitrace-stand-alone-collector)。  
  
2.  停用该功能：  
  
    1.  上**站点操作**在 SharePoint 中，菜单中，选择**站点设置**。  
  
    2.  下**站点操作**，选择**管理站点功能**链接。  
  
    3.  旁边**IntelliTraceTest Feature1**，选择**停用**按钮。  
  
    4.  在警告页上，选择**停用此功能**链接。  
  
     （在这种情况下，由于 FeatureDeactivating() 事件处理程序中引发的错误） 就会出错。  
  
3.  在 PowerShell 窗口中，运行[Stop-webapplicationmonitoring](http://go.microsoft.com/fwlink/?LinkID=313687)命令以创建.iTrace 文件，停止监视，然后重新启动你的 SharePoint 解决方案。  
  
     **Stop-webapplicationmonitoring***"\<SharePointSite >\\< SharePointAppName\>"*   
  
##  <a name="BKMK_DebugSolution"></a>调试并修复 SharePoint 解决方案  
 现在你可以以查找并修复 SharePoint 解决方案中的错误的 Visual Studio 中查看 IntelliTrace 日志文件。  
  
#### <a name="to-debug-and-fix-the-sharepoint-solution"></a>调试并修复 SharePoint 解决方案  
  
1.  在 \IntelliTraceLogs 文件夹中，打开 Visual Studio 中的.iTrace 文件。  
  
     **IntelliTrace 摘要**页将出现。 未处理该错误，因为 SharePoint 相关 ID (GUID) 将出现的未经处理的异常区域中**分析**部分。 选择**调用堆栈**按钮如果你想要查看发生错误的位置的调用堆栈。  
  
2.  选择**调试异常**按钮。  
  
     如果出现提示，则加载符号文件。 在**IntelliTrace**窗口中，该异常被标记为"引发： 发生严重错误 ！"。  
  
     在 IntelliTrace 窗口中，选择要显示的代码，失败的异常。  
  
3.  通过打开 SharePoint 解决方案然后注释掉或删除纠正该错误**引发**语句 FeatureDeactivating() 过程的顶部。  
  
4.  重新生成 Visual Studio 中的解决方案，然后将它重新部署到 SharePoint。  
  
5.  停用该功能，执行以下步骤：  
  
    1.  上**站点操作**在 SharePoint 中，菜单中，选择**站点设置**。  
  
    2.  下**站点操作**，选择**管理站点功能**链接。  
  
    3.  旁边**IntelliTraceTest Feature1**，选择**停用**按钮。  
  
    4.  在警告页上，选择**停用此功能**链接。  
  
6.  打开任务列表中，并确认**状态**停用任务的值"已完成"并将其**完成百分比**值是 100%。  
  
     现在的代码正确运行。  
  
## <a name="see-also"></a>另请参阅  
 [验证和调试 SharePoint 代码](../sharepoint/verifying-and-debugging-sharepoint-code.md)   
 [IntelliTrace](/visualstudio/debugger/intellitrace)   
 [演练： 通过使用单元测试来验证 SharePoint 代码](https://msdn.microsoft.com/en-us/library/gg599006(v=vs.100).aspx)  
  
  