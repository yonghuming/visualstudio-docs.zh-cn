---
caps.handback.revision: 41
---
# SharePoint 解决方案疑难解答
  下面的问题或警报时可能会出现您的 SharePoint 解决方案使用调试程序[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]调试器。  有关详细信息，请参阅 [NIB: Debugging SharePoint 2007 Workflow Solutions](http://msdn.microsoft.com/zh-cn/3a5392f3-66f3-48be-956e-02de23fa6247).  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
## 沙盒的可视 Web 部件中的令牌限制  
 沙盒解决方案中的可视 web 部件不能处理标准的标记，如 $SPUrl，SharePoint 运行时支持。  因此，URL 未得到解决，并无法预览在可视 web 部件设计器的设计视图中的内容，如果它直接在中引用的脚本元素，如在下面的示例：  
  
```  
<script src=”<% $SPUrl:~site/SiteAssets/ListOperations.js %>"></script>  
```  
  
 若要变通解决此限制，并解析标记，请参阅其使用的文本：  
  
```  
<asp:literal ID="Literal1" runat="server" Text="<script src='" />  
<asp:literal ID="Literal2" runat="server" Text="<% $SPUrl:~site/SiteAssets/ListOperations.js %>" />  
<asp:literal ID="Literal3" runat="server" Text="' type='text/javascript' ></script>" />  
```  
  
## 项目和项目项的名称中的字符限制  
 项目和项目项的名称只能包含在 SharePoint 2010 年的部署路径中有效的字符。  允许不使用任何其它字符。  
  
### 错误消息  
 "无效字符"等错误消息。  
  
### 解析  
 对于 SharePoint 项目和项目项的名称，使用以下字符：  
  
-   字母数字 ASCII 字符  
  
-   空间  
  
-   句点 \(.\)  
  
-   逗号 \(，\)  
  
-   下划线 \(\_\)  
  
-   短划线 \(\-\)  
  
-   反斜杠 \(\\\)  
  
 项目打包，有效性规则将验证您要部署的每个文件的部署路径属性包含这些有效的字符。  
  
## 创建自定义字段时出现错误  
 在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，在 XML 中定义的自定义字段。  如果字段未定义或引用通过使用特定格式，则会发生错误。  
  
### 错误消息  
 在打包时"无效字符"错误消息。  
  
### 解析  
 有关字段定义的 ID 必须是一个括在大括号中，如以下示例所示的 GUID：  
  
```  
<Field ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Type="Note"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Group="A Custom Group">  
</Field>.  
```  
  
 下面的示例所示，必须通过使用空元素的格式来定义内容类型中的字段引用 （\< FieldRef \/ \>），不能通过使用元素的开始\/结束 \(\< FieldRef \>\< \/ FieldRef \>\)：  
  
```  
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Required="TRUE"/>  
```  
  
 如果字段的源 XML 的格式不正确、 不是有效的 XML 文件，或出现其他问题，该错误"无法分析文件" 发生。  
  
## 新的非英语网站定义不出现在网站创建页后部署  
 创建并使用非英语版本的部署网站定义后 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]（区域设置版本，即  [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]不是 1033年）、   **SharePoint 自定义** 选项卡未显示在 **模板选择** 框和新站点模板没有出现在 **新的 SharePoint 网站**页。  
  
### 错误消息  
 无。  
  
### 解析  
 出现此问题是由于不正确的值中**路径** webtemp 站点定义配置文件，如 webtemp\_SiteDefinitionProject1.xml 的属性。  在**路径** webtemp 文件中，并位于下面的属性 **部署位置**，到相应的区域设置更改 1033年  [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)].  例如，要使用日语区域设置更改值为 1041年。  有关详细信息，请参阅[由 Microsoft 的区域设置 Id 分配](http://go.microsoft.com/fwlink/?LinkID=165561)在 MSDN 网站上。  
  
## 在干净系统上部署工作流项目时出现错误  
 如果部署工作流项目中的时，会发生此问题[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]在干净系统上。  清理系统是计算机具有全新安装的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]和 SharePoint，但不是部署工作流项目。  
  
### 错误消息  
 找不到 SharePoint 列表： 工作流历史记录。  
  
### 解析  
 由于缺少的工作流历史记录列表会发生此错误。  由于开发环境是干净的系统，部署工作流和工作流历史记录列表尚不存在。  若要解决此问题，请重新打开工作流向导，这将导致创建工作流历史记录列表。  
  
##### 重新输入工作流向导  
  
1.  在**解决方案资源管理器**，选择工作流节点。  
  
2.  在**属性**窗口中，选择具有省略号按钮的任何属性的省略号 \(...\) 按钮。  
  
## 调试视图更新图像时，用户必须刷新应用程序页在浏览器中  
 如果您在调试包含与控件显示图像，如应用程序页的 SharePoint 解决方案[!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)]图像控件，您必须刷新页面在浏览器中显示对图像所做的任何更改。  
  
## 错误: 站点位置无效  
 如果出现此问题，可以[!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]未安装。  如果您没有管理员访问权限中指定的 SharePoint 网站它也可能发生 **SharePoint 自定义向导**。  
  
### 错误消息  
  
-   SharePoint 站点位置是无效的。  
  
### 解析  
  
-   安装 [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].  
  
-   请确保您具备管理员权限，到 SharePoint 网站上。  有关详细信息，请参阅[!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)]在线文章 [授予访问该门户网站](http://go.microsoft.com/fwlink/?LinkId=98310)。  
  
## 事件接收器项目中没有出现网站删除 Web 事件  
 当您创建一个事件接收器项目并选择某些 Web 事件如"正在删除网站" 永远不会发生该事件。  
  
### 错误消息  
 无。  
  
### 解析  
 出现此问题的原因的功能范围必须是"网站" 处理站点级别的事件，但默认功能事件接收器项目的范围是"Web"。  受影响的 Web 事件有：  
  
-   位置被删除 （WebDeleting）  
  
-   已删除网站 \(WebDeleted\)  
  
-   位置被移动 （WebMoving）  
  
-   移动网站 \(WebMoved\)  
  
 若要解决此问题，请按如下所示更改事件接收器的功能范围。  
  
##### 若要更改事件接收器的功能范围  
  
1.  在**解决方案资源管理器**，在中打开事件接收器的.feature 文件 **功能设计器** 通过双击该文件或打开其快捷菜单，然后选择 **打开**。  
  
2.  选择箭头旁边**范围**，然后选择 **网站**中显示的列表中。  
  
## 更改业务数据连接模型项目中的标识符名称后出现部署错误  
 如果您更改业务数据连接 \(BDC\) 模型中实体的标识符名称，然后尝试部署解决方案，将出现此问题。  
  
### 错误消息  
  
-   \<*模型名称*\> 具有以下外部内容类型激活错误。.  
  
-   使用名称 IMetadataObject \<*模型名称*\> 字段的名称中有一个值 重复的命令。.  
  
### 解析  
 若要解决此问题，请手动删除该模型，然后重新部署解决方案。  您可以使用下列工具之一来删除模型：  
  
-   SharePoint 2010 管理中心。  有关详细信息，请参阅 [BDC 模型管理](http://go.microsoft.com/fwlink/?LinkID=181472) Microsoft TechNet 网站上。  
  
-   Windows PowerShell。  您可以通过在命令提示符下键入以下命令来删除模型： **Remove\-SPBusinessDataCatalogModel**.  有关详细信息，请参阅[常规 cmdlet （SharePoint 服务器 2010\)](http://go.microsoft.com/fwlink/?LinkID=182375) Microsoft TechNet 网站上。  
  
## 当您尝试查看 SharePoint 中的可视 Web 部件时，会出现一个错误  
 发生此问题时**路径**的用户控件属性不以字符串"CONTROLTEMPLATES\\"。  
  
### 错误消息  
  
-   该文件 \/\_CONTROLTEMPLATES\/*\< 项目名 \>*\/*\< Web 部件名称 \>*\/*\< 用户控件名称 \>*.ascx 不存在。  
  
-   中的服务器错误 \/ 应用程序。  
  
### 解析  
  
##### 要解决此问题  
  
1.  在**解决方案资源管理器**，选择该用户控件文件，其文件扩展名为.ascx。  
  
2.  在菜单栏中，选择**查看**， **属性窗口**。  
  
3.  在**属性** 窗口中，展开 **部署位置**节点。  
  
4.  确保值的**路径**属性以字符串"CONTROLTEMPLATES\\"开头。  
  
## 包含任务窗体字段导入可重用工作流运行时，会出现错误  
 如果您导入的工作流包含任务窗体，其中包含一个字段，并从中导入它的同一系统上运行新的工作流，将出现此问题。  
  
### 错误消息  
 激活功能这一部署步骤中发生错误： Id 字段 *Guid*\] 特征中定义 \[*Guid*\] 当前网站或子网站中找到。  
  
### 解析  
 此错误是因为导入可重用工作流项目中出现的字段 ID 冲突的结果[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]不会更改任务窗体字段 Id。  如果部署在同一台服务器，其中包含原始工作流导入工作流时，会发生字段 ID 冲突。  
  
 若要解决此问题，请使用查找和替换功能更改所有导入的工作流文件中的字段 ID 属性的值。  
  
## 出现错误时重命名导入列表实例运行  
 如果您重命名导入的列表实例，然后在中运行它，会出现此问题 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
### 错误消息  
 生成错误： 激活功能这一部署步骤中发生错误： 文件 Template\\Features\\ *import project* *feature* *name*\] \\Files\\Lists\\ \[*old* *list name*\] \\Schema.xml 不存在。  
  
### 解析  
 导入列表实例时，名为 CustomSchema 的属性添加到列表实例的 Elements.xml 文件中。  Elements.xml 包括自定义的列表实例 schema.xml 的路径。  当您重命名列表实例中的 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、 自定义的 schema.xml 的部署路径发生变化，但不是更新的 CustomSchema 特性的路径值。  因此，列表实例找不到旧功能被激活时，由 CustomSchema 属性指定的路径中的 schema.xml 文件。  
  
 若要解决此问题，请更新的部署位置的 CustomSchema 属性中的 schema.xml 文件的路径。  
  
## SharePoint 调试 IIS 终止会话  
 如果在中设置一个断点，就会发生此问题 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 解决方案选择 F5 键来运行它，并保持不超过 90 秒断点处。  
  
### 错误消息  
 正在调试 Web 服务器进程已终止通过 Internet Information Services \(IIS\)。  通过在 IIS 中配置应用程序池 ping 设置，可以避免此问题。  请参阅，了解详细信息的帮助。  
  
### 解析  
 默认情况下，IIS 应用程序池等待应用程序以响应之前关闭应用程序时，它为 90 秒。  此过程称为"执行 ping 命令" 该应用程序。  若要解决此问题，您可以增加等待时间或禁用应用程序完全 ping。  
  
##### 若要访问的 IIS 应用程序池设置  
  
1.  打开 IIS 管理器中。  
  
2.  在**连接** 窗格中，展开 SharePoint 服务器节点，然后选择 **应用程序池**节点。  
  
3.  在**应用程序池** 页面上，选择 SharePoint 应用程序池 （通常"SharePoint\-80"），然后，在 **操作** 窗格中，选择 **高级设置**链接。  
  
4.  若要增加 IIS 超时前等待的时间，可更改的值 **Ping 最大响应时间 （秒）** 的值大于 90 秒。  
  
5.  若要禁用 IIS 执行 ping 命令，将**启用 Ping** 到 **False**。  
  
## 在 SharePoint 中自动收回叶孤立的列表实例  
 如果您执行以下步骤，将出现此问题。  
  
1.  创建一个包含列表实例中的列表定义 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  选择 F5 键以运行该解决方案。  
  
3.  停止调试，或关闭 SharePoint 网站。  
  
4.  重新打开 SharePoint 网站，然后打开该列表实例。  
  
### 错误消息  
 中的服务器错误 \/ 应用程序。  
  
### 解析  
 发生这种情况是因为 SharePoint 解决方案的调试会话关闭后自动收回功能会收回解决方案。  收回从 SharePoint 中删除该列表定义，但不会删除该列表的实例。  基础列表定义的列表实例需要。  
  
 若要解决此问题，请部署解决方案，通过在菜单栏中选择**生成**， **部署**。 \(不调试解决方案通过选择 F5 键。） 然后，删除在 SharePoint 列表实例。  
  
## 导出版本将替换原始的 SharePoint 解决方案  
 如果导出的 SharePoint 解决方案时，将导入到解决方案 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，然后将解决方案部署到同一网站导出它，原始的 SharePoint 解决方案将被替换。  如果您将解决方案部署到的服务器上没有激活它的原始解决方案未出现此问题。  
  
### 错误消息  
 无。  
  
### 解析  
 若要避免覆盖从中导出的站点上的解决方案，请更改解决方案 Id 的 Guid 和功能 Id 中的所有导入功能的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]项目。  
  
## 当开始调试时出现错误  
 当您开始调试 Visual Studio 中的 SharePoint 解决方案时，则会显示一个错误，指示 Visual Studio 未能加载的 Web.config 文件，因为给定的键不在字典中。  
  
### 错误消息  
 无法加载的 Web.config 配置文件。  检查文件中的任何格式错误的 XML 元素，然后再试。  出现了以下错误: 给定的键时不在字典中。  
  
### 解析  
 若要解决此问题，请确保 SharePoint 项目中，Visual Studio 中的网站 URL 属性值相匹配的 URL 分配给默认区域，以供在 web 应用程序的备用访问映射。  您不能通过 url 中使用另一个区域，例如内联网，来解决该错误。  网站项目的 URL 和默认值区域中的 URL 必须匹配。  若要访问备用访问映射，打开 SharePoint 2010 管理中心实用程序，请选择**应用程序管理** 链接，然后在 **的 Web 应用程序**，选择 **配置备用访问映射**链接。  有关详细信息，请参阅[为 Web 应用程序创建区域](http://go.microsoft.com/fwlink/?LinkId=192274)。  
  
## 请参阅  
 [SharePoint 打包和部署疑难解答](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)   
 [生成和调试 SharePoint 解决方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [使用 Visual Studio 进行调试](../debugger/debugging-in-visual-studio.md)  
  
  