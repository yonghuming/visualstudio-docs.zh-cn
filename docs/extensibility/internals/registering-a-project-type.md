---
title: "注册项目类型 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3a60ac9de727e8542df7455ee331737403f6bef3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="registering-a-project-type"></a>注册项目类型
在创建新的项目类型时，你必须创建注册表条目，用于启用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]可以识别并使用你的项目类型。 通常情况下，通过使用注册表脚本 (.rgs) 文件需要创建这些注册表项。  
  
 在下面的示例中，从注册表的语句提供的默认路径和数据 （如果适用） 后, 跟包含每个语句的注册表脚本中的项的表。 表提供了脚本条目和语句的附加信息。  
  
> [!NOTE]
>  下面的注册表信息用于类型的示例，你将编写注册你的项目类型的注册表脚本中的条目的目的。 实际条目和它们的使用可能取决于你的项目类型的特定要求。 你应查看这些示例可用于查找一个十分类似于你正在开发的项目的类型，然后查看该示例的注册表脚本。  
  
 以下示例是从 HKEY_CLASSES_ROOT。  
  
## <a name="example"></a>示例  
  
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
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrjFile`|名称和具有扩展.figp 项目类型文件的说明。|  
|`Content Type`|REG_SZ|`Text/plain`|项目文件的内容类型。|  
|`NullFile`|REG_SZ|`Null`||  
|`@`|REG_SZ|`%MODULE%,-206`|此类型的项目使用默认图标。 在 %模块 %语句完成在注册表中的 DLL 的项目类型的默认位置。|  
|`@`|REG_SZ|`&Open in Visual Studio`|将在其中打开此项目类型的默认应用程序。|  
|`@`|REG_SZ|`devenv.exe "%1"`|将此类型的项目打开时运行的默认命令。|  
  
 下面的示例来自 HKEY_LOCAL_MACHINE 且位于注册表项下 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages]。  
  
## <a name="example"></a>示例  
  
```  
\{ACEF4EB2-57CF-11D2-96F4-000000000000} (The CLSID for the VSPackage)  
   @="FigPrj Project Package"  
   "InprocServer32"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\                      Debug\\FigPrj.dll"  
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
  
|名称|类型|数据|描述|  
|----------|----------|----------|-----------------|  
|`@`（默认值）|REG_SZ|`FigPrj Project VSPackage`|这可本地化的名称注册 VSPackage （项目类型）。|  
|`InprocServer32`|REG_SZ|`%MODULE%`|项目类型 DLL 的路径。 IDE 加载此 DLL，并将传递到 VSPackage CLSID`DllGetClassObject`获取<xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory>构造<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>对象。|  
|`CompanyName`|REG_SZ|`Microsoft`|开发项目类型的公司名称。|  
|`ProductName`|REG_SZ|`Figure Project Sample`|对于项目类型的名称。|  
|`ProductVersion`|REG_SZ|`9.0`|发布的项目类型的版本号。|  
|`MinEdition`|REG_SZ|`professional`|要注册 VSPackage 的版本。|  
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|包加载项目 VSPackage 的密钥。 当环境已启动后加载项目，则被验证密钥。|  
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|附属 DLL，它包含对于项目类型的本地化的资源文件名称。|  
|`Path`|REG_SZ|`%RESOURCE_PATH%`|附属 DLL 的路径。|  
|`FigProjectsEvents`|REG_SZ|请参阅值的语句。|确定此自动化事件返回的文本字符串。|  
|`FigProjectItemsEvents`|REG_SZ|请参阅值的语句。|确定此自动化事件返回的文本字符串。|  
  
 以下的所有示例都位于注册表项下 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects]。  
  
## <a name="example"></a>示例  
  
```  
\{C061DB26-5833-11D2-96F5-000000000000} (The CLSID for projects of this type)  
   @="FigPrj Project"  
   "DisplayName"="#2"  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "ProjectTemplatesDir"="C:\\Program Files\\VSIP 9.0\\EnvSDK\\FigPkgs\\                           FigPrj\\FigPrjProjects"  
   "ItemTemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                           FigPrjProjectItems"  
   "DisplayProjectFileExtensions"="#3"  
   "PossibleProjectExtensions"="figp"  
   "DefaultProjectExtension"=".figp"  
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\1       (Folder 1 contains settings for Open Files filters.)  
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
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|名称|类型|数据|说明|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrj Project`|此类型的项目的默认名称。|  
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|在包下注册的名称的资源 ID，从附属 DLL 中检索。|  
|`Package`|REG_SZ|`%CLSID_Package%`|在包下注册的 VSPackage 的类 ID。|  
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|默认的项目模板文件的路径。 这些是显示新项目模板的文件。|  
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|默认的项目项模板文件的路径。 这些是通过添加新项模板显示的文件。|  
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|使 IDE 以实现**打开**对话框。|  
|`PossibleProjectExtensions`|REG_SZ|`figp`|由 IDE 用于确定是否由此项目类型 （项目工厂） 处理打开的项目。 多个条目的格式是以分号分隔列表。 例如"vdproj; vdp"。|  
|`DefaultProjectExtension`|REG_SZ|`.figp`|由 IDE 作为默认文件扩展名另存为操作。|  
|`Filter Settings`|REG_DWORD|各种，请参阅语句和下表的注释。|这些设置用于设置用户界面对话框中显示文件的各个筛选器。|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|添加项模板的资源 ID。|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|在对话框中显示的项目项路径**添加新项**模板。|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|确定显示在文件的树节点中的排序顺序**添加新项**对话框。|  
  
 下表显示在前面的代码段中可用的筛选器选项。  
  
|筛选器选项|描述|  
|-------------------|-----------------|  
|`CommonFindFilesFilter`|指示筛选器是中的常见筛选器之一**在文件中查找**对话框。 前面未标记为公共的筛选器的筛选器列表中列出了常见的筛选器。|  
|`CommonOpenFilesFilter`|指示筛选器是中的常见筛选器之一**打开的文件**对话框。 前面未标记为公共的筛选器的筛选器列表中列出了常见的筛选器。|  
|`FindInFilesFilter`|指示该筛选器将中的筛选器之一**在文件中查找**对话框框中，将在常见的筛选器后列出。|  
|`NotOpenFileFilter`|表示在中将不使用筛选器**打开的文件**对话框。|  
|`NotAddExistingItemFilter`|指示筛选器不会使用在添加**现有项**对话框。|  
  
 默认情况下，如果筛选器不具有一个或多个这些标志集，使用筛选器中**添加现有项**对话框中和**打开的文件**对话框后列出了常见的筛选器。 在不使用的筛选器**在文件中查找**对话框。  
  
 以下的所有示例都位于注册表项下 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects]。  
  
## <a name="example"></a>示例  
  
```  
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)  
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|名称|类型|数据|说明|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|新的项目模板的资源 ID。|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|默认为已注册的项目类型的项目的路径。|  
|`SortPriority`|REG_DWORD|`41 (x29)`|集的排序顺序中的新项目向导对话框中显示的项目。|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 指示仅在新项目对话框中显示此类型的项目。|  
  
 以下的所有示例都位于注册表项下 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects]。  
  
## <a name="example"></a>示例  
  
```  
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)  
   @="Miscellaneous Files Project"  
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1  
                                 (CLSID for Figures Project projects)  
   @="#6"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|名称|类型|数据|说明|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|无|默认值，该值指示以下条目适用于的杂项文件项目项。|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|添加新项模板文件的资源 ID 值。|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|将显示在的项的默认路径**添加新项**对话框。|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|建立的树节点中显示的排序顺序**添加新项**对话框。|  
  
 下面的示例位于注册表项下 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus]。  
  
## <a name="example"></a>示例  
  
```  
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"  
```  
  
 菜单项将 IDE 指向用于检索菜单信息的资源。 当此数据已合并到菜单数据库时，则将注册表 MenusMerged 部分中添加相同的密钥。 VSPackage 不应修改 MenusMerged 部分下的任何内容直接。 在下表中的数据字段中，有三个以逗号分隔的字段。 第一个字段标识菜单资源文件的完整路径：  
  
-   如果省略第一个字段，从附属 VSPackage GUID 标识的 DLL 加载该菜单资源。  
  
 第二个字段标识类型 CTMENU 菜单资源 ID:  
  
-   如果指定的资源 ID，并且由第一个参数提供的文件路径，从的完整文件路径加载的菜单资源。  
  
-   如果提供的资源 ID，但该文件路径不是，从附属 DLL 加载该菜单资源。  
  
-   如果提供的完整文件路径，并且忽略的资源 ID，被应为首席技术官文件要加载的文件。  
  
 最后一个字段标识 CTMENU 资源的版本号。 你可以通过更改的版本号试合并菜单。  
  
|名称|类型|数据|描述|  
|----------|----------|----------|-----------------|  
|%Clsid_package%|REG_SZ|`,1000,1`|要检索的菜单信息的资源。|  
  
 以下的所有示例都位于注册表项下 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates]。  
  
```  
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|名称|类型|数据|说明|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|数字项目新项目模板的资源 ID 值。|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|新的项目目录的默认路径。 此目录中的项将显示在**新项目向导**对话框。|  
|`SortPriority`|REG_DWORD|`41 (x29)`|建立项目将显示的树节点中的顺序**新项目**对话框。|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 指示，此类型的项目的显示仅在**新项目**对话框。|  
  
 下面的示例位于注册表项下 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts]。  
  
```  
\FiguresProductSample  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "UseInterface"=dword:00000001  
```  
  
|名称|类型|数据|说明|  
|----------|----------|----------|-----------------|  
|`Package`|REG_SZ|`%CLSID_Package%`|已注册 VSPackage 的类 ID。|  
|`UseInterface`|REG_DWORD|`1`|1 表示 UI 将用于与此项目进行交互。 0 指示没有 UI 界面。|  
  
 经常控制新的项目类型的 The.vsz 文件包含 RELATIVE_PATH 条目。 此路径下的以下安装程序密钥中的项目类型的 \ProductDir 条目指定的路径的相对路径为：  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup  
  
 例如，企业框架项目模板将添加下列注册表项：  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir = C:\Program Files\Microsoft Visual Studio\EnterpriseFrameworks\  
  
 这意味着如果包括 PROJECT_TYPE =.vsz 文件，环境会找到你.vsz 文件中指定以前的 ProductDir 目录中的 EF 条目。  
  
## <a name="see-also"></a>另请参阅  
 [清单： 创建新项目类型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [项目模型的元素](../../extensibility/internals/elements-of-a-project-model.md)   
 [使用项目工厂创建项目实例](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)