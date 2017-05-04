---
title: "演练：使用 IntelliTrace 调试 SharePoint 应用程序 | Microsoft Docs"
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
helpviewer_keywords: 
  - "IntelliTrace [Visual Studio 中的 SharePoint 开发]"
  - "独立数据收集器"
  - "Visual Studio 中的 SharePoint 开发，IntelliTrace"
  - "数据收集器"
  - "IntelliTrace"
ms.assetid: 4bd80d2f-f680-4bf4-81c3-f14e8185f6a4
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# 演练：使用 IntelliTrace 调试 SharePoint 应用程序
  通过使用 IntelliTrace，您可以更轻松地调试 SharePoint 解决方案。  传统的调试器只会为您提供应用程序当前时间的解决方案的快照。  但是，您可以使用 IntelliTrace 来查看解决方案中过去发生的事件以及这些事件发生和定位到代码的上下文。  
  
 本演练演示如何在 Visual Studio 旗舰版中调试 SharePoint 2010 或 SharePoint 2013 项目，通过使用监视代理从部署的应用程序收集 IntelliTrace 数据。  若要分析该数据，必须使用 Visual Studio 旗舰版。  此项目合并了一个功能接收器，当激活功能时，该接收器将向任务列表添加一个任务并向公告列表添加一个公告。  当停用功能时，相应的任务将会标记为已完成，并且会再次向公告列表添加一个公告。  但是，这个过程包含一个逻辑错误，会阻止项目正确运行。  您将利用 IntelliTrace 来查找并更正该错误。  
  
 **适用于：**主题中的信息适用于在 Visual Studio 中创建的 SharePoint 2010 和 SharePoint 2013 解决方案。  
  
 本演练阐释了以下任务：  
  
-   [创建功能接收器](#BKMK_CreateReceiver)  
  
-   [向功能接收器中添加代码](#BKMK_AddCode)  
  
-   [测试项目](#BKMK_Test1)  
  
-   [使用Microsoft监视代理收集IntelliTrace数据。](#BKMK_CollectDiagnosticData)  
  
-   [调试并修复 SharePoint 解决方案](#BKMK_DebugSolution)  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 系统必备  
 您需要以下组件来完成本演练：  
  
-   支持的 Windows 和 SharePoint 版本。  请参见 [开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio 旗舰版。  
  
##  <a name="BKMK_CreateReceiver"></a> 创建功能接收器  
 首先，创建一个包含功能接收器的空 SharePoint 项目。  
  
#### 创建功能接收器  
  
1.  创建 SharePoint 2010 或 SharePoint 2013 解决方案项，并将其命名为 IntelliTraceTest。  
  
     将显示**“SharePoint 自定义向导”**，您可以在其中指定项目的 SharePoint 站点和解决方案的信任级别。  
  
2.  选择 **部署为场解决方案** 选项按钮，然后选择 **完成** 按钮。  
  
     IntelliTrace 只可用于场解决方案。  
  
3.  在**“解决方案资源管理器”**中，打开**功能**节点的快捷菜单，然后选择**“添加功能”**。  
  
     将显示 Feature1.feature。  
  
4.  打开 Feature1.feature 的快捷菜单，然后选择 **添加事件接收器** 将代码模块添加到该功能。  
  
##  <a name="BKMK_AddCode"></a> 向功能接收器中添加代码  
 接下来，向功能接收器中的以下两个方法添加代码：`FeatureActivated` 和 `FeatureDeactivating`。  只要在 SharePoint 中激活或停用该功能，这两个方法就会分别触发。  
  
#### 向功能接收器中添加代码  
  
1.  在 `Feature1EventReceiver` 类的顶部，添加以下代码以声明用于指定 SharePoint 站点和子站点的变量：  
  
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
  
2.  用下面的代码替换 `FeatureActivated` 方法：  
  
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
  
3.  用下面的代码替换 `FeatureDeactivating` 方法：  
  
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
  
##  <a name="BKMK_Test1"></a> 测试项目  
 即将代码添加到功能接收器，并且数据收集器运行，部署并运行 SharePoint 解决方案测试是否正常工作。  
  
> [!IMPORTANT]  
>  对于此示例，FeatureDeactivating 事件处理程序将引发一个错误。  稍后在此演练中，您通过使用数据收集器创建的iTrace文件找到此错误。  
  
#### 测试项目  
  
1.  部署解决方案到 SharePoint，然后在浏览器中打开 SharePoint 站点。  
  
     该功能会自动激活，从而导致其功能接收器添加公告和任务。  
  
2.  显示声明的目录和任务列表。  
  
     “公告”列表已经有了名为**“Activated feature: IntelliTraceTest\_Feature1”**的新公告，并且“任务”列表中有了名为**“Deactivate feature: IntelliTraceTest\_Feature1”**的新任务。  如果这些项目中的任何一个丢失，请验证是否激活该功能。  如果没有激活它，则激活它。  
  
3.  通过执行以下步骤停用该功能：  
  
    1.  在 SharePoint 中的**“网站操作”**菜单上，选择**“网站设置”**。  
  
    2.  在 **网站操作**下，选择 **管理网站功能** 链接。  
  
    3.  在 **IntelliTraceTest Feature1**旁边，选择 **停用** 按钮。  
  
    4.  在警告页上，选择 **停用此功能** 链接。  
  
     FeatureDeactivating\(\) 事件处理程序引发一个错误。  
  
##  <a name="BKMK_CollectDiagnosticData"></a> 使用Microsoft监视代理收集IntelliTrace数据。  
 如果您安装了系统上正在运行的SharePoint的微软监控代理，您可以通过使用比ItelliTrace返回的通用信息更具体的数据，调试SharePoint解决方案。  当您的 SharePoint 解决方案运行时，代理工作在使用 PowerShell cmdlets 捕获 Visual Studio 之外调试信息。  
  
> [!NOTE]  
>  本节中的配置信息特定于此示例。  有关其他配置选项的更多信息，请参见[使用 IntelliTrace 独立收集器](../debugger/using-the-intellitrace-stand-alone-collector.md)。  
  
1.  在正在运行SharePoint的计算机上[设置Microsoft监控代理，并开始监控您的解决方案](../debugger/using-the-intellitrace-stand-alone-collector.md)。  
  
2.  停用该功能：  
  
    1.  在 SharePoint 中的**“网站操作”**菜单上，选择**“网站设置”**。  
  
    2.  在 **网站操作**下，选择 **管理网站功能** 链接。  
  
    3.  在 **IntelliTraceTest Feature1**旁边，选择 **停用** 按钮。  
  
    4.  在警告页上，选择 **停用此功能** 链接。  
  
     错误 \(在本例中，由于在 FeatureDeactivating\(\) 事件处理程序引发的错误\)。  
  
3.  在PowerShell窗口中，运行[Stop\-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313687) 命令来创建iTrace文件，停止监视，并重新启动您的SharePoint解决方案。  
  
     **Stop\-WebApplicationMonitoring**  *"\<SharePointSite\>\\\<SharePointAppName\>"*  
  
##  <a name="BKMK_DebugSolution"></a> 调试并修复 SharePoint 解决方案  
 现在可以查看 IntelliTrace 日志文件，在 Visual Studio 查找和修复 SharePoint 解决方案的错误。  
  
#### 调试并修复 SharePoint 解决方案  
  
1.  在\\IntelliTraceLogs 文件夹，请在 Visual Studio 中打开 .iTrace 文件。  
  
     **IntelliTrace 摘要**页将出现。  由于该错误未处理，SharePoint 依赖项 ID \(GUID\) 在 **分析** 部分的未经处理的异常区域显示。  如果要查看错误生成的调用堆栈，选择 **调用堆栈** 按钮。  
  
2.  选择 **调试异常** 按钮。  
  
     如果提示，加载符号文件。  在 **IntelliTrace** 窗口，则显示为“引发：严重的错误出现！”。  
  
     在 IntelliTrace 窗口中，选择显示失败的代码的异常。  
  
3.  通过打开 SharePoint 解决方案然后注释或移除 **throw** 在FeatureDeactivating顶部的陈述（）方法修正错误。  
  
4.  在 Visual Studio 重新生成解决方案，然后重新部署到 SharePoint。  
  
5.  通过执行以下步骤停用该功能：  
  
    1.  在 SharePoint 中的**“网站操作”**菜单上，选择**“网站设置”**。  
  
    2.  在 **网站操作**下，选择 **管理网站功能** 链接。  
  
    3.  在 **IntelliTraceTest Feature1**旁边，选择 **停用** 按钮。  
  
    4.  在警告页上，选择 **停用此功能** 链接。  
  
6.  打开任务列表，然后验证 Deactivate 任务的**“状态”**值现在是否已正确设置为“完成”，并验证其**“完成百分比”**的值是否设置为 100%。  
  
     代码正确现在运行。  
  
## 请参阅  
 [验证和调试 SharePoint 代码](../sharepoint/verifying-and-debugging-sharepoint-code.md)   
 [使用 IntelliTrace](../debugger/intellitrace.md)   
 [演练：使用单元测试验证 SharePoint 代码](http://msdn.microsoft.com/zh-cn/3d2c4aaf-3cb5-4825-b21b-f10222abe818)  
  
  