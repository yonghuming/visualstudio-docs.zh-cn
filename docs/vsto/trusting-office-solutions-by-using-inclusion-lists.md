---
title: "使用包含列表信任 Office 解决方案 |Microsoft 文档"
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
- permissions [Office development in Visual Studio]
- inclusion lists [Office development in Visual Studio], about inclusion lists
- security [Office development in Visual Studio], inclusion lists
- inclusion lists [Office development in Visual Studio]
ms.assetid: 6dae0128-435b-4fa1-aed9-73e728fdcacf
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7e50809b5e57a832c9f085172832dd2e1a4db45a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="trusting-office-solutions-by-using-inclusion-lists"></a>使用包含列表信任 Office 解决方案
  包含列表让用户能够向使用标识发布者的证书进行签名的 Office 解决方案授予信任。 包含列表是用户特定的，并可用于文档级自定义项和 VSTO 外接程序。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 当用户启动未针对该用户授予信任的 Office 解决方案时，Microsoft Office 解决方案将使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 信任提示来提示该用户进行安全决策。 如果用户决定信任该解决方案，则将运行自定义项，并且下次不再提示该用户。  
  
## <a name="inclusion-list-and-windows-installer"></a>包含列表和 Windows Installer  
 使用 Windows Installer 将 Office 解决方案安装到 Program Files 目录的操作需要管理员权限。 对于 Program Files 目录中的 Office 解决方案，Visual Studio Tools for Office 运行时将不再检查包含列表，因为已向 Office 解决方案授予 FullTrust 权限。  
  
## <a name="clickonce-trust-prompt"></a>ClickOnce 信任提示  
 通过使用 Office 解决方案的 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 实现，管理员可以将信任提示级别配置为允许提示、禁用提示或需要受信任的证书。 使用控制包含列表访问权限的注册表项完成此配置。  
  
 如果禁用提示，则只能安装具有受信任和已知证书的解决方案。 如果将提示级别设置为需要验证码，解决方案必须使用来自已知颁发机构的证书进行签名，但不需要链接至受信任的根证书颁发机构的证书（受信任的证书）。 如果允许提示，则可以使用具有未知标识的证书进行对解决方案进行签名。 在此场景中，信任决定取决于最终用户，并且临时证书即足以安装解决方案。  
  
 有关详细信息，请参阅 [How to: Configure Inclusion List Security](../vsto/how-to-configure-inclusion-list-security.md) 以及 [配置 ClickOnce 受信任的发布者](http://go.microsoft.com/fwlink/?LinkId=94774)中的表 2（标题为：各提示级别下注册表项值的启动效果）。  
  
## <a name="structure-of-the-inclusion-list"></a>包含列表的结构  
 一个有效的包含列表条目由两部分组成：部署清单的路径和用于对解决方案进行签名的公钥。 将解决方案添加到包含列表后，则将其视为受信任。 运行 Office 解决方案时，Office 应用程序将比较包含列表中的公钥与部署清单中的签名密钥，从而验证当前正在运行的解决方案与原始受信任版本是否相同。  
  
## <a name="see-also"></a>另请参阅  
 [向 Office 解决方案授予信任](../vsto/granting-trust-to-office-solutions.md)   
 [确保 Office 解决方案的安全](../vsto/securing-office-solutions.md)  
  
  