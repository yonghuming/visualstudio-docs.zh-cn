---
title: "Troubleshooting Service References | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther"
  - "msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo"
  - "msvse_wcf.Err.ErrorOnOK"
  - "msvse_wcf.cfg.ConfigurationErrorsException"
helpviewer_keywords: 
  - "service references [Visual Studio], troubleshooting"
  - "WCF services, troubleshooting"
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
caps.latest.revision: 22
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Troubleshooting Service References
本主题列出了在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中使用 [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)]或 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]引用时可能会发生的常见问题。  
  
## 从服务返回数据时出错  
 当您从服务返回 `DataSet` 或 `DataTable` 时，可能会收到“已超过传入消息的最大大小配额”异常。  默认情况下，某些绑定的 `MaxReceivedMessageSize` 属性设置为相对较小的值，以限制受到拒绝服务攻击的可能性。  您可以增大此值以防止出现此异常。  有关更多信息，请参见 <xref:System.ServiceModel.BasicHttpBinding.MaxReceivedMessageSize%2A>。  
  
 修复此错误的方法为：  
  
1.  在**“解决方案资源管理器”**中，双击 app.config 文件将其打开。  
  
2.  找到 `MaxReceivedMessageSize` 属性并将其更改为一个较大的值。  
  
## 在“我的解决方案”中找不到服务  
 当您在**“添加服务引用”**对话框中单击**“发现”**按钮时，解决方案中的一个或多个 WCF 服务库项目不显示在服务列表中。  如果服务库已添加到解决方案中但尚未编译，则会发生这种情况。  
  
 修复此错误的方法为：  
  
-   在**“解决方案资源管理器”**中，右击相应的 WCF 服务库项目，再单击**“生成”**。  
  
## 通过远程桌面访问服务时出错  
 如果用户通过远程桌面连接访问 Web 承载的 WCF 服务并且该用户没有管理权限，则会采用 NTLM 身份验证。  如果用户没有管理权限，则该用户可能会收到如下错误消息：“HTTP 请求未经客户端身份验证方案‘Anonymous’授权。  从服务器收到的身份验证标头为‘NTLM’”。  
  
 修复此错误的方法为：  
  
1.  在网站项目中，打开**“属性”**页。  
  
2.  在**“启动选项”**选项卡上，清除**“NTLM 身份验证”**复选框。  
  
    > [!NOTE]
    >  仅应对只包含 WCF 服务的网站关闭 NTLM 身份验证。  WCF 服务的安全性是通过 web.config 文件中的配置管理的。  因此无需进行 NTLM 身份验证。  
  
 有关更多信息，请参见[关于异常的疑难解答：System.ServiceModel.Security.MessageSecurityException](../misc/troubleshooting-exceptions-system-servicemodel-security-messagesecurityexception.md)。  
  
## “生成的类的访问级别”设置无效  
 将**“配置服务引用”**对话框中的**“生成的类的访问级别”**选项设置为**“Internal”**或**“Friend”**可能并不总是起作用。  尽管看起来在此对话框中设置了此选项，但所得到的支持类将是以 `Public` 访问级别生成的。  
  
 这是某些类型（例如，那些使用 <xref:System.Xml.Serialization.XmlSerializer> 序列化的类型）的已知限制。  
  
## 调试服务代码时出错  
 从客户端代码进入并单步执行 WCF 服务的代码时，您可能会收到一条与缺少符号有关的错误消息。  当作为解决方案组成部分的某项服务发生移动或从解决方案中移除时，可能会发生此情况。  
  
 第一次添加对作为当前解决方案组成部分的某项 WCF 服务的引用时，该服务项目和服务客户端项目之间会添加一个显式生成依赖项。  这样可以确保客户端能够始终访问最新的服务二进制文件，这对于调试方案（如从客户端代码进入并单步执行服务代码）尤其重要。  
  
 如果从解决方案中移除该服务项目，此显式生成依赖项会失效。  Visual Studio 将无法再保证在必要时重新生成该服务项目。  
  
 若要修复此错误，必须手动重新生成该服务项目：  
  
1.  在**“工具”**菜单上，单击**“选项”**。  
  
2.  在**“选项”**对话框中展开**“项目和解决方案”**，然后选择**“常规”**。  
  
3.  确保已选中**“显示高级生成配置”**复选框，然后单击**“确定”**。  
  
4.  加载该 WCF 服务项目。  有关更多信息，请参见[如何：创建多项目解决方案](http://msdn.microsoft.com/zh-cn/02ecd6dd-0114-46fe-b335-ba9c5e3020d6)。  
  
5.  在**“配置管理器”**对话框中，将**“活动解决方案配置”**设置为**“调试”**。  有关更多信息，请参见[如何：创建和编辑配置](../ide/how-to-create-and-edit-configurations.md)。  
  
6.  在**“解决方案资源管理器”**中，选择该 WCF 服务项目。  
  
7.  在**“生成”**菜单上，单击**“重新生成”**以重新生成该 WCF 服务项目。  
  
## WCF 数据服务未在浏览器中显示  
 在尝试查看 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]中数据的 XML 表示形式时，Internet Explorer 可能会将数据错误解释为 RSS 源。  必须确保禁用显示 RSS 源的选项。  
  
 若要修复此错误，请禁用 RSS 源：  
  
1.  在 Internet Explorer 的**“工具”**菜单上，单击**“Internet 选项”**。  
  
2.  在**“内容”**选项卡上的**“源”**区域内单击**“设置”**。  
  
3.  在**“源设置”**对话框中，清除**“打开源阅读视图”**复选框，然后单击**“确定”**。  
  
4.  单击**“确定”**关闭**“Internet 选项”**对话框。  
  
## 请参阅  
 [Windows Communication Foundation Services and WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)   
 [Consuming ASMX and WCF Services Sample](http://msdn.microsoft.com/zh-cn/788ddf2c-2ac1-416b-8789-2fbb1e29b8fe)