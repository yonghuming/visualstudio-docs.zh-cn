---
title: "如何： 配置包含列表安全性 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio
- inclusion lists [Office development in Visual Studio]
ms.assetid: 0609d8f0-4630-4e17-aeb3-14f3134165cf
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7032f3663be7df1a06fa4dc16d4f4473e4666cfc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-configure-inclusion-list-security"></a>如何：配置包含列表安全性
  如果具有管理员权限，则可以配置[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]信任提示，以控制最终用户是否可以通过将信任决定保存到包含列表中安装 Office 解决方案的选择。 有关包含列表的信息，请参阅[使用包含列表信任 Office 解决方案](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 对于每个五个区域中的解决方案，你可以设置以下选项：  
  
-   启用[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]信任提示密钥和包含列表。 你可以允许最终用户能够向使用任何证书进行签名的 Office 解决方案授予信任。  
  
-   限制[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]信任提示密钥和包含列表。 你可以允许最终用户若要使用标识发布服务器，但这不是已受信任的证书安装 Office 解决方案中，进行签名。  
  
-   禁用[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]信任提示密钥和包含列表。 你可以防止最终用户安装未签名的任何 Office 解决方案使用显式信任的证书。  
  
## <a name="enabling-the-inclusion-list"></a>启用包含列表  
 你希望最终用户提供的选项的安装和运行来自该区域任何 Office 解决方案时，请启用区域包含列表。  
  
#### <a name="to-enable-the-inclusion-list-by-using-the-registry-editor"></a>若要启用使用注册表编辑器的包含列表  
  
1.  打开注册表编辑器：  
  
    1.  单击**启动**，然后单击**运行**。  
  
    2.  在**打开**框中，键入**regedt32.exe**，然后单击**确定**。  
  
2.  查找以下注册表项：  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\。NETFramework\Security\TrustManager\PromptingLevel  
  
     如果不存在该键，则创建它。  
  
3.  添加以下子键作为**字符串值**，如果它们尚不存在，及关联的值。  
  
    |字符串值子项|值|  
    |-------------------------|-----------|  
    |**Internet**|**AuthenticodeRequired**|  
    |**UntrustedSites**|**已禁用**|  
    |**MyComputer**|**启用**|  
    |**LocalIntranet**|**启用**|  
    |**TrustedSites**|**启用**|  
  
     默认情况下， **Internet**具有值**AuthenticodeRequired**和**UntrustedSites**具有值**禁用**。  
  
#### <a name="to-enable-the-inclusion-list-programmatically"></a>以编程方式启用包含列表  
  
1.  创建 Visual Basic 或 Visual C# 控制台应用程序。  
  
2.  打开以进行编辑的 Program.vb 或 Program.cs 文件并添加下面的代码。  
  
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
  
## <a name="restricting-the-inclusion-list"></a>限制包含列表  
 限制包含列表，以便与之前提示用户信任决定提供具有已知标识的验证码证书必须对解决方案进行签名。  
  
#### <a name="to-restrict-the-inclusion-list"></a>若要限制包含列表  
  
1.  打开注册表编辑器：  
  
    1.  单击**启动**，然后单击**运行**。  
  
    2.  在**打开**框中，键入**regedt32.exe**，然后单击**确定**。  
  
2.  查找以下注册表项：  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\。NETFramework\Security\TrustManager\PromptingLevel  
  
     如果不存在该键，则创建它。  
  
3.  添加以下子键作为**字符串值**，如果它们尚不存在，及关联的值。  
  
    |字符串值子项|值|  
    |-------------------------|-----------|  
    |**UntrustedSites**|**已禁用**|  
    |**Internet**|**AuthenticodeRequired**|  
    |**MyComputer**|**AuthenticodeRequired**|  
    |**LocalIntranet**|**AuthenticodeRequired**|  
    |**TrustedSites**|**AuthenticodeRequired**|  
  
     默认情况下， **Internet**具有值**AuthenticodeRequired**和**UntrustedSites**具有值**禁用**。  
  
#### <a name="to-restrict-the-inclusion-list-programmatically"></a>若要以编程方式限制包含列表  
  
1.  创建 Visual Basic 或 Visual C# 控制台应用程序。  
  
2.  打开以进行编辑的 Program.vb 或 Program.cs 文件并添加下面的代码。  
  
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
  
## <a name="disabling-the-inclusion-list"></a>禁用包含列表  
 你可以禁用包含列表，以便最终用户可以仅使用受信任和已知证书安装进行签名的解决方案。  
  
#### <a name="to-disable-the-inclusion-list"></a>若要禁用包含列表  
  
1.  打开注册表编辑器：  
  
    1.  单击**启动**，然后单击**运行**。  
  
    2.  在**打开**框中，键入**regedt32.exe**，然后单击**确定**。  
  
2.  如果这尚不存在，请创建以下注册表项：  
  
     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\。NETFramework\Security\TrustManager\PromptingLevel**  
  
3.  添加以下子键作为**字符串值**，如果它们尚不存在，及关联的值。  
  
    |字符串值子项|值|  
    |-------------------------|-----------|  
    |**UntrustedSites**|**已禁用**|  
    |**Internet**|**已禁用**|  
    |**MyComputer**|**已禁用**|  
    |**LocalIntranet**|**已禁用**|  
    |**TrustedSites**|**已禁用**|  
  
#### <a name="to-disable-the-inclusion-list-programmatically"></a>若要以编程方式禁用包含列表  
  
1.  创建 Visual Basic 或 Visual C# 控制台应用程序。  
  
2.  打开以进行编辑的 Program.vb 或 Program.cs 文件并添加下面的代码。  
  
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
  
## <a name="see-also"></a>另请参阅  
 [使用包含列表信任 Office 解决方案](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)   
 [确保 Office 解决方案的安全](../vsto/securing-office-solutions.md)  
  
  