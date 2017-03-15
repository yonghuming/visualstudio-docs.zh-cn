---
title: "请关闭源代码管理插件的兼容性警告 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
caps.latest.revision: 21
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
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: e1dda3bd8c41efcf74a1b27f764fdfbf817f8d63
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>如何︰ 关闭源代码管理插件的兼容性警告
在使用中的源控件时，用户可能会看到几个兼容性警告[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 显示警告取决于源代码管理插件功能，可以禁用详细信息。  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>若要禁用警告:"以确保源代码管理与 Visual Studio …"  
  
-   设置以下注册表项 （如有必要，将添加值）︰  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = dword:&00000;001  
  
     此警告将显示所有非[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)]插件。  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>若要禁用警告:"已安装的源代码管理提供程序不支持所有功能，..."  
  
-   设置以下两个注册表值 （如有必要，将添加值）︰  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider =&00000;000 时表示  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = dword:&00000;001  
  
     如果源代码管理插件不显式支持可重入对多个项目 （即，如果它一次只能有一个文件和项目中检查），则会显示此警告。  
  
     最好是支持可重入 (`SCC_CAP_REENTRANT`功能); 这样做将消除此警告。 但是，如果这种支持不可能实现，可以设置这些注册表项。  
  
## <a name="see-also"></a>另请参阅  
 [功能标志](../extensibility/capability-flags.md)
