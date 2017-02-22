---
title: "如何：为应用程序和部署清单重新签名 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
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
  - "ClickOnce 部署, 对清单签名"
  - "部署应用程序 [ClickOnce], 对清单签名"
  - "部署应用程序, 对清单签名"
  - "Office 应用程序, 对清单签名"
  - "Visual Studio 中的 Office 开发, 对清单签名"
ms.assetid: d53bceb9-4d3b-4c22-b909-8f370e7231fb
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 如何：为应用程序和部署清单重新签名
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您在 Windows 窗体应用程序、Windows Presentation Foundation 应用程序 \(xbap\) 或 Office 解决方案的应用程序清单中修改部署属性后，必须用证书为应用程序和部署清单重新签名。  此过程有助于确保不会在最终用户计算机上安装经过篡改的文件。  
  
 为清单重新签名的另一种可能情况是：客户希望用自己的证书为应用程序和部署清单签名。  
  
## 对应用程序和部署清单重新签名  
 本过程假定您已更改了应用程序清单文件 \(.manifest\)。  有关更多信息，请参见[如何：更改部署属性](http://msdn.microsoft.com/zh-cn/66052a3a-8127-4964-8147-2477ef5d1472)。  
  
#### 使用 Mage.exe 对应用程序和部署清单重新签名  
  
1.  打开**“Visual Studio 命令提示”**窗口。  
  
2.  将目录更改为包含您要签名的清单文件的文件夹。  
  
3.  键入以下命令，对应用程序清单文件进行签名。  将 ManifestFileName 替换为清单文件的名称加上扩展名，  将 Certificate 替换为证书文件的相对路径或完全限定路径，将 Password 替换为证书的密码。  
  
    ```  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     例如，您可以运行以下命令，为外接程序、Windows 窗体应用程序或 Windows Presentation Foundation 浏览器应用程序的应用程序清单签名。  不推荐将 Visual Studio 创建的临时证书部署到生产环境中。  
  
    ```  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4.  键入下面的命令，更新部署清单文件并为其签名，此过程中需像上一步那样替换占位符名称。  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     例如，您可以运行以下命令，对 Excel 外接程序、Windows 窗体应用程序或 Windows Presentation Foundation 浏览器应用程序的部署清单进行更新和签名。  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  还可选择将主部署清单（publish\\*应用程序名*.application）复制到您的版本部署目录（publish\\Application Files\\*应用程序名*\_*版本*）中。  
  
## 对应用程序和部署清单进行更新和重新签名  
 本过程假定您已更改了应用程序清单文件 \(.manifest\)，但还有其他一些文件进行了更新。  更新文件时，表示相应文件的哈希也必须更新。  
  
#### 使用 Mage.exe 对应用程序和部署清单进行更新和重新签名  
  
1.  打开**“Visual Studio 命令提示”**窗口。  
  
2.  将目录更改为包含您要签名的清单文件的文件夹。  
  
3.  从发布的输出文件夹的文件中移除 .deploy 文件扩展名。  
  
4.  键入以下命令以使用已更新文件的新哈希来更新应用程序清单，并对应用程序清单文件进行签名。  将 ManifestFileName 替换为清单文件的名称加上扩展名，  将 Certificate 替换为证书文件的相对路径或完全限定路径，将 Password 替换为证书的密码。  
  
    ```  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     例如，您可以运行以下命令，为外接程序、Windows 窗体应用程序或 Windows Presentation Foundation 浏览器应用程序的应用程序清单签名。  不推荐将 Visual Studio 创建的临时证书部署到生产环境中。  
  
    ```  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  键入下面的命令，更新部署清单文件并为其签名，此过程中需像上一步那样替换占位符名称。  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     例如，您可以运行以下命令，对 Excel 外接程序、Windows 窗体应用程序或 Windows Presentation Foundation 浏览器应用程序的部署清单进行更新和签名。  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6.  将 .deploy 文件扩展名添加回相关文件，应用程序清单文件和部署清单文件除外。  
  
7.  还可选择将主部署清单（publish\\*应用程序名*.application）复制到您的版本部署目录（publish\\Application Files\\*应用程序名*\_*版本*）中。  
  
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
 [如何：配置 ClickOnce 信任提示行为](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)