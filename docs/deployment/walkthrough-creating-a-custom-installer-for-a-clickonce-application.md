---
title: "演练：为 ClickOnce 应用程序创建自定义安装程序 | Microsoft Docs"
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
  - "ClickOnce 部署, 自定义安装程序"
  - "自定义安装程序 [ClickOnce]"
  - "部署应用程序 [ClickOnce], 自定义安装程序"
  - "InPlaceHostingManager [ClickOnce], 自定义安装程序"
  - "安装程序 [ClickOnce], 自定义"
ms.assetid: fb222cc5-8aeb-4b94-8c49-b93e342f5f69
caps.latest.revision: 34
caps.handback.revision: 34
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 演练：为 ClickOnce 应用程序创建自定义安装程序
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

基于 .exe 文件的任何 ClickOnce 应用程序均可通过一个自定义安装程序进行无提示安装和更新。  自定义安装程序可以实现安装期间的自定义用户体验，包括用于安全和维护操作的自定义对话框。  为了执行安装操作，自定义安装程序将使用 <xref:System.Deployment.Application.InPlaceHostingManager> 类。  本演练演示如何创建可进行 ClickOnce 应用程序的无提示安装的自定义安装程序。  
  
## 系统必备  
  
### 创建自定义的 ClickOnce 应用程序安装程序  
  
1.  在 ClickOnce 应用程序中，添加对 System.Deployment 和 System.Windows.Forms 的引用。  
  
2.  向应用程序中添加一个新类，并指定任何名称。  本演练使用名称 `MyInstaller`。  
  
3.  将以下 `Imports` 或 `using` 语句添加到新类的顶部。  
  
    ```vb#  
    Imports System.Deployment.Application  
    Imports System.Windows.Forms  
    ```  
  
    ```c#  
    using System.Deployment.Application;  
    using System.Windows.Forms;  
    ```  
  
4.  将以下方法添加到类中。  
  
     这些方法调用 <xref:System.Deployment.Application.InPlaceHostingManager> 方法以便下载部署清单，断言适当的权限，要求用户提供安装权限，然后将应用程序下载并安装到 ClickOnce 缓存中。  自定义安装程序可以指定 ClickOnce 应用程序是预信任的，或者可以将信任决定推迟到调用 <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A> 方法时。  此代码预信任该应用程序。  
  
    > [!NOTE]
    >  预信任分配的权限不能超越自定义安装程序代码的权限。  
  
     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-cs[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]  
  
5.  若要尝试利用代码进行安装，请调用 `InstallApplication` 方法。  例如，如果将类命名为 `MyInstaller`，则可以用下面的方法调用 `InstallApplication`。  
  
    ```vb#  
    Dim installer As New MyInstaller()  
    installer.InstallApplication("\\myServer\myShare\myApp.application")  
    MessageBox.Show("Installer object created.")  
    ```  
  
    ```c#  
    MyInstaller installer = new MyInstaller();  
    installer.InstallApplication(@"\\myServer\myShare\myApp.application");  
    MessageBox.Show("Installer object created.");  
  
    ```  
  
## 后续步骤  
 ClickOnce 应用程序还可以添加自定义更新逻辑，包括在更新过程中要显示的自定义用户界面。  有关更多信息，请参见 <xref:System.Deployment.Application.UpdateCheckInfo>。  ClickOnce 应用程序还可以使用 `<customUX>` 元素来禁止显示标准的“开始”菜单项、快捷键和“添加或删除程序”项。  有关更多信息，请参见 [\<entryPoint\> 元素](../deployment/entrypoint-element-clickonce-application.md)和 <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>。  
  
## 请参阅  
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)   
 [\<entryPoint\> 元素](../deployment/entrypoint-element-clickonce-application.md)