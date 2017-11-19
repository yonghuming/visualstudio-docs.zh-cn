---
title: "工具窗口在注册表中的 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 38b4415a24a7440a2d3725fb1183863e7a337bbb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="tool-windows-in-the-registry"></a>在注册表中的工具窗口
提供工具窗口的 Vspackage 必须注册[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]一样工具窗口提供程序。 通过使用 Visual Studio 包模板创建的工具窗口默认情况下执行此操作。 工具窗口提供程序具有指定可见性属性，例如默认工具窗口大小和位置，用作工具窗口窗格中和停靠样式的窗口的 GUID 的系统注册表项。  
  
 在开发期间，托管的工具窗口提供程序通过将特性添加到源代码，然后在生成的程序集上运行 RegPkg.exe 实用程序注册工具窗口。 有关详细信息，请参阅[注册工具窗口](../extensibility/registering-a-tool-window.md)。  
  
## <a name="registering-unmanaged-tool-window-providers"></a>通过注册非托管的工具窗口提供程序  
 非托管的工具窗口提供程序必须注册[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]系统注册表的 ToolWindows 部分中。 下面的.reg 文件片断演示注册动态工具窗口可能方式：  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 在上面的示例中的第一个键，版本号是版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，例如 7.1 或 8.0，子项 {f0e1e9a1-9860-484d-ad5d-367d79aabf55} 是工具窗口窗格 (DynamicWindowPane) 和默认值 {的 GUID01069cdd-95ce-4620-ac21-ddff6c57f012} 是 VSPackage 提供的工具窗口的 GUID。 Float 和 DontForceCreate 的子项的说明，请参阅[工具窗口显示配置](../extensibility/tool-window-display-configuration.md)。  
  
 第二个可选的密钥 ToolWindows\Visibility，指定需要让用户看到工具窗口的命令的 Guid。 在这种情况下，没有指定任何命令。 有关详细信息，请参阅[工具窗口显示配置](../extensibility/tool-window-display-configuration.md)。  
  
## <a name="see-also"></a>另请参阅  
 [VSPackage](../extensibility/internals/vspackages.md)