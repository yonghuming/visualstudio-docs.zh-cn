---
title: "如何： 登录 Office 解决方案 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
ms.assetid: d3df5ee6-f1b7-47ed-b7ee-8985679ee3af
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 12a367b6051f7ed1ca1f51e0c9d7e8ada4be4ba6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-sign-office-solutions"></a>如何：对 Office 解决方案进行签名
  如果你登录解决方案，你可以授予对使用证书作为证据解决方案信任。 你可以为多个解决方案，使用相同的证书，所有的解决方案将没有其他安全策略更新受信任。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 如果您手动编辑应用程序和部署清单通过使用清单生成和编辑工具 （mage.exe 和 mageui.exe），你必须重新为清单签名之后才能使用它们。 有关详细信息，请参阅 [How to: Re-sign Application and Deployment Manifests](/visualstudio/deployment/how-to-re-sign-application-and-deployment-manifests)。  
  
## <a name="signing-by-using-a-certificate"></a>使用证书进行签名  
 证书是包含一个唯一键和解决方案发布服务器的标识的文件。 可以从证书颁发机构购买证书或创建你自己的证书，并且有对其进行签名的证书颁发机构。  
  
 Visual Studio 会对签名与一个临时证书来启用调试 Office 解决方案。 作为证据，不应在已部署的解决方案中使用该临时证书。  
  
#### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>使用证书对 Office 解决方案进行签名  
  
1.  上**项目**菜单上，单击*SolutionName***属性**。  
  
2.  单击“签名”选项卡。  
  
3.  选择**ClickOnce 清单签名**。  
  
4.  通过单击找到的证书**从存储中选择**或**从文件中选择**和导航到该证书。  
  
5.  若要验证是否正在使用正确的证书，请单击**更多详细信息**若要查看证书信息。  
  
## <a name="see-also"></a>另请参阅  
 [保护 Office 解决方案](../vsto/securing-office-solutions.md)   
 [向 Office 解决方案授予信任](../vsto/granting-trust-to-office-solutions.md)   
 [“项目设计器”->“签名”页](/visualstudio/ide/reference/signing-page-project-designer)  
  
  