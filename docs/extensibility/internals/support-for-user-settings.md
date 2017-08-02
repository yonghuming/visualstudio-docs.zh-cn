---
title: "对用户设置的支持 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
caps.latest.revision: 26
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 24bd28ad78f1cd3a21167215ed8348dc79edce6b
ms.contentlocale: zh-cn
ms.lasthandoff: 04/05/2017

---
# <a name="support-for-user-settings"></a>对用户设置的支持
VSPackage 可以定义一个或多个设置类别，是一组时用户选择持久保存的状态变量**导入/导出设置**命令**工具**菜单。 若要启用此暂留，你使用设置 Api 中[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]。  
  
 自定义设置点和一个 GUID 称为的注册表项定义 VSPackage 的设置类别。 VSPackage 可以支持多个设置类别，每个由自定义设置点定义。  
  
-   实现基于互操作程序集的设置 (使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings>接口) 应通过编辑注册表，或者使用注册器脚本 (.rgs file) 创建自定义设置点。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> 有关详细信息，请参阅[创建注册器脚本](/cpp/atl/creating-registrar-scripts)。  
  
-   使用托管包框架 (MPF) 的代码应通过将附加创建自定义设置点<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>到每个自定义设置点 VSPackage。</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>  
  
     如果单个 VSPackage 支持多个自定义设置点，由一个单独的类，实现每个自定义设置点和每个注册的唯一的实例的<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>类。</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 因此，实现类设置可以支持多个设置类别。  
  
## <a name="custom-settings-point-registry-entry-details"></a>自定义设置点注册表项的详细信息  
 在以下位置的注册表条目中创建自定义设置点︰ HKLM\Software\Microsoft\VisualStudio\\*\<版本 1>*\UserSettings\\`<CSPName>`，其中`<CSPName>`是 VSPackage 支持的自定义设置点的名称和*\<版本 1>*是版本的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，例如 8.0。  
  
> [!NOTE]
>  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio 的根路径\\*\<版本 1>*可以替换备用根时[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]初始化集成的开发环境 (IDE)。 有关详细信息，请参阅[命令行开关](../../extensibility/command-line-switches-visual-studio-sdk.md)。  
  
 注册表项的结构如下所示︰  
  
 HKLM\Software\Microsoft\VisualStudio\\*\<版本 1>*\UserSettings\  
  
 `<CSPName`1> = '#12345' s  
  
 包 = {XXXXXX XXXX XXXX XXXX XXXXXXXXX}  
  
 类别 = {YYYYYY YYYY YYYY YYYY YYYYYYYYY}  
  
 ResourcePackage = {ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}  
  
 AlternateParent = CategoryName  
  
|名称|类型|数据|说明|  
|----------|----------|----------|-----------------|  
|(默认)|REG_SZ|自定义设置点的名称|该项的名称， `<CSPName`1>，是自定义设置点的未本地化的名称。<br /><br /> 对于基于 MPF 实现，该项的名称获取通过组合`categoryName`和`objectName`的自变量<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>到构造函数`categoryName_objectName`。</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute><br /><br /> 键可以是空的也可以包含到附属 DLL 中的本地化字符串的引用 ID。 此值从获取`objectNameResourceID`参数<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>构造函数。</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>|  
|包|REG_SZ|GUID|实现自定义设置点的 VSPackage 的 GUID。<br /><br /> 实现基于 MPF 使用<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>类，而使用构造函数的`objectType`包含 VSPackage 的自变量<xref:System.Type>和反射获取此值。</xref:System.Type> </xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>|  
|类别|REG_SZ|GUID|标识设置类别的 GUID。<br /><br /> 对于基于互操作程序集的实现，此值可为任意选 GUID，这[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 将传递给<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A>方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> 这两种方法的所有实现应都验证其 GUID 参数。<br /><br /> 对于基于 MPF 实现，此 GUID 通过获取<xref:System.Type>的类实现[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]设置机制。</xref:System.Type>|  
|ResourcePackage|REG_SZ|GUID|可选。<br /><br /> 如果实现 VSPackage 未提供它们的路径以附属 DLL 包含本地化字符串。<br /><br /> MPF 使用反射来获取正确的资源 VSPackage，因此<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>类未设置此自变量。</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>|  
|AlternateParent|REG_SZ|在工具选项页包含此自定义设置点文件夹的名称。|可选。<br /><br /> 您必须设置此值，仅当设置实现支持**工具选项**使用中的持久性机制的页[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]而不是中自动化模型来保存状态的机制。<br /><br /> 在这些情况下，AlternateParent 密钥中的值是`topic`部分`topic.sub-topic`字符串用于标识特定**ToolsOptions**页。 例如，对于**ToolsOptions**页`"TextEditor.Basic"`AlternateParent 的值将会`"TextEditor"`。<br /><br /> 当<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>生成自定义设置点，它是类别名称相同。</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>|
