---
title: "演练：创建多计算机生成环境 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "生成环境, MSBuild"
  - "MSBuild, 在多台计算机上生成"
ms.assetid: ae5391b1-3eec-42f5-beb3-f28630615a9e
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# 演练：创建多计算机生成环境
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

以便它可以参与生成,可以通过安装 Visual Studio 在主机然后复制各种文件创建您的组织中的生成环境和设置为另一台计算机。  不必要在另一台计算机上安装 Visual Studio。  
  
 文档没有给外部软件赋予权利或者给第三方团体建立环境。  
  
||  
|-|  
|免责声明<br /><br /> 此文档在“as\-is”基础上提供.  我们测试概述中的步骤，我们无法详尽测试每个配置。  我们将尝试在文档中当前您了解的任何其他信息。  本文档中的信息（包括 URL 和其他 Internet 网站引用）如有更改，恕不另行通知。  Microsoft不进行担保，表达 或提示，有关所提供的信息。  您必须承担使用它的风险。<br /><br /> 文档不提供所有任何法规权限对所有 Microsoft产品的任何知识产权。  可以复制，并使用该为内部，引用目的文档。<br /><br /> 您没有为Microsoft提供任何关于此文档的建议，注释或其他反馈 \(“反馈”\)的义务 。  但是，您自愿提供的任何反馈可用于Microsoft产品和相关的规范或其他文档 \(统称，“可能被其他第三方又依赖于开发其产品的Microsoft产品”\)。  因此，如果您给Microsoft任何关于此文档的反馈或者Microsoft他们的应用的反馈，您授予：\(a\) Microsoft 可以随意使用，重现，允许，分销和其他商业化的产品中使用你的反馈；\(b\) 还授予第三方，没有费用，因此，只有那些必需的专利权使其他与将您的反馈Microsoft产品的任何特定部分的产品使用或接口；和 \(c\) 不会为Microsoft任何反馈 \(i\) 您具有基于认为是受所有专利、版权或任何第三方的其他知识产权声明或权限；或 \(ii\) 受许可条款查找需要任何Microsoft提供的合并或从这种反馈派生，或其他Microsoft知识产权。，授权或与任何第三方共享。|  
  
 使用 Team Foundation Build，本演练通过在命令行上执行 MSBuild练验以下操作系统。  
  
-   Windows 8（x86 和 x64）  
  
-   Windows 7 Ultimate  
  
-   Windows Server 2008 R2 Standard  
  
 在完成此演练后面的步骤中，可以使用多台计算机环境生成这些 apps:  
  
-   C\+\+ 使用 Windows 8 SDK 的桌面 apps  
  
-   Visual Basic 或 C\# 面向 .NET Framework 4.5 的桌面 apps  
  
 多台计算机环境不能用于生成这些 apps:  
  
-   [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]应用  若要生成 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] apps，在生成计算机上必须安装 Visual Studio。  
  
-   面向 .NET Framework 4 或更早版本的桌面 apps。  若要生成这些 apps，在生成计算机上必须安装 Visual Studio 或 .NET 引用程序集和工具 \(从 windows 7.1 SDK\)。  
  
 本演练分为以下几部分：  
  
-   [在计算机安装软件](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingSoftware)  
  
-   [从主机为生成计算机复制文件](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles)  
  
-   [创建注册表设置](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CreatingRegistry)  
  
-   [设置在生成计算机上的环境变量](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#SettingEnvVariables)  
  
-   [在目标计算机上的全局程序集缓存 (GAC) 中安装MSBuild程序集。](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingMSBuildToGAC)  
  
-   [生成项目](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#BuildingProjects)  
  
-   [创建生成环境，以便可以签入到源控件](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CreatingForSourceControl)  
  
## 系统必备  
  
-   Visual Studio 高级专业版、Visual Studio 旗舰版,Visual Studio 特别版或Visual Studio 专业测试工具版的许可复制。  
  
-   .NET Framework 4.5.1 的一个副本，可以从网站 [Visual Studio](http://www.microsoft.com/visualstudio/eng/downloads#d-additional-software) 下载。  
  
##  <a name="InstallingSoftware"></a> 在计算机安装软件  
 首先，设置主机然后将生成计算机。  
  
 通过在主机安装 Visual Studio ，您将文件和设置复制到生成计算机。  在 x86 或 x64 计算机上安装 Visual Studio，但是，生成计算机的结构必须与主机的体系结构。  
  
#### 在计算机上安装软件  
  
1.  在主机上安装 Visual Studio。  
  
2.  在生成计算机上，安装 .NET Framework 4.5。若要验证已安装，请确保已设置的注册表项 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\NET 结构的值\\NDP\\v4\\Full@Version 从“4.5 "开头。  
  
##  <a name="CopyingFiles"></a> 从主机为生成计算机复制文件  
 本节包括从主机为生成计算机复制特定文件、编译器、生成工具、MSBuild 属性和注册表设置。  这些说明假定，则在默认位置安装了 Visual Studio 主计算机上；如果您在其他位置安装，请相应地调整步骤。  
  
-   在 x86 计算机上，默认位置为 c:\\program files\\microsoft Visual Studio 11.0\\  
  
-   在 x64 计算机上，默认位置为 C:\\Program Files \(x86\)\\Microsoft Visual Studio 11.0\\  
  
 注意程序文件夹的名字取决于所安装的操作系统。  在 x86 计算机上，该名称为\\program files\\;在 x64 计算机，名称为\\program files \(x86\)\\。  不考虑系统体系结构，本演练引用 program files 文件夹为 %ProgramFiles%。  
  
> [!NOTE]
>  在生成计算机上，所有相关文件必须位于同一驱动器；但是，该驱动程序的盘符与 Visual Studio 在主机计算机上安装的驱动程序的盘符可能不同。  无论任何情况，当您根据描述本文档后面部分创建注册表项时必须考虑文件的位置。  
  
#### 为生成计算机复制 Windows SDK 文件  
  
1.  如果您安装了 Windows 8 的Windows SDK，请从主机为生成计算机递归复制这些文件夹：  
  
    -   %ProgramFiles%\\窗口工具中\\8.0\\bin\\  
  
    -   %ProgramFiles%\\窗口工具中\\8.0\\目录  
  
    -   %ProgramFiles%\\窗口工具中\\8.0\\DesignTime\\  
  
    -   %ProgramFiles%\\窗口工具中\\8.0\\include\\  
  
    -   %ProgramFiles%\\窗口工具中\\8.0\\Lib\\  
  
    -   %ProgramFiles%\\窗口工具中\\8.0\\Redist\\  
  
    -   %ProgramFiles%\\窗口工具中\\8.0\\References\\  
  
     如果还有这些其他 Windows 8 工具框…  
  
    -   Microsoft Windows 评估和部署工具Kit  
  
    -   Microsoft Windows 驱动程序工具  
  
    -   Microsoft Windows 硬件身份验证工具集  
  
     …它们可能已经安装了文件到上一步中列出的 %ProgramFiles%\\窗口工具中\\8.0\\ 文件夹，并且，它们的许可条款可能不允许这些文件的生成服务器。  该许可证命名为每个安装的窗口工具中可以验证的选定文件是否能复制到您的生成计算机。  如果许可条款不允许生成服务器权限，则在生成计算机上删除该文件。  
  
2.  从主机为生成计算机递归复制以下文件夹：  
  
    -   %ProgramFiles%\\microsoft SDKs\\windows\\v8.0A\\bin\\NETFX 4.0 tools\\  
  
    -   %ProgramFiles%\\common files\\merge modules\\  
  
    -   %ProgramFiles%\\Microsoft Visual Studio11.0\\ VC\\  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\tools\\ProjectComponents\\  
  
    -   :\\Program Files\\MSBuild\\Microsoft.Cpp\\v4.0\\\\  
  
    -   %ProgramFiles%\\Reference Assemblies\\Microsoft\\Framework\\.NETCore\\v4.5\\  
  
    -   %ProgramFiles%\\Reference Assemblies\\Microsoft\\Framework\\.NETFramework\\v4.5\\  
  
3.  从主机为生成计算机复制文件：  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\msobj110.dll  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\mspdb110.dll  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\mspdb110.dll  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\mspdbsrv.exe  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\msvcdis110.dll  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\Tools\\makehm.exe  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\tools\\VCVarsQueryRegistry.bat  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\tools\\vsvars32.bat  
  
4.  下面的 Visual C\+\+ 运行库是必须的，只要当您运行在生成输出计算机生成输出时—例如,作为自动测试的一部分。  文件通常位于 %ProgramFiles%\\Microsoft Visual Studio 11.0\\VC\\redist\\x86 或\\%ProgramFiles%\\Microsoft Visual Studio 11.0\\VC\\redist\\x64\\文件夹下的子文件夹，根据系统体系结构。  在 x86 系统中，复制 x86 二进制文件放入\\windows\\System32\\文件夹。  在 x64 系统中，复制 x86 二进制文件放入 windows\\SysWOW64\\文件夹和 x64 二进制文件放入 windows\\System32\\文件夹。  
  
    -   \\Microsoft.VC110.ATL\\atl110.dll  
  
    -   \\Microsoft.VC110.CRT\\msvcp110.dll  
  
    -   \\Microsoft.VC110.CRT\\msvcr110.dll  
  
    -   \\Microsoft.VC110.CXXAMP\\vcamp110.dll  
  
    -   \\Microsoft.VC110.MFC\\mfc110.dll  
  
    -   \\Microsoft.VC110.MFC\\mfc110u.dll  
  
    -   \\Microsoft.VC110.MFC\\mfcm110.dll  
  
    -   \\Microsoft.VC110.MFC\\mfcm110u.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110chs.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110cht.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110deu.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110enu.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110deu.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110deu.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110ita.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110jpn.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110kor.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110rus.dll  
  
    -   \\Microsoft.VC110.OPENMP\\vcomp110.dll  
  
5.  仅仅复制\\Debug\_NonRedist\\x86\\或\\Debug\_NonRedist\\x64\\文件夹中的以下文件到生成计算机，如 [准备用于运行调试可执行文件的测试计算机](/visual-cpp/ide/preparing-a-test-machine-to-run-a-debug-executable)所述。  其他文件可能不复制。  
  
    -   \\Microsoft.VC110.DebugCRT\\msvcp110d.dll  
  
    -   \\Microsoft.VC110.DebugCRT\\msvcr110d.dll  
  
    -   \\Microsoft.VC110.DebugCXXAMP\\vcamp110d.dll  
  
    -   \\Microsoft.VC110.DebugMFC\\mfc110d.dll  
  
    -   \\Microsoft.VC110.DebugMFC\\mfc110ud.dll  
  
    -   \\Microsoft.VC110.DebugMFC\\mfcm110d.dll  
  
    -   \\Microsoft.VC110.DebugMFC\\mfcm110ud.dll  
  
    -   \\Microsoft.VC110.DebugOpenMP\\vcomp110d.dll  
  
##  <a name="CreatingRegistry"></a> 创建注册表设置  
 必须创建注册表项配置 MSBuild 的设置。  
  
#### 创建注册表项设置  
  
1.  标识注册表项的父文件夹。  所有注册表项是在同一父项下。  在 x86 计算机上，父键是 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.  在 x64 计算机上，父键是 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\.  不考虑系统体系结构，本演练作为 %RegistryRoot%引用父键  
  
    > [!NOTE]
    >  如果您的主机体系结构与您的生成计算机不同，确保在每台计算机上使用适当父键。  如果您自动导出过程，这一点尤其重要。  
    >   
    >  然后，因此，如果比将使用在生成计算机上的不同盘符在主机使用，请确保更改注册表项的值才能匹配。  
  
2.  在生成计算机上创建下列的注册表项。  所有这些项是字符串类型 \(在注册表Type\=\=“REG\_SZ”\)。  在主机上设置这些与可比较的项相同的值项的值。  
  
    -   %RegistryRoot%\\.NETFramework\\v4.0.30319\\AssemblyFoldersEx\\VCMSBuild 公共 Assemblies@ \(默认值\)  
  
    -   %RegistryRoot%\\microsoft SDKs\\windows\\v8.0@InstallationFolder  
  
    -   %RegistryRoot%\\microsoft SDKs\\windows\\v8.0A@InstallationFolder  
  
    -   %RegistryRoot%\\microsoft SDKs\\windows\\v8.0A\\WinSDK\-NetFx40Tools@InstallationFolder  
  
    -   %RegistryRoot%\\microsoft SDKs\\windows\\v8.0A\\WinSDK\-NetFx40Tools\-x86@InstallationFolder  
  
    -   %RegistryRoot%\\VisualStudio\\11.0@SourceDirectories  
  
    -   %RegistryRoot%\\VisualStudio\\11.0\\setup\\VC@ProductDir  
  
    -   %RegistryRoot%\\VisualStudio\\SxS\\VC7@FrameworkDir32  
  
    -   %RegistryRoot%\\VisualStudio\\SxS\\VC7@FrameworkDir64  
  
    -   %RegistryRoot%\\VisualStudio\\SxS\\VC7@FrameworkDir32  
  
    -   %RegistryRoot%\\VisualStudio\\SxS\\VC7@FrameworkDir64  
  
    -   %RegistryRoot%\\VisualStudio\\SxS\\VC7@11.0  
  
    -   %RegistryRoot%\\VisualStudio\\SxS\\VS7@11.0  
  
    -   %RegistryRoot%\\windows\\工具中安装的 Roots@KitsRoot  
  
    -   %RegistryRoot%\\MSBuild\\ToolsVersions\\4.0\\11.0@VCTargetsPath  
  
    -   %RegistryRoot%\\MSBuild\\ToolsVersions\\4.0\\11.0@VCTargetsPath10  
  
    -   %RegistryRoot%\\MSBuild\\ToolsVersions\\4.0\\11.0@VCTargetsPath11  
  
     在 x64 生成计算机上，也创建以下注册表项和参见主机确定如何设置。  
  
    -   %RegistryRoot%\\microsoft SDKs\\windows\\v8.0A\\WinSDK\-NetFx40Tools\-x64@InstallationFolder  
  
     如果您的生成计算机是 x64，并且希望使用 MSBuild 64 位版本，或者，如果在 x64 计算机上的生成服务您使用的是 Team Foundation Server，可以在本下注册表项。  请参见主机确定如何设置这些项。  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\11.0\\Setup\\VS@ProductDir  
  
    -   \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSBuild\\ToolsVersions\\4.0\\11.0@VCTargetsPath  
  
    -   \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSBuild\\ToolsVersions\\4.0\\11.0@VCTargetsPath10  
  
    -   \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSBuild\\ToolsVersions\\4.0\\11.0@VCTargetsPath11  
  
##  <a name="SettingEnvVariables"></a> 设置在生成计算机上的环境变量  
 若要在生成计算机上使用 MSBuild,必须设置ATH 环境变量。  可以使用 vcvarsall.bat 设置变量，也可以手动配置它们。  
  
#### 使用 vcvarsall.bat 设置环境变量  
  
-   打开在生成计算机上的一个命令提示符窗口并运行 %Program Files%\\Microsoft Visual Studio 11.0\\VC\\vcvarsall.bat。  可以使用命令行参数指定要使用 x86 的工具集，本机 x64 或 x64 交叉编译。  如果不指定命令行参数，使用 x86 工具集。  
  
     下表显示 vcvarsall.bat 支持的参数。  
  
    |Vcvarsall.bat 参数|编译器|生成计算机体系结构|生成输出体系结构|  
    |----------------------|---------|---------------|--------------|  
    |x86（默认）|32 位本机编译器|x86，x64|x86|  
    |x86\_amd64|x64 兼容|x86，x64|x64|  
    |amd64|x64 本机|x64|x64|  
  
     如果 vcvarsall.bat 运行成功，错误消息不是显示—您可以跳过下一个步骤，并继续在此的 [在目标计算机上的全局程序集缓存 (GAC) 中安装MSBuild程序集。](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingMSBuildToGAC) 部分文档。  
  
#### 手动设置环境变量  
  
1.  手动配置命令行环境，请将此路径到 PATH 环境变量：  
  
    -   %Program Files%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\。  
  
2.  或者，还可以添加以下路径变量便于使用 MSBuild 生成解决方案。  
  
     如果要使用本机 32 位 MSBuild，请添加这些路径到路径变量：  
  
    -   %Program Files%\\microsoft SDKs\\windows\\v8.0A\\bin\\NETFX 4.0Tools  
  
    -   %windir%\\Microsoft.NET\\Framework\\v4.0.30319  
  
     如果要使用本机 64 位 MSBuild，请添加这些路径到路径变量：  
  
    -   %Program Files%\\microsoft SDKs\\windows\\v8.0A\\bin\\NETFX 4.0Tools\\x64  
  
    -   %windir%\\Microsoft.NET\\Framework64\\v4.0.30319  
  
##  <a name="InstallingMSBuildToGAC"></a> 在目标计算机上的全局程序集缓存 \(GAC\) 中安装MSBuild程序集。  
 MSBuild 需要执行一些附加程序集安装到生成计算机中的GAC 。  
  
#### 从主机复制程序集并在生成计算机上安装他们。  
  
1.  从主机为生成计算机递归复制以下文件夹：  由于他们将被安装到 GAC，在生成计算机是否放入他们并不重要。  
  
    -   %ProgramFiles%\\MSBuild\\Microsoft.Cpp\\v4.0\\v110\\Microsoft.Build.CPPTasks.Common.v110.dll  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\CommonExtensions\\microsoft\\VC\\projects\\Microsoft.VisualStudio.Project.VisualC.VCProjectEngine.dll  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\PublicAssemblies\\Microsoft.VisualStudio.VCProjectEngine.dll  
  
2.  若要将程序集安装到 GAC 中，找到 gacutil.exe 计算机典型的生成，它在 %ProgramFiles%\\microsoft SDKs\\windows\\v8.0A\\bin\\NETFX 4.0 tools\\。  如果无法找到此文件夹，请重复本演练中的 [从主机为生成计算机复制文件](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles) 节中的步骤。  
  
     打开具有管理权限的命令提示符窗口并运行每个文件的以下命令：  
  
     **gacutil \-i \<file\>**  
  
    > [!NOTE]
    >  完全安装程序集到 GAC 中可能需要重新启动硬盘。  
  
##  <a name="BuildingProjects"></a> 生成项目  
 可以使用 Team Foundation Build 生成 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 项目和解决方案，也可以在命令行生成它们。  当您使用 Team Foundation Build 生成项目时，将调用对应于系统体系结构可执行的 MSBuild。在命令行上，可以使用 MSBuild 32 位或 64 位 MSBuild，因此，您可以选择通过将 PATH 环境变量或通过直接调用可执行文件结构的具体的 MSBuild MSBuild 体系结构。  
  
 若要在命令提示处使用 msbuild.exe ，运行以下命令，*solution.sln* 是您的解决方案的名称的占位符。  
  
 **msbuild** *solution.sln*  
  
 有关如何在命令行使用MSBuild 的更多信息，请参见[命令行参考](../msbuild/msbuild-command-line-reference.md)。  
  
> [!NOTE]
>  若要生成 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 项目，则必须使用“v110”平台工具集。  如果您不要编辑 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 项目文件，可以使用此命令行参数来设置平台工具集：  
>   
>  **msbuild** *solution.sln* **\/p:PlatformToolset\=v110**  
  
##  <a name="CreatingForSourceControl"></a> 创建生成环境，以便可以签入到源控件  
 可以在不同计算机上部署创建生成计算机环境，并且不需要 GAC文件或者修改注册表设置。  以下步骤是一种方式来实现此目的。  采用这些步骤是您的生成环境的唯一特征。  
  
> [!NOTE]
>  必须禁用持续地建立，以便 tracker.exe 不会引发错误。  若要禁用增量生成，请设置此生成参数：  
>   
>  **msbuild** *solution.sln* **\/p:TrackFileAccess\=false**  
  
#### 创建可签入到源控件的生成环境  
  
1.  创建主计算机上的“维护站”目录。  
  
     这些步骤是指作为 %Depot%的内容  
  
2.  [从主机为生成计算机复制文件](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles) 节中所述复制目录和文件，并将其粘贴到您创建的 %Depot% 目录下。  例如，请复制 %ProgramFiles%\\窗口工具中\\8.0\\bin\\到 %Depot%\\窗口工具中\\8.0\\bin\\。  
  
3.  当文件位于 %Depot% 中粘贴，请进行这些更改：  
  
    -   在 %Depot%\\MSBuild\\Microsoft.Cpp\\v4.0\\v110\\Microsoft.CPP.Targets，\\Microsoft.Cpp.InvalidPlatforms.targets\\，\\Microsoft.cppbuild.targets\\，和 \\Microsoft.CppCommon.targets\\，改变每个实例  
  
         AssemblyName\= " Microsoft.Build.CppTasks.Common.v110，Version\= 4.0.0.0，Culture\=neutral，PublicKeyToken\=b03f5f7f11d50a3a”  
  
         设置为  
  
         AssemblyFile\= " $ \(VCTargetsPath11\) Microsoft.Build.CppTasks.Common.v110.dll”。  
  
         前命名文件在程序集成为GAC'ed。  
  
    -   在 %Depot% \\MSBuild\\Microsoft.Cpp\\v4.0\\v110\\Microsoft.CPPClean.Targets，改变每一个实例  
  
         AssemblyName\= " Microsoft.Build.CppTasks.Common.v110，Version\= 4.0.0.0，Culture\=neutral，PublicKeyToken\=b03f5f7f11d50a3a”  
  
         设置为  
  
         AssemblyFile\= " $ \(VCTargetsPath11\) Microsoft.Build.CppTasks.Common.v110.dll”。  
  
4.  创建 .props 文件 \(例如，Partner.AutoImports.props— 并将其置于包含项目文件夹的根目录。  此文件用于设置 MSBuild 用于查找各种资源的变量。  如果变量不受此文件设置，它们都依赖于注册表值的其他文件由 .props 和 .targets 文件设置。  由于我们不设置任何注册表值，这些变量为空，并生成将失败。  相反，请添加到 Partner.AutoImports.props:  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <!-- This file must be imported by all project files at the top of the project file. -->  
    <Project ToolsVersion="4.0"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
    <VCTargetsPath>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath>  
    <VCTargetsPath11>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath11>  
    <MSBuildExtensionsPath>$(DepotRoot)MSBuild</MSBuildExtensionsPath>  
    <MSBuildExtensionsPath32>$(DepotRoot)MSBuild</MSBuildExtensionsPath32>  
    <VCInstallDir_110>$(DepotRoot)Microsoft Visual Studio 11.0\VC\</VCInstallDir_110>  
    <VCInstallDir>$(VCInstallDir_110)</VCInstallDir>  
    <WindowsKitRoot>$(DepotRoot)Windows Kits\</WindowsKitRoot>  
    <WindowsSDK80Path>$(WindowsKitRoot)</WindowsSDK80Path>  
    <WindowsSdkDir_80>$(WindowsKitRoot)8.0\</WindowsSdkDir_80>  
    <WindowsSdkDir>$(WindowsSDKDir_80)</WindowsSdkDir>  
    <WindowsSdkDir_80A>$(DepotRoot)Microsoft SDKs\Windows\v8.0A\</WindowsSdkDir_80A>  
    </PropertyGroup>  
    </Project>  
    ```  
  
5.  在每一个项目文件，在顶层将添加以下行为，在 `<Project Default Targets…>` 行后面。  
  
    ```  
    <Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), Partner.AutoImports.props))\Partner.AutoImports.props"/>  
    ```  
  
6.  更改命令行环境如下所示：  
  
    -   设置 Depot\=*location of the Depot directory that you created in step 1*  
  
    -   设置 path\=%path%;*location of MSBuild on the computer*; %Depot%\\windows\\System32; %Depot%\\windows\\SysWOW64; %Depot%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\  
  
         对于本机 64 位生成，请指向 64 位 MSBuild。  
  
## 请参阅  
 [准备用于运行调试可执行文件的测试计算机](/visual-cpp/ide/preparing-a-test-machine-to-run-a-debug-executable)   
 [命令行参考](../msbuild/msbuild-command-line-reference.md)