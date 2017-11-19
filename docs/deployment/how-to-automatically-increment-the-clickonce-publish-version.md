---
title: "如何： 自动递增 ClickOnce 发布版本 |Microsoft 文档"
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
- deploying applications [ClickOnce], incrementing publish version automatically
- Publish Version property, incrementing
- ClickOnce deployment, incrementing publish version automatically
- publishing, ClickOnce
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 71665ea5053a4d3ddbdb933d2ecdf4ea20ba83c8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>如何：自动递增 ClickOnce 发布版本
发布时[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序，更改`Publish Version`属性导致应用程序作为更新发布。 默认情况下，Visual Studio 会自动增大`Revision`数`Publish Version`每次您发布应用程序。  
  
 你可以在禁用此行为**发布**页**项目设计器**。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
### <a name="to-disable-automatically-incrementing-the-publish-version"></a>若要禁用自动递增发布版本  
  
1.  在“解决方案资源管理器” 中选择了项目的情况下，在“项目”  菜单上单击“属性” 。  
  
2.  单击**发布**选项卡。  
  
3.  在**发布版本**部分中，清除**自动递增每个版本的修订号**复选框。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 设置 ClickOnce 发布版本](../deployment/how-to-set-the-clickonce-publish-version.md)   
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)   
 [如何：使用发布向导发布 ClickOnce 应用程序](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)