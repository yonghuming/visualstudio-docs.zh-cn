---
title: "用户设置的的支持 | Microsoft Docs"
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
  - "自定义设置点"
  - "注册的持久性支持用户设置 [Visual Studio SDK]"
  - "持久性、 注册设置"
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
caps.latest.revision: 26
caps.handback.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
---
# 用户设置的的支持
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

VSPackage 可以定义一个或多个设置类别，是一组时用户选择持久保存的状态变量 **导入\/导出设置** 命令 **工具** 菜单。 若要启用此暂留，您使用设置 Api 中 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]。  
  
 自定义设置点和一个 GUID 称为一个注册表项定义的 VSPackage 设置类别。 VSPackage 可支持多个设置类别，每个定义的自定义设置点。  
  
-   实现基于互操作程序集的设置 \(使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> 接口\) 应通过编辑注册表，或者使用注册器脚本 （.rgs 文件） 创建自定义设置点。 有关更多信息，请参见[Creating Registrar Scripts](/visual-cpp/atl/creating-registrar-scripts)。  
  
-   使用管理包框架 \(MPF\) 的代码应通过将附加创建自定义设置点 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 到每个自定义设置点 VSPackage。  
  
     如果单个 VSPackage 支持自定义设置的多个点，由一个单独的类，实现自定义设置的每个点并通过一个唯一实例已注册的每个 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 类。 因此，实现类设置都可以支持多个设置类别。  
  
## 自定义设置点注册表项的详细信息  
 在以下位置的注册表条目中创建自定义设置点︰ HKLM\\Software\\Microsoft\\VisualStudio\\*\< 版本 \>*\\UserSettings\\`<CSPName>`, ，其中 `<CSPName>` 是 VSPackage 支持的点的自定义设置的名称和 *\< 版本 \>* 是版本 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ，例如 8.0。  
  
> [!NOTE]
>  HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\ 的根路径*\< 版本 \>* 可以将其覆盖备用根时 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 初始化集成的开发环境 \(IDE\)。 有关详细信息，请参阅[命令行开关](../../extensibility/command-line-switches-visual-studio-sdk.md)。  
  
 注册表条目的结构如下图所示︰  
  
 HKLM\\Software\\Microsoft\\VisualStudio\\*\< 版本 \>*\\UserSettings\\  
  
 `<CSPName`\> \= '\#12345' s  
  
 包 \= ' {XXXXXX XXXX XXXX XXXX XXXXXXXXX}  
  
 类别 \= ' {YYYYYY YYYY YYYY YYYY YYYYYYYYY}  
  
 ResourcePackage \= ' {ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}  
  
 AlternateParent \= CategoryName  
  
|名称|类型|数据|描述|  
|--------|--------|--------|--------|  
|\(默认\)|REG\_SZ|自定义设置点的名称|该项的名称， `<CSPName`\>，点的自定义设置的未本地化名称。<br /><br /> 对于基于 MPF 实现，该项的名称通过组合 `categoryName` 和 `objectName` 参数 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 到构造函数 `categoryName_objectName`。<br /><br /> 键可以是空的或者它可以包含一个附属 DLL 中的本地化字符串的引用的 ID。 此值从获取 `objectNameResourceID` 参数 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 构造函数。|  
|package|REG\_SZ|GUID|实现自定义设置点 VSPackage 的 GUID。<br /><br /> 实现基于 MPF 使用 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 类，请使用构造函数的 `objectType` 参数，其中包含 VSPackage <xref:System.Type> 和反射来获取此值。|  
|类别|REG\_SZ|GUID|标识类别设置 GUID。<br /><br /> 对于基于互操作程序集的实现，此值可以是任意选择的 GUID，其 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 将传递给 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> 方法。 这两种方法的所有实现应都验证其 GUID 参数。<br /><br /> 对于基于 MPF 实现，此 GUID 通过获取 <xref:System.Type> 类实现的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 设置机制。|  
|ResourcePackage|REG\_SZ|GUID|可选。<br /><br /> 如果实现 VSPackage 未提供这些，路径以附属 DLL 包含本地化字符串。<br /><br /> MPF 使用反射来获取正确的资源 VSPackage，因此 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 类不会设置此参数。|  
|AlternateParent|REG\_SZ|在工具选项页包含此自定义设置点文件夹的名称。|可选。<br /><br /> 您必须设置此值，仅当设置实现支持 **工具选项** 使用中的持久性机制的页面 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 而不是要保存状态的自动化模型中的机制。<br /><br /> 在这些情况下，AlternateParent 项中的值是 `topic` 部分 `topic.sub-topic` 用来确定特定字符串 **工具选项** 页。 例如，对于 **工具选项** 页 `"TextEditor.Basic"` AlternateParent 的值将为 `"TextEditor"`。<br /><br /> 当 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 生成点的自定义的设置，它是类别名称相同。|