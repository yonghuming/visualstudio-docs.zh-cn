---
title: "Windows Communication Foundation 服务和 Visual Studio 中的 WCF 数据服务 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- services, WCF Data
- WCF services, binding to
- WCF services, asynchronous service methods
- service references [Visual Studio]
- WCF Data Services
- asynchronous calls
- service references [Visual Studio], type sharing
- endpoints [WCF]
- asynchronous service methods
- service references [Visual Studio] endpoints
- WCF services, type sharing
- Windows Communication Foundation, in Visual Studio
- services, WCF
- WCF service, Visual Studio
- data services, WCF
- services, in Visual Studio
- data binding [Visual Studio], WCF
- service endpoints [Visual Studio]
- service references [Visual Studio], asynchronous calls
- services, Windows Communication Foundation
- type sharing in WCF services
- WCF services, endpoints
- service method, called asynchronously[Visual Studio]
ms.assetid: d56f12cb-e139-4fec-b3e4-488383356642
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 39c9ac7b1cbed8c64ee3b87fde4c990f998157a4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Visual Studio 中的 Windows Communication Foundation 服务和 WCF 数据服务
Visual Studio 提供用于处理与 Windows Communication Foundation (WCF) 的工具和[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]，Microsoft 技术，用于创建分布式应用程序。 本主题提供介绍了从服务[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]透视。 有关完整文档，请参阅[WCF 数据服务 4.5](/dotnet/framework/data/wcf/index)。  
  
## <a name="what-is-wcf"></a>WCF 是什么？  
 [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)]是一个统一的框架，用于创建安全、 可靠、 事务处理，且可互操作的分布式应用程序。 它将替换较旧的进程间通信技术，如 ASMX Web 服务、.NET 远程处理、 企业服务 (DCOM) 和 MSMQ。 WCF 将结合在一起的下一个统一的编程模型的所有这些技术的功能。 这可以简化开发分布式应用程序的体验。  
  
#### <a name="what-are-wcf-data-services"></a>WCF 数据服务有哪些？  
 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]是标准的开放数据 (OData) 协议的实现。  WCF 数据服务，您可以将表格数据公开为一组 REST Api，从而可以返回数据，如使用标准 HTTP 谓词 GET、 POST、 PUT 或 DELETE。 在服务器端中，WCF 数据服务正在被取代[ASP.NET Web API](http://www.asp.net/web-api)用于创建新的 OData 服务。 WCF 数据服务客户端库仍然是一个不错的选择为使用.NET 应用程序从 Visual Studio 中的 OData 服务 (**项目 &#124;添加服务引用**)。 有关详细信息，请参阅[WCF 数据服务 4.5](http://go.microsoft.com/fwlink/?LinkID=119952)。  
  
### <a name="wcf-programming-model"></a>WCF 编程模型  
 WCF 编程模型基于两个实体之间的通信： WCF 服务和 WCF 客户端。 编程模型封装在<xref:System.ServiceModel>中的命名空间[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。  
  
#### <a name="wcf-service"></a>WCF 服务  
 WCF 服务开始算起定义服务和客户端之间的协定的接口。 将标有<xref:System.ServiceModel.ServiceContractAttribute>特性，如以下代码所示：  
  
 [!code-csharp[WCFWalkthrough#6](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.cs)]
 [!code-vb[WCFWalkthrough#6](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.vb)]  
  
 [!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.cs)]
 [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.vb)]  
  
 定义函数或方法，将其与标记公开的 WCF 服务<xref:System.ServiceModel.OperationContractAttribute>属性。 此外，您可以公开标记的复合类型的序列化的数据<xref:System.Runtime.Serialization.DataContractAttribute>属性。 这使客户端中的数据绑定。  
  
 定义一个接口和其方法后，将它们封装在实现接口的类。 单一的 WCF 服务类可以实现多个服务协定。  
  
 WCF 服务公开的消耗通过什么称为*终结点*。 终结点提供与服务; 通信的唯一方法就像对待其他类，不能通过直接引用访问服务。  
  
 终结点由地址、 绑定和协定组成。 地址用于定义服务所在的位置;这可能是一个 URL，将 FTP 地址，或网络或本地路径。 绑定所定义的与服务通信的方式。 WCF 绑定提供了通用模型来指定协议，如 HTTP 或 FTP，如 Windows 身份验证或用户名和密码，一种安全机制，等等。 协定包含由 WCF 服务类公开的操作。  
  
 可将单个 WCF 服务公开多个终结点。 这样不同客户端与同一服务通信以不同的方式。 例如，银行服务可能会提供一个终结点为员工和另一个外部客户的每个使用不同的地址、 绑定和/或协定。  
  
#### <a name="wcf-client"></a>WCF 客户端  
 WCF 客户端组成*代理*这样的应用程序与 WCF 服务进行通信并为服务定义与终结点匹配的终结点。 该代理在 app.config 文件中的客户端上生成，并包括信息的类型和由服务公开的方法。 对于公开多个终结点的服务，客户端可以选择一个最适合其需求，例如，若要通过 HTTP 进行通信和使用 Windows 身份验证。  
  
 创建 WCF 客户端后，你服务你在代码中引用就像任何其他对象。 例如，若要调用`GetData`显示更早版本，则应编写如下所示的代码的方法：  
  
 [!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.cs)]
 [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.vb)]  
  
## <a name="wcf-tools-in-visual-studio"></a>Visual Studio 中的 WCF 工具  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]提供工具以帮助您创建 WCF 服务和 WCF 客户端。 有关演示工具的演练，请参阅[演练： 在 Windows 窗体中创建一个简单的 WCF 服务](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)。  
  
### <a name="creating-and-testing-wcf-services"></a>创建和测试 WCF 服务  
 您可以使用 WCF[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]模板为基础快速创建你自己的服务。 然后可以使用 WCF 服务自动主机和 WCF 测试客户端进行调试和测试服务。 这些工具一起提供快速方便地完成调试和测试周期，并使无需在早期阶段提交给承载模型。  
  
#### <a name="wcf-templates"></a>WCF 模板  
 WCF[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]模板为服务开发提供基本的类结构。 可以使用在一些 WCF 模板**添加新项目**对话框。 其中包括 WCF 服务库项目、 WCF 服务网站和 WCF 服务项模板。  
  
 当你选择的模板时，文件将添加为服务协定、 服务实现和服务配置。 已添加所有必需的属性，创建简单的"Hello World"类型的服务，并不需要编写任何代码。 你将当然，想要添加代码以提供函数和方法用于实际服务，但模板提供了基本的基础。  
  
 若要了解有关 WCF 模板的详细信息，请参阅[WCF Visual Studio 模板](/dotnet/framework/wcf/wcf-vs-templates)。  
  
#### <a name="wcf-service-host"></a>WCF 服务主机  
 当你启动[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]调试器 （通过按 F5） 的 WCF 服务项目中，工具会自动启动承载服务本地 WCF 服务主机。 WCF 服务主机枚举 WCF 服务项目中的服务、 加载项目的配置，并为它找到的每个服务主机进行实例化。  
  
 通过使用 WCF 服务主机，可以测试 WCF 服务，而无需额外编写代码或在开发过程中提交到特定的主机。  
  
 若要了解有关 WCF 服务主机的详细信息，请参阅[WCF 服务主机 (WcfSvcHost.exe)](/dotnet/framework/wcf/wcf-service-host-wcfsvchost-exe)。  
  
#### <a name="wcf-test-client"></a>WCF 测试客户端  
 WCF 测试客户端工具使您能够输入测试参数、 将提交的输入的 WCF 服务，并查看服务发回的响应。 它可以提供方便服务时将其与 WCF 服务主机中结合测试体验。 在 \Common7\IDE 文件夹中，即 for Visual Studio 2015 安装在驱动器 c： 此处可以找到此工具： **C:\Program Files (x86) \Microsoft Visual Studio 14.0\Common7\IDE\\**。  
  
 按 F5 调试 WCF 服务项目时，WCF 测试客户端将打开并显示在配置文件中定义的服务终结点的列表。 你可以测试参数和启动服务，且不重复此过程以继续测试和验证你的服务。  
  
 若要了解有关 WCF 测试客户端的详细信息，请参阅[WCF 测试客户端 (WcfTestClient.exe)](/dotnet/framework/wcf/wcf-test-client-wcftestclient-exe)。  
  
### <a name="accessing-wcf-services-in-visual-studio"></a>访问 Visual Studio 中的 WCF 服务  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]简化了创建自动生成代理和通过使用添加的服务的终结点的 WCF 客户端的任务**添加服务引用**对话框。 所有必要的配置信息添加到 app.config 文件中。 大多数情况下，你所要做的所有实例化服务才能使用它。  
  
 **添加服务引用**对话框中，可以输入服务的地址或搜索在你的解决方案中定义的服务。 对话框中返回服务和这些服务提供的操作的列表。 它还可定义将依据引用代码中的服务的命名空间。  
  
 **配置服务引用**对话框允许你自定义服务的配置。 你可以更改服务的地址，指定访问级别、 异步行为和消息协定类型，并配置类型重用。  
  
## <a name="how-to-select-a-service-endpoint"></a>如何： 选择服务终结点  
某些 Windows Communication Foundation (WCF) 服务公开通过该客户端可能与服务通信的多个终结点。 例如，服务可能会公开一个终结点使用 HTTP 绑定和用户名称 / 密码安全和使用 FTP 和 Windows 身份验证的第二个终结点。 第一个终结点可能使用的应用程序访问防火墙之外，从服务中，而可能在 intranet 上使用第二个。  
  
在这种情况下，你可以指定`endpointConfigurationName`作为参数传递给服务引用的构造函数。  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-select-a-service-endpoint"></a>若要选择的服务终结点  
  
1.  右键单击解决方案资源管理器中的项目节点并选择添加到 WCF 服务的引用**添加服务引用**。
  
2.  在代码编辑器中，添加服务引用的构造函数：  
  
    ```vb  
    Dim proxy As New ServiceReference.Service1Client(  
    ```  
  
    ```csharp  
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(  
    ```  
  
    > [!NOTE]
    >  替换*ServiceReference*服务引用和替换的命名空间与*Service1Client*与服务的名称。  
  
3.  智能感知列表将显示具有构造函数重载。 选择`endpointConfigurationName As String`重载。  
  
4.  该重载后面，键入`=` *ConfigurationName*，其中*ConfigurationName*是你想要使用的终结点的名称。  
  
    > [!NOTE]
    >  如果不知道的可用终结点的名称，你可以在 app.config 文件中找到它们。  
  
#### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>若要查找的可用终结点的 WCF 服务  
  
1.  在**解决方案资源管理器**，右键单击包含服务引用的项目的 app.config 文件，然后单击**打开**。 该文件将显示在代码编辑器中。  
  
2.  搜索`<Client>`文件中的标记。  
  
3.  下方搜索`<Client>`开头的标记的标记`<Endpoint>`。  
  
     如果服务引用提供了多个终结点，将有两个或多个`<Endpoint`标记。  
  
4.  内部`<EndPoint>`标记将查找`name="` *SomeService* `"`参数 (其中*SomeService*表示终结点名称)。 这是可以传递给终结点的名称`endpointConfigurationName As String`的服务引用的构造函数重载。  
  
## <a name="how-to-call-a-service-method-asynchronously"></a>如何： 以异步方式调用服务方法  
Windows Communication Foundation (WCF) 服务中的大多数方法可能是同步还是异步调用。 以异步方式调用的方法使应用程序能够继续工作时通过慢速连接运行时调用该方法。  
  
默认情况下，服务引用添加到项目时它配置为以同步方式调用方法。 你可以更改行为，以便以异步方式调用方法，通过更改中的设置**配置服务引用**对话框。  
  
> [!NOTE]
>  此选项设置每个服务为准。 如果以异步方式调用服务的一个方法，必须以异步方式调用所有方法。  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-call-a-service-method-asynchronously"></a>以异步方式调用服务方法  
  
1.  在**解决方案资源管理器**，选择服务引用。  
  
2.  上**项目**菜单上，单击**配置服务引用**。  
  
3.  在**配置服务引用**对话框中，选择**生成异步操作**复选框。  
  
## <a name="how-to-bind-data-returned-by-a-service"></a>如何： 将由服务返回的数据绑定  
你可以将绑定到控件返回由 Windows Communication Foundation (WCF) 服务，就像可以将任何其他数据源绑定到控件的数据。 当你添加到 WCF 服务的引用，如果服务包含返回数据的复合类型时，会自动添加到**数据源**窗口。  
  
#### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>若要将控件绑定到 WCF 服务返回的单个数据字段  
  
1.  在 **“数据”** 菜单上，单击 **“显示数据源”**。 **数据源**窗口将会显示。  
  
2.  在**数据源**窗口中，展开服务引用节点。 将显示服务返回的任何复合类型。  
  
3.  展开一种类型的节点。 将显示该类型的数据字段。  
  
4.  选择字段，并单击下拉箭头以显示可用于的数据类型的控件的列表。  
  
5.  单击你想要绑定到控件的类型。  
  
6.  将字段拖到窗体上。 该控件将添加到窗体连同<xref:System.Windows.Forms.BindingSource>组件和<xref:System.Windows.Forms.BindingNavigator>组件。  
  
7.  请重复步骤 4 到 6 的任何其他字段，你想要绑定。  
  
#### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>若要将控件绑定到 WCF 服务返回的复合类型  
  
1.  上**数据**菜单上，选择**显示数据源**。 **数据源**窗口将会显示。  
  
2.  在**数据源**窗口中，展开服务引用节点。 将显示服务返回的任何复合类型。  
  
3.  选择一种类型的节点，然后单击下拉箭头以显示可用选项的列表。  
  
4.  单击**DataGridView**以在网格中显示数据或**详细信息**以在单独控件中显示数据。  
  
5.  将节点拖到窗体。 这些控件将添加到窗体连同<xref:System.Windows.Forms.BindingSource>组件和<xref:System.Windows.Forms.BindingNavigator>组件。  
  
## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>如何： 配置服务以重新使用现有的类型  
服务引用添加到项目中，在服务中定义的所有类型的本地项目中都生成。 在许多情况下，这将创建重复的类型时服务使用常见[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]类型在共享库的定义时。  
  
若要避免此问题，默认情况下共享引用的程序集中的类型。 如果你想要禁用类型共享的一个或多个程序集，则可以在执行**配置服务引用**对话框。  
  
#### <a name="to-disable-type-sharing-in-a-single-assembly"></a>若要在单个程序集禁用类型共享  
  
1.  在**解决方案资源管理器**，选择服务引用。  
  
2.  上**项目**菜单上，单击**配置服务引用**。  
  
3.  在**配置服务引用**对话框中，选择**重新使用类型指定引用的程序集中**。  
  
4.  每个程序集想要启用类型共享选中的复选框。 若要禁用类型共享的程序集，请清除复选框。  
  
#### <a name="to-disable-type-sharing-in-all-assemblies"></a>若要在所有程序集禁用类型共享  
  
1.  在**解决方案资源管理器**，选择服务引用。  
  
2.  上**项目**菜单上，单击**配置服务引用**。  
  
3.  在**配置服务引用**对话框中，清除**重新使用引用的程序集中的类型**复选框。  
  
## <a name="related-topics"></a>相关主题  
  
|标题|描述|  
|-----------|-----------------|  
|[演练：在 Windows 窗体中创建简单的 WCF 服务](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)|提供创建和使用中的 WCF 服务的分步演示[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。|  
|[演练：通过 WPF 和 Entity Framework 创建 WCF 数据服务](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md)|提供如何创建和使用的分步演示[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]中[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。|  
|[使用 WCF 开发工具](/dotnet/framework/wcf/using-the-wcf-development-tools)|讨论如何创建和测试中的 WCF 服务[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。|  
||[如何：添加、更新或删除 WCF 数据服务引用](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)|讨论如何引用并使用[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]中[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。|  
|[服务引用疑难解答](../data-tools/troubleshooting-service-references.md)|提供服务引用以及如何使它们可以发生的一些常见错误。|  
|[调试 WCF 服务](../debugger/debugging-wcf-services.md)|描述常见调试问题和调试 WCF 服务时可能遇到的技术。|  
|[Windows Communication Foundation 身份验证服务概述](http://msdn.microsoft.com/Library/6e121a28-89e8-4974-88a8-70aaa6a7d52b)|描述如何使用 WCF 可提供一种角色服务网站。|  
|[演练：创建 N 层数据应用程序](../data-tools/walkthrough-creating-an-n-tier-data-application.md)|提供有关创建类型化数据集并将 TableAdapter 和数据集代码分离到多个项目中的分步说明。|  
|[“配置服务引用”对话框](../data-tools/configure-service-reference-dialog-box.md)|描述的用户界面元素**配置服务引用**对话框。|  
  
## <a name="reference"></a>参考  
 <xref:System.ServiceModel>  
  
 <xref:System.Data.Services>  
  
## <a name="see-also"></a>另请参阅  
 [适用于 NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)