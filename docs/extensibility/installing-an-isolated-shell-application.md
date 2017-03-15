---
title: "安装独立的 Shell 应用程序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Shell [Visual Studio]，部署基于 shell 的应用程序"
  - "Visual Studio shell，部署基于 shell 的应用程序"
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: 40
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 40
---
# 安装独立的 Shell 应用程序
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

要安装的外壳应用程序必须执行以下步骤。  
  
-   准备您的解决方案。  
  
-   创建您的应用程序的 Windows Installer \(MSI\) 包。  
  
-   创建安装程序引导程序。  
  
 所有本文档中的代码示例来自 [外壳程序部署示例](http://go.microsoft.com/fwlink/?LinkId=262245), ，可以从 MSDN 网站上的代码库下载该。 此示例演示了执行上述每个步骤的结果。  
  
## 先决条件  
 若要执行本主题介绍的过程，必须在您的计算机上安装以下工具。  
  
-   Visual SDK Studio  
  
-   [Windows Installer XML 工具集](http://go.microsoft.com/fwlink/?LinkId=82720) 3.6 版  
  
 此示例还要求 Microsoft 可视化和建模 SDK，这并不是所有外壳程序要求。  
  
## 准备您的解决方案  
 默认情况下，Shell 模板构建到 VSIX 包，但此行为旨在主要用于调试目的。 外壳应用程序部署时，必须使用 MSI 包以在安装过程中允许注册表访问以及重新启动的。 若要准备您的应用程序的 MSI 部署，请执行以下步骤。  
  
#### 若要准备 MSI 部署一个外壳应用程序  
  
1.  编辑您的解决方案中每个.vsixmanifest 文件。  
  
     在 `Identifier` 元素中，添加 `InstalledByMSI` 元素和一个 `SystemComponent` 元素，然后将其值设置为 `true`。  
  
     这些元素可防止 VSIX 安装程序尝试从使用卸载安装您的组件和用户 **扩展和更新** 对话框。  
  
2.  对于每个项目，其中包含 VSIX 清单，编辑生成任务输出内容将在其中安装您的 MSI 的位置。 生成输出中包括的 VSIX 清单，但不生成.vsix 文件。  
  
## 为您的 Shell 创建 MSI  
 若要生成 MSI 包，我们建议你使用 [Windows Installer XML 工具集](http://go.microsoft.com/fwlink/?LinkId=82720) 因为它提供了更大的灵活性比标准安装程序项目。  
  
 在 Product.wxs 文件中，设置检测块和外壳程序组件的布局。  
  
 在您的解决方案的.reg 文件和 ApplicationRegistry.wxs 中，然后创建注册表项。  
  
### 检测块  
 检测块组成 `Property` 元素，用于指定进行检测的先决条件和 `Condition` 元素，它指定要返回到系统必备组件不是计算机上存在的消息。 例如，外壳应用程序将需要可再发行组件，Microsoft Visual Studio Shell，检测块将类似于下面的标记。  
  
```xml  
<Property Id="ISOSHELLSFX"> <RegistrySearch Id="IsoShellSfx" Root="HKLM" Key="Software\Microsoft\DevDiv\vs\Servicing\\$(var.ShellVersion)\IsoShell\$(var.ProductLanguage)" Name="Install" Type="raw" /> </Property> <Property Id="INTSHELLSFX"> <RegistrySearch Id="IntShellSfx" Root="HKLM" Key="SOFTWARE\Microsoft\DevDiv\vs\Servicing\$(var.ShellVersion)\devenv\$(var.ProductLanguage)" Name="Install" Type="raw" /> </Property> <Condition Message="This application requires $(var.IsoShellName).  Please install $(var.IsoShellName) then run this installer again."> <![CDATA[Installed OR ISOSHELLSFX]]> </Condition> <Condition Message="This application requires $(var.IntShellName).  Please install $(var.IntShellName) then run this installer again."> <![CDATA[Installed OR INTSHELLSFX]]> </Condition>  
  
```  
  
### 外壳程序组件的布局  
 您必须添加元素来标识目标目录结构和要安装的组件。  
  
##### 若要设置命令行程序组件的布局  
  
1.  创建的层次结构 `Directory` 元素来表示所有要在目标计算机上的文件系统上创建如以下示例所示的目录。  
  
    ```xml  
    <Directory Id="TARGETDIR" Name="SourceDir"> <Directory Id="ProgramFilesFolder"> <Directory Id="CompanyDirectory" Name="$(var.CompanyName)"> <Directory Id="INSTALLDIR" Name="$(var.FullProductName)"> <Directory Id="ExtensionsFolder" Name="Extensions" /> <Directory Id="Folder1033" Name="1033" /> </Directory> </Directory> </Directory> <Directory Id="ProgramMenuFolder"> <Directory Id="ApplicationProgramsFolder" Name="$(var.FullProductName)"/> </Directory> </Directory>  
    ```  
  
     通过引用这些目录 `Id` 时指定了必须安装的文件。  
  
2.  标识外壳和外壳应用程序需要，如以下示例所示的组件。  
  
    > [!NOTE]
    >  某些元素可以引用其他.wxs 文件中定义。  
  
    ```xml  
    <Feature Id="ProductFeature" Title="$(var.ShortProductName)Shell" Level="1"> <ComponentGroupRef Id="ApplicationGroup" /> <ComponentGroupRef Id="HelpAboutPackage" /> <ComponentRef Id="GeneralProfile" /> <ComponentGroupRef Id="EditorAdornment"/> <ComponentGroupRef Id="SlideShowDesignerGroup"/> <!-- Note: The following ComponentGroupRef is required to pull in generated authoring from project references. --> <ComponentGroupRef Id="Product.Generated" /> </Feature>  
    ```  
  
    1.  `ComponentRef` 元素引用另一个标识当前组件所需文件的.wxs 文件。 例如，GeneralProfile HelpAbout.wxs 中具有以下定义。  
  
        ```xml  
        <Fragment Id="FragmentProfiles"> <DirectoryRef Id="INSTALLDIR"> <Directory Id="ProfilesFolder" Name="Profiles"> <Component Id='GeneralProfile' Guid='*'> <File Id='GeneralProfile' Name='General.vssettings' DiskId='1' Source='$(var.BuildOutputDir)Profiles\General.vssettings' KeyPath='yes' /> </Component> </Directory> </DirectoryRef> </Fragment>  
        ```  
  
         `DirectoryRef` 元素指定在用户的计算机上转这些文件。`Directory` 元素指定，它将安装到子目录中，并且每个 `File` 元素都表示一个内置或中，作为解决方案的一部分存在，并且标识该文件可找到的位置创建 MSI 文件时的文件。  
  
    2.  `ComponentGroupRef` 元素表示一组的其他组件 \(或组件和组件组\)。 例如， `ComponentGroupRef` ApplicationGroup 中定义，如下所示 Application.wxs 中。  
  
        ```xml  
        <ComponentGroup Id="ApplicationGroup"> <ComponentGroupRef Id="DebuggerProxy" /> <ComponentRef Id="MasterPkgDef" /> <ComponentRef Id="SplashResource" /> <ComponentRef Id="IconResource" /> <ComponentRef Id="WinPrfResource" /> <ComponentRef Id="AppExe" /> <ComponentRef Id="AppConfig" /> <ComponentRef Id="AppPkgDef" /> <ComponentRef Id="AppPkgDefUndef" /> <ComponentRef Id="$(var.ShortProductName)UI1033" /> <ComponentRef Id="ApplicationShortcut"/> <ComponentRef Id="ApplicationRegistry"/> </ComponentGroup>  
        ```  
  
    > [!NOTE]
    >  所需的 Shell \(独立\) 应用程序依赖项: DebuggerProxy，MasterPkgDef，资源 \(尤其是.winprf 文件\)，应用程序和 PkgDefs。  
  
### 注册表项  
 Shell \(独立\) 项目模板包含 *p o j*用于合并安装上的注册表项的.reg 文件。 这些注册表项必须是安装和清理目的的 MSI 的一部分。 您还必须在 ApplicationRegistry.wxs 创建匹配的注册表块。  
  
##### 若要将集成到 MSI 的注册表项  
  
1.  在 **外壳自定义设置** 文件夹中，打开 *p o j*。 登记  
  
2.  目标安装目录的路径替换 $RootFolder$ 标记的所有实例。  
  
3.  添加应用程序所需的任何其他注册表项。  
  
4.  打开 ApplicationRegistry.wxs。  
  
5.  每个注册表项中 *p o j*.reg，添加相应的注册表块，如以下示例所示。  
  
    |*P o j*.reg|ApplicationRegisty.wxs|  
    |-----------------|----------------------------|  
    |\[HKEY\_CLASSES\_ROOT\\CLSID\\ {bb431796\-a179\-4df7\-b65d\-c0df6bda7cc6}\]<br /><br /> @\="PhotoStudio DTE 对象"|\< 注册表项 Id \= DteClsidRegKey 根 \= 'HKCR Key \=' $\(var。DteClsidRegKey\) 操作 \= 'createAndRemoveOnUninstall \><br /><br /> \< RegistryValue 类型 \= 字符串 Name \=' @' 值 \= $\(var。ShortProductName\) DTE 对象 \/ \><br /><br /> \< \/ 注册表项 \>|  
    |\[HKEY\_CLASSES\_ROOT\\CLSID\\ {bb431796\-a179\-4df7\-b65d\-c0df6bda7cc6} \\LocalServer32\]<br /><br /> @\="$RootFolder$\\PhotoStudio.exe"|\< 注册表项 Id \= DteLocSrv32RegKey 根 \= 'HKCR Key \=' $\(var。DteClsidRegKey\) \\LocalServer32' 操作 \= 'createAndRemoveOnUninstall \><br /><br /> \< RegistryValue 类型 \= 字符串 Name \=' @' 值 \= \[INSTALLDIR\] $\(var。ShortProductName\).exe \/ \><br /><br /> \< \/ 注册表项 \>|  
  
     在此示例中，Var.DteClsidRegKey 将解析为最上面一行中的注册表项。 Var.ShortProductName 解析为 `PhotoStudio`。  
  
## 创建安装程序引导程序  
 仅当第一次安装所有必备组件，将安装在已完成的 MSI。 为了便于最终用户体验，请创建收集并安装您的应用程序之前安装所有必备软件的安装程序。 若要确保成功安装，请执行以下操作:  
  
-   强制执行由管理员安装。  
  
-   检测是否安装了 Visual Studio Shell \(独立\)。  
  
-   按顺序运行一个或两个命令行程序安装程序。  
  
-   处理重新启动请求。  
  
-   运行您的 MSI。  
  
### 强制执行由管理员安装  
 启用安装程序以访问所必需的目录，如 \\program 需要此过程。  
  
##### 若要强制执行由管理员安装  
  
1.  打开安装项目的快捷菜单，然后选择 **属性**。  
  
2.  在下 **配置属性\/链接器\/清单文件**, ，请设置 **UAC 执行级别** 到 **requireAdministrator**。  
  
     此属性将需要到嵌入的清单文件，以管理员身份运行程序的属性。  
  
### 检测外壳程序安装  
 若要确定是否必须安装 Visual Studio Shell \(独立\)，请首先确定是否已安装通过检查注册表值为 HKLM\\Software\\Microsoft\\DevDiv\\vs\\Servicing\\ShellVersion\\isoshell\\LCID\\Install。  
  
> [!NOTE]
>  这些值也是由外壳检测块中 Product.wxs 只读的。  
  
 HKLM\\Software\\Microsoft\\AppEnv\\14.0\\ShellFolder 指定的位置，在安装 Visual Studio Shell，并可以检查那里文件。  
  
 有关如何检测外壳程序安装的示例，请参阅 `GetProductDirFromReg` Utilities.cpp 外壳程序部署示例中的函数。  
  
 如果在计算机上未安装一个或两个包所需的 Visual Studio Shell，必须将它们添加到您要安装的组件的列表。 有关示例，请参阅 `ComponentsPage::OnInitDialog` ComponentsPage.cpp 外壳程序部署示例中的函数。  
  
### 运行命令行程序安装程序  
 若要运行的命令行程序安装程序，请使用正确的命令行参数调用 Visual Studio Shell 可再发行组件。 最低限度上，必须使用命令行参数 **\/norestart \/q** ，并观察返回代码，以确定应下一步做什么。 下面的示例运行 Shell \(独立\) 可再发行组件。  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### 运行的 Shell 语言包安装程序  
 如果您改为查找已安装的命令行程序或 shell，只需要一种语言包，您可以如以下示例所示安装语言包。  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### 解读的返回值  
 在某些操作系统上 Visual Studio Shell \(独立\) 安装将需要重新启动计算机。 这种情况可通过对调用的返回代码来确定 `ExecCmd`。  
  
|返回值|描述|  
|---------|--------|  
|ERROR\_SUCCESS|安装已完成。 你现在可以安装你的应用程序。|  
|ERROR\_SUCCESS\_REBOOT\_REQUIRED|安装已完成。 重新启动计算机后，您可以安装你的应用程序。|  
|3015|正在进行安装。 重启计算机才能继续安装。|  
  
### 处理重新启动  
 当您通过使用运行程序安装程序 **\/norestart** 参数，指定它不会重新启动计算机或要求重新启动计算机。 但是，可能需要重新启动，并且必须确保您的安装程序将继续后重新启动计算机。  
  
 若要正确地处理重新启动操作，请确保只有一个安装程序设置了继续恢复过程将被正确处理。  
  
 如果返回 ERROR\_SUCCESS\_REBOOT\_REQUIRED 或 3015 时，您的代码应重新启动计算机，在安装继续之前。  
  
 若要处理的重启，请执行以下操作:  
  
-   设置注册表以继续安装，在 Windows 启动时。  
  
-   执行双引导程序重启。  
  
-   删除命令行程序安装程序 ResumeData 注册表项。  
  
-   重启 Windows。  
  
-   重置 MSI 开始路径。  
  
### 在 Windows 启动时继续运行安装程序将注册表设置  
 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\RunOnce\\ 注册表项执行在系统启动具有管理权限，然后擦写。HKEY\_CURRENT\_USER 包含一个类似的密钥，但它以普通用户身份运行，并不适用于安装。 您可以通过将一个字符串值放入您的安装程序将调用 RunOnce 项继续安装。 但是，我们建议使用调用安装程序 **\/restart** 或类似的参数，以通知它正在继续而不启动应用程序。 此外可以包含参数，以指示您在安装过程中，这可能需要多次重新启动的安装中特别有用的位置。  
  
 下面的示例演示 RunOnce 注册表项值用于继续安装。  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### 安装双引导程序重新启动  
 如果直接从 RunOnce 使用安装程序，则将无法完全加载桌面。 要提供完整的用户界面，必须创建另一个执行安装程序并结束 RunOnce 实例。  
  
 必须重新执行安装程序，以便获取正确的权限，并且必须为其指定足够的信息来了解您停止的位置重新启动前，如以下示例所示。  
  
```  
if (_cmdLineInfo.IsRestart()) { TCHAR path[MAX_PATH]={0}; GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR)); ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL ); }  
  
```  
  
### 正在删除命令行程序安装程序 ResumeData 密钥  
 命令行程序安装程序集 HKLM\\Software\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData 提供数据，从而重启后继续运行安装程序的注册表项。 由于应用程序中，不是命令行程序安装程序，将重新开始，删除该注册表项，如以下示例所示。  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData")); RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### 重启 Windows  
 设置所需的注册表项后，你可以重新启动 Windows。 下面的示例调用不同的 Windows 操作系统的重新启动命令。  
  
```  
OSVERSIONINFO ov; HANDLE htoken ; //Ask for the SE_SHUTDOWN_NAME token as this is needed by the thread calling for a system shutdown. if (OpenProcessToken(GetCurrentProcess(), TOKEN_ADJUST_PRIVILEGES | TOKEN_QUERY, &htoken)) { LUID luid ; LookupPrivilegeValue(NULL, SE_SHUTDOWN_NAME, &luid) ; TOKEN_PRIVILEGES    privs ; privs.Privileges[0].Luid = luid ; privs.PrivilegeCount = 1 ; privs.Privileges[0].Attributes = SE_PRIVILEGE_ENABLED ; AdjustTokenPrivileges(htoken, FALSE, &privs, 0, (PTOKEN_PRIVILEGES) NULL, 0) ; } //Use InitiateSystemShutdownEx to avoid unexpected restart message box try { if ( (ov.dwMajorVersion > 5) || ( (ov.dwMajorVersion == 5) && (ov.dwMinorVersion  > 0) )) { bExitWindows = InitiateSystemShutdownEx(0, _T(""), 0, TRUE, TRUE, REASON_PLANNED_FLAG); } else { #pragma prefast(suppress:380,"ignore warning about legacy api") bExitWindows = InitiateSystemShutdown(0, _T(""), 0, TRUE, TRUE); } } catch(...) { //advapi32.dll call not available! Will not restart! }  
  
```  
  
### 重置 MSI 开始的路径  
 在重新启动之前, 的当前目录是你的安装程序的位置，但是，重新启动后，位置将成为 system32 目录。 如以下示例所示，你的安装程序应重置 MSI 每次调用中之前, 的当前目录。  
  
```  
CString GetSetupPath() { TCHAR file[MAX_PATH]; GetModuleFileName(NULL, file, MAX_PATH * sizeof(TCHAR)); CString path(file); int fpos = path.ReverseFind('\\'); if (fpos != -1) { path = path.Left(fpos + 1); } return path; }  
  
```  
  
### 运行应用程序 MSI  
 Visual Studio Shell 安装程序返回 ERROR\_SUCCESS 后，您可以为您的应用程序运行 MSI。 由于你的安装程序提供的用户界面，以安静模式下启动您的 MSI \(**\/q**\) 并使用日志记录 \(**\/L**\)，如下面的示例所示。  
  
```cpp#  
TCHAR temp[MAX_PATH]; GetTempPath(MAX_PATH, temp); CString boutiqueInstallCmd, msi, log; CString cmdLine(MAKEINTRESOURCE("msiexec /q /I %s /L*vx %s REBOOT=ReallySuppress")); CString name(MAKEINTRESOURCE("PhotoStudioIntShell.msi")); log.Format(_T("\"%s%s.log\""), temp, name); msi.Format(_T("\"%s%s\""), GetSetupPath(), name); boutiqueInstallCmd.Format(cmdLine, msi, log); //TODO: You can use MSI API to gather and present install progress feedback from your MSI. dwResult = ExecCmd(boutiqueInstallCmd, FALSE);  
```  
  
## 请参阅  
 [演练: 创建基本的独立的 Shell 应用程序](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)