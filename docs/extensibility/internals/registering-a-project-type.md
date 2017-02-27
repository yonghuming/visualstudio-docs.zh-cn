---
title: "注册一种项目类型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "项目 [Visual Studio SDK]，新项目的注册表项"
  - "注册表中，新的项目类型"
  - "注册时，新的项目类型"
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# 注册一种项目类型
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在创建新的项目类型时，您必须创建使 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 标识以及与项目类型一起使用的注册表项。  使用注册表脚本 \(.rgs\) 文件，通常需要创建这些注册表项。  
  
 在下面的示例中，从注册表中的语句提供默认路径和数据其中适用，后跟包含从注册表脚本的项每个语句的表。  表提供了脚本项和其他信息语句。  
  
> [!NOTE]
>  以下注册表信息应为项的类型和用途的示例在注册编写项类型的注册表脚本的。  实际项及其用法可能会因项目类型的特定要求。  您应查看可用的示例查找非常类似于项目的类型您开发的工作项，然后检查该示例的注册表脚本。  
  
 下面的示例摘自 HKEY\_CLASSES\_ROOT。  
  
## 示例  
  
```  
\.figp  
   @="FigPrjFile"  
   "Content Type"="text/plain"  
\.figp\ShellNew  
   "NullFile"=""  
\FigPrjFile  
   @="Figure Project File"  
\DefaultIcon  
   @="<Visual Studio SDK installation path>\\9.0VSIntegration\\SomeFolder\\FigPkgs\\FigPrj\\Debug\\FigPrj.dll,-206"  
\shell\open  
   @="&Open in Visual Studio"  
\shell\open\command  
   @="devenv.exe \"%1\""  
```  
  
|名称|类型|数据|说明|  
|--------|--------|--------|--------|  
|`@`|REG\_SZ|`FigPrjFile`|该项的名称和说明键入扩展 .figp 的文件。|  
|`Content Type`|REG\_SZ|`Text/plain`|项目文件的内容类型。|  
|`NullFile`|REG\_SZ|`Null`||  
|`@`|REG\_SZ|`%MODULE%,-206`|默认使用此类型的项的图标。  %MODULE% 语句在对项类型 DLL 的默认位置的注册表完成。|  
|`@`|REG\_SZ|`&Open in Visual Studio`|默认此项目类型要打开的应用程序。|  
|`@`|REG\_SZ|`devenv.exe "%1"`|默认要运行的命令，在打开时此类型的项。|  
  
 下面的示例摘自 HKEY\_LOCAL\_MACHINE 并将位于键 \[HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\99.0Exp\\Packages 下的\] 注册表。  
  
## 示例  
  
```  
\{ACEF4EB2-57CF-11D2-96F4-000000000000} (The CLSID for the VSPackage)  
   @="FigPrj Project Package"  
   "InprocServer32"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\                      Debug\\FigPrj.dll"  
   "CompanyName"="Microsoft"  
   "ProductName"="Figure Project Sample"  
   "ProductVersion"="9.0"  
   "MinEdition"="professional"  
   "ID"=dword:00000001  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\SatelliteDLL  
   "DllName"="FigPrjUI.dll"  
   "Path"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\Debug\\"  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\Automation  
   "FigProjects"=""  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\AutomationEvents  
   "FigProjectsEvents"="Returns the FigProjectsEvents Object"  
   "FigProjectItemsEvents"="Returns the FigProjectItemsEvents Object"  
```  
  
|名称|类型|数据|说明|  
|--------|--------|--------|--------|  
|`@`\(默认值\)|REG\_SZ|`FigPrj Project VSPackage`|此注册的 VSPackage \(项目类型\) 的可本地化的名称。|  
|`InprocServer32`|REG\_SZ|`%MODULE%`|项类型的 DLL 路径。  IDE 加载此 DLL 并通过 VSPackage CLSID 对 `DllGetClassObject` 获取 <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> 构造 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> 对象。|  
|`CompanyName`|REG\_SZ|`Microsoft`|开发项目类型公司的名称。|  
|`ProductName`|REG\_SZ|`Figure Project Sample`|项目的名称类型。|  
|`ProductVersion`|REG\_SZ|`9.0`|项类型的版本号。|  
|`MinEdition`|REG\_SZ|`professional`|注册的 VSPackage 中编辑。|  
|`ID`|REG\_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|项目的 VSPackage 包打入键。  密钥验证，当加载项目时，该环境启动后。|  
|`DllName`|REG\_SZ|`%RESOURCE_DLL%`|包含项目类型的本地化资源附属 DLL 的文件名。|  
|`Path`|REG\_SZ|`%RESOURCE_PATH%`|附属 DLL 的路径。|  
|`FigProjectsEvents`|REG\_SZ|为值参见语句。|确定用于此自动化事件返回的文本字符串。|  
|`FigProjectItemsEvents`|REG\_SZ|为值参见语句。|确定用于此自动化事件返回的文本字符串。|  
  
 所有下面的示例位于键 \[HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\9.0Exp\\Projects 下的\] 注册表。  
  
## 示例  
  
```  
\{C061DB26-5833-11D2-96F5-000000000000} (The CLSID for projects of this type)  
   @="FigPrj Project"  
   "DisplayName"="#2"  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "ProjectTemplatesDir"="C:\\Program Files\\VSIP 9.0\\EnvSDK\\FigPkgs\\                           FigPrj\\FigPrjProjects"  
   "ItemTemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                           FigPrjProjectItems"  
   "DisplayProjectFileExtensions"="#3"  
   "PossibleProjectExtensions"="figp"  
   "DefaultProjectExtension"=".figp"  
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\1       (Folder 1 contains settings for Open Files filters.)  
   @="#4"  
   "CommonOpenFilesFilter"=dword:00000000  
   "CommonFindFilesFilter"=dword:00000000  
   "NotAddExistingItemFilter"=dword:00000000  
   "FindInFilesFilter"=dword:00000000  
   "NotOpenFileFilter"=dword:00000000  
   "SortPriority"=dword:000003e8  
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\2  
      (Folder 2 contains settings for Find in Files filters.)  
   @="#5"  
   "CommonOpenFilesFilter"=dword:00000000  
   "CommonFindFilesFilter"=dword:00000000  
   "NotAddExistingItemFilter"=dword:00000001  
   "FindInFilesFilter"=dword:00000001  
   "NotOpenFileFilter"=dword:00000000  
   "SortPriority"=dword:000003e8  
\{C061DB26-5833-11D2-96F5-000000000000}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (Second GUID indicates the registered project type for the Add Items templates.)  
   @="#6"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|名称|类型|数据|说明|  
|--------|--------|--------|--------|  
|`@`|REG\_SZ|`FigPrj Project`|此类型的默认项目名称。|  
|`DisplayName`|REG\_SZ|`#%IDS_PROJECT_TYPE%`|从附属 DLL 中检索的名称的资源 ID 注册在包的下方。|  
|`Package`|REG\_SZ|`%CLSID_Package%`|类别 VSPackage 的 ID 注册在包的下方。|  
|`ProjectTemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|项模板文件的默认路径。  这些是新项目模板显示的文件。|  
|`ItemTemplatesDir`|REG\_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|项目项模板文件的默认路径。  这些是添加新项目模板显示的文件。|  
|`DisplayProjectFileExtensions`|REG\_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|使 IDE 实现 **打开** 对话框。|  
|`PossibleProjectExtensions`|REG\_SZ|`figp`|用于确定由 IDE 中打开的项目是否由此项目类型 \(项目工厂\) 处理。  多个项的格式是分号分隔的列表。  例如 “vdproj; vdp”。|  
|`DefaultProjectExtension`|REG\_SZ|`.figp`|使用由 IDE 作为默认文件扩展名用于保存操作。|  
|`Filter Settings`|REG\_DWORD|各种，请参见语句和注释下表。|这些设置用于设置显示的文件各种筛选器在 UI 对话框。|  
|`@`|REG\_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|添加项目模板的资源 ID。|  
|`TemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|在 **添加新项目** 模板的对话框中显示的项目项的路径。|  
|`SortPriority`|REG\_DWORD|`100 (vcprx64)`|确定在 **添加新项目** 对话框中显示的文件树节点的排序顺序。|  
  
 下表显示了筛选器可在前面的代码段。  
  
|筛选器选项|说明|  
|-----------|--------|  
|`CommonFindFilesFilter`|指示筛选器是某个 **查看文件** 对话框的常用的筛选器。  常用的筛选器在筛选器列出在属于常规未标记的筛选器之前列表。|  
|`CommonOpenFilesFilter`|指示筛选器是某个 **打开文件** 对话框的常用的筛选器。  常用的筛选器在筛选器列出在属于常规未标记的筛选器之前列表。|  
|`FindInFilesFilter`|指示筛选器将为某个 **在文件中查找** 对话框的筛选器，并在常见的筛选器之后。|  
|`NotOpenFileFilter`|指示筛选器不使用 **打开文件** 对话框。|  
|`NotAddExistingItemFilter`|指示筛选器不使用添加 **现有项目** 对话框。|  
  
 默认情况下，因此，如果筛选器不具有一个或多个设置了这些标志，筛选器用于 **添加现有项目** 对话框和 **打开文件** 对话框中，在常见的筛选器列表后。  筛选器不使用 **在文件中查找** 对话框。  
  
 所有下面的示例位于键 \[HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\9.0Exp\\Projects 下的\] 注册表。  
  
## 示例  
  
```  
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)  
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|名称|类型|数据|说明|  
|--------|--------|--------|--------|  
|`@`|REG\_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|新项目模板的资源 ID。|  
|`TemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|默认签入的项类型的项目的路径。|  
|`SortPriority`|REG\_DWORD|`41 (x29)`|sets 对新项目向导 " 对话框中显示的项顺序。|  
|`NewProjectDialogOnly`|REG\_DWORD|`0`|0 指示此类型项目 " 新建项目 " 对话框仅显示。|  
  
 所有下面的示例位于键 \[HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\9.0Exp\\Projects 下的\] 注册表。  
  
## 示例  
  
```  
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)  
   @="Miscellaneous Files Project"  
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1  
                                 (CLSID for Figures Project projects)  
   @="#6"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|名称|类型|数据|说明|  
|--------|--------|--------|--------|  
|`@`|REG\_SZ|无|指示的默认以下项用于杂项文件项目项。|  
|`@`|REG\_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|资源添加新项模板文件的 ID 值。|  
|`TemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|默认 **添加新项目** 在对话框中显示项目的路径。|  
|`SortPriority`|REG\_DWORD|`100 (vcprx64)`|establishes 排序显示的命令在 **添加新项目** 对话框的树节点。|  
  
 下面的示例位于键 \[HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\9.0Exp\\Menus 下的\] 注册表。  
  
## 示例  
  
```  
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"  
```  
  
 菜单入口点 IDE 用于的资源检索菜单信息。  在此数据合并到菜单数据库，同一个键在注册表中 MenusMerged 部分中添加。  VSPackage 不应直接修改任何 MenusMerged 部分。  在数据字段在下表中，有三个逗号分隔字段。  第一个字段标识菜单资源文件的完整路径:  
  
-   如果第一个忽略 domain，菜单资源从 VSPackage GUID 确定附属 DLL 加载。  
  
 第二个字段标识类型 CTMENU 的菜单资源 ID:  
  
-   如果资源 ID 指定，因此，第一个形参提供文件路径，菜单资源从完整文件路径加载。  
  
-   如果提供资源 ID，但是，文件路径不是，菜单资源从附属 DLL 被加载。  
  
-   如果提供完整文件路径，并资源 ID 省略，要加载的文件应为 CTO 文件。  
  
 最后一个字段标识 CTMENU 资源的版本号。  您可以通过更改版本号重新合并菜单。  
  
|名称|类型|数据|说明|  
|--------|--------|--------|--------|  
|%CLSID\_Package%|REG\_SZ|`,1000,1`|检索菜单信息的资源。|  
  
 所有下面的示例位于键 \[HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\9.0Exp\\NewProjectTemplates 下的\] 注册表。  
  
```  
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|名称|类型|数据|说明|  
|--------|--------|--------|--------|  
|`@`|REG\_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|资源上的 ID 值项目新项目模板。|  
|`TemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|新的项目目录的默认路径。  此目录中的项。 **新建项目向导** 将显示对话框。|  
|`SortPriority`|REG\_DWORD|`41 (x29)`|建立项目在 **新项目** 对话框的树节点要显示的顺序。|  
|`NewProjectDialogOnly`|REG\_DWORD|`0`|0 指示此类型项。 **新项目** 对话框仅显示。|  
  
 下面的示例位于键 \[HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\9.0Exp\\InstalledProducts 下的\] 注册表。  
  
```  
\FiguresProductSample  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "UseInterface"=dword:00000001  
```  
  
|名称|类型|数据|说明|  
|--------|--------|--------|--------|  
|`Package`|REG\_SZ|`%CLSID_Package%`|注册的 VSPackage 的类 ID。|  
|`UseInterface`|REG\_DWORD|`1`|1 表示 UI 将用于与此项目进行交互。  0 表示没有 UI 接口。|  
  
 控制新项类型的 The.vsz 文件通常包含 RELATIVE\_PATH 项。  此路径是相对路径指定在 \\ProductDir entry of the project type in the following Setup 项下:  
  
 HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\7.0Exp\\Setup  
  
 例如，业务文件项模板添加以下注册表项:  
  
 HKEY\_LOCAL\_MACHINE \\ \\SOFTWARE\\Microsoft\\VisualStudio\\7.0Exp\\Setup\\EF\\ProductDir \= C:\\Program Files\\Microsoft Visual Studio\\EnterpriseFrameworks  
  
 这意味着，如果在 .vsz 文件中 PROJECT\_TYPE\=EF 项，环境查看以前指定的 ProductDir 内容的 .vsz 文件。  
  
## 请参阅  
 [清单︰ 创建新的项目类型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [项目模型的元素](../../extensibility/internals/elements-of-a-project-model.md)   
 [通过使用项目工厂来创建项目实例](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)