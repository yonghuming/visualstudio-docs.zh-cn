---
title: "注册自定义选项页 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "注册, 自定义工具选项页"
  - "工具选项页 [Visual Studio SDK], 注册"
ms.assetid: 0ac6377d-a679-4f7d-be80-451c829b56f2
caps.latest.revision: 28
caps.handback.revision: 28
manager: "douge"
---
# 注册自定义选项页
对于支持 **工具选项** 的页可供用户使用和自动化，它必须相应地移动到 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 集成开发环境注册 \(IDE\)。  
  
 根据托管包结构的**工具选项** 页通过应用 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 实例注册于提供页的 VSPackage。  自动化支持由设置 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsAutomation%2A> 属性表示于 `true`。  
  
## 工具选项调用注册  
 与集成 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的自定义 **工具选项** 页在以下位置需要注册表项的创建:HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\*\<版本\>*\\ ToolsOptionsPages，其中 *\<版本\>* 是 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]的版本，如 8.0。  
  
 项具有类别 \(`<PageCategory>`\) 的主键 **工具选项** 页和包含页的子类别 \(`<PageSubCategory>`\) 的名称一个子元素。  
  
 例如， **工具选项** 页标识与字符串， **TextEditor.Basic**，具有 \=Basic `<PageSubCategory>`的子级的注册表项 `<PageCategory>`\=textEditor。  
  
 注册表项的结构如下:  
  
 HKLM \\ SOFTWARE \\ Microsoft \\ VisualStudio \\*\<版本\>*\\ \\ ToolsOptionsPages  
  
 `<PageCategory>` \= '\#12345'  
  
 包 \= “{}”  
  
 ResourcePackage \= “{YYYYYY YYYY YYYY YYYY YYYYYYYYY}”  
  
 HKLM \\ SOFTWARE \\ Microsoft \\ VisualStudio \\*\<版本\>*\\ ToolsOptionsPages \\`<PageCategory>`  
  
 `<PageSubCategory>>` \= '\#67890'  
  
 页 \= “{ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}”  
  
 包 \= “{AAAAAA、、、 AAAAAAAAA}”  
  
 ResourcePackage \= “{BBBBBB BBBB BBBB BBBB BBBBBBBBB}”  
  
 NoShowAllView \= 0\/1  
  
 下表列出了值在 HKLM \\ SOFTWARE \\ Microsoft \\ VisualStudio \\*\<版本\>*\\ ToolsOptionsPages \\`<PageCategory>`下。  
  
|名称|类型|数据|说明|  
|--------|--------|--------|--------|  
|（默认值）|REG\_SZ|自定义 **工具选项** 页的规范类名称|名称， `<PageCategory>`，是 **工具选项** 页的规范非本地化类别名称。 **Note:**  如果自动化支持，规范非本地化的类别和子类别名称用于获取 **工具选项** 页的 <xref:EnvDTE.Properties> 集合。  有关更多信息，请参见 [使用选项页](../misc/using-options-pages.md)。 <br /><br /> 对于基于托管包结构的实现， `<PageCategory`\> 从 `categoryName` 参数获取到 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 构造函数。<br /><br /> 这些项可以为 null，也可以包含引用 ID 为本地化的字符串在实现附属 DLL。<br /><br /> 对于基于托管包结构的实现，此值从 `categoryResourceID` 参数获取到 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 构造函数。|  
|Package|REG\_SZ|GUID|实现自定义 **工具选项** 页的 VSPackage 的 GUID。<br /><br /> 根据托管包结构的实现使用 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 使用反射获取此值。|  
|ResourcePackage|REG\_SZ|GUID|可选。<br /><br /> 包含本地化的字符串的附属 DLL，如果实现的 VSPackage 不提供它们。<br /><br /> 托管包框架使用反射获取正确的资源包，因此， <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 未设置此参数。|  
  
 下表列出了值在 HKLM \\ SOFTWARE \\ Microsoft \\ VisualStudio \\*\<版本\>*\\ ToolsOptionsPages \\`<PageCategory>`\\`<PageSubCategory>`下。  
  
|名称|类型|数据|说明|  
|--------|--------|--------|--------|  
|（默认值）|REG\_SZ|自定义 **工具选项** 页的规范子类别名称|名称， `<PageSubCategory`\>，是 **工具选项** 页子类别的规范非本地化名称。 **Note:**  如果自动化支持，规范非本地化的类别和子类别名称用于获取 **工具选项** 页的 <xref:EnvDTE.Properties> 集合。  有关更多信息，请参见 [使用选项页](../misc/using-options-pages.md)。 <br /><br /> 对于基于托管包结构的实现， `<PageSubegory`\> 从 `pageName` 参数获取到 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 构造函数。<br /><br /> 这些项可以为 null，也可以包含引用 ID 为本地化的字符串在实现附属 DLL。<br /><br /> 对于基于托管包结构的实现，此值从 `pageNameResourceID` 参数获取到 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 构造函数。|  
|页|REG\_SZ|GUID|实现自定义 **工具选项** 页的对象的 GUID。<br /><br /> 根据托管包结构的实现使用 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 使用包含 VSPackage 的 <xref:System.Type> 和镜像的构造函数的 `pageType` 参数获取此值。|  
|Package|REG\_SZ|GUID|根据托管包结构的实现使用 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 使用反射获取此值。|  
|ResourcePackage|REG\_SZ|GUID|可选。<br /><br /> 包含本地化的字符串的附属 DLL，如果实现的 VSPackage 不提供它们。<br /><br /> 托管包框架使用反射获取正确的资源 DLL，因此， <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 未设置此参数。|  
|NoShowAllView|REG\_DWORD|0 或 1|可选。<br /><br /> 指示特定 **工具选项** 页是否应显示在 **工具选项** 页复杂 \(默认视图\)。  支持程序环境 \(例如， Visual Basic 中，具有复合特定 **工具选项** 的页常见设置为用户提供选项专用的简化视图。<br /><br /> 如果 REG\_DWORD 项不为零， **工具选项** 页未出现在一个复杂的视图。<br /><br /> 有关更多信息，请参见 [“选项”对话框](../ide/reference/options-dialog-box-visual-studio.md)。<br /><br /> 根据托管包结构的实现可以通过设置 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.NoShowAllView%2A> 属性将此值分配给 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 构造函数的 `true` 。|  
  
 基于一个互操作程序集或对象的 VSPackage 可以实现多个 **工具选项** 页。  每个实现要求在 HKLM \\ SOFTWARE \\ Microsoft \\ VisualStudio \\*\<版本\>*\\ ToolsOptionsPages 的新项。  
  
 当托管包结构实例化提供 **工具选项** 页的对象，每页应具有自己的实现对象，独立于 <xref:Microsoft.VisualStudio.Shell.Package>的 VSPackage 的实现。  
  
## 自动化支持  
 如果自动化支持使用实现 **工具选项** 页，因此它必须注册为自动化提供程序。  为属性控制若要使用自动化并使用其保持机制保存 **工具选项** 页状态，它必须注册为 `AutomationProperty` 提供程序。  
  
### 注册 VSPackage 作为自动化提供程序 \(仅适用于工具根据互操作程序集的选项卡页\)  
 作为 VSPackage 中实现类的一部分，根据互操作程序集的**工具选项** 页中实现。  
  
 在这种情况下，因此，如果 **工具选项** 页是支持自动化，必须注册互操作基于程序集的 VSPackage 作为自动化提供程序。  
  
> [!NOTE]
>  自动在托管包框架支持 VSPackage 中实现的对象独立提供。  如果该对象支持自动化，这通过 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 构造函数的 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsAutomation%2A> 属性注册。  
  
 注册的 VSPackage 项作为自动化提供程序是窗体 HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\*\<版本\>*\\ packages \\ \\*\<PackageGUID\>*自动化，其中 *\<版本\>* 是 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的版本 \(如 8.0\)，并 *\<PackageGUID\>* 是实现自动化对象的 VSPackage 的 GUID。  
  
> [!NOTE]
>  ，当 Visual Studio shell 初始化时， HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\*\<版本\>* 根路径可以重写与替换根。  有关更多信息，请参见 [命令行开关](../extensibility/command-line-switches-visual-studio-sdk.md)。  
  
 注册表项机制是:  
  
 HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\*\<版本\>*\\ packages \\ \\*\<PackageGUID\>*自动化  
  
 `<AutomationObjectName>`  
  
|名称|类型|数据|说明|  
|--------|--------|--------|--------|  
|自动化|REG\_SZ|未定义|未定义。<br /><br /> 此密钥将出现一 *\<PackageGUID\>* 引用的 VSPackage 支持自动化。<br /><br /> 该字段来存储文档。<br /><br /> <xref:Microsoft.VisualStudio.Shell.ProvideAutomationObjectAttribute> 自动创建基于托管包 framework 的应用程序的此密钥。|  
|`<AutomationObjectName>`|REG\_SZ|提供的自动化对象的规范名称|仅名称是相关的。  用于自动执行操作。<br /><br /> 该字段来存储文档。<br /><br /> 对于基于托管包结构的实现，此键的名称取决于 <xref:Microsoft.VisualStudio.Shell.ProvideAutomationObjectAttribute> 构造函数的 `name` 参数。<br /><br /> 如果 <xref:Microsoft.VisualStudio.Shell.ProvideAutomationObjectAttribute> 构造函数具有有效的字符串提供给其 <xref:Microsoft.VisualStudio.Shell.ProvideAutomationObjectAttribute.Description%2A> 属性，请插入此值示。|  
  
### 注册工具选项称为为支持自动化  
 **工具选项** 页的托管包结构和基于互操作程序集的实现必须允许访问 **工具选项** 页的自动化访问的注册。  这是通过 <xref:EnvDTE>包括自动化属性保持机制以及对页。  这是 VSPackage 中注册的独立作为自动化服务提供程序。  
  
 与上面提到的 **工具选项** 页面注册，项具有类别 \(`<PageCategory>`\) 的主键 **工具选项** 页和包含页的子类别 \(`<PageSubcategory>`\) 的名称一个子元素。  
  
 如果使用管理的包结构，请使用 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 注册类作为提供 **工具选项** 页并设置 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsAutomation%2A> 属性设置为 `true` 指示页支持自动化。  
  
 在注册表项 HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\*\<版本\>*\\ AutomationProperties 找到资源，其中 *\<版本\>* 是 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]的版本，如 8.0。  
  
> [!NOTE]
>  HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\*\<版本\>* 根路径可以重写与替换根，当 Visual Studio shell 初始化时，，以便更多信息，请参见 [命令行开关](../extensibility/command-line-switches-visual-studio-sdk.md)。  
  
 注册表项的结构如下:  
  
 HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\*\<版本\>\\*AutomationProperties  
  
 `<PageCategory>` \= ‘\#456’  
  
 ResourcePackage \= “{}”  
  
 `<PageSubCategory>` \= ‘\#789’  
  
 包 \= “{YYYYYY YYYY YYYY YYYY YYYYYYYYY}”  
  
 名称 \= “`<PageCategory>` 。`<PageSubcategory>`”  
  
 “ProfileSave \= 1\/0  
  
 下表列出了值在 HKEY\_LOCAL\_MACHINE \\ software \\ Microsoft \\ VisualStudio \\*\<版本\>*\\ AutomationProperties \\`<PageCategory>`下。  
  
|名称|类型|数据|说明|  
|--------|--------|--------|--------|  
|（默认值）|REG\_SZ|自定义 **工具选项** 页的规范类名称|名称， `<PageCategory`\>，是 **工具选项** 页类别的规范非本地化名称。 **Note:**  如果自动化支持，规范非本地化的类别和子类别名称用于获取 **工具选项** 页的 <xref:EnvDTE.Properties> 集合。  有关更多信息，请参见 [使用选项页](../misc/using-options-pages.md)。 <br /><br /> 这些项可以为 null，也可以包含引用 ID 为本地化的字符串在实现附属 DLL。<br /><br /> 对于基于托管包结构的实现， `<PageCategory`\> 从 `categoryName` 参数获取到 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 构造函数。|  
|ResourcePackage|REG\_SZ|GUID|可选。<br /><br /> 包含本地化的字符串的附属 DLL，如果实现的 VSPackage 不提供它们。<br /><br /> 托管包框架使用反射获取正确的资源 VSPackage，因此， <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 未设置此参数。|  
  
 下表列出了值在 HKEY\_LOCAL\_MACHINE \\ software \\ Microsoft \\ VisualStudio \\*\<版本\>*\\ AutomationProperties \\`<PageCategory>\<PageSubCategory>`下。  
  
|名称|类型|数据|说明|  
|--------|--------|--------|--------|  
|（默认值）|REG\_SZ|自定义 **工具选项** 页的子类别名称|名称， `<PageSubCategory`\>，是 **工具选项** 页子类别的规范非本地化名称。 **Note:**  如果自动化支持，规范非本地化的类别和子类别名称用于获取 **工具选项** 页的 <xref:EnvDTE.Properties> 集合。  有关更多信息，请参见 [使用选项页](../misc/using-options-pages.md)。 <br /><br /> 这些项可以为 null，也可以包含引用 ID 为本地化的字符串在实现附属 DLL。<br /><br /> 对于基于托管包结构的实现， `<PageSubCategory>` 从 `pageName` 参数获取到 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 构造函数。|  
|Package|REG\_SZ|GUID|实现自定义 **工具选项** 页的 VSPackage 的 GUID。<br /><br /> 根据托管包结构的实现使用 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 使用反射获取此值。|  
|名称|REG\_SZ|**工具选项** 页属性集合的名称|用于的 `<PageCategory>.<PageSubCategory>` 字符串引用 **工具选项** 页。  有关更多信息，请参见 [使用选项页](../misc/using-options-pages.md)。<br /><br /> 对于基于托管包结构的实现，该名称与参数获取到 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 构造函数并为窗体 `categoryName.pageName`。|  
|ProfileSave|DWORD|1\/0|可选。<br /><br /> 此值指示 **工具选项** 页导航是否由 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 设置结构保存，当用户在 **工具** 菜单中单击 **导入\/导出设置** 命令。<br /><br /> 如果该项存在，并且其值为 1，则 **工具选项** 页请求设置的支持。<br /><br /> ，如果 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 构造函数集所提供 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> 属性。 `true`，根据托管包结构的实现将此值设置为。|  
  
## 请参阅  
 [Creating Registrar Scripts](/visual-cpp/atl/creating-registrar-scripts)   
 [使用选项页](../misc/using-options-pages.md)   
 [使用互操作程序集创建选项页](/visual-cpp/misc/creating-options-pages-by-using-interop-assemblies)   
 [如何：创建自定义选项页](../Topic/How%20to:%20Create%20Custom%20Options%20Pages.md)   
 [选项页](../misc/options-pages.md)   
 [选项页的自动化支持](../extensibility/internals/automation-support-for-options-pages.md)