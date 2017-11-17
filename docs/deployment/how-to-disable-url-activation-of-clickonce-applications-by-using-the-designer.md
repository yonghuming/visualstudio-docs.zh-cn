---
title: "如何： 使用设计器禁用 ClickOnce 应用程序的 URL 激活 |Microsoft 文档"
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
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
caps.latest.revision: "16"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: f694b7bf80d15fa3674d64bb7d062cdf0953c14b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>如何：使用设计器禁用 ClickOnce 应用程序的 URL 激活
通常情况下，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]安装从 Web 服务器之后立即应用程序将自动启动。 出于安全原因，您可以决定禁用此行为，并告知用户启动应用程序从**启动**菜单相反。 以下过程描述了如何禁用 URL 激活。  
  
 此方法仅适用于从 Web 服务器安装到用户计算机上的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序。 它不能用于仅联机应用程序，可以仅通过使用其 URL 启动。 有关仅联机且已安装的应用程序之间区别的详细信息，请参阅[选择 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)。  
  
 此过程使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 您还可以通过以下方式完成此任务使用[!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]。 有关详细信息，请参阅[如何： 禁用 URL 激活的 ClickOnce 应用程序](../deployment/how-to-disable-url-activation-of-clickonce-applications.md)。  
  
## <a name="procedure"></a>过程  
  
#### <a name="to-disable-url-activation-for-your-application"></a>禁用应用程序的 URL 激活的步骤  
  
1.  右键单击项目名称**解决方案资源管理器**，然后单击**属性**。  
  
2.  上**属性**页上，单击**发布**选项卡。  
  
3.  单击“选项” 。  
  
4.  单击**清单**。  
  
5.  选择标记的复选框**阻止通过 URL 激活应用程序**。  
  
6.  部署应用程序。  
  
## <a name="see-also"></a>另请参阅  
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)