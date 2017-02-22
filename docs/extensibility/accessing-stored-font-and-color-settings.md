---
title: "访问存储的字体和颜色设置 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "字体，访问存储的设置"
  - "字体和颜色控件 [Visual Studio SDK] 持久性"
  - "颜色，访问存储的设置"
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
caps.latest.revision: 26
caps.handback.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
---
# 访问存储的字体和颜色设置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 集成的开发环境 (IDE) 将存储修改后的设置字体和颜色在注册表中。 你可以使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 接口来访问这些设置。  
  
## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>若要启动的字体和颜色的状态持久性  
 字体和颜色信息存储在以下注册表位置中按类别: [HKCU\SOFTWARE\Microsoft \Visual Studio\\*\< Visual Studio 版本>*\FontAndColors\\*\< CategoryGUID>*]，其中 *\< CategoryGUID>* 类别 GUID。  
  
 因此，若要启动持久性，VSPackage 必须︰  
  
-   获取 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 接口通过调用 `QueryService` 针对全球服务提供程序。  
  
     `QueryService` 必须使用的服务 ID 自变量调用 `SID_SVsFontAndColorStorage` 和的接口 ID 参数 `IID_IVsFontAndColorStorage`。  
  
-   使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> 方法打开某个类别，以作为自变量中使用的类别的 GUID 和模式标志其进行持久化。  
  
     通过指定的模式 `fFlags` 自变量，构造中的值 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> 枚举。 此模式控制︰  
  
    -   可以通过设置 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 接口。  
  
    -   所有设置或仅那些用户修改且可通过检索 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 接口。  
  
    -   将更改传播到用户设置的方式。  
  
    -   所使用的颜色值的格式。  
  
## <a name="to-use-state-persistence-of-fonts-and-colors"></a>若要使用的字体和颜色的状态持久性  
 保留的字体和颜色包括︰  
  
-   使用存储在注册表中设置同步的 IDE 设置。  
  
-   传播注册表修改信息。  
  
-   设置和检索存储在注册表中设置。  
  
 同步与 IDE 设置的存储设置是很大程度上透明的。 基础 IDE 自动写入更新的设置 **显示项** 到注册表项的类别。  
  
 如果多个 Vspackage 共享的特定类别，VSPackage 应要求将生成的事件时的方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 使用接口来修改存储的注册表设置。  
  
 默认情况下，不启用事件生成。 若要启用事件生成，类别必须打开使用 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>。 这将导致 IDE 以调用适当 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> VSPackage 实现的方法。  
  
> [!NOTE]
>  通过修改 **字体和颜色** 属性页生成事件的独立 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>。 你可以使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> 接口来确定是否在调用的方法之前需要缓存的字体和颜色设置的更新 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 类。  
  
### <a name="storing-and-retrieving-information"></a>存储和检索信息  
 若要获取或配置用户可以修改为在打开的类别命名的显示项的信息，Vspackage 调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> 方法。  
  
 使用获取特定类别信息字体属性 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> 方法。  
  
> [!NOTE]
>   `fFlags` 自变量传递给 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> 方法打开该类别时定义的行为 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> 方法。 默认情况下，这些方法仅返回信息 aboutdisplay itemsthat 已更改。 但是，如果通过打开类别 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> 标志，同时更新，并可以通过访问不变的显示项 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>。  
  
 默认情况下，仅更改 **显示项** 信息保留在注册表中。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 接口不能用于检索所有设置的字体和颜色。  
  
> [!NOTE]
>   <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> 方法返回有关不变的 REGDB_E_KEYMISSING，(0x80040152L) 时使用它们来检索信息 **显示项**。  
  
 所有设置 **显示项** 以特定 **类别** 可以通过使用的方法来获取 `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` 接口。  
  
## <a name="see-also"></a>请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>   
 [实现自定义类别和显示项](../extensibility/implementing-custom-categories-and-display-items.md)