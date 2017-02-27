---
title: "”项目设计器“ -&gt;“安全”页 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesSecurity"
  - "vb.XBAPProjectPropertiesSecurity"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "项目设计器，“安全”页"
  - "项目设计器中的“安全”页"
ms.assetid: 641d9cd3-fa07-498a-8568-3c169bb4d3d5
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# ”项目设计器“ -&gt;“安全”页
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

**“项目设计器”**的**“安全性”**页用于为使用 [!INCLUDE[ndptecclick](../../deployment/includes/ndptecclick_md.md)] 部署技术部署的应用程序配置代码访问安全设置。  有关更多信息，请参见 [ClickOnce 应用程序的代码访问安全性](../../deployment/code-access-security-for-clickonce-applications.md)。  
  
 若要访问**“安全性”**页，请在**“解决方案资源管理器”**中单击项目节点，然后在**“项目”**菜单上单击**“属性”**。  当**“项目设计器”**出现时，单击**“安全性”**选项卡。  
  
## 安全设置  
 **启用 ClickOnce 安全设置**  
 确定是否在设计时启用安全设置。  如果清除此选项，则**“安全性”**页上的所有其他选项将不可用。  
  
> [!NOTE]
>  当使用**“发布”**向导发布应用程序时，将自动启用此选项。  
  
 当选中此选项时，可以选择以下两个单选选项按钮之一：**“这是完全可信的应用程序”**或**“这是不完全可信的应用程序”**。  
  
 对于 WPF Web 浏览器应用程序项目，默认情况下将选中此选项。  
  
 对于所有其他项目类型，默认情况下清除此选项。  
  
 **这是完全可信的应用程序**  
 如果选择此选项，则当在客户端计算机上安装或运行应用程序时，该应用程序会请求“完全信任”权限。  在可能的情况下应避免使用完全信任，因为这会授予您的应用程序无限制访问资源的权限，例如访问文件系统和注册表。  
  
 默认情况下，对于 WPF Web 浏览器应用程序项目，此选项设置为“不完全可信”。  
  
 默认情况下，对于所有其他项目类型，此选项设置为“完全信任”。  
  
 **这是不完全可信的应用程序**  
 如果选择此选项，则当在客户端计算机上安装或运行应用程序时，该应用程序会请求“不完全可信”权限。  *部分信任*表示仅在请求的代码访问安全权限下允许运行这些操作。  有关如何配置安全权限的详细信息，请参见 [ClickOnce 应用程序的代码访问安全性](../../deployment/code-access-security-for-clickonce-applications.md)。  
  
 可以通过配置**“ClickOnce 安全权限”**区域中的选项指定“不完全可信”安全设置。  
  
## ClickOnce 安全权限  
 **将要从中安装应用程序的区域**  
 指定一组默认的代码访问安全权限。  为受限制的权限集选择**“Internet”**或**“本地 Intranet”**，或选择**“\(自定义\)”** 来配置自定义权限集。  如果应用程序请求的权限多余区域中授予的权限，则将对最终用户显示 ClickOnce 信任提示以授予其他权限。  有关如何配置安全权限的详细信息，请参见 [ClickOnce 应用程序的代码访问安全性](../../deployment/code-access-security-for-clickonce-applications.md)。  
  
 默认情况下，对于 WPF Web 浏览器应用程序项目，此选项设置为**“Internet”**。  
  
 **编辑权限 XML**  
 打开应用程序清单模板 \(app.manifest\) 以配置**“（自定义）”**权限集的权限。  
  
 **高级**  
 打开 [“高级安全设置”对话框](../../ide/reference/advanced-security-settings-dialog-box.md)，它用于为调试具有受限制权限的应用程序配置设置。  调试过程中会检查这些设置，权限异常指示您的应用程序可能需要的权限比区域中定义的要多。  
  
## 请参阅  
 <xref:System.Security.Permissions.WebBrowserPermission>   
 <xref:System.Security.Permissions.MediaPermission>   
 [ClickOnce 应用程序的代码访问安全性](../../deployment/code-access-security-for-clickonce-applications.md)   
 [如何：启用 ClickOnce 安全设置](../../deployment/how-to-enable-clickonce-security-settings.md)   
 [如何：为 ClickOnce 应用程序设置安全区域](../../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [如何：设置 ClickOnce 应用程序的自定义权限](../../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [如何：使用受限权限对 ClickOnce 应用程序进行调试](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [ClickOnce 安全和部署](../../deployment/clickonce-security-and-deployment.md)   
 [项目属性引用](../../ide/reference/project-properties-reference.md)   
 [“高级安全设置”对话框](../../ide/reference/advanced-security-settings-dialog-box.md)