---
redirect_url: shell/installing-an-isolated-shell-application
title: "安装独立的 Shell 应用程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], deploying shell-based applications
- Visual Studio shell, deploying shell-based applications
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: "40"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e3c6d5d88563d97c18081cbf44b67e247d98a468
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="installing-an-isolated-shell-application"></a>安装独立的 Shell 应用程序
若要安装 Shell 应用程序必须执行以下步骤。  
  
-   准备你的解决方案。  
  
-   创建你的应用程序的 Windows Installer (MSI) 包。  
  
-   创建安装程序引导程序。  
  
 所有本文档中的代码示例来自于[Shell 部署示例](http://go.microsoft.com/fwlink/?LinkId=262245)，可以从 MSDN 网站上的代码库下载该。 此示例演示执行每个步骤的结果。  
  
## <a name="prerequisites"></a>先决条件  
 若要执行本主题介绍的过程，必须在你的计算机上安装以下工具。  
  
-   Visual Studio SDK  
  
-   [Windows Installer XML 工具集](http://go.microsoft.com/fwlink/?LinkId=82720)3.6 版  
  
 该示例还需要 Microsoft 可视化和建模 SDK，这不是所有 shell 都需要。  
  
## <a name="preparing-your-solution"></a>准备你的解决方案  
 默认情况下，命令行程序模板构建到 VSIX 包，但此行为旨在主要用于调试目的。 Shell 应用程序部署时，必须使用 MSI 包以在安装期间允许进行注册表访问和重新启动。 若要准备用于 MSI 部署应用程序，请执行以下步骤。  
  
#### <a name="to-prepare-a-shell-application-for-msi-deployment"></a>若要准备用于 MSI 部署 Shell 应用程序  
  
1.  编辑你的解决方案中每个的.vsixmanifest 文件。  
  
     在`Identifier`元素中，添加`InstalledByMSI`元素和`SystemComponent`元素，然后将其值设置为`true`。  
  
     这些元素可防止 VSIX 安装程序尝试从使用卸载安装你的组件和用户**扩展和更新**对话框。  
  
2.  对于每个项目包含 VSIX 清单，编辑用于输出的内容将在其中安装你 MSI 的位置的生成任务。 在生成输出中，包括 VSIX 清单，但不生成.vsix 文件。  
  
## <a name="creating-an-msi-for-your-shell"></a>对于你 Shell 创建 MSI  
 若要生成你的 MSI 包，我们建议你使用[Windows Installer XML 工具集](http://go.microsoft.com/fwlink/?LinkId=82720)因为它提供更大的灵活性比标准的安装程序项目。  
  
 在 Product.wxs 文件中，设置检测块和外壳程序组件的布局。  
  
 在你的解决方案的.reg 文件和 ApplicationRegistry.wxs 中，然后创建注册表项。  
  
### <a name="detection-blocks"></a>检测块  
 检测块组成`Property`元素，指定进行检测的先决条件和`Condition`元素，它指定要返回到系统必备组件如果不存在的计算机上的消息。 例如，Shell 应用程序将需要可再发行组件，Microsoft Visual Studio Shell 和检测块将类似于以下的标记。  
  
```xml  
<Property Id="ISOSHELLSFX">  
  <RegistrySearch Id="IsoShellSfx" Root="HKLM" Key="Software\Microsoft\DevDiv\vs\Servicing\\$(var.ShellVersion)\IsoShell\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
<Property Id="INTSHELLSFX">  
  <RegistrySearch Id="IntShellSfx" Root="HKLM" Key="SOFTWARE\Microsoft\DevDiv\vs\Servicing\$(var.ShellVersion)\devenv\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
  
<Condition Message="This application requires $(var.IsoShellName).  Please install $(var.IsoShellName) then run this installer again.">  
  <![CDATA[Installed OR ISOSHELLSFX]]>  
</Condition>  
<Condition Message="This application requires $(var.IntShellName).  Please install $(var.IntShellName) then run this installer again.">  
  <![CDATA[Installed OR INTSHELLSFX]]>  
</Condition>  
  
```  
  
### <a name="layout-of-shell-components"></a>外壳程序组件的布局  
 你必须添加元素来确定目标目录结构和要安装的组件。  
  
##### <a name="to-set-the-layout-of-shell-components"></a>若要设置命令行程序组件的布局  
  
1.  创建层次结构的`Directory`元素来表示的所有目录后，若要创建在目标计算机上的文件系统，如以下示例所示。  
  
    ```xml  
    <Directory Id="TARGETDIR" Name="SourceDir">  
      <Directory Id="ProgramFilesFolder">  
        <Directory Id="CompanyDirectory" Name="$(var.CompanyName)">  
          <Directory Id="INSTALLDIR" Name="$(var.FullProductName)">  
            <Directory Id="ExtensionsFolder" Name="Extensions" />  
            <Directory Id="Folder1033" Name="1033" />  
          </Directory>  
        </Directory>  
      </Directory>  
      <Directory Id="ProgramMenuFolder">  
        <Directory Id="ApplicationProgramsFolder" Name="$(var.FullProductName)"/>  
      </Directory>  
    </Directory>  
    ```  
  
     这些目录到引用的`Id`时指定了必须安装的文件。  
  
2.  标识要 Shell 和 Shell 应用程序需要，如以下示例所示的组件。  
  
    > [!NOTE]
    >  某些元素可能引用其他.wxs 文件中的定义。  
  
    ```xml  
    <Feature Id="ProductFeature" Title="$(var.ShortProductName)Shell" Level="1">  
      <ComponentGroupRef Id="ApplicationGroup" />  
      <ComponentGroupRef Id="HelpAboutPackage" />  
      <ComponentRef Id="GeneralProfile" />  
      <ComponentGroupRef Id="EditorAdornment"/>        
      <ComponentGroupRef Id="SlideShowDesignerGroup"/>  
  
      <!-- Note: The following ComponentGroupRef is required to pull in generated authoring from project references. -->  
      <ComponentGroupRef Id="Product.Generated" />  
    </Feature>  
    ```  
  
    1.  `ComponentRef`元素引用标识当前的组件需要的文件的另一个.wxs 文件。 例如，GeneralProfile HelpAbout.wxs 中具有以下定义。  
  
        ```xml  
        <Fragment Id="FragmentProfiles">  
          <DirectoryRef Id="INSTALLDIR">  
            <Directory Id="ProfilesFolder" Name="Profiles">  
              <Component Id='GeneralProfile' Guid='*'>  
                <File Id='GeneralProfile' Name='General.vssettings' DiskId='1' Source='$(var.BuildOutputDir)Profiles\General.vssettings' KeyPath='yes' />  
              </Component>  
            </Directory>  
          </DirectoryRef>  
        </Fragment>  
        ```  
  
         `DirectoryRef`元素指定在用户的计算机上转这些文件。 `Directory`元素指定，则将安装到子目录，和每个`File`元素表示生成或，作为解决方案的一部分存在，并且标识该文件可以找到 MSI 文件创建时的文件。  
  
    2.  `ComponentGroupRef`元素表示一组的其他组件 （或组件和组件组）。 例如，`ComponentGroupRef`下 ApplicationGroup 定义，如下所示 Application.wxs 中。  
  
        ```xml  
        <ComponentGroup Id="ApplicationGroup">  
          <ComponentGroupRef Id="DebuggerProxy" />  
          <ComponentRef Id="MasterPkgDef" />  
          <ComponentRef Id="SplashResource" />  
          <ComponentRef Id="IconResource" />  
          <ComponentRef Id="WinPrfResource" />  
          <ComponentRef Id="AppExe" />  
          <ComponentRef Id="AppConfig" />  
          <ComponentRef Id="AppPkgDef" />  
          <ComponentRef Id="AppPkgDefUndef" />  
          <ComponentRef Id="$(var.ShortProductName)UI1033" />  
          <ComponentRef Id="ApplicationShortcut"/>  
          <ComponentRef Id="ApplicationRegistry"/>  
        </ComponentGroup>  
        ```  
  
    > [!NOTE]
    >  所需的 Shell （独立） 应用程序的依赖关系： DebuggerProxy，MasterPkgDef，资源 （尤其是.winprf 文件），应用程序和 PkgDefs。  
  
### <a name="registry-entries"></a>注册表项  
 Shell （独立） 项目模板包括*ProjectName*合并安装上的注册表项的.reg 文件。 这些注册表项必须是用于安装和清理目的 MSI 的一部分。 你还必须在 ApplicationRegistry.wxs 中创建匹配注册表块。  
  
##### <a name="to-integrate-registry-entries-into-the-msi"></a>若要将集成到 MSI 的注册表项  
  
1.  在**外壳自定义设置**文件夹中，打开*ProjectName*。 reg。  
  
2.  $RootFolder$ 令牌的所有实例都替换为目标安装目录的路径。  
  
3.  添加应用程序所需的任何其他注册表项。  
  
4.  打开 ApplicationRegistry.wxs。  
  
5.  中每个注册表条目*ProjectName*.reg，添加相应的注册表块，如以下示例所示。  
  
    |*ProjectName*.reg|ApplicationRegisty.wxs|  
    |-----------------------|----------------------------|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @="PhotoStudio DTE Object"|\<RegistryKey Id = DteClsidRegKey 根 = HKCR Key = $（差异DteClsidRegKey) 操作 createAndRemoveOnUninstall = ><br /><br /> \<RegistryValue 类型 = 'string' 名称 = @ 值 = $（差异ShortProductName) DTE 对象 / ><br /><br /> \</ RegistryKey >|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6} \LocalServer32]<br /><br /> @="$RootFolder$\PhotoStudio.exe"|\<RegistryKey Id = DteLocSrv32RegKey 根 = HKCR Key = $（差异DteClsidRegKey) \LocalServer32 操作 createAndRemoveOnUninstall = ><br /><br /> \<RegistryValue 类型 = 'string' 名称 = @ 值 = [INSTALLDIR] $（差异ShortProductName).exe / ><br /><br /> \</ RegistryKey >|  
  
     在此示例中，Var.DteClsidRegKey 将解析为最上面一行中的注册表项。 Var.ShortProductName 解析为`PhotoStudio`。  
  
## <a name="creating-a-setup-bootstrapper"></a>创建安装程序引导程序  
 仅当第一次安装所有必备组件时，将安装已完成的 MSI。 若要简化最终用户体验，创建收集并安装你的应用程序之前安装所有必备组件的安装程序。 若要确保成功安装，请执行下列操作：  
  
-   强制执行由管理员安装。  
  
-   检测是否安装了 Visual Studio Shell （独立）。  
  
-   按顺序运行一个或两个命令行程序安装程序。  
  
-   处理重新启动请求。  
  
-   运行您的 MSI。  
  
### <a name="enforcing-installation-by-administrator"></a>强制执行由管理员安装  
 此过程需要以启用安装程序以访问所需的目录，如 \Program Files\\。  
  
##### <a name="to-enforce-installation-by-administrator"></a>若要强制执行由管理员安装  
  
1.  打开安装项目的快捷菜单，然后选择**属性**。  
  
2.  下**配置属性 / 链接器 / 清单文件**，将其设置**UAC 执行级别**到**requireAdministrator**。  
  
     此属性将需要到嵌入的清单文件，以管理员身份运行程序的属性。  
  
### <a name="detecting-shell-installations"></a>检测 Shell 安装  
 若要确定是否必须安装 Visual Studio Shell （独立），首先确定是否已安装通过检查 HKLM\Software\Microsoft\DevDiv\vs\Servicing\ShellVersion\isoshell\LCID\Install 的注册表值。  
  
> [!NOTE]
>  这些值也是由 Product.wxs 中的 Shell 检测块只读的。  
  
 HKLM\Software\Microsoft\AppEnv\14.0\ShellFolder 指定其中已安装 Visual Studio Shell，并可以检查存在文件的位置。  
  
 有关如何检测 Shell 安装的示例，请参阅`GetProductDirFromReg`Utilities.cpp Shell 部署示例中的函数。  
  
 如果在计算机上未安装一个或两个包所需的 Visual Studio Shell，你必须将它们添加到你要安装组件的列表。 有关示例，请参阅`ComponentsPage::OnInitDialog`ComponentsPage.cpp Shell 部署示例中的函数。  
  
### <a name="running-the-shell-installers"></a>运行命令行程序安装程序  
 若要运行的命令行程序安装程序，请使用正确的命令行自变量调用 Visual Studio Shell 可再发行文件。 至少，你必须使用命令行自变量**/norestart /q**监视为返回代码，以确定应如何下一步。 下面的示例运行可再发行组件 Shell （独立）。  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### <a name="running-the-shell-language-pack-installers"></a>运行命令行程序语言包安装程序  
 如果你改为查找已安装的命令行程序或 shell，只需要一种语言包，你可以如以下示例所示安装语言包。  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### <a name="deciphering-return-values"></a>解密返回值  
 在某些操作系统上的 Visual Studio Shell （独立） 安装将需要重新启动。 这种情况也可由调用的返回代码`ExecCmd`。  
  
|返回值|描述|  
|------------------|-----------------|  
|ERROR_SUCCESS|安装已完成。 你现在可以安装你的应用程序。|  
|ERROR_SUCCESS_REBOOT_REQUIRED|安装已完成。 重新启动计算机后，你可以安装你的应用程序。|  
|3015|安装过程正在进行。 重启计算机才能继续安装。|  
  
### <a name="handling-restarts"></a>处理重新启动  
 通过使用运行程序安装程序时**/norestart**自变量，指定它不会重新启动计算机或要求重新启动计算机。 但是，可能需要重新启动，并且你必须确保安装程序继续后重新启动计算机。  
  
 若要正确处理重新启动，请确保该只有一个安装程序是设置为恢复，而恢复进程将被正确处理。  
  
 如果返回 ERROR_SUCCESS_REBOOT_REQUIRED 或 3015 时，你的代码在安装继续前应重新启动计算机。  
  
 若要处理重新启动，执行下列操作：  
  
-   设置注册表以继续安装，在 Windows 启动时。  
  
-   执行双引导程序重新启动。  
  
-   删除命令行程序安装程序 ResumeData 密钥。  
  
-   重新启动 Windows。  
  
-   重置 MSI 开始路径。  
  
### <a name="setting-the-registry-to-resume-setup-when-windows-starts"></a>设置注册表以在 Windows 启动时继续运行安装程序  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce\ 注册表项在系统启动具有管理权限执行，然后被擦除。 HKEY_CURRENT_USER 包含类似的密钥，但它以普通用户身份运行，而且不适合安装。 您可以通过将字符串值放在调用安装程序的 RunOnce 密钥来继续安装。 但是，我们建议使用调用安装**/重新启动**或类似的参数，用于通知它正在恢复而不启动应用程序。 您还可以包含参数，以指示你所在在安装过程中，这可能需要多个重新启动的安装中特别有用。  
  
 下面的示例演示用于恢复安装 RunOnce 注册表项值。  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### <a name="installing-double-restart-of-bootstrapper"></a>安装引导程序的双精度重新的启动  
 如果安装程序用于直接从 RunOnce，桌面将无法完全加载。 若要提供完整的用户界面，必须创建另一个执行的安装程序并结束 RunOnce 实例。  
  
 必须重新执行安装程序，以便获取正确的权限，并且你必须向它提供足够的信息来了解你停止的位置之前重新启动，如以下示例所示。  
  
```  
if (_cmdLineInfo.IsRestart())  
{  
    TCHAR path[MAX_PATH]={0};  
    GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR));      
    ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL );  
}  
  
```  
  
### <a name="deleting-the-shell-installer-resumedata-key"></a>正在删除 Shell 安装程序 ResumeData 密钥  
 程序安装程序设置提供数据，从而在重新启动后继续运行安装程序的 HKLM\Software\Microsoft\VisualStudio\14.0\Setup\ResumeData 注册表项。 由于你的应用程序，不是命令行程序安装程序，正在恢复，删除该注册表项，如以下示例所示。  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData"));  
RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### <a name="restarting-windows"></a>重启 Windows  
 设置必需的注册表项后，你可以重新启动 Windows。 下面的示例调用不同的 Windows 操作系统的重新启动命令。  
  
```  
OSVERSIONINFO ov;  
HANDLE htoken ;  
//Ask for the SE_SHUTDOWN_NAME token as this is needed by the thread calling for a system shutdown.  
if (OpenProcessToken(GetCurrentProcess(), TOKEN_ADJUST_PRIVILEGES | TOKEN_QUERY, &htoken))  
{  
    LUID luid ;  
    LookupPrivilegeValue(NULL, SE_SHUTDOWN_NAME, &luid) ;  
    TOKEN_PRIVILEGES    privs ;  
    privs.Privileges[0].Luid = luid ;  
    privs.PrivilegeCount = 1 ;  
    privs.Privileges[0].Attributes = SE_PRIVILEGE_ENABLED ;  
    AdjustTokenPrivileges(htoken, FALSE, &privs, 0, (PTOKEN_PRIVILEGES) NULL, 0) ;  
}   
  
//Use InitiateSystemShutdownEx to avoid unexpected restart message box  
try  
{              
    if ( (ov.dwMajorVersion > 5) || ( (ov.dwMajorVersion == 5) && (ov.dwMinorVersion  > 0) ))  
    {  
        bExitWindows = InitiateSystemShutdownEx(0, _T(""), 0, TRUE, TRUE, REASON_PLANNED_FLAG);  
    }  
    else  
    {  
#pragma prefast(suppress:380,"ignore warning about legacy api")  
        bExitWindows = InitiateSystemShutdown(0, _T(""), 0, TRUE, TRUE);  
    }  
}  
catch(...)  
{  
    //advapi32.dll call not available! Will not restart!  
}  
  
```  
  
### <a name="resetting-the-start-path-of-msi"></a>重置 MSI 开始路径  
 在重新启动之前, 的当前目录是你的安装程序的位置，但是，重新启动后，位置将成为 system32 目录。 如以下示例所示，你的安装程序应该重置每个 MSI 调用之前, 的当前目录。  
  
```  
CString GetSetupPath()  
{  
    TCHAR file[MAX_PATH];  
    GetModuleFileName(NULL, file, MAX_PATH * sizeof(TCHAR));  
    CString path(file);  
    int fpos = path.ReverseFind('\\');  
    if (fpos != -1)  
    {  
        path = path.Left(fpos + 1);  
    }  
  
    return path;  
}  
  
```  
  
### <a name="running-the-application-msi"></a>运行应用程序 MSI  
 Visual Studio Shell 安装程序返回 ERROR_SUCCESS 后，你可以为你的应用程序运行 MSI。 因为你的安装程序会向用户界面，在静默模式下启动你 MSI (**/q**) 日志记录 (**/L**)，如下面的示例所示。  
  
```cpp  
TCHAR temp[MAX_PATH];  
GetTempPath(MAX_PATH, temp);  
  
CString boutiqueInstallCmd, msi, log;  
CString cmdLine(MAKEINTRESOURCE("msiexec /q /I %s /L*vx %s REBOOT=ReallySuppress"));  
CString name(MAKEINTRESOURCE("PhotoStudioIntShell.msi"));  
log.Format(_T("\"%s%s.log\""), temp, name);  
msi.Format(_T("\"%s%s\""), GetSetupPath(), name);  
boutiqueInstallCmd.Format(cmdLine, msi, log);  
  
//TODO: You can use MSI API to gather and present install progress feedback from your MSI.  
dwResult = ExecCmd(boutiqueInstallCmd, FALSE);  
```  
  
## <a name="see-also"></a>另请参阅  
 [演练：创建基本的独立 Shell 应用程序](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)