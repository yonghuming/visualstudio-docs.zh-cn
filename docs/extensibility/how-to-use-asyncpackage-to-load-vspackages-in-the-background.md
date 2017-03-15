---
title: "如何︰ 使用 AsyncPackage 加载在后台的 Vspackage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
caps.latest.revision: 8
ms.author: "gregvanl"
caps.handback.revision: 8
---
# 如何︰ 使用 AsyncPackage 加载在后台的 Vspackage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

加载并初始化一个 VS 软件包会导致磁盘 I\/O。 如果此类 I\/O 情况在 UI 线程上发生，它可能导致响应能力问题。 若要解决此问题，Visual Studio 2015 引入 <xref:Microsoft.VisualStudio.Shell.AsyncPackage> 就能在后台线程上的包加载的类。  
  
## 创建 AsyncPackage  
 您可以通过创建一个 VSIX 项目开始 \(**文件 \/ 新建 \/ 项目 \/ Visual C\# \/ 可扩展性 \/ VSIX 项目**\) 并添加到项目的 VSPackage \(右键单击该项目和 **添加 \/ 新建项 \/ C\# 项目扩展性\/\/visual Studio 包**\)。 然后，可以创建您的服务，并将这些服务添加到您的包。  
  
1.  派生从包 <xref:Microsoft.VisualStudio.Shell.AsyncPackage>。  
  
2.  如果你要提供的服务的查询可能会导致您要加载的包︰  
  
     向 Visual Studio 指示您的程序包是可安全执行后台加载并决定执行到此行为，您 <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> 应设置 **AllowsBackgroundLoading** 属性设为 true 属性构造函数中。  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]  
  
    ```  
  
     若要指示 Visual Studio，则可以安全地实例化您的服务在后台线程上，应设置 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> 属性设为 true 中 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> 构造函数。  
  
    ```c#  
    [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]  
  
    ```  
  
3.  如果您正在加载通过 UI 上下文中，则应指定 **PackageAutoLoadFlags.BackgroundLoad** 为 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> 或作为包的自动加载项的值写入到标志的值 \(0x2\)。  
  
    ```c#  
    [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]  
  
    ```  
  
4.  如果您有异步初始化工作要做，则应重写 <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>。 删除 **initialize （\)** VSIX 模板所提供的方法。 \( **Initialize （\)** 中的方法 **AsyncPackage** 都密封的\)。 您可以使用任一 <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> 方法将异步服务添加到您的包。  
  
     注意︰ 若要调用 **基。InitializeAsync\(\)**, ，可以更改到您的源代码︰  
  
    ```c#  
    await base.InitializeAsync(cancellationToken, progress);  
    ```  
  
5.  您必须小心以免使 Rpc （删除过程调用） 在异步初始化代码中 \(在 **InitializeAsync**\)。 可以在调用时 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 直接或间接。  当同步加载是必需的时 UI 线程将阻止使用 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>。 默认阻止模型禁用 Rpc。 这意味着，如果您尝试使用 RPC 从异步任务，您将发生死锁，如果 UI 线程本身等待您要加载的包。 常规的替代方法是进行封送到 UI 线程代码，如果需要使用类似 **加入任务工厂**的 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> 或不使用 RPC 的某种其他机制。  请不要使用 **ThreadHelper.Generic.Invoke** 或通常阻止调用线程正在等待获取对 UI 线程。  
  
     注意︰ 应避免使用 **GetService** 或 **QueryService** 中您 **InitializeAsync** 方法。 如果您必须使用这些，您需要先切换到 UI 线程。 替代方法是使用 <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> 从您 **AsyncPackage** \(通过它强制转换为 <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>。\)  
  
 C\# 中︰ 创建 AsyncPackage:  
  
```c#  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]       
[ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]   
public sealed class TestPackage : AsyncPackage   
{   
    protected override Task InitializeAsync(System.Threading.CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)   
    {               
        this.AddService(typeof(SMyTestService), CreateService, true);   
        return Task.FromResult<object>(null);   
    }   
}  
```  
  
## 将现有的 VSPackage 转换为 AsyncPackage  
 大部分工作是创建一个新相同 **AsyncPackage**。 您需要执行步骤 1 至 5 更高版本。 您还需要特别注意以下︰  
  
1.  请记住删除任何 **初始化** 已将在您的包的替代。  
  
2.  避免死锁︰ 可能有隐藏代码现在发生这种情况在后台线程中的 Rpc。 您需要确保，如果要进行 RPC \(例如 **GetService**\)、 你需要转到主线程 \(1\) 或 （2） 使用的 API，如果一个异步版本存在 \(例如 **GetServiceAsync**\)。  
  
3.  不会改变过于频繁地在线程之间。 请尝试进行本地化的工作，以及在后台线程可能会发生。 这将减少加载时间。  
  
## AsyncPackage 从服务中查询  
 **AsyncPackage** 可能或可能不会加载以异步方式具体取决于调用方。 例如，  
  
-   如果调用方调用 **GetService** 或 **QueryService** \(这两个同步 Api\) 或  
  
-   如果调用方调用 **IVsShell::LoadPackage** \(或 **IVsShell5::LoadPackageWithContext**\) 或  
  
-   由 UI 上下文中，触发负载，但未指定 UI 上下文机制可以以异步方式加载您  
  
 然后，您的包将以同步方式加载。  
  
 请注意，您的包仍有机会 （在异步初始化阶段） 来完成的工作出 UI 线程，但该 UI 线程将阻止该工作完成。 如果调用方使用 **IAsyncServiceProvider** 以异步方式查询您的服务，然后加载和初始化将完成异步假定立即不阻止在生成的任务对象上。  
  
 C\# 中︰ 如何以异步方式查询服务︰  
  
```c#  
using Microsoft.VisualStudio.Shell;   
using Microsoft.VisualStudio.Shell.Interop;   
  
IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;   
IMyTestService testService = await ayncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;  
```