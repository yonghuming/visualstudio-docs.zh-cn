---
title: "&lt;InstallChecks&gt; 元素（引导程序） | Microsoft Docs"
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
  - "<InstallChecks> 元素 [引导程序]"
ms.assetid: ad329c87-b0ad-4304-84de-ae9496514c42
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 23
---
# &lt;InstallChecks&gt; 元素（引导程序）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`InstallChecks` 元素支持对本地计算机进行多种测试，以确保已经为应用程序安装了所有适当的必备组件。  
  
## 语法  
  
```  
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
        FileName  
        SearchDepth  
    />  
</InstallChecks>  
```  
  
## AssemblyCheck  
 此元素是 `InstallChecks` 的可选子元素。  对于 `AssemblyCheck` 的每个实例，引导程序都将确保该元素标识的程序集存在于全局程序集缓存 \(GAC\) 中。  它不包含任何元素，但具有下列特性。  
  
|特性|说明|  
|--------|--------|  
|`Property`|必选。  用于存储结果的属性的名称。  可以从 `InstallConditions` 元素下的测试引用此属性，该元素是 `Command` 元素的子元素。  有关更多信息，请参见 [\<Commands\> 元素](../deployment/commands-element-bootstrapper.md)。|  
|`Name`|必选。  要检查的程序集的完全限定名。|  
|`PublicKeyToken`|必选。  与此强名称程序集关联的公钥的缩写形式。  存储在 GAC 中的所有程序集都必须具有名称、版本和公钥。|  
|`Version`|必选。  程序集的版本。<br /><br /> 版本号的格式为：\<*主版本*\>.\<*次版本*\>.\<*内部版本*\>.\<*修订版本*\>。|  
|`Language`|可选。  本地化程序集的语言。  默认值为 `neutral`。|  
|`ProcessorArchitecture`|可选。  此安装的目标计算机处理器。  默认值为 `msil`。|  
  
## ExternalCheck  
 此元素是 `InstallChecks` 的可选子元素。  对于 `ExternalCheck` 的每个实例，引导程序都将在单独的进程中执行指定的外部程序，并将其退出代码存储在 `Property` 所指示的属性中。  `ExternalCheck` 在下列情况下非常有用：当要实现复杂的依赖项检查时，或者当检查组件是否存在的唯一方法是对其进行实例化时。  
  
 `ExternalCheck` 不包含任何元素，但具有下列特性。  
  
|特性|说明|  
|--------|--------|  
|`Property`|必选。  用于存储结果的属性的名称。  可以从 `InstallConditions` 元素下的测试引用此属性，该元素是 `Command` 元素的子元素。  有关更多信息，请参见 [\<Commands\> 元素](../deployment/commands-element-bootstrapper.md)。|  
|`PackageFile`|必选。  要执行的外部程序。  该程序必须是安装程序分发包的一部分。|  
|`Arguments`|可选。  为 `PackageFile` 指定的可执行文件提供命令行参数。|  
  
## FileCheck  
 此元素是 `InstallChecks` 的可选子元素。  对于 `FileCheck` 的每个实例，引导程序都将确定指定的文件是否存在，并返回该文件的版本号。  如果文件没有版本号，则引导程序会将 `Property` 指定的属性设置为 0。  如果文件不存在，则 `Property` 不会设置为任何值。  
  
 `FileCheck` 不包含任何元素，但具有下列特性。  
  
|特性|说明|  
|--------|--------|  
|`Property`|必选。  用于存储结果的属性的名称。  可以从 `InstallConditions` 元素下的测试引用此属性，该元素是 `Command` 元素的子元素。  有关更多信息，请参见 [\<Commands\> 元素](../deployment/commands-element-bootstrapper.md)。|  
|`FileName`|必选。  要查找的文件的名称。|  
|`SearchPath`|必选。  文件的查找位置（磁盘或文件夹）。  如果分配了 `SpecialFolder`，则此位置必须是相对路径；否则，必须是绝对路径。|  
|`SpecialFolder`|可选。  对 Windows 或 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 具有特殊意义的文件夹。  默认情况下将 `SearchPath` 解释为绝对路径。  有效值包括：<br /><br /> `AppDataFolder`。  此 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序的应用程序数据文件夹；特定于当前用户。<br /><br /> `CommonAppDataFolder`。  供所有用户使用的应用程序数据文件夹。<br /><br /> `CommonFilesFolder`。  当前用户的 Common Files 文件夹。<br /><br /> `LocalDataAppFolder`。  非漫游应用程序的数据文件夹。<br /><br /> `ProgramFilesFolder`。  32 位应用程序的标准 Program Files 文件夹。<br /><br /> `StartUpFolder`。  包含系统启动时启动的所有应用程序的文件夹。<br /><br /> `SystemFolder`。  包含 32 位系统 DLL 的文件夹。<br /><br /> `WindowsFolder`。  包含 Windows 系统安装的文件夹。<br /><br /> `WindowsVolume`。  包含 Windows 系统安装的驱动器或分区。|  
|`SearchDepth`|可选。  在子文件夹中搜索指定文件时可达到的深度。  该搜索为深度优先。  默认值为 0，这会将搜索范围限定为 `SpecialFolder` 和 **SearchPath** 指定的顶级文件夹。|  
  
## MsiProductCheck  
 此元素是 `InstallChecks` 的可选子元素。  对于 `MsiProductCheck` 的每个实例，引导程序都会进行相应的检查，以确定指定的 Microsoft Windows Installer 安装是否已运行完毕。  将根据该安装产品的状态来设置属性值。  正值指示产品已安装，0 或 \-1 指示产品未安装。  （有关更多信息，请参见 Windows Installer SDK 函数 MsiQueryFeatureState。）.  如果计算机上没有安装 Windows Installer，将不会设置 `Property`。  
  
 `MsiProductCheck` 不包含任何元素，但具有下列特性。  
  
|特性|说明|  
|--------|--------|  
|`Property`|必选。  用于存储结果的属性的名称。  可以从 `InstallConditions` 元素下的测试引用此属性，该元素是 `Command` 元素的子元素。  有关更多信息，请参见 [\<Commands\> 元素](../deployment/commands-element-bootstrapper.md)。|  
|`Product`|必选。  所安装产品的 GUID。|  
|`Feature`|可选。  所安装应用程序的特定功能的 GUID。|  
  
## RegistryCheck  
 此元素是 `InstallChecks` 的可选子元素。  对于 `RegistryCheck` 的每个实例，引导程序都会进行相应的检查，以确定指定的注册表项是否存在，或者它是否具有指示的值。  
  
 `RegistryCheck` 不包含任何元素，但具有下列特性。  
  
|特性|说明|  
|--------|--------|  
|`Property`|必选。  用于存储结果的属性的名称。  可以从 `InstallConditions` 元素下的测试引用此属性，该元素是 `Command` 元素的子元素。  有关更多信息，请参见 [\<Commands\> 元素](../deployment/commands-element-bootstrapper.md)。|  
|`Key`|必选。  注册表项的名称。|  
|`Value`|可选。  要检索的注册表值的名称。  默认设置为返回默认值的文本。  `Value` 必须是字符串或 DWORD。|  
  
## RegistryFileCheck  
 此元素是 `InstallChecks` 的可选子元素。  对于 `RegistryFileCheck` 的每个实例，引导程序都将检索指定文件的版本，并首先尝试从指定的注册表项检索该文件的路径。  当要在指定为注册表中的值的某个目录中查找文件时，这一点尤其有用。  
  
 `RegistryFileCheck` 不包含任何元素，但具有下列特性。  
  
|特性|说明|  
|--------|--------|  
|`Property`|必选。  用于存储结果的属性的名称。  可以从 `InstallConditions` 元素下的测试引用此属性，该元素是 `Command` 元素的子元素。  有关更多信息，请参见 [\<Commands\> 元素](../deployment/commands-element-bootstrapper.md)。|  
|`Key`|必选。  注册表项的名称。  除非设置了 `File` 特性，否则它的值将解释为文件的路径。  如果此项不存在，则不会设置 `Property`。|  
|`Value`|可选。  要检索的注册表值的名称。  默认设置为返回默认值的文本。  `Value` 必须是字符串。|  
|`FileName`|可选。  文件的名称。  如果已指定，则假定从注册表项中获取的值为目录路径，并将此名称追加到该路径的后面。  如果未指定，则假定从注册表返回的值为文件的完整路径。|  
|`SearchDepth`|可选。  在子文件夹中搜索指定文件时可达到的深度。  该搜索为深度优先。  默认值为 0，这会将搜索范围限定为该注册表项的值指定的顶级文件夹。|  
  
## 备注  
 虽然 `InstallChecks` 下的元素定义了要运行的测试，但它们并不执行这些测试。  要执行这些测试，必须在 `Commands` 元素下创建 `Command` 元素。  
  
## 示例  
 下面的代码示例演示在 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 的产品文件中使用的 `InstallChecks` 元素。  
  
```  
<InstallChecks>  
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />  
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />  
</InstallChecks>  
```  
  
## InstallConditions  
 计算 `InstallChecks` 时，它们将生成一些属性。  接下来，`InstallConditions` 将使用这些属性确定是应安装数据包、绕过数据包还是令其安装失败。  下表列出了 `InstallConditions`：  
  
|||  
|-|-|  
|`FailIf`|如果有任何 `FailIf` 条件计算为 true，数据包将失败。  同时将不再计算剩余的条件。|  
|`BypassIf`|如果有任何 `BypassIf` 条件计算为 true，将绕过数据包。  同时将不再计算剩余的条件。|  
  
## 预定义属性  
 下表列出了 `BypassIf` 和 `FailIf` 元素：  
  
|属性|注释|可能的值|  
|--------|--------|----------|  
|`Version9X`|Windows 9X 操作系统的版本号。|4.10 \= Windows 98|  
|`VersionNT`|基于 Windows NT 的操作系统的版本号。|Major.Minor.ServicePack<br /><br /> 5.0 \= Windows 2000<br /><br /> 5.1.0 \= Windows XP<br /><br /> 5.1.2 \= Windows XP Professional SP2<br /><br /> 5.2.0 \= Windows Server 2003|  
|`VersionNT64`|基于 64 位 Windows NT 的操作系统的版本号。|与上述内容相同。|  
|`VersionMsi`|Windows Installer 服务的版本号。|2.0 \= Windows Installer 2.0|  
|`AdminUser`|指定用户在基于 Windows NT 的操作系统上是否具有管理员特权。|0 \= 无管理员特权<br /><br /> 1 \= 管理员特权|  
  
 例如，若要在运行 Windows 95 的计算机上阻止安装，请使用诸如以下内容的代码：  
  
```  
<!-- Block install on Windows 95 -->  
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>  
```  
  
## 请参阅  
 [\<Commands\> 元素](../deployment/commands-element-bootstrapper.md)   
 [产品和包架构引用](../deployment/product-and-package-schema-reference.md)