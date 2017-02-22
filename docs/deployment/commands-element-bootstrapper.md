---
title: "&lt;Commands&gt; 元素（引导程序） | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
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
  - "<Commands> 元素 [引导程序]"
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;Commands&gt; 元素（引导程序）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`Commands` 元素实现 `InstallChecks` 元素下的元素描述的测试，并声明当测试失败时，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 引导程序应安装的包。  
  
## 语法  
  
```  
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
```  
  
## 元素和特性  
 `Commands` 元素是必需的。  该元素具有以下特性。  
  
|特性|说明|  
|--------|--------|  
|`Reboot`|可选。  确定如果有任意包返回重新启动退出代码，系统是否应重新启动。  下面的列表显示有效的值：<br /><br /> `Defer`。  重新启动推迟到将来的某个时间执行。<br /><br /> `Immediate`。  如果其中一个包返回重新启动退出代码，将立即重新启动。<br /><br /> `None`。  忽略任何重新启动请求。<br /><br /> 默认值为 `Immediate`。|  
  
## Command  
 `Command` 元素是 `Commands` 元素的子元素。  `Commands` 元素可以有一个或多个 `Command` 元素。  它具有下列特性。  
  
|特性|说明|  
|--------|--------|  
|`PackageFile`|必选。  当 `InstallConditions` 指定的一个或多个条件返回 false 时，要安装的包的名称。  必须使用 `PackageFile` 元素在同一个文件中定义该包。|  
|`Arguments`|可选。  要传入包文件的一组命令行参数。|  
|`EstimatedInstallSeconds`|可选。  估计安装该包将花费的时间（以秒为单位）。  该值决定了引导程序显示给用户的进度栏的大小。  默认值为 0，在这种情况下将不会指定估计的时间。|  
|`EstimatedDiskBytes`|可选。  估计该包在安装完成后将占用的磁盘空间量（以字节为单位）。  该值用在引导程序显示给用户的硬盘空间要求中。  默认值为 0，在这种情况下，引导程序将不会显示任何硬盘空间要求。|  
|`EstimatedTempBytes`|可选。  估计该包需要的临时磁盘空间量（以字节为单位）。|  
|`Log`|可选。  该包生成的日志文件的路径，该路径是相对于包的根目录而言的。|  
  
## InstallConditions  
 `InstallConditions` 元素是 `Command` 元素的子元素。  每个 `Command` 元素最多只能有一个 `InstallConditions` 元素。  如果不存在任何 `InstallConditions` 元素，则 `Condition` 指定的包将始终运行。  
  
## BypassIf  
 `BypassIf` 元素是 `InstallConditions` 元素的子元素，它描述了一个肯定的条件，在这个条件下不应执行该命令。  每个 `InstallConditions` 元素可以有零个或零个以上的 `BypassIf` 元素。  
  
 `BypassIf` 具有下列特性。  
  
|特性|说明|  
|--------|--------|  
|`Property`|必选。  要测试的属性的名称。  该属性必须事先已经由 `InstallChecks` 元素的子元素定义。  有关更多信息，请参见 [\<InstallChecks\> 元素](../deployment/installchecks-element-bootstrapper.md)。|  
|`Compare`|必选。  要执行的比较的类型。  下面的列表显示有效的值：<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|必选。  要与该属性进行比较的值。|  
|`Schedule`|可选。  `Schedule` 标记的名称，该标记定义何时计算此规则。|  
  
## FailIf  
 `FailIf` 元素是 `InstallConditions` 元素的子元素，它描述了一个肯定的条件，在这个条件下安装应停止。  每个 `InstallConditions` 元素可以有零个或零个以上的 `FailIf` 元素。  
  
 `FailIf` 具有下列特性。  
  
|特性|说明|  
|--------|--------|  
|`Property`|必选。  要测试的属性的名称。  该属性必须事先已经由 `InstallChecks` 元素的子元素定义。  有关更多信息，请参见 [\<InstallChecks\> 元素](../deployment/installchecks-element-bootstrapper.md)。|  
|`Compare`|必选。  要执行的比较的类型。  下面的列表显示有效的值：<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|必选。  要与该属性进行比较的值。|  
|`String`|可选。  失败后要显示给用户的文本。|  
|`Schedule`|可选。  `Schedule` 标记的名称，该标记定义何时计算此规则。|  
  
## ExitCodes  
 `ExitCodes` 元素是 `Command` 元素的子元素。  `ExitCodes` 元素包含一个或多个 `ExitCode` 元素，该元素确定安装应执行何种操作来响应来自包的退出代码。  `Command` 元素下可以有一个可选的 `ExitCode` 元素。  `ExitCodes` 没有特性。  
  
## ExitCode  
 `ExitCode` 元素是 `ExitCodes` 元素的子元素。  `ExitCode` 元素确定安装应执行何种操作来响应来自包的退出代码。  `ExitCode` 不包含任何子元素，且具有下列特性。  
  
|特性|说明|  
|--------|--------|  
|`Value`|必选。  此 `ExitCode` 元素适用的退出代码值。|  
|`Result`|必选。  安装应如何响应此退出代码。  下面的列表显示有效的值：<br /><br /> `Success`。  将该包标记为已成功安装。<br /><br /> `SuccessReboot`。  将该包标记为已成功安装，并指示系统重新启动。<br /><br /> `Fail`。  将该包标记为失败。<br /><br /> `FailReboot`。  将该包标记为失败，并指示系统重新启动。|  
|`String`|可选。  为响应此退出代码而显示给用户的值。|  
|`FormatMessageFromSystem`|可选。  确定是使用系统提供的、对应于退出代码的错误消息，还是使用 `String` 中提供的值。  有效值为 `true` 和 `false`，前者表示使用系统提供的错误，后者表示使用 `String` 提供的字符串。  默认值为 `false`。  如果此属性为 `false`，但是未设置 `String`，则将会使用系统提供的错误。|  
  
## 示例  
 下面的代码示例定义了用于安装 .NET Framework 2.0 的命令。  
  
```  
<Commands Reboot="Immediate">  
    <Command PackageFile="instmsia.exe"  
             Arguments= ' /q /c:"msiinst /delayrebootq"'  
             EstimatedInstallSeconds="20" >  
        <InstallConditions>  
           <BypassIf Property="VersionNT" Compare="ValueExists"/>  
             BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="2.0"/>  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode Value="0" Result="SuccessReboot"/>  
            <ExitCode Value="1641" Result="SuccessReboot"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
    </Command>  
    <Command PackageFile="WindowsInstaller-KB884016-v2-x86.exe"  
             Arguments= '/quiet /norestart'   
             EstimatedInstallSeconds="20" >  
      <InstallConditions>  
          <BypassIf Property="Version9x" Compare="ValueExists"/>  
          <BypassIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3"/>  
          <BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="3.0"/>  
          <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
      </InstallConditions>  
      <ExitCodes>  
          <ExitCode Value="0" Result="Success"/>  
          <ExitCode Value="1641" Result="SuccessReboot"/>  
          <ExitCode Value="3010" Result="SuccessReboot"/>  
          <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
      </ExitCodes>  
    </Command>  
    <Command PackageFile="dotnetfx.exe"   
         Arguments=' /q:a /c:"install /q /l"'   
         EstimatedInstalledBytes="21000000"   
         EstimatedInstallSeconds="300">  
  
        <!-- These checks determine whether the package is to be installed -->  
        <InstallConditions>  
            <!-- Either of these properties indicates the .NET Framework is already installed -->  
            <BypassIf Property="DotNetInstalled" Compare="ValueNotEqualTo" Value="0"/>  
  
            <!-- Block install if user does not have adminpermissions -->  
            <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
  
            <!-- Block install on Windows 95 -->  
            <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatformWin9x"/>  
  
            <!-- Block install on Windows 2000 SP 2 or less -->  
            <FailIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3" String="InvalidPlatformWinNT"/>  
  
            <!-- Block install if Internet Explorer 5.01 or later is not present -->  
            <FailIf Property="IEVersion" Compare="ValueNotExists" String="InvalidPlatformIE" />  
            <FailIf Property="IEVersion" Compare="VersionLessThan" Value="5.01" String="InvalidPlatformIE" />  
  
            <!-- Block install if the operating system does not support x86 -->  
            <FailIf Property="ProcessorArchitecture" Compare="ValueNotEqualTo" Value="Intel" String="InvalidPlatformArchitecture" />  
       </InstallConditions>  
  
        <ExitCodes>  
            <ExitCode Value="0" Result="Success"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <ExitCode Value="4097" Result="Fail" String="AdminRequired"/>  
            <ExitCode Value="4098" Result="Fail" String="WindowsInstallerComponentFailure"/>  
            <ExitCode Value="4099" Result="Fail" String="WindowsInstallerImproperInstall"/>  
            <ExitCode Value="4101" Result="Fail" String="AnotherInstanceRunning"/>  
            <ExitCode Value="4102" Result="Fail" String="OpenDatabaseFailure"/>  
            <ExitCode Value="4113" Result="Fail" String="BetaNDPFailure"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
  
    </Command>  
</Commands>  
```  
  
## 请参阅  
 [产品和包架构引用](../deployment/product-and-package-schema-reference.md)   
 [\<InstallChecks\> 元素](../deployment/installchecks-element-bootstrapper.md)