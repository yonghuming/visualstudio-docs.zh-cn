---
title: "工具窗口在注册表中的 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
caps.latest.revision: 12
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: dc99605a367bb3584f9766b50aa2a4ff382656c4
ms.lasthandoff: 02/22/2017

---
# <a name="tool-windows-in-the-registry"></a>在注册表中的工具窗口
必须使用注册提供的工具窗口的 Vspackage[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]为工具窗口提供程序。 工具窗口使用 Visual Studio Package 模板创建的默认情况下执行此操作。 工具窗口提供程序具有指定可见性属性，例如默认工具窗口大小和位置，窗口中，用作工具窗口窗格中和停靠样式的 GUID 的系统注册表项。  
  
 在开发期间，托管的工具窗口提供程序通过将属性添加到源代码中，然后上和运行 RegPkg.exe 实用程序生成的程序集注册工具窗口。 有关详细信息，请参阅[注册工具窗口](../extensibility/registering-a-tool-window.md)。  
  
## <a name="registering-unmanaged-tool-window-providers"></a>通过注册非托管的工具窗口提供程序  
 非托管的工具窗口提供程序必须使用注册[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ToolWindows 部分在系统注册表中。 下面的.reg 文件片断演示如何动态工具窗口可能会注册︰  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 在第一项在上面的示例中，版本号是版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、 如 7.1 或 8.0，子项 {f0e1e9a1-9860-484d-ad5d-367d79aabf55} 是在工具窗口窗格 (DynamicWindowPane) 的 GUID 和 {01069cdd-95ce-4620-ac21-ddff6c57f012} 的默认值是 VSPackage 提供工具窗口中的 GUID。 浮点型和 DontForceCreate 子项的说明，请参阅[工具窗口中显示配置](../extensibility/tool-window-display-configuration.md)。  
  
 第二个可选键 ToolWindows\Visibility，指定需要工具窗口中可见的命令的 Guid。 在这种情况下，没有指定命令。 有关详细信息，请参阅[工具窗口中显示配置](../extensibility/tool-window-display-configuration.md)。  
  
## <a name="see-also"></a>另请参阅  
 [VSPackage 要点](../misc/vspackage-essentials.md)
