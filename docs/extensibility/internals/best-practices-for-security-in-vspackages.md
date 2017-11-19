---
title: "Vspackage 中的安全性的最佳实践 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 770dff4b531bf4a7347cb648ca4c930b28b79bea
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="best-practices-for-security-in-vspackages"></a>在 Vspackage 中的安全性的最佳做法
若要安装[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]在计算机上，你必须在运行的管理凭据的上下文。 安全和部署的基本单位[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]应用程序是[Vspackage](../../extensibility/internals/vspackages.md)。 必须使用注册 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，这也要求管理凭据。  
  
 管理员具有完全权限将写入到注册表和文件系统，并运行任何代码。 你必须具有这些权限来开发、 部署或安装 VSPackage。  
  
 就会立即安装，则 VSPackage 是完全受信任。 由于此高的级别的 VSPackage 与关联的权限，则可以无意中安装 VSPackage 具有恶意攻击的损害。  
  
 用户应确保它们仅从可信的源安装 Vspackage。 公司开发 VSPackages 应强命名，并对它们进行签名，以确保用户该篡改阻止。 公司开发 VSPackages 应检查其外部的依赖项，如 web 服务和远程安装，以评估并更正任何安全问题。  
  
 详细信息，请参阅.NET Framework 安全编码准则 ([http://msdn.microsoft.com/library/d55zzx87.aspx](http://msdn.microsoft.com/library/d55zzx87.aspx))。  
  
## <a name="see-also"></a>另请参阅  
 [外接程序安全性](http://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)   
 [DDEX 安全](http://msdn.microsoft.com/en-us/44a52a70-5c98-450e-993d-4a3b32f69ba8)