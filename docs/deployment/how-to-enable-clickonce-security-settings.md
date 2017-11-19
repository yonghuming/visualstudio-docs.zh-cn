---
title: "如何： 启用 ClickOnce 安全设置 |Microsoft 文档"
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
- security [Visual Studio], ClickOnce applications
- ClickOnce deployment, security settings
- security settings, ClickOnce deployment
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
caps.latest.revision: "8"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 7fc7df79f798596901d74d089baf1b84f1dcd152
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-enable-clickonce-security-settings"></a>How to: Enable ClickOnce Security Settings
若要发布应用程序，必须启用 ClickOnce 应用程序的代码访问安全性。 在发布使用发布向导的应用程序时，这会自动完成。  
  
 在某些情况下，启用代码访问安全性可能会影响性能时生成或调试应用程序;在这些情况下，你可能想要暂时禁用的安全设置。  
  
 可以启用 ClickOnce 安全设置，或将其上禁用**安全**页**项目设计器**。  
  
### <a name="to-enable-clickonce-security-settings"></a>若要启用 ClickOnce 安全设置  
  
1.  在“解决方案资源管理器” 中选择了项目的情况下，在“项目”  菜单上单击“属性” 。  
  
2.  单击 **“安全”** 选项卡。  
  
3.  选中“启用 ClickOnce 安全设置”  复选框。  
  
     现在可以自定义你在安全页上的应用程序的安全设置。  
  
    > [!NOTE]
    >  通过发布应用程序每次都会自动选中此复选框**发布**向导。  
  
### <a name="to-disable-clickonce-security-settings"></a>若要禁用 ClickOnce 安全设置  
  
1.  在“解决方案资源管理器” 中选择了项目的情况下，在“项目”  菜单上单击“属性” 。  
  
2.  单击 **“安全”** 选项卡。  
  
3.  清除**启用 ClickOnce 安全设置**复选框。  
  
     你的应用程序将运行与完全信任的安全设置;上的任何设置**安全**页面将被忽略。  
  
    > [!NOTE]
    >  每次发布应用程序时使用发布向导中，将选中此复选框;你必须在每个成功发布后再次清除它。  
  
## <a name="see-also"></a>另请参阅  
 [保护 ClickOnce 应用程序](../deployment/securing-clickonce-applications.md)   
 [ClickOnce 应用程序的代码访问安全性](../deployment/code-access-security-for-clickonce-applications.md)   
 
