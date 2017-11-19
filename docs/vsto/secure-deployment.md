---
title: "安全部署 |Microsoft 文档"
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
- deploying applications [Office development in Visual Studio], security
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- ClickOnce deployment [Office development in Visual Studio], security
ms.assetid: c5ba86b1-e87f-4508-8c5a-1295681a9590
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c77d5fb404be8dda323720c1e0c1ab2c1887c88f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="secure-deployment"></a>安全部署
  时创建 Office 解决方案时，将自动更新你的开发计算机以允许你运行的项目中的代码。 但是，在部署你的解决方案时，你必须提供通过签名解决方案使用证书，或使用基于信任决定的证据[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]信任提示密钥。 有关详细信息，请参阅[向 Office 解决方案授予信任](../vsto/granting-trust-to-office-solutions.md)。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 对于文档级自定义项，如果将文档部署到网络位置，你还必须添加该文档的位置到的信任中心中的 Office 应用程序的受信任位置的列表。 有关如何设置最终用户计算机文档权限的详细信息，请参阅[向文档授予信任](../vsto/granting-trust-to-documents.md)。  
  
## <a name="preventing-office-solutions-from-running-code"></a>阻止 Office 解决方案运行代码  
 管理员可以使用注册表以防止所有 Office 解决方案的计算机上运行。 具有托管代码扩展的 Office 解决方案打开时，Visual Studio Tools for Office 运行时检查的条目是否同名`Disabled`存在在计算机上的以下注册表项之一：  
  
-   `HKEY_CURRENT_USER\Software\Microsoft\VSTO`  
  
-   `HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO`  
  
 若要阻止 Office 解决方案运行代码，请创建`Disabled`下一个或两个这些注册表项的项并指定一种的以下数据类型和值`Disabled`:  
  
-   REG_SZ 或 REG_EXPAND_SZ 设置为"0"（零） 以外的任何字符串。  
  
-   设置为 0 （零） 以外的任何值的 REG_DWORD。  
  
 若要启用 Office 解决方案运行代码，可以设置这两个`Disabled`条目为 0 （零），或删除的注册表项。  
  
## <a name="see-also"></a>另请参阅  
 [部署 Office 解决方案](../vsto/deploying-an-office-solution.md)   
 [准备计算机以运行或承载 Office 解决方案](http://msdn.microsoft.com/en-us/be1b173f-7261-4d74-aa4e-94ccd43db8d8)   
 [确保 Office 解决方案的安全](../vsto/securing-office-solutions.md)  
  
  