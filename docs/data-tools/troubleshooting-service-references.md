---
title: "服务引用疑难解答 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther
- msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo
- msvse_wcf.Err.ErrorOnOK
- msvse_wcf.cfg.ConfigurationErrorsException
helpviewer_keywords:
- service references [Visual Studio], troubleshooting
- WCF services, troubleshooting
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: e46c8bf778ff18ea25096e524716bcb44916f460
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="troubleshooting-service-references"></a>服务引用疑难解答
本主题列出了你正在使用时可能发生的常见问题[!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)]或[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]中引用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="error-returning-data-from-a-service"></a>从服务返回数据时出错  
 当您返回`DataSet`或`DataTable`从一种服务，你可能会收到"已超过为传入消息的最大大小配额"异常。 默认情况下，`MaxReceivedMessageSize`对于某些绑定的属性设置为一个相对较小的值，以降低遭受拒绝服务攻击。 您可以增大此值以避免此异常。 有关详细信息，请参阅<xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A>。  
  
 若要修复此错误：  
  
1.  在**解决方案资源管理器**，双击 app.config 文件以打开它。  
  
2.  找到`MaxReceivedMessageSize`属性并将它更改为更大的值。  
  
## <a name="cannot-find-a-service-in-my-solution"></a>找不到我的解决方案中的服务  
 当你单击**发现**按钮**添加服务引用**对话框中，解决方案中的一个或多个 WCF 服务库项目并不出现在服务列表。 如果服务库已添加到解决方案，但尚未编译便会出现此问题。  
  
 若要修复此错误：  
  
-   在**解决方案资源管理器**，右键单击 WCF 服务库项目，然后单击**生成**。  
  
## <a name="error-accessing-a-service-over-a-remote-desktop"></a>通过远程桌面访问服务时出错  
 如果用户访问 Web 承载的 WCF 服务通过远程桌面连接和用户不具有管理权限，则使用 NTLM 身份验证。 如果用户不具有管理权限，用户可能会收到以下错误消息:"HTTP 请求得到具有客户端身份验证方案匿名身份验证。 从服务器收到的身份验证标头已 NTLM。"  
  
 若要修复此错误：  
  
1.  在网站项目中，打开**属性**页。  
  
2.  上**启动选项**选项卡上，清除**NTLM 身份验证**复选框。  
  
    > [!NOTE]
    >  你应关闭仅针对以独占方式包含 WCF 服务的网站的 NTLM 身份验证。 WCF 服务的安全是通过 web.config 文件中的配置管理。 这使得 NTLM 身份验证不必要。  
  
## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>生成的类的访问级别设置不起作用  
 设置**访问生成的类级别**选项**配置服务引用**对话框**内部**或**友元**可能无法始终工作。 尽管会显示该选项将在对话框中，将以一种访问级别的生成所产生的支持类`Public`。  
  
 这是某些类型，如那些使用序列化的已知的限制<xref:System.Xml.Serialization.XmlSerializer>。  
  
## <a name="error-debugging-service-code"></a>错误调试服务代码  
 当你单步执行 WCF 服务的代码从客户端代码时，你可能会收到与缺少符号相关的错误。 原因可能是你的解决方案的一部分的服务已移动或从解决方案中移除时。  
  
 第一次添加到了当前解决方案的一部分的 WCF 服务引用时，服务项目和服务客户端项目之间添加显式生成依赖项。 这可保证客户端始终访问最新的服务二进制文件，这一点尤为重要的调试方案，比如从客户端代码单步执行服务代码。  
  
 如果从解决方案中移除的服务项目，此显式生成依赖项将会失效。 Visual Studio 可以不再保证会重新生成服务项目，根据需要。  
  
 若要修复此错误，你必须手动重新生成服务项目：  
  
1.  在 **“工具”** 菜单上，单击 **“选项”**。  
  
2.  在**选项**对话框框中，展开**项目和解决方案**，然后选择**常规**。  
  
3.  请确保**显示高级生成配置**复选框被选中，并且然后单击**确定**。  
  
4.  加载该 WCF 服务项目。  
  
5.  在**Configuration Manager**对话框中，设置**活动解决方案配置**到**调试**。 有关详细信息，请参阅[如何：创建和编辑配置](../ide/how-to-create-and-edit-configurations.md)。  
  
6.  在**解决方案资源管理器**，选择该 WCF 服务项目。  
  
7.  上**生成**菜单上，单击**重新生成**重新生成 WCF 服务项目。  
  
## <a name="wcf-data-services-do-not-display-in-the-browser"></a>WCF 数据服务不会显示在浏览器  
 在尝试查看的 XML 表示形式中的数据[!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]，Internet 资源管理器可能错误解释为 RSS 源的数据。 必须确保禁用显示 RSS 源的选项。  
  
 若要修复此错误，请禁用 RSS 源：  
  
1.  在 Internet Explorer 中，在**工具**菜单上，单击**Internet 选项**。  
  
2.  上**内容**选项卡上，在**馈送**部分中，单击**设置**。  
  
3.  在**源设置**对话框中，清除**打开源阅读视图**复选框，并依次**确定**。  
  
4.  单击**确定**关闭**Internet 选项**对话框。  
  
## <a name="see-also"></a>另请参阅  
 [Visual Studio 中的 Windows Communication Foundation 服务和 WCF 数据服务](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)