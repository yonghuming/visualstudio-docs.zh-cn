---
redirect_url: shell/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file
title: "通过使用修改独立的 Shell。Pkgdef 文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .pkgdef file
ms.assetid: 69e8f78e-bcf1-46cb-8866-7de37d134997
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4716a2c69d64586131c913cde8e3e2d780f9aa69
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgdef-file"></a>通过使用修改独立的 Shell。Pkgdef 文件
.Pkgdef 文件以支持可用于自定义独立的 shell 应用程序的设置。 它指定当创建应用程序安装在一台计算机并且启动应用程序时所引用的 Visual Studio shell 的值。 基于适用的注册表项的文件进行组织设置。  
  
> [!WARNING]
>  请注意在 Visual Studio 启动时不会扫描 VSPackage 的.vsixmanifest 文件中未声明的.pkgdef 文件。  
  
 .Pkgdef 文件包含每个由键标识，或者的各节`[$RootKey$]`或`[$RootKey$\`*子项*`]`，其中 $RootKey$ 是应用程序的根密钥。  
  
 每个部分包含具有以下格式的名称/值对： `"` *ValueName*`"=`*值*。  
  
 值为一个字符串，用引号引起来或一个 32 位整数，它表示为一个 dword 值。 值具有以下约束：  
  
-   所有的 dword 值是以十六进制格式，例如`dword:00000001`。  
  
     对于布尔值，1 表示 true，，0 表示 false。  
  
-   所有的 GUID 字符串都处于注册表格式，例如， `"{00000000-0000-0000-0000-000000000000}"`。  
  
-   所有可本地化的资源标识符具有形式"@*resourceID*"或"#*resourceID*"，其中*resourceID*是应用程序 UI 包中的资源标识符例如， `"@102"`。 应用程序 UI 包是在 AppLocalizationPackage 设置中引用的包。  
  
 例如，  
  
```  
"HideSolutionConcept"=dword:00000001  
"DefaultDebugEngine"="{00000000-0000-0000-0000-000000000000}"  
```  
  
 你可以向.pkgdef 文件添加注释。 单行注释与前两个字符具有两个斜杠。  
  
 替换字符串的列表，请参阅[中使用的替换字符串。Pkgdef 和。Pkgundef 文件](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md)。  
  
 下列各节描述影响的行为的 Visual Studio shell 隔离模式的特定注册表值。 你还可以在此文件中定义应用程序的其他注册表的值。  
  
> [!NOTE]
>  如果在.pkgdef 文件中未提供一种设置，则没有相应条目进行注册表中。  
  
## <a name="settings"></a>设置  
 下表介绍 [$RootKey$] 下定义的值。  
  
|名称|类型|值|  
|----------|----------|-----------|  
|AddinsAllowed|dword|如果可以加载外接程序; 则为 true否则为 false。<br /><br /> 默认值为 true。|  
|AllowsDroppedFilesOnMainWindow|dword|主窗口可以接受拖放的文件; 如果为 true否则为 false。 在主窗口中的文件打开使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A>方法。 这相当于使用打开文档**打开**命令**文件**应用程序中的菜单。<br /><br /> 默认值为 true。|  
|AppIcon|string|程序图标的完整路径。 应用程序名称左侧的标题栏中会显示此图标。<br /><br /> 默认值是"$RootFolder$\\*solutionName*.ico"，其中*solutionName*是应用程序解决方案文件的名称。|  
|AppLocalizationPackage|string|包含应用程序的 UI 附属程序集的 VSPackage 的 GUID。 此 VSPackage 包括.vsct 文件的已编译的版本，可以包括其他本地化的字符串。 功能集和菜单命令，可以启用或禁用通过更改 UI 项目.vsct 文件中的设置组。<br /><br /> 默认值为"{*vsUiPackageGuid*}"，其中*vsUiPackageGuid*是分配给应用程序 UI 包的 GUID。|  
|AppName|string|应用程序的名称。 名称出现在应用程序窗口的标题栏。<br /><br /> 默认值为应用程序解决方案文件的名称。|  
|CommandLineLogo|string|在控制台窗口中运行应用程序时的横幅文本。 此设置会影响仅支持命令行生成操作的应用程序。<br /><br /> 默认值是"*companyName**solutionName* 1.0 版。"，其中*companyName*名称提供安装 Windows 时，公司和*solutionName*是应用程序解决方案文件的名称。|  
|DefaultDebugEngine|string|默认值的 GUID 调试引擎以使用该应用程序。<br /><br /> 注意： 一个空的 GUID （全部为零） 指示应用程序未指定默认调试引擎。 这使调试器能够选择要使用的调试引擎。<br /><br /> 默认值为"{00000000-0000-0000-0000-000000000000}"。|  
|DefaultHomePage|string|内部的 Web 浏览器窗口默认主页 URL。<br /><br /> 如果**主页**选项在应用程序，可用，则此设置还会影响选项的默认状态。 有关详细信息，请参阅[Web 浏览器中，环境中，选项对话框](../ide/reference/web-browser-environment-options-dialog-box.md)。<br /><br /> 默认值是安装 Windows 时提供的公司的 URL。|  
|DefaultProjectsLocation|string|默认项目文件夹的完整路径。 例如，<br /><br /> `"DefaultProjectsLocation"="$MyDocuments$\MyVSShellStub\Projects"`<br /><br /> 如果**Visual Studio 项目位置**选项在应用程序，可用，则此设置还会影响选项的默认状态。 有关详细信息，请参阅[NIB： 常规、 项目和解决方案、 选项对话框](http://msdn.microsoft.com/en-us/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)。<br /><br /> 默认值是"$MyDocuments$\\*solutionName*"，其中*solutionName*是应用程序解决方案文件的名称。|  
|DefaultSearchPage|string|内部的 Web 浏览器窗口默认搜索页 URL。<br /><br /> 如果**搜索页**选项在应用程序，可用，则此设置还会影响选项的默认状态。 有关详细信息，请参阅[Web 浏览器中，环境中，选项对话框](../ide/reference/web-browser-environment-options-dialog-box.md)。<br /><br /> 默认值为"http://search.live.com"。|  
|DefaultUserFilesFolderRoot|string|用户文件夹，相对于当前用户的名称的我的文档文件夹。<br /><br /> 默认值为应用程序解决方案文件的名称。|  
|DisableOutputWindow|dword|指示是否为已禁用，独立的 shell 应将输出窗口。<br /><br /> 如果此值设置为 true，Visual Studio 将不显示中的解决方案生成管理器输出**输出**窗口中，并隐藏**显示输出窗口在生成开始时**中的复选框**项目和解决方案**中的类别**选项**对话框。<br /><br /> 默认值为 False。|  
|HideMiscellaneousFilesByDefault|dword|为 true，则隐藏**杂项文件**在默认情况下的文件夹**解决方案资源管理器**; 否则为 false。<br /><br /> 如果**在解决方案资源管理器中的显示杂项文件**选项在应用程序，可用，则此设置还会影响选项的默认状态。 有关详细信息，请参阅[文档，环境中，选项对话框](../ide/reference/documents-environment-options-dialog-box.md)。<br /><br /> 默认值为 False。|  
|HideSolutionConcept|dword|若要创建独立的项目的所有项目，并将解决方案和独立项目与解决方案相关的命令隐藏默认设置。否则为 false。<br /><br /> 如果**总是显示解决方案**选项在应用程序，可用，则此设置还会影响选项的默认状态。 有关详细信息，请参阅[NIB： 常规、 项目和解决方案、 选项对话框](http://msdn.microsoft.com/en-us/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)。<br /><br /> 默认值为 False。|  
|NewProjDlgInstalledTemplatesHdr|string|中的 Visual Studio nstalled 模板标头名称**模板**列入**新项目**对话框。 这是一个字符串，或者从应用程序 UI 包加载的可本地化的资源标识符。<br /><br /> 默认值是"*solutionName*已安装的模板"，其中*solutionName*是应用程序解决方案文件的名称。|  
|NewProjDlgSlnTreeNodeTitle|string|名称**Visual Studio 解决方案**中的节点**项目类型**树**新项目**对话框。 这是一个字符串，或者从应用程序 UI 包加载的可本地化的资源标识符。<br /><br /> 默认值是"*solutionName*已安装的模板"，其中*solutionName*是应用程序解决方案文件的名称。|  
|SolutionFileCreatorIdentifier|string|应用程序标识符，它显示为应用程序生成的解决方案文件中的第二行。 这条线指示创建该文件的应用程序。 按照约定，此值包含名称应用程序和应用程序的版本号。 例如，<br /><br /> `"SolutionFileCreatorIdentifier"="MyVSShellStub Solution File, Format Version 10.00"`<br /><br /> VSLauncher.exe 程序，这是用于打开 Visual Studio 解决方案文件的默认程序，使用此第二行来确定要在其中打开解决方案文件的 Visual Studio 版本。 应用程序需要其自己的启动器以处理其关联的解决方案文件。 启动器无法也使用此第二个行中的解决方案文件以确定哪一个版本的应用程序以打开该解决方案。<br /><br /> 注意： Visual Studio VSLauncher.exe 程序不处理由独立的 shell 应用程序的.sln 文件。<br /><br /> 默认值是"*solutionName*解决方案文件和格式版本 10.00"，其中*solutionName*是应用程序解决方案文件的名称。|  
|SolutionFileExt|string|应用程序解决方案文件扩展名。 我们建议你选择唯一的文件名扩展名 (not.sln)。<br /><br /> 默认值是"*solutionName*_sln"，其中*solutionName*是应用程序解决方案文件的名称。|  
|SplashScreenBitmap|string|应用程序的初始屏幕的位图文件完整路径。<br /><br /> 默认值为"$RootFolder$\Splash.bmp"。|  
|ThisVersionDTECLSID|string|应用程序的自动化对象类标识符 (CLSID)。<br /><br /> 应用程序自动化对象是中的 Visual Studio shell 自动化模型和实现的应用程序的顶级对象<xref:EnvDTE._DTE?displayProperty=fullName>接口。<br /><br /> 如果应用程序自动化对象已正确注册下 HKEY_CLASSES_ROOT\CLSID 注册表项，则可以使用[CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)函数来直接创建的应用程序实例。<br /><br /> Visual Studio shell 使用此 CLSID 注册应用程序自动化对象在运行对象表 (ROT) 使用 ACTIVEOBJECT_WEAK 标志。 这样便可以使用[GetActiveObject](http://msdn.microsoft.com/en-us/a276e30c-6a7f-4cde-9639-21a9f5170b62)函数可检索到的应用程序运行的实例的指针。 此外，如果你定义应用程序自动化对象的 ProgID，然后 Visual Studio shell 还会注册应用程序的每个实例到 ROT 中通过使用窗体项标记*progID*:*processID*，其中*progID*是应用程序自动化对象的 ProgID 和*processID*是应用程序实例的进程标识符。 例如，如果你创建一个名字对象，如下所示：<br /><br /> `CreateItemMoniker(L"!",`  *instanceString*`, &instanceMoniker)`<br /><br /> 其中`instanceString`是*progID*:*processID*字符串。 然后，您无法使用`instanceMoniker`用 ROT GetObject 函数来获取的实例。<br /><br /> 如果省略 ThisVersionDTECLSID 设置，应用程序不是公开通过组件对象模型 (COM)。 无法在此情况下，通过调用创建的应用程序实例[CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)函数，并且不能在 ROT 中注册。<br /><br /> 每个版本的 VSPackage 必须具有不同的 CLSID。<br /><br /> 默认值为 Visual Studio 生成的应用程序的自动化对象的 GUID。|  
|ThisVersionSolutionCLSID|string|应用程序的解决方案对象的 CLSID。<br /><br /> 解决方案自动化对象包含有关应用程序和实现的实例中当前打开的解决方案信息<xref:EnvDTE._Solution?displayProperty=fullName>接口。<br /><br /> 如果解决方案自动化对象已正确注册下 HKEY_CLASSES_ROOT\CLSID 注册表项，则可以使用[CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)函数来直接创建一个用于应用程序的解决方案对象。<br /><br /> Visual Studio shell 使用此 CLSID 来使用 ACTIVEOBJECT_WEAK 标志 ROT 中注册的解决方案自动化对象。<br /><br /> 如果省略此设置，则解决方案类未注册与组件对象模型 (COM) 中，并且无法通过调用创建的解决方案对象[CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)函数，并且不能在中注册ROT。<br /><br /> 默认值为 Visual Studio 生成的应用程序的解决方案对象的 GUID。|  
|UserFilesSubFolderName|string|在其中应用程序创建用户文件和子文件夹的用户的 My Documents 文件夹下的子文件夹的名称。<br /><br /> 默认值为应用程序解决方案文件的名称。|  
|UserOptsFileExt|string|应用程序的解决方案用户选项文件的扩展名。<br /><br /> 默认值为应用程序解决方案文件的名称。|  
  
## <a name="binding-path-settings"></a>绑定路径设置  
 [$RootKey$ \BindingPaths\\{00000000-0000-0000-0000-000000000000}] 键包含的命令行界面，检查程序集的目录列表。 这些目录将添加到的外壳程序探测专用程序集的应用程序的目录列表。  
  
 默认情况下，没有绑定路径条目添加到.pkgdef 文件中。 但是，Visual Studio 安装目录的以下子目录自动添加到注册表中的应用程序绑定路径列表中。  
  
-   Common7\IDE\  
  
-   Common7\IDE\\\PrivateAssemblies  
  
-   Common7\IDE\\\PublicAssemblies  
  
 若要将目录添加到的绑定路径，添加窗体的条目"*directoryName*"=""，其中*directoryName*为绝对路径。 例如，  
  
```  
[$RootKey$\BindingPaths\{00000000-0000-0000-0000-000000000000}]  
"$RootFolder$\directory1"=""  
"%CommonProgramFiles%\directory2"=""  
```  
  
## <a name="profile-settings"></a>配置文件设置  
 下表介绍每个相关包下 [$RootKey$ \Profile] 定义的值。  
  
|名称|类型|值|  
|----------|----------|-----------|  
|AutoSaveFile|string|应用程序将自动保存文件存储在其中的目录。<br /><br /> 默认值为"$RootFolder$\Profiles\CurrentSettings.vssettings"。|  
  
## <a name="package-satellite-dll-settings"></a>包附属 DLL 设置  
 下表介绍了下定义的值 [$RootKey$ \Packages\\{*vsPackageGuid*} \SatelliteDll] 对附属 DLL 的每个关联的包，其中*vsPackageGuid*是关联的包的 GUID。  
  
|名称|类型|值|  
|----------|----------|-----------|  
|Dll 名称|string|DLL 文件名称。<br /><br /> 默认值是"*solutionName*ui.dll"，其中*solutionName*是应用程序解决方案文件的名称。|  
|路径|string|包含附属 DLL 的目录。<br /><br /> 默认值为"$PackageFolder$"。|  
  
## <a name="package-menu-item-settings"></a>包菜单项设置  
 [$RootKey$ \Menus] 注册表项定义的应用程序的 UI 资源文件。  
  
 菜单项值具有窗体"{*vsUiPackageGuid*}"="、 *resourceId*， *versionNumber*"，其中*vsUiPackageGuid*是的 GUID应用程序 UI 包， *resourceId*是包含用户界面元素中的 CTMENU 资源的资源标识符和*versionNumber*虚拟版本号为 CTMENU资源。 有关详细信息，请参阅[注册互操作程序集命令处理程序](../extensibility/internals/registering-interop-assembly-command-handlers.md)。  
  
 默认情况下，应用程序 UI 包的.pkgdef 文件中创建菜单项项。  
  
 每个包，它提供菜单项和，它不随应用程序的一部分，将添加为包的一个菜单项项。  
  
## <a name="see-also"></a>另请参阅  
 [自定义独立的 Shell](../extensibility/customizing-the-isolated-shell.md)   
 [.Pkgundef 文件](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md)