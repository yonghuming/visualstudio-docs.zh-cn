---
title: "SharePoint 解决方案的疑难解答 |Microsoft 文档"
ms.custom: 
ms.date: 02/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Microsoft.VisualStudio.Tools.SharePoint.Errors.Debugging
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, troubleshooting
ms.assetid: d3c8a01c-8fac-40d0-bf9e-476901f1490a
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fa3ecb6be4ba458c7a703e77e56c6ba51490887d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="troubleshooting-sharepoint-solutions"></a>SharePoint 解决方案疑难解答
  使用调试 SharePoint 解决方案时，可能发生以下问题或警报[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]调试器。 有关详细信息，请参阅[调试 SharePoint 2007 工作流解决方案](http://msdn.microsoft.com/en-us/3a5392f3-66f3-48be-956e-02de23fa6247)。
  
## <a name="token-restrictions-in-sandboxed-visual-web-parts"></a>沙盒可视 Web 部件中的标记限制  
 沙盒解决方案中的可视 Web 部件无法处理标准标记，例如 SharePoint 运行时支持的 $SPUrl。 因此不会解析 URL，并且如果您直接在脚本元素中引用 URL，则无法在可视 Web 部件设计器的“设计”视图中预览内容：  
  
```xml  
<script src="<% $SPUrl:~site/SiteAssets/ListOperations.js %>"></script>  
```  
  
 若要解决此限制并解析标记，请使用以下文本引用标记：  
  
```xml  
<asp:literal ID="Literal1" runat="server" Text="<script src='" />  
<asp:literal ID="Literal2" runat="server" Text="<% $SPUrl:~site/SiteAssets/ListOperations.js %>" />  
<asp:literal ID="Literal3" runat="server" Text="' type='text/javascript' ></script>" />  
```  
  
## <a name="character-restrictions-in-names-of-projects-and-project-items"></a>项目和项目项名称中的字符限制  
 在 SharePoint 2010 中，项目和项目项名称只能包含部署路径中有效的字符。 不允许使用任何其他字符。  
  
### <a name="error-message"></a>错误消息  
 "无效字符"错误消息。  
  
### <a name="resolution"></a>解决方法  
 对于 SharePoint 项目和项目项名称，仅使用以下字符：  
  
-   字母数字 ASCII 字符  
  
-   空格  
  
-   句点 （.）  
  
-   逗号 （，）  
  
-   下划线 (_)  
  
-   短划线 （-）  
  
-   反斜杠 (\\)  
  
 在打包项目时，验证规则将验证要部署的每个文件的部署路径属性是否只包含上述有效字符。  
  
## <a name="errors-when-creating-custom-fields"></a>创建自定义字段时的错误  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的自定义字段是使用 XML 定义的。 如果未使用特定格式定义或引用字段，则会出错。  
  
### <a name="error-message"></a>错误消息  
 在打包时"无效字符"错误消息。  
  
### <a name="resolution"></a>解决方法  
 如下面的示例所示，字段定义的 ID 必须是大括号括起来的 GUID：  
  
```xml  
<Field ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Type="Note"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Group="A Custom Group">  
</Field>.  
```  
  
 如下面的示例所示，必须通过使用空元素格式定义中的内容类型的字段引用 (\<f /> / >)，不能通过使用开始/结束元素 (\<f /> >\</FieldRef >):  
  
```xml  
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Required="TRUE"/>  
```  
  
 如果字段的源 XML 格式不正确、不是有效的 XML 文件或出现一些其他问题，则会出现“无法分析文件”错误。  
  
## <a name="new-non-english-site-definitions-do-not-appear-in-site-creation-page-after-deployment"></a>新的非英语站点定义不会出现在站点创建页在部署后  
 创建和使用非英语版本的部署站点定义后[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)](即的区域设置版本[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]不是 1033年)，则**SharePoint 自定义**选项卡不显示在**模板选择**框并且新的站点模板不显示在**新建 SharePoint 网站**页。  
  
### <a name="error-message"></a>错误消息  
 无。  
  
### <a name="resolution"></a>解决方法  
 出现此问题是由于中的值不正确**路径**webtemp 站点定义配置文件，例如 webtemp_SiteDefinitionProject1.xml 的属性。 在**路径**webtemp 文件，位于属性**部署位置**，更改为相应区域设置 1033年[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]。 例如，若要使用日文区域设置将值更改为 1041年。 有关详细信息，请参阅[由 Microsoft 分配的区域设置 Id](http://go.microsoft.com/fwlink/?LinkID=165561) MSDN 网站上。  
  
## <a name="error-appears-when-a-workflow-project-is-deployed-on-a-clean-system"></a>在干净系统上部署工作流项目时，会出现错误  
 如果在干净系统上部署 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的工作流项目，则会发生此问题。 干净系统是指以全新方式安装了 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 和 SharePoint 但未部署工作流项目的计算机。  
  
### <a name="error-message"></a>错误消息  
 找不到 SharePoint 列表： 工作流历史记录。  
  
### <a name="resolution"></a>解决方法  
 由于缺少的工作流历史记录列表出现此错误。 由于开发环境是干净系统，部署任何工作流，并且尚不存在工作流历史记录列表。 若要解决此问题，重新打开工作流向导中，这会导致要创建的工作流历史记录列表。  
  
##### <a name="to-reenter-the-workflow-wizard"></a>重新输入工作流向导  
  
1.  在**解决方案资源管理器**，选择工作流节点。  
  
2.  在**属性**窗口中，选择具有省略号按钮任何属性上的省略号 （...） 按钮。  
  
## <a name="user-must-refresh-application-page-in-browser-while-debugging-to-view-updated-image"></a>调试到视图更新映像时，用户必须刷新浏览器中的应用程序页  
 如果你正在调试 SharePoint 解决方案，其中包含应用程序页会显示一个映像，如某个控件一起[!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)]图像控件，您必须刷新浏览器将显示对映像进行了任何更改中的页。  
  
## <a name="error-the-site-location-is-not-valid"></a>错误： 站点位置无效  
 如果出现此问题，可以[!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]未安装。 如果你还没有到中指定的 SharePoint Web 站点的管理员访问权限也可能发生**SharePoint 自定义向导**。  
  
### <a name="error-message"></a>错误消息  
  
-   SharePoint 站点位置不是有效的。  
  
### <a name="resolution"></a>解决方法  
  
-   安装 [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]。  
  
-   确保你到 SharePoint 网站上具有管理员访问权限。 有关详细信息，请参阅[!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)]联机文章[授予访问权限的门户网站](http://go.microsoft.com/fwlink/?LinkId=98310)。  
  
## <a name="site-deletion-web-event-does-not-occur-in-event-receiver-project"></a>站点删除 Web 事件未发生在事件接收器项目  
 当你创建一个事件接收器项目并且你选择某些 Web 事件，如"正在删除站点"时，永远不会发生该事件。  
  
### <a name="error-message"></a>错误消息  
 无。  
  
### <a name="resolution"></a>解决方法  
 因为功能作用域必须是"站点"，以处理站点级事件，但事件接收器项目的默认功能作用域是"Web"，将发生此问题。 受影响这些 Web 事件是：  
  
-   站点正在删除 (WebDeleting)  
  
-   网站已被删除 (WebDeleted)  
  
-   站点正在移动 (WebMoving)  
  
-   站点已移动 (WebMoved)  
  
 若要解决此问题，请按如下所示更改的事件接收器中，将功能的范围。  
  
##### <a name="to-change-the-feature-scope-of-the-event-receiver"></a>若要更改的事件接收器的功能作用域  
  
1.  在**解决方案资源管理器**，在中打开事件接收器的.feature 文件**功能设计器**通过双击文件或打开其快捷菜单并选择**打开**.  
  
2.  选择箭头旁边**作用域**，然后选择**站点**中显示的列表。  
  
## <a name="deployment-error-appears-after-the-name-of-an-identifier-in-a-business-data-connectivity-model-project-is-changed"></a>更改业务数据连接模型项目中的标识符的名称后，会出现部署错误  
 如果更改业务数据连接 (BDC) 模型中实体的标识符名称，然后尝试部署解决方案，则会发生此问题。  
  
### <a name="error-messages"></a>错误消息  
  
-   \<*模型名称*> 具有以下外部内容类型激活错误...  
  
-   同名的 IMetadataObject\<*模型名称*> 包含字段 name 的重复值...  
  
### <a name="resolution"></a>解决方法  
 若要解决此问题，请手动删除模型，然后重新部署解决方案。  可以通过使用以下工具之一来删除模型：  
  
-   SharePoint 2010 管理中心。 有关详细信息，请参阅[BDC 模型管理](http://go.microsoft.com/fwlink/?LinkID=181472)Microsoft TechNet 网站上。  
  
-   Windows PowerShell。 你可以通过在命令提示符下键入以下命令来删除模型：**删除 SPBusinessDataCatalogModel**。 有关详细信息，请参阅[常规 cmdlet (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkID=182375) Microsoft TechNet 网站上。  
  
## <a name="an-error-appears-when-you-try-to-view-a-visual-web-part-in-sharepoint"></a>当你尝试查看 SharePoint 中的可视 Web 部件时，会出现一个错误  
 出现此问题时**路径**用户控件的属性不会开始以字符串"CONTROLTEMPLATES\\"。  
  
### <a name="error-messages"></a>错误消息  
  
-   文件 /_CONTROLTEMPLATES/*\<项目名称 >*/*\<Web 部件名称 >*/*\<用户控件名称 >*.ascx 不存在。  
  
-   '/' 应用程序中的服务器错误。  
  
### <a name="resolution"></a>解决方法  
  
##### <a name="to-resolve-this-issue"></a>若要解决此问题  
  
1.  在**解决方案资源管理器**，选择其文件扩展名是.ascx 的用户控件文件。  
  
2.  在菜单栏上，选择**视图**，**属性窗口**。  
  
3.  在**属性**窗口中，展开**部署位置**节点。  
  
4.  确保值**路径**以字符串开头的属性"CONTROLTEMPLATES\\"。  
  
## <a name="error-appears-when-an-imported-reusable-workflow-that-contains-a-task-form-field-is-run"></a>当运行包含一个任务窗体字段导入可重用工作流时会出现错误  
 如果你导入包含的任务窗体具有的字段，工作流，然后运行从中导入它的相同系统上的新工作流，则会发生此问题。  
  
### <a name="error-message"></a>错误消息  
 部署步骤激活功能中发生错误： 具有 Id 的字段 [*Guid*] 中功能定义 [*Guid*] 在当前站点集合或子站点中找到。  
  
### <a name="resolution"></a>解决方法  
 此错误是发生是因为导入可重用工作流项目中的字段 ID 冲突的结果[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]不会更改任务窗体字段 Id。 如果部署包含原始工作流的相同服务器上的导入工作流时，会发生字段 ID 冲突。  
  
 若要解决此问题，请使用查找和替换功能更改中的所有导入工作流文件的字段 ID 属性的值。  
  
## <a name="error-appears-when-a-renamed-imported-list-instance-is-run"></a>出现错误时重命名导入运行列表实例  
 如果你重命名导入的列表实例，然后运行它，则会发生此问题[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
### <a name="error-message"></a>错误消息  
 生成错误： 部署步骤激活功能中发生错误： 文件 Template\Features\\[*导入项目**功能**名称*] \Files\Lists\\[*旧**列表名称*] \Schema.xml 不存在。  
  
### <a name="resolution"></a>解决方法  
 当你导入的列表实例时，一个名为 CustomSchema 特性添加到列表实例的 Elements.xml 文件中。 Elements.xml 包含列表实例自定义 schema.xml 的路径。 如果重命名中的列表实例[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、 自定义 schema.xml 的部署路径发生变化，但不是更新 CustomSchema 属性的路径值。 因此，列表实例找不到 schema.xml 文件时激活该功能由 CustomSchema 特性指定的旧路径中。  
  
 若要解决此问题，更新 CustomSchema 属性中的 schema.xml 文件的部署位置的路径。  
  
## <a name="sharepoint-debugging-session-terminated-by-iis"></a>调试 IIS 终止的会话的 SharePoint  
 如果中设置断点，则会发生此问题[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 解决方案中，选择 F5 键以运行它，然后保持在 90 秒以上的断点处。  
  
### <a name="error-message"></a>错误消息  
 程序已正在调试的 Web 服务器进程已终止由 Internet 信息服务 (IIS)。 您可通过在 IIS 中配置应用程序池 Ping 设置来避免此问题。 请参阅有关进一步的详细信息的帮助。  
  
### <a name="resolution"></a>解决方法  
 默认情况下，IIS 应用程序池在等待 90 秒应用程序，以响应之前它将关闭应用程序。 此过程称为"执行 ping 操作的"应用程序。 若要解决此问题，你可以增加的等待时间或禁用应用程序完全 ping。  
  
##### <a name="to-access-the-iis-app-pool-settings"></a>访问 IIS 应用程序池设置  
  
1.  打开 IIS 管理器。  
  
2.  在**连接**窗格中，展开 SharePoint 服务器节点，然后依次**应用程序池**节点。  
  
3.  上**应用程序池**页上，选择 SharePoint 应用程序池 (通常为"SharePoint-80")，然后在**操作**窗格中，选择**高级设置**链接。  
  
4.  若要增加 IIS 超时前的等待时间，更改的值**Ping 最大响应时间 （秒）**为大于 90 秒的值。  
  
5.  若要禁用 IIS 执行 ping 操作，设置**启用 Ping**到**False**。  
  
## <a name="auto-retract-leaves-orphaned-list-instance-in-sharepoint"></a>在 SharePoint 中自动收回使孤立的列表实例  
 如果你执行以下步骤，则会发生此问题。  
  
1.  创建一个在具有列表实例的列表定义[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  选择 F5 以运行该解决方案。  
  
3.  停止调试，或关闭 SharePoint 站点。  
  
4.  重新打开 SharePoint 站点并打开列表实例。  
  
### <a name="error-message"></a>错误消息  
 '/' 应用程序中的服务器错误。  
  
### <a name="resolution"></a>解决方法  
 这是因为关闭调试会话的 SharePoint 解决方案后, 自动收回功能将收回解决方案。 收回从 SharePoint 删除该列表定义，但不会删除列表的实例。 列表实例需要的基础列表定义。  
  
 若要解决此问题，以部署解决方案，在菜单栏中，选择**生成**，**部署**。 （不要通过选择 F5 调试解决方案。）然后，删除 SharePoint 中的列表实例。  
  
## <a name="original-sharepoint-solution-is-replaced-by-an-exported-version"></a>由导出版本替换原始 SharePoint 解决方案  
 如果导出 SharePoint 解决方案时，导入到解决方案[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，然后将解决方案部署到同一站点从其导出，将替换原始的 SharePoint 解决方案。 如果将解决方案部署到不具有在其上激活原始解决方案的服务器，就不会出现此问题。  
  
### <a name="error-message"></a>错误消息  
 无。  
  
### <a name="resolution"></a>解决方法  
 若要避免覆盖从中导出的站点的解决方案，请更改解决方案 Id 的 Guid 和中的所有导入功能的功能 Id[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]项目。  
  
## <a name="error-appears-when-debugging-starts"></a>开始调试时出错  
 在 Visual Studio 中开始调试 SharePoint 解决方案时出现错误，表明由于字典中没有给定键，Visual Studio 无法加载 Web.config 文件。  
  
### <a name="error-message"></a>错误消息  
 无法加载 Web.config 配置文件。 检查任何格式不正确的 XML 元素的文件，然后重试。 出现以下错误： 给定的键时不在字典中存在。  
  
### <a name="resolution"></a>解决方法  
 若要解决此问题，请确保 Visual Studio 中的 SharePoint 项目的“站点 URL”属性值与分配给 Web 应用程序的备用访问映射的默认区域的 URL 一致。 对 URL 使用其他区域（如 Intranet）将无法解决此错误。 项目的站点 URL 与默认区域中的 URL 必须一致。 若要访问备用访问映射，请打开 SharePoint 2010 管理中心实用工具，选择**应用程序管理**链接，然后，在**Web 应用程序**，选择**配置备用访问映射**链接。 有关详细信息，请参阅[创建 Web 应用程序的区域](http://go.microsoft.com/fwlink/?LinkId=192274)。  
  
## <a name="see-also"></a>另请参阅  
 [SharePoint 打包和部署疑难解答](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)   
 [生成和调试 SharePoint 解决方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [在 Visual Studio 中进行调试](/visualstudio/debugger/debugging-in-visual-studio)  
  
  
