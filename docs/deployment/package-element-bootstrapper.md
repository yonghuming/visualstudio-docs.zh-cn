---
title: "&lt;Package&gt; 元素（引导程序） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<package> 元素 [引导程序]"
ms.assetid: ecd06658-ad02-4440-bccd-88437b7fb816
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# &lt;Package&gt; 元素（引导程序）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`Package` 元素是包文件内的顶级 XML 元素。  
  
## 语法  
  
```  
<Package  
    Culture  
    Name  
    LicenseAgreement  
>  
    <InstallChecks>  
        <AssemblyCheck   
            Property  
            Name  
            PublicKeyToken  
            Version  
            Language  
            ProcessorArchitecture  
        />  
        <RegistryCheck  
            Property  
            Key  
            Value  
        />  
        <ExternalCheck   
            PackageFile  
            Property  
            Arguments  
            Log  
        />  
        <FileCheck   
            Property  
            FileName  
            SearchPath  
            SpecialFolder  
            SearchDepth  
        />  
        <MsiProductCheck   
            Property  
            Product  
            Feature  
        />  
        <RegistryFileCheck   
            Property  
            Key  
            Value  
            File  
            SearchDepth  
        />  
    </InstallChecks>  
  
    <Commands  
        Reboot  
    >  
        <Command  
            PackageFile  
            Arguments  
            EstimatedInstallSeconds  
            EstimatedDiskBytes  
            EstimatedTempBytes  
            Log  
        >  
            <InstallConditions>  
                <BypassIf   
                    Property  
                    Compare  
                    Value  
                    Schedule  
                />  
                <FailIf   
                    Property  
                    Compare  
                    Value  
                    String  
                    Schedule  
                />  
            </InstallConditions>  
            <ExitCodes>  
                <ExitCode   
                    Value  
                    Result  
                    String  
                />  
            </ExitCodes>  
        </Command>  
    </Commands>  
  
    <PackageFiles  
        CopyAllComponents  
    >  
        <PackageFile   
            Name  
            Path  
            HomeSite  
            PublicKey  
        />  
    </PackageFiles>  
  
    <Strings>  
        <String  
            Name  
        >  
        </String>  
    </Strings>  
  
    <Schedules>  
        <Schedule  
            Name  
        >  
           <BuildList />  
           <BeforePackage />  
           <AfterPackage />  
        </Schedule>  
    </Schedules>  
</Package>  
```  
  
## 元素和特性  
 `Package` 元素是必需的。  它具有以下特性：  
  
|特性|说明|  
|--------|--------|  
|`Culture`|必选。  定义此包的区域性，以确定要使用的语言。  此特性是 `Strings` 元素中的一个项，该元素为安装期间的产品名称和错误信息列出了区域性特定的字符串。|  
|`Name`|必选。  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 等工具中显示给开发人员的包名称。  此特性是 `Strings` 元素中的一个项，该元素应包含 `Name` 和 `Culture` 属性设置为与 `Package` 的 `Name` 和 `Culture` 属性匹配的 `String` 元素。|  
|`LicenseAgreement`|可选。  指定分发包中包含最终用户许可协议 \(EULA\) 的文件的名称。  此文件可以是纯文本格式 \(.txt\)，也可以是 RTF 格式。  \(.rtf\)|  
  
## 示例  
 下面的代码示例演示用于再发行 [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] 的完整包文件。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
  
<Package  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  Name="DisplayName"  
  Culture="Culture"  
  LicenseAgreement="eula.rtf"  
>  
  
    <PackageFiles>  
        <PackageFile Name="eula.rtf"/>  
    </PackageFiles>  
  
    <!-- Defines a localizable string table for error messages-->  
    <Strings>  
        <String Name="DisplayName">.NET Framework 2.0</String>  
        <String Name="Culture">en</String>  
        <String Name="AdminRequired">Administrator permissions are required to install the .NET Framework 2.0. Contact your administrator.</String>  
        <String Name="InvalidPlatformWin9x">Installation of the .NET Framework 2.0 is not supported on Windows 95. Contact your application vendor.</String>  
        <String Name="InvalidPlatformWinNT">Installation of the .NET Framework 2.0 is not supported on Windows NT 4.0. Contact your application vendor.</String>  
        <String Name="InvalidPlatformIE">Installation of the .NET Framework 2.0 requires Internet Explorer 5.01 or greater. Contact your application vendor.</String>  
        <String Name="InvalidPlatformArchitecture">This version of the .NET Framework 2.0 is not supported on a 64-bit operating system. Contact your application vendor.</String>  
        <String Name="WindowsInstallerImproperInstall">Due to an error with Windows Installer, the installation of the .NET Framework 2.0 cannot proceed.</String>  
        <String Name="AnotherInstanceRunning">Another instance of setup is already running. The running instance must complete before this setup can proceed.</String>  
        <String Name="BetaNDPFailure">A beta version of the .NET Framework was detected on the computer. Uninstall any previous beta versions of .NET Framework before continuing.</String>  
        <String Name="GeneralFailure">A failure occurred attempting to install the .NET Framework 2.0.</String>  
        <String Name="DotNetFXExe">http://go.microsoft.com/fwlink/?LinkId=37283</String>  
        <String Name="InstMsiAExe">http://go.microsoft.com/fwlink/?LinkId=37285</String>  
        <String Name="Msi30Exe">http://go.microsoft.com/fwlink/?LinkId=37287</String>  
    </Strings>  
  
</Package>  
```  
  
## 请参阅  
 [产品和包架构引用](../deployment/product-and-package-schema-reference.md)