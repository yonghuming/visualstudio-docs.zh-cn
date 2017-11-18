---
title: "演练： 创建自定义安装 ClickOnce 应用程序 |Microsoft 文档"
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
- ClickOnce deployment, custom installer
- installer [ClickOnce], custom
- deploying applications [ClickOnce], custom installer
- InPlaceHostingManager [ClickOnce], custom installer
- custom installer [ClickOnce]
ms.assetid: fb222cc5-8aeb-4b94-8c49-b93e342f5f69
caps.latest.revision: "34"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 3b6a7069b520c1c4834ee3ca1a5824660803a665
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="walkthrough-creating-a-custom-installer-for-a-clickonce-application"></a>演练：为 ClickOnce 应用程序创建自定义安装程序
任何基于.exe 文件的 ClickOnce 应用程序可以以无提示方式安装和更新的自定义安装程序。 自定义安装程序可以在安装期间，包括有关安全性和维护操作的自定义对话框实现自定义用户体验。 若要执行安装操作，自定义安装程序使用<xref:System.Deployment.Application.InPlaceHostingManager>类。 本演练演示如何创建一个自定义安装程序，以无提示方式安装 ClickOnce 应用程序。  
  
## <a name="prerequisites"></a>先决条件  
  
### <a name="to-create-a-custom-clickonce-application-installer"></a>若要创建自定义 ClickOnce 应用程序安装程序  
  
1.  在 ClickOnce 应用程序中，添加对 System.Deployment 和 System.Windows.Forms 的引用。  
  
2.  将新类添加到你的应用程序，并指定任何名称。 本演练使用名称`MyInstaller`。  
  
3.  添加以下`Imports`或`using`到新类的顶部的语句。  
  
    ```vb  
    Imports System.Deployment.Application  
    Imports System.Windows.Forms  
    ```  
  
    ```csharp  
    using System.Deployment.Application;  
    using System.Windows.Forms;  
    ```  
  
4.  将以下方法添加到你的类。  
  
     这些方法调用<xref:System.Deployment.Application.InPlaceHostingManager>方法以下载部署清单，断言适当的权限，要求用户提供权限，以安装，然后下载并安装应用程序到 ClickOnce 缓存。 自定义安装程序可以指定 ClickOnce 应用程序预受信任，，或可以延迟到信任决定<xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A>方法调用。 此代码预信任应用程序。  
  
    > [!NOTE]
    >  通过预先信任分配的权限不能超过的自定义安装程序代码的权限。  
  
     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]  
  
5.  若要尝试在代码中的安装，调用`InstallApplication`方法。 例如，如果将类命名为`MyInstaller`，您可能要调用`InstallApplication`方式如下。  
  
    ```vb  
    Dim installer As New MyInstaller()  
    installer.InstallApplication("\\myServer\myShare\myApp.application")  
    MessageBox.Show("Installer object created.")  
    ```  
  
    ```csharp  
    MyInstaller installer = new MyInstaller();  
    installer.InstallApplication(@"\\myServer\myShare\myApp.application");  
    MessageBox.Show("Installer object created.");  
    ```  
  
## <a name="next-steps"></a>后续步骤  
 ClickOnce 应用程序还可以添加自定义更新逻辑，包括要显示在更新过程中自定义用户界面。 有关详细信息，请参阅<xref:System.Deployment.Application.UpdateCheckInfo>。 ClickOnce 应用程序可以同时禁止显示的标准的开始菜单项、 快捷方式，和添加或删除程序条目使用`<customUX>`元素。 有关详细信息，请参阅[\<入口点 > 元素](../deployment/entrypoint-element-clickonce-application.md)和<xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>。  
  
## <a name="see-also"></a>另请参阅  
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)   
 [\<入口点 > 元素](../deployment/entrypoint-element-clickonce-application.md)