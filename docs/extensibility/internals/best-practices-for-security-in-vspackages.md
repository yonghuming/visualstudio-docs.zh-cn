---
title: "在 Vspackage 中的安全最佳实践 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: c7ceb884ad060ea45c0fd204b5611ce284d3d2af
ms.lasthandoff: 02/22/2017

---
# <a name="best-practices-for-security-in-vspackages"></a>在 Vspackage 中安全性的最佳做法
若要安装[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]在计算机上，您必须在运行具有管理凭据的上下文。 安全和部署的基本单位[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]应用程序是[Vspackage](../../extensibility/internals/vspackages.md)。 必须使用注册 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，这也要求管理凭据。  
  
 管理员具有完全权限写入到注册表和文件系统中，并运行任何代码。 您必须具有这些权限才能开发、 部署或安装 VSPackage。  
  
 只要安装它，就完全受信任 VSPackage。 由于这种高度的 VSPackage 的关联权限，就可能会无意中安装具有恶意企图的 VSPackage。  
  
 用户应确保他们仅从可信来源安装 Vspackage。 开发 Vspackage 的公司应强命名并签名，以确保用户该篡改被禁止。 开发 Vspackage 的公司应检查其外部依赖关系，如 web 服务和远程安装，以评估并更正任何安全问题。  
  
 详细信息，请参阅.NET Framework 安全编码准则 ([http://msdn.microsoft.com/library/d55zzx87.aspx](http://msdn.microsoft.com/library/d55zzx87.aspx))。  
  
## <a name="see-also"></a>另请参阅  
 [外接程序安全性](http://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)   
 [DDEX 安全](http://msdn.microsoft.com/en-us/44a52a70-5c98-450e-993d-4a3b32f69ba8)
