---
title: "加载 Vspackage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Vspackage，自动加载"
  - "Vspackage，加载"
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# 加载 Vspackage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

仅当需要它们的功能时，VSPackages 迁移都会加载到 Visual Studio。 例如，Visual Studio 将项目工厂或 VSPackage 实现的服务时，将加载 VSPackage。 此功能称为延迟的加载，这尽可能使用以提高性能。  
  
> [!NOTE]
>  Visual Studio 可以确定某些 VSPackage 信息，如 VSPackage 提供，而不加载 VSPackage 的命令。  
  
 VSPackages 迁移可以设置为自动加载在特定用户界面 \(UI\) 上下文中，例如，打开解决方案时。<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> 属性可设置此上下文中。  
  
### 自动加载 VSPackage 中特定的上下文  
  
-   添加 `ProvideAutoLoad` 属性设为 VSPackage 属性︰  
  
    ```c#  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     请参阅的枚举的字段 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> 有关 UI 上下文和它们的 GUID 值的列表。  
  
-   中设置断点 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 方法。  
  
-   生成 VSPackage 并启动调试。  
  
-   加载解决方案或创建一个。  
  
     VSPackage 加载，并在断点处停止。  
  
## 强制加载的 VSPackage  
 在某些情况下可能需要强制另一个要加载的 VSPackage VSPackage。 例如，轻量 VSPackage 可能会加载更大的 VSPackage 中不能作为 CMDUIContext 的上下文。  
  
 您可以使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> 方法，以强制加载的 VSPackage。  
  
-   将此代码插入 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 强制另一个 VSPackage 加载 VSPackage 的方法︰  
  
    ```c#  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     当初始化 VSPackage 时，它会强制 `PackageToBeLoaded` 加载。  
  
     强制加载不应该用于 VSPackage 通信。 请改用 [使用并提供服务](../extensibility/using-and-providing-services.md)。  
  
## 使用自定义属性来注册 VSPackage  
 在某些情况下可能需要创建一个新的注册属性，您的扩展。 若要添加新的注册表项，或将新值添加到现有的密钥，可以使用注册属性。 新的属性必须派生自 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, ，并且它必须重写 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> 和 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> 方法。  
  
## 创建注册表项  
 在下面的代码中，创建自定义特性 **自定义** 在 VSPackage 正在注册的项下的子项。  
  
```c#  
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
  
## 创建在现有的注册表项下的新值  
 可以将自定义值添加到现有的密钥。 下面的代码演示如何将新值添加到 VSPackage 注册密钥。  
  
```c#  
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
  
## 请参阅  
 [Vspackage](../extensibility/internals/vspackages.md)