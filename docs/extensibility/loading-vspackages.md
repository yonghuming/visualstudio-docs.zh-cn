---
title: "加载 Vspackage |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 29022d14311e71b7ee33f5339f8e450c47d1ce5c
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2017
---
# <a name="loading-vspackages"></a>加载 Vspackage
仅当需要其功能时，Vspackage 都会加载到 Visual Studio。 例如，当 Visual Studio 使用项目工厂或 VSPackage 实现的服务时，将加载 VSPackage。 此功能称为延迟的加载，这可以提高性能时，需要使用。  
  
> [!NOTE]
>  Visual Studio 可以确定某些 VSPackage 信息，如 VSPackage 提供，而无需加载 VSPackage 的命令。  
  
 Vspackage 可以设置为自动上载在特定用户界面 (UI) 上下文中，例如，打开解决方案时。 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>属性设置此上下文。  
  
### <a name="autoloading-a-vspackage-in-a-specific-context"></a>在特定上下文中 VSPackage 自动加载  
  
-   添加`ProvideAutoLoad`属性设为 VSPackage 属性：  
  
    ```csharp  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     请参阅的枚举的字段<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>有关 UI 上下文和其 GUID 值的列表。  
  
-   中设置断点<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>方法。  
  
-   生成 VSPackage 并启动调试。  
  
-   加载的解决方案或创建一个。  
  
     VSPackage 加载并在断点处停止。  
  
## <a name="forcing-a-vspackage-to-load"></a>强制 VSPackage 加载  
 在某些情况下可能需要强制另一个 VSPackage 加载 VSPackage。 例如，轻型 VSPackage 可能会加载更大 VSPackage 不可作为 CMDUIContext 的上下文中。  
  
 你可以使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A>方法，以强制 VSPackage 加载。  
  
-   将此代码插入<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>强制加载的另一个 VSPackage 的 vspackage 的方法：  
  
    ```csharp  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     初始化 VSPackage 时，它会强制`PackageToBeLoaded`加载。  
  
     强制加载不应该用于 VSPackage 通信。 使用[使用和提供服务](../extensibility/using-and-providing-services.md)相反。
  
## <a name="see-also"></a>请参阅  
 [VSPackage](../extensibility/internals/vspackages.md)
