---
title: "如何︰ 安装了源代码管理插件 | Microsoft Docs"
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
  - "安装 [Visual Studio SDK]，源代码管理插件"
  - "源控件的插件安装"
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
caps.latest.revision: 32
caps.handback.revision: 32
ms.author: "gregvanl"
manager: "ghogen"
---
# 如何︰ 安装了源代码管理插件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

创建源代码管理插件包括三个步骤︰  
  
1.  创建与在本文档的源控制插件 API 参考部分中定义的函数的 DLL。  
  
2.  实现的源控制插件 API 定义函数。 当 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 调用，使接口和对话框可从插件。  
  
3.  通过进行相应的注册表项注册 DLL。  
  
## <a name="integration-with-visual-studio"></a>与 Visual Studio 的集成  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 支持源控件插件符合源控制插件 API。  
  
### <a name="registering-the-source-control-plug-in"></a>注册源代码管理插件  
 正在运行的集成的开发环境 (IDE) 可以调入源代码管理系统之前，必须首先找到源控制导出 API 的插件 DLL。  
  
##### <a name="to-register-the-source-control-plug-in-dll"></a>若要注册的源控件插件 DLL  
  
1.  指定你的产品名称子项后跟你公司名称子项中的软件子项中再添加两项在 HKEY_LOCAL_MACHINE 键下。 模式是 HKEY_LOCAL_MACHINE\SOFTWARE\\*[公司名称]*\\*[产品名称]*\\*[entry]* = value。 SCCServerName 和 SCCServerPath 始终调用两个条目。 每个是规则的字符串。  
  
     例如，如果你的公司名称是 Microsoft 和你的源代码控制产品名为 SourceSafe，则此注册表路径将 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe。 在此子项中的第一个条目，SCCServerName，为命名你的产品用户可读字符串。 第二个条目，SCCServerPath，是对源的完整路径控制 IDE 应连接到的插件 DLL。 下面提供了示例注册表条目︰  
  
    |示例注册表条目|示例值|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|c:\vss\win32\ssscc.dll|  
  
    > [!NOTE]
    >  SCCServerPath 是 SourceSafe 插件的完整路径。 你的源代码管理插件将使用不同的公司和产品名称，但相同的注册表项路径。  
  
2.  以下可选的注册表条目可以用于修改你的源代码管理插件的行为。 这些项进入 SccServerPath SccServerName 以及相同的子项。  
  
    -   如果你不希望您的源控件即插即用-接程序显示的插件选择列表中，可以使用 HideInVisualStudioregistry 条目 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 此条目还将影响自动切换到源代码管理插件。 为此条目的一个可能的用途是如果你提供替换你的源代码管理插件源代码管理包，但你想要方便用户来迁移来自使用源代码管理插件到源代码管理包。 安装源代码管理包时，它会设置此注册表项，这样可以隐藏该插件。  
  
         HideInVisualStudio 为 DWORD 值，并设置为 1 以隐藏插件或 0，则显示插件。 如果未显示的注册表项，默认行为是显示该插件。  
  
    -   可以使用 DisableSccManager 注册表项来禁用或隐藏 **启动 \< 源代码管理服务器>** 通常下显示的菜单选项 **文件** -> **源代码管理** 子菜单。 选择此菜单选项调用 [SccRunScc](../../extensibility/sccrunscc-function.md) 函数。 你的源代码管理插件可能不支持外部程序，因此你可能想要禁用或甚至隐藏 **启动** 菜单选项。  
  
         DisableSccManager 是 DWORD 值设置为 0，以启用 **启动 \< 源代码管理服务器>** 菜单选项，设置为 1 可禁用的菜单选项，并将设置为 2，若要隐藏菜单选项。 如果未显示此注册表项，默认行为是显示的菜单选项。  
  
    |示例注册表条目|示例值|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio|1|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager|1|  
  
3.  添加下的子项，SourceCodeControlProvider，在软件的子项的 HKEY_LOCAL_MACHINE 键。  
  
     在此子项下的注册表项 ProviderRegKey 设置为一个字符串，表示放置在步骤 1 中的注册表子项。 模式是 HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey = 软件\\*[公司名称]*\\*[产品名称]*。  
  
     下面是此子项的示例内容。  
  
    |注册表项|示例值|  
    |--------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  你的源代码管理插件将使用相同的子项和条目名称，但值会不同。  
  
4.  创建名 InstalledSCCProviders 为 SourceCodeControlProvider 子项下, 一个子项，然后进行该子项下的一个条目。  
  
     此条目的名称为提供程序 （与相同为 SCCServerName 条目指定的值），用户可读名称，值再次，为步骤 1 中创建的子项。 模式是 HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\*[显示名称]* = 软件\\*[公司名称]*\\*[产品名称]*。  
  
     例如：  
  
    |示例注册表条目|示例值|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  可以有多个源控制插件在这种方式中注册。 这是如何 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 查找所有安装基于源控制插件 API 的插件。  
  
## <a name="how-an-ide-locates-the-dll"></a>一个 IDE 如何定位 DLL  
  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 提供两种方法可以查找源控制插件 DLL:  
  
-   找到默认的源代码管理插件，并以无提示方式连接到它。  
  
-   查找所有已注册的源控件插件从中用户选择其中之一。  
  
 若要在第一种方法中查找该 DLL，IDE 将查找在条目 ProviderRegKey HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider 子项下。 此项的值是指向另一个子项。 IDE 将然后查找名 SccServerPath 为在该第二个子项中 HKEY_LOCAL_MACHINE 下的条目。 此项的值在 DLL 中指向 IDE。  
  
> [!NOTE]
>  IDE 不会从相对路径 (例如，.\NewProvider.DLL) 加载 Dll。 必须指定 DLL 的完整路径 (例如，c:\Providers\NewProvider.DLL)。 这可在 IDE 的安全增强通过阻止未经授权或模拟插件 Dll 的加载。  
  
 若要在第二种方法中查找该 DLL，IDE 将查找所有条目的 HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders 子项下*。* 每个条目都具有一个名称和值。 IDE 为用户显示这些名称的列表*。* 当用户选择一个名称时，IDE 将查找指向一个子项的所选名称的值。 IDE 将查找名 SccServerPath 为在该子项中 HKEY_LOCAL_MACHINE 下的条目。 该条目的值将 IDE 指向正确的 DLL。  
  
 源代码管理插件需要支持查找 DLL 的这两种方式，并因此，设置 ProviderRegKey，覆盖任何以前的设置。 更重要的是，它必须添加本身到 InstalledSccProviders 列表以便用户可以选择的源代码管理插件，以使用。  
  
> [!NOTE]
>  因为使用 HKEY_LOCAL_MACHINE 键时，只有一个源代码管理插件可以注册为默认的源代码管理插件给定计算机上 (但是， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，用户可以确定哪些源代码管理插件他们想要实际使用的特定解决方案)。 在安装过程中，检查以确定是否已设置源代码管理插件;如果是这样，，询问用户要设置新的源代码管理插件安装为默认值。 取消-在安装期间，不要删除共有的所有源控制插件在 HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider; 其他注册表子项删除仅你特定的 SCC 子项。  
  
## <a name="how-the-ide-detects-version-1213-support"></a>IDE 如何检测版本 1.2/1.3 支持  
 如何未 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 检测是否插件支持源控制插件 API 版本 1.2 和 1.3 功能？ 若要声明高级的功能，源代码管理插件必须实现相应的函数。  
  
 首先， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 检查通过调用返回的值 [SccGetVersion](../../extensibility/sccgetversion-function.md)。 它必须大于或等于 1.2。  
  
 接下来， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 确定是否将特定的新功能支持通过检查 `lpSccCaps` 参数 [SccInitialize](../../extensibility/sccinitialize-function.md)。  
  
 如果满足这两种情况，可以调用在版本 1.2 和 1.3 支持的新函数。  
  
## <a name="see-also"></a>请参阅  
 [入门](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)