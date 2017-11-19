---
title: "如何： 设置 ClickOnce 发布版本 |Microsoft 文档"
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
- ClickOnce deployment, setting publish version
- publishing, ClickOnce
- Publish Version property
ms.assetid: 06f15504-6385-40a6-b01d-cd90ca36dc73
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: be66edb3880e8ef91f8fd95d7f11fe465322451f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-set-the-clickonce-publish-version"></a>如何：设置 ClickOnce 发布版本
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version`属性确定你发布的应用程序是否将被视为更新。 每个时间版本将递增，将作为更新发布应用程序。  
  
 `Publish Version`属性可以设置上**发布**页**项目设计器**。  
  
> [!NOTE]
>  没有一种项目选项，将自动递增`Publish Version`属性每次发布应用程序; 默认情况下启用此选项。 有关详细信息，请参阅[如何： 自动递增 ClickOnce 发布版本](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)。  
  
### <a name="to-change-the-publish-version"></a>若要更改发布版本  
  
1.  在“解决方案资源管理器” 中选择一个项目，然后在“项目”  菜单上单击“属性” 。  
  
2.  单击**发布**选项卡。  
  
3.  在**发布版本**字段中，递增**主要**，**次要**，**生成**，或**修订**版本数字。  
  
    > [!NOTE]
    >  你应永远不会递减版本号;这样做可能导致不可预知的更新行为。  
  
## <a name="see-also"></a>另请参阅  
 [选择 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)   
 [如何： 自动递增 ClickOnce 发布版本](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)   
 [如何：使用发布向导发布 ClickOnce 应用程序](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)