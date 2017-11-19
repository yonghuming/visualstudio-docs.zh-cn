---
title: "注册旧语言 Service2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f64b02521fcea9abef9d7196a27e4a209100a892
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="registering-a-legacy-language-service"></a>注册旧语言服务
以下部分提供的注册表项列表的各种语言中可用的服务选项[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 以下列表的注册表项中*VS Reg 根*等于 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y*，其中*X.Y*是[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]版本号。  
  
## <a name="registry-entries-for-language-service-options"></a>语言服务选项的注册表项  
 *VS Reg 根*\Languages\Language 服务\\*语言名称*键可包含以下值。  
  
|名称|类型|范围|描述|  
|----------|----------|-----------|-----------------|  
|(默认)|REG_SZ|*\<GUID >*|语言服务的 GUID。|  
|LangResID|REG_DWORD|0x0 0xffff|字符串的语言的本地化的文本名称的资源标识符 (ResID)。|  
|Package|REG_SZ|*\<GUID >*|VSPackage 的 GUID。|  
|ShowCompletion|REG_DWORD|0-1|指定是否**语句结束**中的选项**选项**对话框中启用。|  
|ShowSmartIndent|REG_DWORD|0-1|指定是否可以选择**智能**中缩进**选项**对话框框处于启用状态。|  
|RequestStockColors|REG_DWORD|0-1|指定是否自定义或默认颜色用于颜色关键字。|  
|ShowHotURLs|REG_DWORD|0-1|指定用户是否可以单击 Url。|  
|默认为非热 Url|REG_DWORD|0-1|指定的初始设置**启用单击 URL 定位**选项**选项**对话框。|  
|DefaultToInsertSpaces|REG_DWORD|0-1|指定语言服务是否具有为其默认选项卡上选项的"插入空格"。|  
|ShowDropdownBarOption|REG_DWORD|0-1|启用或禁用**导航栏**选项**选项**对话框中，显示或隐藏**导航栏**。|  
|仅适用于单个代码窗口|REG_DWORD|0-1|启用或禁用**新窗口**choice 中**窗口**语言服务的菜单。|  
|EnableAdvancedMembersOption|REG_DWORD|0-1|启用或禁用**选项**对话框框中的设置**隐藏高级成员**。|  
|支持 CF_HTML|REG_DWORD|0-1|指定使用编辑器，复制和粘贴的 HTML 数据。|  
|EnableLineNumbersOption|REG_DWORD|0-1|指定是否**行号**中的选项**选项**对话框中启用语言服务。|  
|HideAdvancedMembersByDefault|REG_DWORD|0-1|指定是否在完成列表中隐藏高级的成员如私有字段。|  
|ShowBraceCompletion|REG_DWORD|0-1|指定是否**大括号完成**选项**选项**对话框框处于启用状态。|  
  
### <a name="example"></a>示例  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      C/C++\  
        (Default)             = reg_sz:{B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
        LangResID             = reg_dword:0x00000000  
        Package               = reg_sz:{8C2EA640-ABC1-11D0-9D62-00C04FD9DFD9}  
        ShowCompletion        = reg_dword:0x00000001  
        ShowSmartIndent       = reg_dword:0x00000001  
        ShowDropdownBarOption = reg_dword:0x00000001  
```  
  
## <a name="registry-entries-for-debugger-languages-options"></a>调试器语言选项的注册表项  
 *VS Reg 根*\Languages\Language 服务\\*语言名称*\Debugger 语言\\*GUID*\ 密钥可以包括以下值。  
  
|名称|类型|范围|描述|  
|----------|----------|-----------|-----------------|  
|(默认)|REG_SZ|文本|默认值可以用于文档的语言的名称。 此键的名称是在中有相应条目的表达式计算器的 GUID  *\<VS Reg 根 >*\AD7Metrics\Expression 计算器。|  
  
### <a name="example"></a>示例  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      C/C++\  
        Debugger Languages\  
          {3A12D0B7-C26C-11D0-B442-00A0244A1DD2}\  
            (Default) = reg_sz:C++  
```  
  
## <a name="registry-entries-for-editor-tools-options"></a>编辑器工具选项的注册表项  
 你可以添加 EditorToolsOptions 项下的属性页和属性节点的注册表项。 这些密钥和它们的值标识中的属性页**选项**对话框 (上**工具**菜单)，用于配置语言服务。 在下面的示例中，*页名称*是属性页中，名称和*节点名称*是树中节点的名称上**选项**对话框。 必须单独指定页面条目和节点条目。  
  
|名称|类型|范围|描述|  
|----------|----------|-----------|-----------------|  
|(默认)|REG_SZ|ResID|此选项页的本地化的显示名称。 名称可以是文本或 #`nnn`，其中`nnn`附属 DLL 的指定 VSPackage 中的字符串资源 id。|  
|Package|REG_SZ|*GUID*|实现该选项页的 VSPackage 的 GUID。|  
|页|REG_SZ|*GUID*|在属性页的 GUID，通过调用从 VSPackage 请求<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>方法。 如果此注册表项不存在，注册表项将描述一个节点，而不是页面。|  
  
### <a name="example"></a>示例  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      CSharp\  
        EditorToolsOptions\  
          Formatting\  
            (Default) = reg_sz:#242  
            Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
            General\  
              (Default) = reg_sz:#255  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{3EB2CC0B-033E-4D75-B26A-B2362C25227E}  
            Indentation\  
              (Default) = reg_sz:#250  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{5E21D017-6D2A-4114-A1F1-C923F001CBBB}  
            Newlines\  
              (Default) = reg_sz:#253  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{607D8062-68D1-41E4-9A35-B5E7F14D0481}  
```  
  
## <a name="registry-entries-for-file-name-extension-options"></a>文件名称扩展选项的注册表项  
 文件扩展名的条目应包含前导句点，例如".myext"。  
  
|名称|类型|范围|描述|  
|----------|----------|-----------|-----------------|  
|(默认)|REG_SZ|*GUID*|此文件名称扩展类型的默认语言服务的服务 GUID。|  
  
### <a name="example"></a>示例  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    File Extensions\  
      .cpp\  
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
```  
  
## <a name="registry-entries-for-editor-options"></a>编辑器选项的注册表项  
 *VS Reg 根*\Editors 键可包含以下值：  
  
|名称|类型|范围|描述|  
|----------|----------|-----------|-----------------|  
|(默认)|REG_SZ|""|未使用;你可以输入您的姓名此处的文档。|  
|DefaultToolboxTab|REG_SZ|""|工具箱选项卡，可以在编辑器处于活动状态时使用默认名称。|  
|DisplayName|REG_SZ|ResID|要显示名称在**打开**对话框。 名称为采用标准格式字符串资源 ID 或名称。|  
|ExcludeDefTextEditor|REG_DWORD|0-1|用于**打开**菜单命令。 如果您不想要列出的可用编辑器的特定文件类型列表中的默认文本编辑器，请将此值设置为 1。|  
|LinkedEditorGUID|REG_SZ|*\<GUID >*|用于代码页支持可以打开的文件的任何语言服务。 例如，当你打开.txt 文件使用**打开**命令时，选项提供用于使用源代码编辑器和无需编码。<br /><br /> 子项的名称指定的 GUID 是代码页编辑器工厂;在此特定的注册表项中指定的链接的 GUID 是正则编辑器工厂。 此项的目的是，如果 IDE 未使用的默认编辑器打开文件，IDE 将尝试使用列表中的下一步的编辑器。 此下一步编辑器不应为代码页编辑器工厂，因为此编辑器工厂基本上是失败的编辑器工厂相同。|  
|Package|REG_SZ|*\<GUID >*|显示名称 ResID 的 VSPackage GUID。|  
  
### <a name="example"></a>示例  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      (Default)            = reg_sz:Html Editor with Encoding  
      DefaultToolboxTab    = reg_sz:HTML  
      DisplayName          = reg_sz:#20101  
      LinkedEditorGUID     = reg_sz:{C76D83F8-A489-11D0-8195-00A0C91BBEE3}  
      Package              = reg_sz:{1B437D20-F8FE-11D2-A6AE-00104BCC7269}  
```  
  
## <a name="registry-entries-for-logical-view-options"></a>逻辑视图选项的注册表项  
 *VS Reg 根*\Editors\\*编辑器 GUI >*\LogicalViews 键可包含以下值。  
  
|名称|类型|范围|描述|  
|----------|----------|-----------|-----------------|  
|(默认)|REG_SZ||未使用。|  
|*\<GUID >*|REG_SZ|""|支持的逻辑视图键。 根据需要你可以拥有与许多种。 注册表条目的名称是什么是重要的是，不值，该值始终为空字符串。|  
  
### <a name="example"></a>示例  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      LogicalViews\  
       (Default) = reg_sz:  
       {7651a700-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a701-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a702-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a703-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
```  
  
## <a name="registry-entries-for-editor-extension-options"></a>编辑器扩展选项的注册表项  
 *VS Reg 根*\Editors\\*编辑器 GUID*\Extensions 键可包含以下值。 文件扩展名不包括前导句点。  
  
|名称|类型|范围|描述|  
|----------|----------|-----------|-----------------|  
|(默认)|REG_SZ||未使用。|  
|*\<ext >*|REG_DWORD|0 0xffffffff|扩展的相对优先级。 如果两个或多个语言共享相同的扩展名，则选择优先级较高的语言。|  
  
 此外，当前用户的默认编辑器选择存储在 HKEY_Current_User\Software\Microsoft\VisualStudio\\*X.Y*\Default 编辑器\\*ext*。所选的语言服务的 GUID 是自定义项中。 此方法将为当前用户的优先。  
  
### <a name="example"></a>示例  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      Extensions\  
       (Default) = reg_sz:  
       *         = reg_dword:0x00000018  
       html      = reg_dword:0x00000027  
       shtm      = reg_dword:0x00000027  
       shtml     = reg_dword:0x00000027  
```  
  
## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>托管的包框架语言服务选项的注册表项  
 下面的注册表条目是特定于托管的包框架 (MPF) 语言服务类。 这些注册表项指示中语言服务为各种 IntelliSense 功能和其他高级编辑功能的支持。  
  
 通过访问这些注册表项<xref:Microsoft.VisualStudio.Package.LanguagePreferences>类。  
  
|名称|类型|范围|描述|  
|----------|----------|-----------|-----------------|  
|CodeSense|REG_DWORD|0-1|支持的智能感知操作。|  
|MatchBraces|REG_DWORD|0-1|匹配语言对，如大括号、 圆括号和方括号的支持。|  
|QuickInfo|REG_DWORD|0-1|支持的 IntelliSense 快速信息操作。|  
|ShowMatchingBrace|REG_DWORD|0-1|支持在状态栏中显示匹配的语言对。|  
|MatchBracesAtCaret|REG_DWORD|0-1|支持显示匹配的语言对，通常通过突出显示的两个元素。|  
|MaxErrorMessages|REG_DWORD|0-n|可以在显示的错误的最大数**错误列表**窗口。|  
|CodeSenseDelay|REG_DWORD|0-n|若要在启动分析 IntelliSense 操作任何后台之前延迟的毫秒数。|  
|EnableAsyncCompletion|REG_DWORD|0-1|支持的背景分析。|  
|EnableCommenting|REG_DWORD|0-1|支持注释掉选定时间段的文本，并且还意味着对 uncommenting 所选文本的支持。|  
|EnableFormatSelection|REG_DWORD|0-1|支持格式如自动缩进的文本或调整大括号的位置。|  
|AutoOutlining|REG_DWORD|0-1|以大纲方式显示 （可以折叠的区域） 的支持。|  
|MaxRegions|REG_DWORD|0-n|每个文件的隐藏区域中最大的数。|  
  
```  
ExampleHKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      XML\  
        (Default)             = reg_sz:{f6819a78-a205-47b5-be1c-675b3c7f0b8e}  
        MatchBraces           = reg_dword:0x00000001  
        QuickInfo             = reg_dword:0x00000001  
        ShowMatchingBrace     = reg_dword:0x00000001  
        MatchBracesAtCaret    = reg_dword:0x00000000  
        MaxErrorMessages      = reg_dword:0x00000064  
        CodeSenseDelay        = reg_dword:0x000001f4  
        MaxRegions            = reg_dword:0x0000000a  
```  
  
## <a name="see-also"></a>另请参阅  
 [开发旧版语言服务](../../extensibility/internals/developing-a-legacy-language-service.md)