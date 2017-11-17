---
title: "如何： 指定 ClickOnce 部署的详细日志文件 |Microsoft 文档"
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
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 2fccf1b0c9d7a67ca1eeb6058c1294cea2f2005a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>如何：指定 ClickOnce 部署的详细日志文件
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]维护活动的所有部署的日志文件。 这些日志记录详细信息与安装、 初始化、 更新和卸载相关[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署。 若要增加详细信息，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]写入这些日志文件，使用注册表编辑器 (**regedit.exe**) 来指定详细级别。  
  
> [!CAUTION]
>  注册表编辑器使用不当可造成严重的问题，可能需要重新安装操作系统。 使用注册表编辑器的风险由用户自行承担。  
  
 以下过程说明如何指定详细级别为[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]日志为当前用户的文件。 若要减少的详细级别，请删除此注册表值。  
  
### <a name="to-specify-verbose-log-files"></a>指定详细日志文件  
  
1.  打开**Regedit.exe**。  
  
2.  导航到的节点`HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`。  
  
3.  如有必要，创建一个名为的新字符串值`LogVerbosityLevel`。  
  
4.  设置`LogVerbosityLevel`值赋给`1`。  
  
## <a name="see-also"></a>另请参阅  
 [ClickOnce 部署疑难解答](../deployment/troubleshooting-clickonce-deployments.md)