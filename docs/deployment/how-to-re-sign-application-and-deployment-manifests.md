---
title: "如何： 对应用程序和部署清单重新签名 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Office applications, signing manifests
- deploying applications [ClickOnce], signing manifests
- deploying applications, signing manifests
- ClickOnce deployment, signing manifests
- Office development in Visual Studio, signing manifests
ms.assetid: d53bceb9-4d3b-4c22-b909-8f370e7231fb
caps.latest.revision: "17"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: baa3e9310946482a4c7c64fdb619ce612a21dbda
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>如何：为应用程序和部署清单重新签名
对 Windows 窗体应用程序、 Windows Presentation Foundation 应用程序 (xbap) 或 Office 解决方案的应用程序清单中的部署属性进行更改后，这两个应用程序必须重新进行签名和部署清单与证书。 此过程有助于确保不会在最终用户计算机上安装经过篡改的文件。  
  
 可能会重新对清单签名的另一种情况是当你的客户想要为应用程序签名和部署清单用他们自己的证书。  
  
## <a name="re-signing-the-application-and-deployment-manifests"></a>对清单进行重新签名的应用程序和部署  
 此过程假定你已对你应用程序清单文件 (.manifest) 中进行了更改。 有关详细信息，请参阅[如何： 更改部署属性](http://msdn.microsoft.com/en-us/66052a3a-8127-4964-8147-2477ef5d1472)。  
  
#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>使用 Mage.exe 重新签名的应用程序和部署清单  
  
1.  打开**Visual Studio 命令提示符**窗口。  
  
2.  将目录更改为包含要用于登录的清单文件的文件夹。  
  
3.  键入以下命令以对应用程序清单文件进行签名。 ManifestFileName 替换为你的清单文件扩展名的名称。 将替换为证书文件的相对或完全限定路径的证书并将 Password 替换为证书的密码。  
  
    ```  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     例如，你可以运行以下命令以登录外接程序、 Windows 窗体应用程序或 Windows Presentation Foundation 浏览器应用程序的应用程序清单。 对于部署到生产环境不建议使用 Visual Studio 创建的临时证书。  
  
    ```  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4.  键入以下命令以更新并对签名部署清单文件，替换占位符名称与前面步骤。  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     例如，你可以运行以下命令以更新和为 Excel 外接程序、 Windows 窗体应用程序或 Windows Presentation Foundation 浏览器应用程序部署清单签名。  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  或者，将复制主部署清单 (发布\\*appname*.application) 到你的版本部署目录 (publish\Application 文件\\*appname*_*版本*)。  
  
## <a name="updating-and-re-signing-the-application-and-deployment-manifests"></a>更新和重新签名的应用程序和部署清单  
 此过程假定你已进行了更改应用程序清单文件 (.manifest)，但没有其他已更新的文件。 文件更新时，还必须更新表示的文件的哈希。  
  
#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>更新并重新对签名的应用程序和部署清单使用 Mage.exe  
  
1.  打开**Visual Studio 命令提示符**窗口。  
  
2.  将目录更改为包含要用于登录的清单文件的文件夹。  
  
3.  从发布输出文件夹中的文件中删除.deploy 文件扩展名。  
  
4.  键入以下命令以使用更新的文件的新哈希更新应用程序清单并对应用程序清单文件进行签名。 ManifestFileName 替换为你的清单文件扩展名的名称。 将替换为证书文件的相对或完全限定路径的证书并将 Password 替换为证书的密码。  
  
    ```  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     例如，你可以运行以下命令以登录外接程序、 Windows 窗体应用程序或 Windows Presentation Foundation 浏览器应用程序的应用程序清单。 对于部署到生产环境不建议使用 Visual Studio 创建的临时证书。  
  
    ```  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  键入以下命令以更新并对签名部署清单文件，替换占位符名称与前面步骤。  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     例如，你可以运行以下命令以更新和为 Excel 外接程序、 Windows 窗体应用程序或 Windows Presentation Foundation 浏览器应用程序部署清单签名。  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6.  将.deploy 文件扩展名添加回文件，但应用程序和部署清单文件。  
  
7.  或者，将复制主部署清单 (发布\\*appname*.application) 到你的版本部署目录 (publish\Application 文件\\*appname*_*版本*)。  
  
## <a name="see-also"></a>另请参阅  
 [保护 ClickOnce 应用程序](../deployment/securing-clickonce-applications.md)   
 [ClickOnce 应用程序的的代码访问安全性](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce 和 Authenticode](../deployment/clickonce-and-authenticode.md)   
 [受信任的应用程序部署概述](../deployment/trusted-application-deployment-overview.md)   
 [如何： 启用 ClickOnce 安全设置](../deployment/how-to-enable-clickonce-security-settings.md)   
 [如何： 为 ClickOnce 应用程序设置安全区域](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [How to: Set Custom Permissions for a ClickOnce Application](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [如何： 调试 ClickOnce 应用程序具有受限权限](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [如何： 为 ClickOnce 应用程序添加到客户端计算机的受信任的发布服务器](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [如何：配置 ClickOnce 信任提示行为](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)