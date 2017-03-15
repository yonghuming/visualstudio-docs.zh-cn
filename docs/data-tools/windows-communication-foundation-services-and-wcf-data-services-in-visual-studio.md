---
title: "Windows Communication Foundation Services and WCF Data Services in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "services, WCF Data"
  - "WCF services, binding to"
  - "WCF services, asynchronous service methods"
  - "service references [Visual Studio]"
  - "WCF Data Services"
  - "asynchronous calls"
  - "service references [Visual Studio], type sharing"
  - "endpoints [WCF]"
  - "asynchronous service methods"
  - "service references [Visual Studio] endpoints"
  - "WCF services, type sharing"
  - "Windows Communication Foundation, in Visual Studio"
  - "services, WCF"
  - "WCF service, Visual Studio"
  - "data services, WCF"
  - "services, in Visual Studio"
  - "data binding [Visual Studio], WCF"
  - "service endpoints [Visual Studio]"
  - "service references [Visual Studio], asynchronous calls"
  - "services, Windows Communication Foundation"
  - "type sharing in WCF services"
  - "WCF services, endpoints"
  - "service method, called asynchronously[Visual Studio]"
ms.assetid: d56f12cb-e139-4fec-b3e4-488383356642
caps.latest.revision: 26
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Communication Foundation Services and WCF Data Services in Visual Studio
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 2008 提供了使用 Windows Communication Foundation \(WCF\) 和 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]（用于创建分布式应用程序的 Microsoft 技术）的工具。  本主题从 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的角度介绍了服务。  
  
## 什么是 WCF？  
 [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] 是一个统一框架，用于创建既安全可靠又可交互的分布式事务处理应用程序。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的早期版本中存在一些可用于在应用程序之间进行通信的技术。  
  
 如果要以一种能够实现从任何平台访问信息的方式来共享信息，则应使用 Web 服务（也称为 ASMX Web 服务）。  如果只想在客户端和正在 Windows 操作系统上运行的服务器之间移动数据，则应使用 .NET 远程处理。  如果需要事务处理通信，则应使用企业服务 \(DCOM\)，或者如果需要排队的模型，则应使用消息队列（也称为 MSMQ）。  
  
 WFC 将所有这些技术的功能汇集到一个统一编程模型中。  这简化了开发分布式应用程序的过程。  
  
#### 什么是 WCF 数据服务  
 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] 为可直接与数据库进行交互的服务，它允许您使用标准 HTTP 谓词（如 GET、POST、PUT 或 DELETE）返回数据。  通常，[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] 对于用于创建、更新或删除数据库中的记录的应用程序来说，是一个好选择。  有关更多信息，请参见 [ADO.NET Data Services Framework](http://go.microsoft.com/fwlink/?LinkID=119952)（ADO.NET 数据服务框架）。  
  
### WCF 编程模型  
 WCF 编程模型基于以下两个实体之间的通信：WCF 服务和 WFC 客户端。  该编程模型封装在 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 的 <xref:System.ServiceModel> 命名空间中。  
  
#### WCF 服务  
 WCF 服务基于一个定义服务与客户端之间的协定的接口。  它是用 <xref:System.ServiceModel.ServiceContractAttribute> 特性进行标记的，如下列代码中所示：  
  
 [!code-cs[WCFWalkthrough#6](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.cs)]
 [!code-vb[WCFWalkthrough#6](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.vb)]  
  
 [!code-cs[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.cs)]
 [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.vb)]  
  
 通过使用 <xref:System.ServiceModel.OperationContractAttribute> 特性标记 WCF 服务公开的函数和方法，可以定义这些函数和方法。  另外，通过使用 <xref:System.Runtime.Serialization.DataContractAttribute> 特性标记复合类型，可以公开序列化数据。  这样可以在客户端中进行数据绑定。  
  
 定义了接口及其方法后，会将它们封装在一个实现该接口的类中。  单一的 WCF 服务类可以实现多个服务协定。  
  
 为了使用 WCF 服务，通过通常所说的“终结点”公开了此服务。  只有使用终结点提供的方法才能与服务进行通信；您不能像访问其他类那样通过直接引用来访问该服务。  
  
 终结点由地址、绑定和协定组成。  地址定义服务的位置；该地址可以是 URL、FTP 地址、网络路径或本地路径。  绑定定义与服务通信的方法。  WCF 绑定提供一个用于指定协议（如 HTTP 和 FTP）、安全机制（如 Windows 身份验证或用户名和密码）和更多内容的通用模型。  协定包括 WCF 服务类公开的操作。  
  
 可以针对单一的 WCF 服务公开多个终结点。  这样，不同的客户端便可以采用不同的方法与同一服务进行通信。  例如，银行服务可以为雇员提供一个终结点，为外部客户提供另一个终结点，每个终结点都使用不同的地址、绑定、和\/或协定。  
  
#### WCF 客户端  
 WCF 客户端由“代理”和终结点所组成，前者使应用程序能够与 WCF 服务通信，后者与针对服务定义的终结点相匹配。  该代理在 app.config 文件中的客户端上生成并包括有关服务所公开的类型和方法的信息。  例如，对于公开多个终结点的服务，客户端可以选择最能满足其需求的服务，以便通过 HTTP 进行通信以及使用 Windows 身份验证。  
  
 创建 WCF 客户端后，可以像引用任何其他对象那样在代码中引用服务。  例如，若要调用之前显示的 `GetData` 方法，则应编写与下列内容相似的代码：  
  
 [!code-cs[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.cs)]
 [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.vb)]  
  
## Visual Studio 中的 WCF 工具  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 2008 提供帮助创建 WCF 服务和 WCF 客户端的工具。  有关演示这些工具的演练，请参见[Walkthrough: Creating and Accessing WCF Services](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)。  
  
### 创建并测试 WCF 服务  
 可以使用 WCF [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 模板为基础快速创建自己的服务。  然后可以使用 WCF 服务自动主机和 WCF 测试客户端来调试和测试此服务。  通过共同使用这些工具，可以快速方便地进行调试和测试，从而缩短调试和测试周期，并且不必在早期阶段提交给承载模型。  
  
#### WCF 模板  
 WCF [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 模板为服务开发提供一个基类结构。  在**“添加新项目”**对话框中可以使用一些 WCF 模板。  这些模板包括 WCF 服务库项目、WCF 服务网站、和 WCF 服务项模板。  
  
 选择模板时，将为服务协定、服务实现、以及服务配置添加文件。  所有必需的特性都已添加，同时将创建简单的“Hello World”服务类型，且不必编写任何代码。  当然，您将需要添加代码以便为实际服务提供函数和方法，但是模板会提供基础。  
  
 若要了解有关 WCF 模板的更多信息，请参见 [WCF Visual Studio 模板](../Topic/WCF%20Visual%20Studio%20Templates.md)。  
  
#### WCF 服务主机  
 为 WCF 服务项目启动 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 调试程序（通过按 F5）时，将自动启动 WCF 服务主机工具以便以本地方式承载服务。  WCF 服务主机将枚举 WCF 服务项目中的服务、加载该项目的配置、并为它所找到的每个服务实例化主机。  
  
 通过使用 WCF 服务主机，可以测试 WCF 服务，而不用在开发期间编写额外代码或提交给特定主机。  
  
 若要了解有关 WCF 服务主机的更多信息，请参见 [WCF 服务主机 \(WcfSvcHost.exe\)](../Topic/WCF%20Service%20Host%20\(WcfSvcHost.exe\).md)。  
  
#### WCF 测试客户端  
 通过使用 WCF 测试客户端工具，可以输入测试参数、将该输入提交给 WCF 服务、并查看该服务发送回的响应。  如果将 WCF 测试客户端与 WCF 服务主机结合起来，会提供满意的服务测试体验。  
  
 按 F5 调试 WCF 服务项目时，WCF 测试客户端将打开并显示在配置文件中定义的服务终结点的列表。  可以测试参数并启动服务，重复此过程以连续测试和验证您的服务。  
  
 若要了解有关 WCF 测试客户端的更多信息，请参见 [WCF 测试客户端 \(WcfTestClient.exe\)](../Topic/WCF%20Test%20Client%20\(WcfTestClient.exe\).md)。  
  
### 在 Visual Studio 中访问 WCF 服务  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 简化创建 WCF 客户端的任务，自动生成代理和终结点。使用 **添加服务引用** 对话框，您添加的服务。  所有必需的配置信息将添加到 app.config 文件中。大多数情况下，只需实例化该服务便可以使用它。  
  
 通过使用**“添加服务引用”**对话框，可以输入服务的地址或搜索在解决方案中定义的服务。  该对话框将返回由服务和这些服务提供的操作所组成的列表。  通过使用此对话框，还可以定义用于在代码中引用服务的命名空间。  
  
 通过使用**“配置服务引用”**对话框，可以自定义服务的配置。  可以更改服务地址，指定访问级别、异步行为和消息协定类型，以及配置类型重用。  
  
## 如何:选择一个服务终结点  
 有些 Windows Communication Foundation \(WCF\) 服务公开多个终结点，客户端可通过这些终结点与服务进行通信。  例如，某个服务可能会公开两个终结点，一个使用 HTTP 绑定和用户名\/密码安全性，而另一个使用 FTP 和 Windows 身份验证。  第一个终结点可由从防火墙外部访问服务的应用程序使用，而第二个终结点可在 Intranet 上使用。  
  
 在这种情况下，可将 `endpointConfigurationName` 指定为服务引用的构造函数的参数。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### 选择服务终结点  
  
1.  添加对 WCF 服务的引用。  有关更多信息，请参见[How to: Add, Update, or Remove a Service Reference](../Topic/How%20to:%20Add,%20Update,%20or%20Remove%20a%20Service%20Reference.md)。  
  
2.  在代码编辑器中，为该服务引用添加一个构造函数：  
  
    ```vb#  
    Dim proxy As New ServiceReference.Service1Client(  
    ```  
  
    ```c#  
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(  
    ```  
  
    > [!NOTE]
    >  将 *ServiceReference* 替换为该服务引用的命名空间，并将 *Service1Client* 替换为该服务的名称。  
  
3.  此时将显示一个 IntelliSense 列表，其中包含该构造函数的重载。  选择 `endpointConfigurationName As String` 重载。  
  
4.  在该重载后面，键入 `=` *配置名*，其中*配置名* 是要使用的终结点的名称。  
  
    > [!NOTE]
    >  如果不知道可用终结点的名称，可在 app.config 文件中查找它们。  
  
#### 查找 WCF 服务的可用终结点  
  
1.  在**“解决方案资源管理器”**中，右击包含该服务引用的项目的 app.config 文件，然后单击**“打开”**。  该文件将显示在代码编辑器中。  
  
2.  在该文件中搜索 `<Client>` 标记。  
  
3.  在 `<Client>` 标记下方搜索以 `<Endpoint>` 开头的标记。  
  
     如果该服务引用提供了多个终结点，则会有两个或更多 `<Endpoint` 标记。  
  
4.  在 `<EndPoint>` 标记中，您可以找到 `name="`*SomeService*`"` 参数（其中 *SomeService* 表示终结点名称）。  这是以下终结点的名称：该终结点可传递给服务引用的构造函数的 `endpointConfigurationName As String` 重载。  
  
## 如何:异步调用服务方法  
 可同步或异步调用 Windows Communication Foundation \(WCF\) 服务中的大多数方法。  在应用程序通过很慢的连接运行时，异步调用方法使应用程序在调用此方法的过程中可继续运行。  
  
 默认情况下，在向项目添加服务引用时，该服务引用将配置为同步调用方法。  可以通过在**“配置服务引用”**对话框中更改设置将这一行为更改为异步调用方法。  
  
> [!NOTE]
>  该选项是逐服务设置的。  如果某一服务有一个方法是异步调用的，则所有方法都必须异步调用。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### 异步调用服务方法  
  
1.  在**“解决方案资源管理器”**中，选择服务引用。  
  
2.  在**“项目”**菜单上，单击**“配置服务引用”**。  
  
3.  在**“配置服务引用”**对话框中，选中**“生成异步操作”**复选框。  
  
## 如何:服务返回的数据绑定  
 可以将 Windows Communication Foundation \(WCF\) 服务返回的数据绑定到控件，就像可以将任何其他数据源绑定到控件一样。  添加对 WCF 服务的引用时，如果该服务包含返回数据的复合类型，则这些复合类型会自动添加到**“数据源”**窗口。  
  
#### 将控件绑定到 WCF 服务返回的单个数据字段  
  
1.  在**“数据”**菜单上，单击**“显示数据源”**。  将出现**“数据源”**窗口。  
  
2.  在**“数据源”**窗口中，展开服务引用的节点。  将显示该服务返回的所有复合类型。  
  
3.  展开类型的一个节点。  将显示该类型的数据字段。  
  
4.  选择一个字段，然后单击下拉箭头以显示可用于该数据类型的控件列表。  
  
5.  单击要绑定到的控件的类型。  
  
6.  将此字段拖到窗体上。  此控件将连同一个 <xref:System.Windows.Forms.BindingSource> 组件和一个 <xref:System.Windows.Forms.BindingNavigator> 组件一起添加到窗体上。  
  
7.  对您要绑定的所有其他字段重复执行步骤 4 至步骤 6。  
  
#### 将控件绑定到 WCF 服务返回的复合类型  
  
1.  在**“数据”**菜单上，选择**“显示数据源”**。  将出现**“数据源”**窗口。  
  
2.  在**“数据源”**窗口中，展开服务引用的节点。  将显示该服务返回的所有复合类型。  
  
3.  选择某一类型的一个节点，然后单击下拉箭头以显示可用选项的列表。  
  
4.  单击**“数据网格视图”**以显示网格中的数据，或单击**“详细信息”**以显示各个控件中的数据。  
  
5.  将此节点拖到窗体上。  这些控件将连同一个 <xref:System.Windows.Forms.BindingSource> 组件和一个 <xref:System.Windows.Forms.BindingNavigator> 组件一起添加到窗体上。  
  
## 如何:配置一个服务重用现有类型  
 向项目添加服务引用时，将在本地项目中生成该服务中定义的所有类型。  在很多情况下，如果服务使用的是通用 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 类型或类型是在共享库中定义的，这会创建重复的类型。  
  
 为避免此问题，默认情况下会共享引用的程序集中的类型。  如果要对一个或多个程序集禁用类型共享，则可在**“配置服务引用”**对话框中进行此操作。  
  
#### 在单个程序集中禁用类型共享  
  
1.  在**“解决方案资源管理器”**中，选择服务引用。  
  
2.  在**“项目”**菜单上，单击**“配置服务引用”**。  
  
3.  在**“配置服务引用”**对话框中，选择**“重新使用所引用的指定程序集中的类型”**。  
  
4.  选中您要启用类型共享的每个程序集的复选框。  若要对某一程序集禁用类型共享，请将其复选框保留清除状态。  
  
#### 在所有程序集中禁用类型共享  
  
1.  在**“解决方案资源管理器”**中，选择服务引用。  
  
2.  在**“项目”**菜单上，单击**“配置服务引用”**。  
  
3.  在**“配置服务引用”**对话框中，清除**“重新使用引用的程序集中的类型”**复选框。  
  
## 相关主题  
  
|标题|说明|  
|--------|--------|  
|[Walkthrough: Creating and Accessing WCF Services](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)|逐步演示了如何在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中创建和使用 WCF 服务。|  
|[Walkthrough: Creating and Accessing a WCF Data Service in Visual Studio](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md)|逐步演示了如何在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中创建和使用 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]。|  
|[使用 WCF 开发工具](../Topic/Using%20the%20WCF%20Development%20Tools.md)|讨论如何在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中创建和测试 WCF 服务。|  
|[How to: Add, Update, or Remove a Service Reference](../Topic/How%20to:%20Add,%20Update,%20or%20Remove%20a%20Service%20Reference.md)|描述如何从项目中添加、更新或移除 WCF 服务。|  
|[How to: Add, Update, or Remove a WCF Data Service Reference](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)|讨论如何在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中引用和使用 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]。|  
|[How to: Add a Reference to a Web Service](../Topic/How%20to:%20Add%20a%20Reference%20to%20a%20Web%20Service.md)|描述如何将对 XML \(ASMX\) Web 服务的引用添加到项目中。|  
|[Troubleshooting Service References](../data-tools/troubleshooting-service-references.md)|介绍服务引用可能发生的一些常见错误以及如何防止这些错误。|  
|[调试 WCF 服务](../debugger/debugging-wcf-services.md)|描述在调试 WCF 服务时可能会遇到的常见调试问题和技术。|  
|[Windows Communication Foundation Authentication Service Overview](../Topic/Windows%20Communication%20Foundation%20Authentication%20Service%20Overview.md)|描述如何使用 WCF 为网站提供角色服务。|  
|[Messaging in the .NET Compact Framework](http://msdn.microsoft.com/zh-cn/fb74d82c-f81e-46f9-aceb-f875c5c6be4f)|描述 .NET Compact Framework 中对 WCF 消息处理层的支持。|  
|[演练：创建 N 层数据应用程序](../data-tools/walkthrough-creating-an-n-tier-data-application.md)|提供分步说明，介绍如何创建类型化数据集，并将 TableAdapter 和数据集代码分离到多个项目中。|  
|[Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md)|描述**“添加服务引用”**对话框的用户界面元素。|  
|[“配置服务引用”对话框](../data-tools/configure-service-reference-dialog-box.md)|描述**“配置服务引用”**对话框的用户界面元素。|  
  
## 引用  
 <xref:System.ServiceModel>  
  
 <xref:System.Data.Services>