---
title: "Send 活动设计器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.ServiceModel.Activities.Send.UI
ms.assetid: b514f2e4-767c-4b94-ac61-dd3a54d4b96d
caps.latest.revision: "7"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: abe4a4f418e2204355d55c16194ea31b939383aa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="send-activity-designer"></a>Send 活动设计器
**发送**活动设计器用于创建和配置<xref:System.ServiceModel.Activities.Send>活动。  
  
## <a name="the-send-activity"></a>Send 活动  
 <xref:System.ServiceModel.Activities.Send> 活动用于向服务发送消息。 作为客户端上请求/响应消息交换模式的一部分接收消息的 <xref:System.ServiceModel.Activities.ReceiveReply> 活动可绑定到 <xref:System.ServiceModel.Activities.Send> 活动。  
  
### <a name="using-the-send-activity-designer"></a>使用 Send 活动设计器  
 **发送**在找不到活动设计器**消息**类别**工具箱**，通过单击访问的哪一**工具箱**选项卡中[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)](或者，选择**工具栏**从**视图**菜单或 CTRL + ALT + X。)  
  
 **发送**活动设计器可以拖动从**工具箱**拖放到[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]图面任何位置通常放置活动的。 这将创建具有 Send 的默认 <xref:System.ServiceModel.Activities.Send> 的 <xref:System.Activities.Activity.DisplayName%2A> 活动。 <xref:System.Activities.Activity.DisplayName%2A>可以在的标头中编辑**发送**活动设计器中或在**DisplayName**属性网格的框。  
  
 若要创建<xref:System.ServiceModel.Activities.ReceiveReply>活动并将其绑定到所选<xref:System.ServiceModel.Activities.Send>活动，右键单击**发送**活动设计器中，单击**创建 ReceiveReply**上下文菜单中的项和**ReceiveReplyForSend**如下所示设计器**发送**设计器。 <xref:System.ServiceModel.Activities.ReceiveReply> 活动是作为客户端上请求/响应消息交换模式的一部分接收消息的一个活动。 可以使用配置**ReceiveReplyForSend**设计器。  
  
 或者， **SendAndReceiveReply**模板设计器中的**消息**类别**工具箱**可以用于创建一对预配置<xref:System.ServiceModel.Activities.Send>和<xref:System.ServiceModel.Activities.ReceiveReply>活动。 [!INCLUDE[crabout](../test/includes/crabout_md.md)]使用**SendAndReceiveReply**和**ReceiveReplyForSend**模板，请参阅[SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)主题。  
  
### <a name="the-send-activity-properties"></a>Send 活动属性  
 下表列出 <xref:System.ServiceModel.Activities.Send> 属性并说明如何在设计器中使用它们。 这些属性可以在属性网格中或 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上进行编辑。  
  
|属性名|必需|用法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.Send> 活动的友好名称。 默认值为 Send。 虽然 <xref:System.Activities.Activity.DisplayName%2A> 不是绝对必需的，但最好使用该属性。|  
|<xref:System.ServiceModel.Activities.Send.OperationName%2A>|True|由此 <xref:System.ServiceModel.Activities.Send> 活动调用的服务操作的名称。 此属性用于构造的默认值为**操作**属性如果**操作**属性未显式设置。|  
|<xref:System.ServiceModel.Activities.Send.ServiceContractName%2A>|True|实现了要调用的服务的服务协定的名称。|  
|<xref:System.ServiceModel.Activities.Send.Content%2A>|False|指定要接收的消息或参数内容。 它可为 <xref:System.ServiceModel.Activities.ReceiveMessageContent> 活动或 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 活动。 通过单击旁的省略号按钮来编辑此属性**内容**在属性网格或单击字段**定义...**按钮旁边**内容**上的标签**接收**活动设计器图面。 两者都显示**内容定义**对话框。 [!INCLUDE[crabout](../test/includes/crabout_md.md)]如何使用此框，请参阅[内容定义对话框](../workflow-designer/content-definition-dialog-box.md)主题。|  
|<xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A>|False|指定用于将消息路由到相应工作流实例的 <xref:System.ServiceModel.Activities.CorrelationHandle>。<br /><br /> 单击省略号按钮旁边<xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A>属性在属性网格中，若要打开**表达式编辑器**对话框。 [!INCLUDE[crabout](../test/includes/crabout_md.md)]使用此对话框中，请参阅[如何： 使用表达式编辑器](../workflow-designer/how-to-use-the-expression-editor.md)主题。|  
|<xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A>|False|指定在工作流中对配置此 <xref:System.ServiceModel.Activities.CorrelationInitializer> 活动的多个 <xref:System.ServiceModel.Activities.CorrelationHandle> 对象进行初始化的 <xref:System.ServiceModel.Activities.Send> 对象的集合。 单击省略号按钮旁边<xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A>属性在属性网格中，若要打开**添加相关初始值设定项**对话框。 [!INCLUDE[crabout](../test/includes/crabout_md.md)]使用此框中，请参阅[添加 CorrelationInitializers 对话框](../workflow-designer/add-correlationinitializers-dialog-box.md)主题。|  
|<xref:System.ServiceModel.Activities.Send.KnownTypes%2A>|False|此 <xref:System.ServiceModel.Activities.Send> 活动要调用的服务操作的已知类型集合。 此属性应与设置为 <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> 的 <xref:System.Runtime.Serialization.DataContractSerializer> 属性结合使用。 如果使用了 <xref:System.Xml.Serialization.XmlSerializer>，则忽略此项。<br /><br /> 单击旁的省略号按钮**KnownTypes**字段在属性网格中显示**类型集合编辑器**与其可添加相关类型的对话框。<br /><br /> 单击旁的省略号按钮**KnownTypes**字段在属性网格中显示**类型集合编辑器**对话框中可以使用该对话框添加相关类型。 [!INCLUDE[crabout](../test/includes/crabout_md.md)]使用此框中，请参阅[类型集合编辑器对话框](../workflow-designer/type-collection-editor-dialog-box.md)主题。|  
|<xref:System.ServiceModel.Activities.Send.ProtectionLevel%2A>|True|指定消息的 <xref:System.Net.Security.ProtectionLevel>。<br /><br /> 1。<xref:System.Net.Security.ProtectionLevel>意味着仅身份验证。<br />2。<xref:System.Net.Security.ProtectionLevel>意味着数据进行签名以帮助确保传输的数据的完整性。<br />3。<xref:System.Net.Security.ProtectionLevel>方法进行加密和签名数据以帮助确保保密性和传输数据的完整性。|  
|<xref:System.ServiceModel.Activities.Send.SerializerOption%2A>|True|<xref:System.ServiceModel.Activities.Send> 活动要调用的服务操作所用的序列化程序。 默认值为 <xref:System.Runtime.Serialization.DataContractSerializer>，它使用提供的数据协定将类型实例序列化和反序列化为 XML 流或文档。|  
|<xref:System.ServiceModel.Activities.Send.Action%2A>|False|指定消息的操作标头。 如果它未显式设置，其默认值为： https://tempuri.org/ {服务协定命名空间} / {服务协定名称} / {操作名称}。 如果该值是对 <xref:System.ServiceModel.Activities.Send> 活动指定的，则接收消息的 <xref:System.ServiceModel.Activities.Receive> 活动必须具有同一值才能正确传递该消息。|  
|<xref:System.ServiceModel.Activities.Send.TokenImpersonationLevel%2A>||<xref:System.Security.Principal.TokenImpersonationLevel> 可用于消息的接收方。 它定义安全模拟级别，控制服务器进程可以向其代表的客户端进程的程度。<xref:System.Security.Principal.TokenImpersonationLevel>指示未分配模拟级别。 <xref:System.Security.Principal.TokenImpersonationLevel> 指示服务器进程无法获取有关客户端的标识信息，且无法模拟客户端。 <xref:System.Security.Principal.TokenImpersonationLevel> 指示服务器进程可以获取有关客户端的信息（如安全标识符和特权），但它无法模拟客户端。 这对于导出自身对象的服务器非常有用，例如，导出表和视图的数据库产品。 在不能使用其他正使用客户端安全上下文的服务的情况下，服务器可以使用检索到的客户端安全信息做出访问验证决策。 <xref:System.Security.Principal.TokenImpersonationLevel> 指示服务器进程可以在其本地系统上模拟客户端的安全上下文。 服务器无法在远程系统上模拟客户端。 <xref:System.Security.Principal.TokenImpersonationLevel> 指示服务器进程可以在远程系统上模拟客户端的安全上下文。|  
|<xref:System.ServiceModel.Activities.Send.Endpoint%2A>||<xref:System.ServiceModel.Endpoint> 活动要将消息发送到的 <xref:System.ServiceModel.Activities.Send>。 如果设置此属性<xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A>属性应为**null**。|  
|<xref:System.ServiceModel.Activities.Send.EndpointAddress%2A>||要将消息发送到的 <xref:System.ServiceModel.EndpointAddress>。|  
|<xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A>||终结点配置的名称。 在配置文件中配置终结点时设置此属性。 此属性应设置为中给定的名称**\<终结点 >**配置文件中的元素。 如果设置此属性，<xref:System.ServiceModel.Activities.Send.Endpoint%2A>属性应为**null**。|  
  
## <a name="see-also"></a>另请参阅  
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [接收](../workflow-designer/receive-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)