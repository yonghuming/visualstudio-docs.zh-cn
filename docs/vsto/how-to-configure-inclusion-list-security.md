---
title: "如何：配置包含列表安全性 | Microsoft Docs"
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
  - "包含列表 [Visual Studio 中的 Office 开发]"
  - "权限 [Visual Studio 中的 Office 开发"
ms.assetid: 0609d8f0-4630-4e17-aeb3-14f3134165cf
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# 如何：配置包含列表安全性
  如果有管理员权限，可以通过将信任决定保存到包含列表中来配置 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 信任提示，以控制是否向最终用户提供安装 Office 解决方案的选项。  有关包含列表的信息，请参见[使用包含列表信任 Office 解决方案](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 对于位于五个区域每个区域中的解决方案，您可以设置以下选项：  
  
-   启用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 信任提示密钥和包含列表。  可以允许最终用户向用任何证书签名的 Office 解决方案授予信任。  
  
-   限制 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 信任提示密钥和包含列表。  可以允许最终用户安装用标识发布者的证书（但不是已信任的证书）签名的 Office 解决方案。  
  
-   禁用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 信任提示密钥和包含列表。  可以防止最终用户安装未用显式信任的证书签名的 Office 解决方案。  
  
## 启用包含列表  
 如果想要向最终用户呈现选项，使他们可以选择安装和运行来自某个区域的任何 Office 解决方案，请为该区域启用包含列表。  
  
#### 使用注册表编辑器启用包含列表  
  
1.  打开注册表编辑器：  
  
    1.  单击**“开始”**，然后单击**“运行”**。  
  
    2.  在**“打开”**框中，键入 **regedt32.exe**，然后单击**“确定”**。  
  
2.  查找以下注册表项：  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     如果该项不存在，请创建它。  
  
3.  以**“字符串值”**的形式添加具有关联值的以下子项（如果这些子项尚不存在）。  
  
    |字符串值子项|值|  
    |------------|-------|  
    |**Internet**|**AuthenticodeRequired**|  
    |**UntrustedSites**|**禁用**|  
    |**MyComputer**|**Enabled**|  
    |**LocalIntranet**|**Enabled**|  
    |**TrustedSites**|**Enabled**|  
  
     默认情况下，**Internet** 的值为 **AuthenticodeRequired**，并且 **UntrustedSites** 的值为 **Disabled**。  
  
#### 以编程方式启用包含列表  
  
1.  创建一个 Visual Basic 或 Visual C\# 控制台应用程序。  
  
2.  打开 Program.vb 或 Program.cs 文件进行编辑，并添加以下代码。  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Enabled")  
    key.SetValue("LocalIntranet", "Enabled")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "Enabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
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
  
## 限制包含列表  
 对包含列表进行限制，这样，在提示用户做出信任决定之前，必须用具有已知标识的 Authenticode 证书对解决方案进行签名。  
  
#### 限制包含列表  
  
1.  打开注册表编辑器：  
  
    1.  单击**“开始”**，然后单击**“运行”**。  
  
    2.  在**“打开”**框中，键入 **regedt32.exe**，然后单击**“确定”**。  
  
2.  查找以下注册表项：  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     如果该项不存在，请创建它。  
  
3.  以**“字符串值”**的形式添加具有关联值的以下子项（如果这些子项尚不存在）。  
  
    |字符串值子项|值|  
    |------------|-------|  
    |**UntrustedSites**|**禁用**|  
    |**Internet**|**AuthenticodeRequired**|  
    |**MyComputer**|**AuthenticodeRequired**|  
    |**LocalIntranet**|**AuthenticodeRequired**|  
    |**TrustedSites**|**AuthenticodeRequired**|  
  
     默认情况下，**Internet** 的值为 **AuthenticodeRequired**，并且 **UntrustedSites** 的值为 **Disabled**。  
  
#### 以编程方式限制包含列表  
  
1.  创建一个 Visual Basic 或 Visual C\# 控制台应用程序。  
  
2.  打开 Program.vb 或 Program.cs 文件进行编辑，并添加以下代码。  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "AuthenticodeRequired")  
    key.SetValue("LocalIntranet", "AuthenticodeRequired")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "AuthenticodeRequired")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
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
  
## 禁用包含列表  
 您可以禁用包含列表，以使最终用户只能安装用受信任的已知证书签名的解决方案。  
  
#### 禁用包含列表  
  
1.  打开注册表编辑器：  
  
    1.  单击**“开始”**，然后单击**“运行”**。  
  
    2.  在**“打开”**框中，键入 **regedt32.exe**，然后单击**“确定”**。  
  
2.  如果以下注册表项尚不存在，请创建该注册表项：  
  
     **\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel**  
  
3.  以**“字符串值”**的形式添加具有关联值的以下子项（如果这些子项尚不存在）。  
  
    |字符串值子项|值|  
    |------------|-------|  
    |**UntrustedSites**|**禁用**|  
    |**Internet**|**禁用**|  
    |**MyComputer**|**禁用**|  
    |**LocalIntranet**|**禁用**|  
    |**TrustedSites**|**禁用**|  
  
#### 以编程方式禁用包含列表  
  
1.  创建一个 Visual Basic 或 Visual C\# 控制台应用程序。  
  
2.  打开 Program.vb 或 Program.cs 文件进行编辑，并添加以下代码。  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Disabled")  
    key.SetValue("LocalIntranet", "Disabled")  
    key.SetValue("Internet", "Disabled")  
    key.SetValue("TrustedSites", "Disabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
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
 [使用包含列表信任 Office 解决方案](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)   
 [保护 Office 解决方案的安全](../vsto/securing-office-solutions.md)  
  
  