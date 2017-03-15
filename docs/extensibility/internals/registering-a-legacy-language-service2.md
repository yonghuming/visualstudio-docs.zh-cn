---
title: "注册旧语言 Service2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "注册语言服务"
  - "语言服务，注册表信息"
  - "注册表中，语言服务"
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# 注册早期语言服务
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

以下各节提供的列表的注册表项的各种语言中可用的服务选项 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 下面的注册表项的列表中 *VS Reg 根* 等于 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*X.Y*, ，其中 *X.Y* 是 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 版本号。  
  
## 语言服务选项的注册表项  
 *VS Reg 根*\\Languages\\Language Services\\*语言名称* 键可包含以下值。  
  
|名称|类型|范围|描述|  
|--------|--------|--------|--------|  
|\(默认\)|REG\_SZ|*\< GUID \>*|语言服务的 GUID。|  
|LangResID|REG\_DWORD|0x0 0xffff|资源标识符 \(ResID\) 的语言的本地化的文本名称的字符串。|  
|package|REG\_SZ|*\< GUID \>*|VSPackage 的 GUID。|  
|ShowCompletion|REG\_DWORD|0\-1|指定是否 **语句完成** 中选项 **选项** 对话框中启用。|  
|ShowSmartIndent|REG\_DWORD|0\-1|指定是否可以选择 **智能** 中缩进 **选项** 对话框框处于启用状态。|  
|RequestStockColors|REG\_DWORD|0\-1|指定是否自定义或默认颜色用于颜色关键字。|  
|ShowHotURLs|REG\_DWORD|0\-1|指定用户是否可以通过单击 Url。|  
|默认为非热 Url|REG\_DWORD|0\-1|指定的初始设置 **启用单击 URL 定位** 选项 **选项** 对话框。|  
|DefaultToInsertSpaces|REG\_DWORD|0\-1|指定语言服务是否具有为其默认选项卡上选项的"插入空格"。|  
|ShowDropdownBarOption|REG\_DWORD|0\-1|启用或禁用 **ǖ 凝  ** 选项 **选项** 对话框中，显示或隐藏 **ǖ 凝  **。|  
|仅适用于单个代码窗口|REG\_DWORD|0\-1|启用或禁用 **新窗口** choice 中 **窗口** 语言服务的菜单。|  
|EnableAdvancedMembersOption|REG\_DWORD|0\-1|启用或禁用 **选项** 对话框设置为 **隐藏高级成员**。|  
|支持 CF\_HTML|REG\_DWORD|0\-1|指定使用编辑器，复制和粘贴的 HTML 数据。|  
|EnableLineNumbersOption|REG\_DWORD|0\-1|指定是否 **行号** 中选项 **选项** 对话框中启用的语言服务。|  
|HideAdvancedMembersByDefault|REG\_DWORD|0\-1|指定是否在完成列表中隐藏高级的成员，如私有字段。|  
|ShowBraceCompletion|REG\_DWORD|0\-1|指定是否 **大括号完成** 选项 **选项** 对话框框处于启用状态。|  
  
### 示例  
  
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
  
## 调试器语言选项的注册表项  
 *VS Reg 根*\\Languages\\Language Services\\*语言名称*\\Debugger Languages\\*GUID*\\ 密钥可以包括以下值。  
  
|名称|类型|范围|描述|  
|--------|--------|--------|--------|  
|\(默认\)|REG\_SZ|文本|默认值可以用于文档的语言名称。 此密钥的名称是在中有相应条目的表达式计算器的 GUID *\< VS Reg 根 \>*\\AD7Metrics\\Expression 计算器。|  
  
### 示例  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      C/C++\  
        Debugger Languages\  
          {3A12D0B7-C26C-11D0-B442-00A0244A1DD2}\  
            (Default) = reg_sz:C++  
```  
  
## 编辑器工具选项的注册表项  
 您可以添加 EditorToolsOptions 项下的注册表项是在属性页和属性节点。 这些注册表项和它们的值标识中的属性页 **选项** 对话框中 \(在 **工具** 菜单\)，用于配置的语言服务。 在下面的示例中， *页名称* 属性页中，名称和 *节点名称* 树中节点的名称位于 **选项** 对话框。 必须单独指定页面条目和节点的条目。  
  
|名称|类型|范围|描述|  
|--------|--------|--------|--------|  
|\(默认\)|REG\_SZ|ResID|此选项页的本地化的显示名称。 名称可以是文字文本或 \#`nnn`, ，其中 `nnn` 是附属 DLL 指定 VSPackage 中的字符串资源 ID。|  
|package|REG\_SZ|*GUID*|实现该选项页的 VSPackage 的 GUID。|  
|页|REG\_SZ|*GUID*|属性页上的 GUID，通过调用从 VSPackage 请求 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> 方法。 如果此注册表项不存在，注册表项描述一个节点上，不是一个页面。|  
  
### 示例  
  
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
  
## 文件名扩展选项的注册表项  
 文件扩展名的条目应包括前导句点，例如".myext"。  
  
|名称|类型|范围|描述|  
|--------|--------|--------|--------|  
|\(默认\)|REG\_SZ|*GUID*|此文件名称扩展类型的默认语言服务的服务 GUID。|  
  
### 示例  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    File Extensions\  
      .cpp\  
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
```  
  
## 编辑器选项的注册表项  
 *VS Reg 根*\\Editors 键可包含以下值︰  
  
|名称|类型|范围|描述|  
|--------|--------|--------|--------|  
|\(默认\)|REG\_SZ|""|未使用;您可将您的姓名的文档。|  
|DefaultToolboxTab|REG\_SZ|""|工具箱选项卡上，可以在编辑器处于活动状态时使用默认的名称。|  
|DisplayName|REG\_SZ|ResID|要显示名称在 **打开** 对话框。 名称是以标准格式字符串资源 ID 或名称。|  
|ExcludeDefTextEditor|REG\_DWORD|0\-1|用于 **打开** 菜单命令。 如果您不想要列出的可用编辑器的特定文件类型列表中的默认文本编辑器，请将此值设置为 1。|  
|LinkedEditorGUID|REG\_SZ|*\< GUID \>*|用于任何可以使用代码页支持打开文件的语言服务。 例如，当您打开一个.txt 文件，通过使用 **打开** 命令，而无需编码与使用源代码编辑器提供了选项。<br /><br /> 该子项的名称指定的 GUID 进行代码页编辑器工厂;在此特定的注册表项中指定的链接的 GUID 适用于正则编辑器工厂。 此项的目的是，如果 IDE 不会使用默认编辑器中打开一个文件，IDE 将尝试使用列表中的下一步的编辑器。 此下一步编辑器不应为代码页编辑器工厂，因为此编辑器工厂基本上是相同的编辑器工厂的失败。|  
|package|REG\_SZ|*\< GUID \>*|显示名称 ResID 的 VSPackage GUID。|  
  
### 示例  
  
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
  
## 逻辑视图选项的注册表项  
 *VS Reg 根*\\Editors\\*编辑器 GUI \>*\\LogicalViews 键可包含以下值。  
  
|名称|类型|范围|描述|  
|--------|--------|--------|--------|  
|\(默认\)|REG\_SZ||未使用。|  
|*\< GUID \>*|REG\_SZ|""|支持的逻辑视图的键。 您可以根据需要可以拥有任意数量的这些。 注册表项的名称是什么是重要的是，没有值，该值始终为空字符串。|  
  
### 示例  
  
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
  
## 编辑器扩展选项的注册表项  
 *VS Reg 根*\\Editors\\*编辑器 GUID*\\Extensions 键可包含以下值。 文件扩展名不包括前导句点。  
  
|名称|类型|范围|描述|  
|--------|--------|--------|--------|  
|\(默认\)|REG\_SZ||未使用。|  
|*\< 扩展 \>*|REG\_DWORD|0 0xffffffff|扩展的相对优先级。 如果两个或多个语言共享相同的扩展名，则选择优先级较高的语言。|  
  
 此外，当前用户的默认编辑器选择存储在 HKEY\_Current\_User\\Software\\Microsoft\\VisualStudio\\*X.Y*\\Default Editors\\*ext*。 所选的语言服务的 GUID 是在自定义项中。 这将为当前用户的优先。  
  
### 示例  
  
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
  
## 托管的包框架语言服务选项的注册表项  
 以下注册表项是特定于托管的包框架 \(MPF\) 语言服务类。 这些注册表条目指示各种智能感知功能和其他高级编辑功能的语言服务中的支持。  
  
 这些注册表项可通过访问 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 类。  
  
|名称|类型|范围|描述|  
|--------|--------|--------|--------|  
|CodeSense|REG\_DWORD|0\-1|支持智能感知操作。|  
|MatchBraces|REG\_DWORD|0\-1|对匹配的语言对如大括号、 圆括号和方括号的支持。|  
|QuickInfo|REG\_DWORD|0\-1|支持的 IntelliSense 快速信息操作。|  
|ShowMatchingBrace|REG\_DWORD|0\-1|在状态栏中显示匹配的语言对的支持。|  
|MatchBracesAtCaret|REG\_DWORD|0\-1|显示匹配的语言对，通常是通过突出显示的两个元素的支持。|  
|MaxErrorMessages|REG\_DWORD|0\-n|最大可以中显示的错误数 **错误列表** 窗口。|  
|CodeSenseDelay|REG\_DWORD|0\-n|要启动分析智能感知操作任何背景前的延迟的毫秒数。|  
|EnableAsyncCompletion|REG\_DWORD|0\-1|背景分析支持。|  
|EnableCommenting|REG\_DWORD|0\-1|对注释掉选定的文本块的支持，并且还暗示支持取消注释所选的文本。|  
|EnableFormatSelection|REG\_DWORD|0\-1|支持格式文本，如自动缩进或调整大括号的位置。|  
|AutoOutlining|REG\_DWORD|0\-1|以大纲方式显示 （可折叠的区域） 的支持。|  
|MaxRegions|REG\_DWORD|0\-n|每个文件的隐藏区域最大数量。|  
  
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
  
## 请参阅  
 [开发语言服务](../../extensibility/internals/developing-a-legacy-language-service.md)