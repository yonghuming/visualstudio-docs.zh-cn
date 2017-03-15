---
title: "如何：配置 ClickOnce 信任提示行为 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce 应用程序, 无提示安装"
  - "ClickOnce 应用程序, 信任提示"
  - "ClickOnce 部署, 无提示安装"
  - "ClickOnce 部署, 信任提示"
  - "部署应用程序 [ClickOnce], 信任提示"
ms.assetid: cc04fa75-012b-47c9-9347-f4216be23cf2
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：配置 ClickOnce 信任提示行为
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可以配置 ClickOnce 信任提示以控制是否允许最终用户选择安装 ClickOnce 应用程序，如 Windows Forms 应用程序、Windows Presentation Foundation 应用程序、控制台应用程序、WPF 浏览器应用程序和 Office 解决方案。  可以通过在每个最终用户的计算机上设置注册表项来配置信任提示。  
  
 下表显示了可应用于五个区域（即 Internet、UntrustedSites、MyComputer、LocalIntranet 和 TrustedSites）中的每个区域的配置选项。  
  
|选项|注册表设置值|说明|  
|--------|------------|--------|  
|启用信任提示。|`Enabled`|显示 ClickOnce 信任提示以便最终用户能够向 ClickOnce 应用程序授予信任。|  
|限制信任提示。|`AuthenticodeRequired`|ClickOnce 信任提示仅在已用标识发行者的证书对 ClickOnce 应用程序进行签名的情况下显示。|  
|禁用信任提示。|`禁用`|对于未用显式信任证书进行签名的任何 ClickOnce 应用程序，不显示 ClickOnce 信任提示。|  
  
 下表显示了每个区域的默认行为。  “应用程序”列指的是 Windows Forms 应用程序、Windows Presentation Foundation 应用程序、WPF 浏览器应用程序和控制台应用程序。  
  
|区域|应用程序|Office 解决方案|  
|--------|----------|-----------------|  
|`MyComputer`|`Enabled`|`Enabled`|  
|`LocalIntranet`|`Enabled`|`Enabled`|  
|`TrustedSites`|`Enabled`|`Enabled`|  
|`Internet`|`Enabled`|`AuthenticodeRequired`|  
|`UntrustedSites`|`禁用`|`禁用`|  
  
 通过启用、限制或禁用 ClickOnce 信任提示，可以重写这些设置。  
  
## 启用 ClickOnce 信任提示  
 如果想要向最终用户呈现选项，使他们可以选择安装和运行来自某个区域的任何 ClickOnce 应用程序，请为该区域启用信任提示。  
  
#### 使用注册表编辑器启用 ClickOnce 信任提示  
  
1.  打开注册表编辑器：  
  
    1.  单击**“开始”**，然后单击**“运行”**。  
  
    2.  在**“打开”**框中，键入 `regedit32`，然后单击**“确定”**。  
  
2.  查找以下注册表项：  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     如果该项不存在，请创建它。  
  
3.  按下表所示，以**“字符串值”**的形式添加以下子项（如果这些子项尚不存在）及关联的值。  
  
    |字符串值子项|值|  
    |------------|-------|  
    |`Internet`|`Enabled`|  
    |`UntrustedSites`|`禁用`|  
    |`MyComputer`|`Enabled`|  
    |`LocalIntranet`|`Enabled`|  
    |`TrustedSites`|`Enabled`|  
  
     对于 Office 解决方案，`Internet` 的默认值为 `AuthenticodeRequired`，而 `UntrustedSites` 的默认值为 `Disabled`。  对于所有其他应用程序，`Internet` 的默认值为 `Enabled`。  
  
#### 以编程方式启用 ClickOnce 信任提示  
  
1.  在 Visual Studio 中创建一个 Visual Basic 或 Visual C\# 控制台应用程序。  
  
2.  打开 Program.vb 或 Program.cs 文件进行编辑，并添加以下代码。  
  
    ```vb#  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Enabled")  
    key.SetValue("LocalIntranet", "Enabled")  
    key.SetValue("Internet", "Enabled")  
    key.SetValue("TrustedSites", "Enabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```c#  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Enabled");  
    key.SetValue("LocalIntranet", "Enabled");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "Enabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3.  生成并运行应用程序。  
  
## 限制 ClickOnce 信任提示  
 对信任提示进行限制，这样，在提示用户做出信任决定之前，必须使用具有已知标识的 Authenticode 证书对解决方案进行签名。  
  
#### 使用注册表编辑器限制 ClickOnce 信任提示  
  
1.  打开注册表编辑器：  
  
    1.  单击**“开始”**，然后单击**“运行”**。  
  
    2.  在**“打开”**框中，键入 `regedit`，然后单击**“确定”**。  
  
2.  查找以下注册表项：  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     如果该项不存在，请创建它。  
  
3.  按下表所示，以**“字符串值”**的形式添加以下子项（如果这些子项尚不存在）及关联的值。  
  
    |字符串值子项|值|  
    |------------|-------|  
    |`UntrustedSites`|`禁用`|  
    |`Internet`|`AuthenticodeRequired`|  
    |`MyComputer`|`AuthenticodeRequired`|  
    |`LocalIntranet`|`AuthenticodeRequired`|  
    |`TrustedSites`|`AuthenticodeRequired`|  
  
#### 以编程方式限制 ClickOnce 信任提示  
  
1.  在 Visual Studio 中创建一个 Visual Basic 或 Visual C\# 控制台应用程序。  
  
2.  打开 Program.vb 或 Program.cs 文件进行编辑，并添加以下代码。  
  
    ```vb#  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "AuthenticodeRequired")  
    key.SetValue("LocalIntranet", "AuthenticodeRequired")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "AuthenticodeRequired")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```c#  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "AuthenticodeRequired");  
    key.SetValue("LocalIntranet", "AuthenticodeRequired");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "AuthenticodeRequired");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3.  生成并运行应用程序。  
  
## 禁用 ClickOnce 信任提示  
 可以禁用信任提示，使最终用户无法选择安装其安全策略已不信任的解决方案。  
  
#### 使用注册表编辑器禁用 ClickOnce 信任提示  
  
1.  打开注册表编辑器：  
  
    1.  单击**“开始”**，然后单击**“运行”**。  
  
    2.  在**“打开”**框中，键入 `regedit`，然后单击**“确定”**。  
  
2.  查找以下注册表项：  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     如果该项不存在，请创建它。  
  
3.  按下表所示，以**“字符串值”**的形式添加以下子项（如果这些子项尚不存在）及关联的值。  
  
    |字符串值子项|值|  
    |------------|-------|  
    |`UntrustedSites`|`禁用`|  
    |`Internet`|`禁用`|  
    |`MyComputer`|`禁用`|  
    |`LocalIntranet`|`禁用`|  
    |`TrustedSites`|`禁用`|  
  
#### 以编程方式禁用 ClickOnce 信任提示  
  
1.  在 Visual Studio 中创建一个 Visual Basic 或 Visual C\# 控制台应用程序。  
  
2.  打开 Program.vb 或 Program.cs 文件进行编辑，并添加以下代码。  
  
    ```vb#  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Disabled")  
    key.SetValue("LocalIntranet", "Disabled")  
    key.SetValue("Internet", "Disabled")  
    key.SetValue("TrustedSites", "Disabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```c#  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Disabled");  
    key.SetValue("LocalIntranet", "Disabled");  
    key.SetValue("Internet", "Disabled");  
    key.SetValue("TrustedSites", "Disabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
  
    ```  
  
3.  生成并运行应用程序。  
  
## 请参阅  
 [保护 ClickOnce 应用程序](../deployment/securing-clickonce-applications.md)   
 [ClickOnce 应用程序的代码访问安全性](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce 和 Authenticode](../deployment/clickonce-and-authenticode.md)   
 [受信任的应用程序部署概述](../deployment/trusted-application-deployment-overview.md)   
 [如何：启用 ClickOnce 安全设置](../deployment/how-to-enable-clickonce-security-settings.md)   
 [如何：为 ClickOnce 应用程序设置安全区域](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [如何：设置 ClickOnce 应用程序的自定义权限](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [如何：使用受限权限对 ClickOnce 应用程序进行调试](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [如何：为 ClickOnce 应用程序向客户端计算机添加一个受信任的发行者](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [如何：为应用程序和部署清单重新签名](../deployment/how-to-re-sign-application-and-deployment-manifests.md)