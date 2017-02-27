---
title: "如何：指定部署更新的其他位置 | Microsoft Docs"
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
  - "ClickOnce 部署, 更新"
  - "部署更新, 可选位置"
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：指定部署更新的其他位置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

最初可以通过 CD 或文件共享来安装 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序，但该应用程序必须在 Web 上检查定期更新。  您可以为部署清单中的更新指定备用位置，以便应用程序可以在初始安装之后通过 Web 进行自我更新。  
  
> [!NOTE]
>  若要使用此功能，必须将应用程序配置为本地安装。  有关更多信息，请参见[演练：手动部署 ClickOnce 应用程序](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。  另外，如果通过网络安装 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序，则设置备用位置会导致 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 使用该位置进行初始安装和所有后续更新。  如果在本地安装应用程序（例如，从 CD 安装），将会使用原始媒体执行初始安装，而所有后续更新都将使用备用位置。  
  
### 使用 MageUI.exe（基于 Windows 窗体的实用工具）指定用于更新的备用位置  
  
1.  打开 .NET Framework 命令提示窗口并键入：  
  
     **mageui.exe**  
  
2.  在**“文件”**菜单上选择**“打开”**，以打开应用程序的部署清单。  
  
3.  选择**“部署选项”**选项卡。  
  
4.  在名为**“启动位置”**的文本框中，输入应用程序更新的部署清单所在目录的 URL。  
  
5.  保存该部署清单。  
  
### 使用 Mage.exe 指定用于更新的备用位置  
  
1.  打开 .NET Framework 命令提示窗口。  
  
2.  使用下面的命令设置更新位置。  在此示例中，**HelloWorld.exe.application** 是 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序清单的路径，该路径始终带有 .application 扩展名，而 **http:\/\/adatum.com\/Update\/Path** 则是 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 用来检查应用程序更新的 URL。  
  
     **Mage \-Update HelloWorld.exe.application \-ProviderUrl http:\/\/adatum.com\/Update\/Path**  
  
3.  保存该文件。  
  
    > [!NOTE]
    >  您现在需要使用 Mage.exe 对该文件重新签名。  有关更多信息，请参见[演练：手动部署 ClickOnce 应用程序](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。  
  
## .NET Framework 安全性  
 如果从脱机介质（如 CD）安装应用程序，并且计算机处于联机状态，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 将会首先检查由部署清单中的 `<deploymentProvider>` 标记指定的 URL，以确定该更新位置是否包含较新版本的应用程序。  如果包含，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 将直接从该处安装应用程序，而不是从初始安装目录安装，同时公共语言运行时 \(CLR\) 会使用 `<deploymentProvider>` 来确定应用程序的信任级别。  如果计算机处于脱机状态，或 `<deploymentProvider>` 无法访问，则 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 将从 CD 安装，同时 CLR 会基于安装点授予信任级别；对于 CD 安装，这意味着应用程序接收完全信任。  所有后续更新将继承该信任级别。  
  
 使用 `<deploymentProvider>` 的所有 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序都应该在其应用程序清单中显式声明它们所需的权限，以便应用程序不会在不同计算机上接收不同的信任级别。  
  
## 请参阅  
 [演练：手动部署 ClickOnce 应用程序](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)   
 [保护 ClickOnce 应用程序](../deployment/securing-clickonce-applications.md)   
 [选择 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)