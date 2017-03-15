---
title: "Send 活动设计器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.Send.UI"
ms.assetid: b514f2e4-767c-4b94-ac61-dd3a54d4b96d
caps.latest.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Send 活动设计器
**“Send”**活动设计器用于创建和配置 <xref:System.ServiceModel.Activities.Send> 活动。  
  
## Send 活动  
 <xref:System.ServiceModel.Activities.Send> 活动用于向服务发送消息。作为客户端上请求\/响应消息交换模式的一部分接收消息的 <xref:System.ServiceModel.Activities.ReceiveReply> 活动可绑定到 <xref:System.ServiceModel.Activities.Send> 活动。  
  
### 使用 Send 活动设计器  
 **“Send”**活动设计器可在**“工具箱”**的**“消息传递”**类别中找到，“工具箱”可通过单击 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 中的**“工具箱”**选项卡（或者，从**“视图”**菜单中选择**“工具栏”**或按 Ctrl\+Alt\+X）来访问。  
  
 可以将**“Send”**活动设计器从**“工具箱”**拖放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上通常放置活动的任何位置。这将创建具有 Sent 的默认 <xref:System.Activities.Activity.DisplayName%2A> 的 <xref:System.ServiceModel.Activities.Send> 活动。可以在**“Send”**活动设计器的标头中或在属性网格的**“DisplayName”**框中编辑 <xref:System.Activities.Activity.DisplayName%2A>。  
  
 若要创建 <xref:System.ServiceModel.Activities.ReceiveReply> 活动并将其绑定到所选 <xref:System.ServiceModel.Activities.Send> 活动，请右击**“Send”**活动设计器，然后在上下文菜单中单击**“创建 ReceiveReply”**项，此时**“ReceiveReplyForSend”**设计器将显示在**“Send”**设计器下。<xref:System.ServiceModel.Activities.ReceiveReply> 活动是作为客户端上请求\/响应消息交换模式的一部分接收消息的一个活动。它可通过**“ReceiveReplyForSend”**设计器进行配置。  
  
 另外，**SendAndReceiveReply** 模版设计者在 **消息** 分类的 **工具箱** 可以用来创建一对预配置 <xref:System.ServiceModel.Activities.Send> 和 <xref:System.ServiceModel.Activities.ReceiveReply> 活动。[!INCLUDE[crabout](../test/includes/crabout_md.md)] 使用 **SendAndReceiveReply** 和 **ReceiveReplyForSend** 模版，请参见 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) 主题。  
  
### Sent 活动属性  
 下表列出 <xref:System.ServiceModel.Activities.Send> 属性并说明如何在设计器中使用它们。这些属性可以在属性网格中或 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上进行编辑。  
  
|属性名|必需|用法|  
|---------|--------|--------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.Send> 活动的友好名称。默认值是 Send。虽然 <xref:System.Activities.Activity.DisplayName%2A> 不是绝对必需的，但最好使用该属性。|  
|<xref:System.ServiceModel.Activities.Send.OperationName%2A>|True|由此 <xref:System.ServiceModel.Activities.Send> 活动调用的服务操作的名称。如果未显式设置 **Action** 属性，则此属性用于构造 **Action** 属性的默认值。|  
|<xref:System.ServiceModel.Activities.Send.ServiceContractName%2A>|True|实现了要调用的服务的服务协定的名称。|  
|<xref:System.ServiceModel.Activities.Send.Content%2A>|False|指定要接收的消息或参数内容。它可为 <xref:System.ServiceModel.Activities.ReceiveMessageContent> 活动或 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 活动。编辑此属性的方法是单击属性网格中**“内容”**字段旁的椭圆形按钮，或单击**“Receive”**活动设计器图面上**“内容”**标签旁的**“定义…”**按钮。两者都显示**“内容定义”**对话框。[!INCLUDE[crabout](../test/includes/crabout_md.md)] 本主题演示如何使用对话框，请参见 [“内容定义”对话框](../workflow-designer/content-definition-dialog-box.md) 主题。|  
|<xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A>|False|指定用于将消息路由到相应工作流实例的 <xref:System.ServiceModel.Activities.CorrelationHandle>。<br /><br /> 单击属性旁边的省略号<xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A>，打开**“集合编辑器”**对话框。[!INCLUDE[crabout](../test/includes/crabout_md.md)]使用此对话框，请参见 [如何：使用表达式编辑器](../workflow-designer/how-to-use-the-expression-editor.md) 主题。|  
|<xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A>|False|指定在工作流中对配置此 <xref:System.ServiceModel.Activities.Send> 活动的多个 <xref:System.ServiceModel.Activities.CorrelationHandle> 对象进行初始化的 <xref:System.ServiceModel.Activities.CorrelationInitializer> 对象的集合。单击属性旁边的省略号 <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> 打开 **“添加相关初始值设定项”** 对话框。[!INCLUDE[crabout](../test/includes/crabout_md.md)] 使用对话框，请参见 [“添加相关初始值设定项”对话框](../workflow-designer/add-correlationinitializers-dialog-box.md) 主题。|  
|<xref:System.ServiceModel.Activities.Send.KnownTypes%2A>|False|此 <xref:System.ServiceModel.Activities.Send> 活动要调用的服务操作的已知类型集合。此属性应与设置为 <xref:System.Runtime.Serialization.DataContractSerializer> 的 <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> 属性结合使用。如果使用了 <xref:System.Xml.Serialization.XmlSerializer>，则忽略此项。<br /><br /> 在属性网格中单击**“KnownTypes”**字段旁的椭圆形按钮可显示**“类型集合编辑器”**对话框，使用该对话框可添加相关类型。<br /><br /> 在属性网格中单击**“KnownTypes”**字段旁的椭圆形按钮可显示**“类型集合编辑器”**对话框，使用该对话框可添加相关类型。[!INCLUDE[crabout](../test/includes/crabout_md.md)] 使用对话框，请参见 [“类型集合编辑器”对话框](../workflow-designer/type-collection-editor-dialog-box.md) 主题。|  
|<xref:System.ServiceModel.Activities.Send.ProtectionLevel%2A>|True|指定消息的 <xref:System.Net.Security.ProtectionLevel>。<br /><br /> 1.  <xref:System.Net.Security.ProtectionLevel> 表示仅进行身份验证。<br />2.  <xref:System.Net.Security.ProtectionLevel> 表示对数据进行签名以帮助确保所传输数据的完整性。<br />3.  <xref:System.Net.Security.ProtectionLevel> 表示对数据进行加密和签名以帮助确保所传输数据的保密性和完整性。|  
|<xref:System.ServiceModel.Activities.Send.SerializerOption%2A>|True|<xref:System.ServiceModel.Activities.Send> 活动要调用的服务操作所用的序列化程序。默认值为 <xref:System.Runtime.Serialization.DataContractSerializer>，它使用提供的数据协定将类型实例序列化和反序列化为 XML 流或文档。|  
|<xref:System.ServiceModel.Activities.Send.Action%2A>|False|指定消息的操作标头。如果未显式设置，则其默认值为：https:\/\/tempuri.org\/{服务协定命名空间}\/{服务协定名称}\/{操作名称}。如果该值是对 <xref:System.ServiceModel.Activities.Send> 活动指定的，则接收消息的 <xref:System.ServiceModel.Activities.Receive> 活动必须具有同一值才能正确传递该消息。|  
|<xref:System.ServiceModel.Activities.Send.TokenImpersonationLevel%2A>||<xref:System.Security.Principal.TokenImpersonationLevel> 可用于消息的接收方。默认安全模拟级别控制服务器进程可以在何种程度上代表客户端进程执行操作。<xref:System.Security.Principal.TokenImpersonationLevel> 指示未指定模拟级别。<xref:System.Security.Principal.TokenImpersonationLevel> 指示服务器进程无法获取有关客户端的标识信息，且无法模拟客户端。<xref:System.Security.Principal.TokenImpersonationLevel> 指示服务器可以获取有关客户端的信息（如安全标识符和特权），但它无法模拟客户端。这对于导出自身对象的服务器非常有用，例如，导出表和视图的数据库产品。在不能使用其他正使用客户端安全上下文的服务的情况下，服务器可以使用检索到的客户端安全信息做出访问验证决策。<xref:System.Security.Principal.TokenImpersonationLevel> 指示服务器可以在其本地系统上模拟客户端的安全上下文。服务器无法在远程系统上模拟客户端。<xref:System.Security.Principal.TokenImpersonationLevel> 指示服务器可以在其本地系统上模拟客户端的安全上下文。|  
|<xref:System.ServiceModel.Activities.Send.Endpoint%2A>||<xref:System.ServiceModel.Activities.Send> 活动要将消息发送到的 <xref:System.ServiceModel.Endpoint>。如果设置了此属性，则 <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> 属性应为 **null**。|  
|<xref:System.ServiceModel.Activities.Send.EndpointAddress%2A>||要将消息发送到的 <xref:System.ServiceModel.EndpointAddress>。|  
|<xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A>||终结点配置的名称。要在配置文件中配置一个终结点时设置此属性。此属性应设置为配置文件的 **\<endpoint\>** 元素中给定的名称。如果设置了此属性，则 <xref:System.ServiceModel.Activities.Send.Endpoint%2A> 属性应为 **null**。|  
  
## 请参阅  
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)