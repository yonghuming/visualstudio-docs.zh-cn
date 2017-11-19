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
ms.openlocfilehash: 94db8d3bb95e254a3fa528a424048162916fce99
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
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
  
## <a name="using-a-custom-attribute-to-register-a-vspackage"></a>使用自定义特性注册 VSPackage  
 在某些情况下可能需要创建你的扩展的新注册属性。 若要添加新的注册表项，或将新值添加到现有的密钥，你可以使用注册特性。 新的属性必须派生自<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>，且必须重写<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A>和<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A>方法。  
  
## <a name="creating-a-registry-key"></a>创建注册表项  
 在下面的代码中，创建自定义特性**自定义**子项下要注册的 VSPackage 的密钥。  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
    }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");  
}  
  
```  
  
## <a name="creating-a-new-value-under-an-existing-registry-key"></a>创建现有的注册表项下的新值  
 可以将自定义值添加到现有密钥。 下面的代码演示如何将新值添加到 VSPackage 注册密钥。  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
                }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [VSPackage](../extensibility/internals/vspackages.md)