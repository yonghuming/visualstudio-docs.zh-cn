---
title: "如何：禁用 ClickOnce 应用程序的 URL 激活 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "ClickOnce 部署, URL 激活"
  - "disallowUrlActivation"
  - "URL 激活, ClickOnce 应用程序"
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 如何：禁用 ClickOnce 应用程序的 URL 激活
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

通常，从 Web 服务器安装 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序后它会立即自动启动。  出于安全原因，你可以决定禁用此行为，并告诉用户改为从“开始”菜单启动该应用程序。  以下过程描述了如何禁用 URL 激活。  
  
 此方法仅适用于从 Web 服务器安装到用户计算机上的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序。  它不能用于仅联机应用程序，仅联机应用程序可以通过使用其 URL 启动。  有关仅联机应用程序与已安装应用程序之间的差异的详细信息，请参阅[选择 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)。  
  
 此过程使用了 [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] 工具 MageUI.exe。  有关此工具的详细信息，请参阅[MageUI.exe（图形化客户端中的清单生成和编辑工具）](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)。  你还可以使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 执行此过程。  
  
## 过程  
  
#### 禁用应用程序的 URL 激活的步骤  
  
1.  在 MageUI.exe 中打开部署清单。  如果尚未创建一个清单，请按照[演练：手动部署 ClickOnce 应用程序](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)中的步骤创建。  
  
2.  选择“部署选项”选项卡。  
  
3.  清除“安装后自动运行应用程序”复选框。  
  
4.  保存并对清单进行签名。  
  
## 请参阅  
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)