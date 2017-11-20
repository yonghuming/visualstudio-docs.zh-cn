---
title: "&lt;InstallChecks&gt;元素 （引导程序） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords: <InstallChecks> element [bootstrapper]
ms.assetid: ad329c87-b0ad-4304-84de-ae9496514c42
caps.latest.revision: "23"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 2a731c504355cbd3869790720af1f67f6c6bf0eb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ltinstallchecksgt-element-bootstrapper"></a>&lt;InstallChecks&gt;元素 （引导程序）
`InstallChecks`元素支持启动各种对本地计算机，以确保所有的应用程序的相应先决条件都已安装的测试。  
  
## <a name="syntax"></a>语法  
  
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
  
## <a name="assemblycheck"></a>AssemblyCheck  
 此元素为可选子元素的`InstallChecks`。 每个实例`AssemblyCheck`，引导程序将确保元素标识的程序集位于全局程序集缓存 (GAC)。 它不包含任何元素，并具有以下属性。  
  
|特性|说明|  
|---------------|-----------------|  
|`Property`|必需。 要将结果存储的属性名称。 此属性可以从下一个测试引用`InstallConditions`元素，它是子节点的`Command`元素。 有关详细信息，请参阅[\<命令 > 元素](../deployment/commands-element-bootstrapper.md)。|  
|`Name`|必需。 要检查的程序集的完全限定的名称。|  
|`PublicKeyToken`|必需。 与此强名称程序集关联的公钥的缩写的形式。 存储在 GAC 中的所有程序集必须具有名称、 版本和公钥。|  
|`Version`|必需。 该程序集的版本。<br /><br /> 版本号具有格式\<*主要版本*>。\<*次要版本*>。\<*生成版本*>。\<*修订版本*>。|  
|`Language`|可选。 本地化的程序集的语言。 默认值为 `neutral`。|  
|`ProcessorArchitecture`|可选。 此安装的目标计算机处理器。 默认值为 `msil`。|  
  
## <a name="externalcheck"></a>ExternalCheck  
 此元素为可选子元素的`InstallChecks`。 每个实例`ExternalCheck`，引导程序将在单独的进程中执行指定的外部程序并将其退出代码存储在由指示的属性`Property`。 `ExternalCheck`用于实现复杂的依赖关系检查，或检查存在的一个组件的唯一方法是其进行实例化很有用。  
  
 `ExternalCheck`不包含任何元素，并具有以下属性。  
  
|特性|说明|  
|---------------|-----------------|  
|`Property`|必需。 要将结果存储的属性名称。 此属性可以从下一个测试引用`InstallConditions`元素，它是子节点的`Command`元素。 有关详细信息，请参阅[\<命令 > 元素](../deployment/commands-element-bootstrapper.md)。|  
|`PackageFile`|必需。 要执行的外部程序。 程序必须是安装程序分发包的一部分。|  
|`Arguments`|可选。 提供了通过名为的可执行文件的命令行自变量`PackageFile`。|  
  
## <a name="filecheck"></a>签  
 此元素为可选子元素的`InstallChecks`。 每个实例`FileCheck`，引导程序将确定是否已命名的文件存在，并返回该文件的版本号。 如果该文件没有版本号，引导程序设置命名的属性`Property`为 0。 如果文件不存在，`Property`未设置为任何值。  
  
 `FileCheck`不包含任何元素，并具有以下属性。  
  
|特性|说明|  
|---------------|-----------------|  
|`Property`|必需。 要将结果存储的属性名称。 此属性可以从下一个测试引用`InstallConditions`元素，它是子节点的`Command`元素。 有关详细信息，请参阅[\<命令 > 元素](../deployment/commands-element-bootstrapper.md)。|  
|`FileName`|必需。 要查找的文件的名称。|  
|`SearchPath`|必需。 磁盘或要在其中查找文件的文件夹。 这必须是相对路径，如果`SpecialFolder`分配; 否则，它必须是绝对路径。|  
|`SpecialFolder`|可选。 文件夹具有特别的意义，到 Windows，或者为[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]。 默认值是解释`SearchPath`为绝对路径。 包括以下有效值：<br /><br /> `AppDataFolder`。 此应用程序数据文件夹[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序; 特定于当前用户。<br /><br /> `CommonAppDataFolder`。 所有用户都使用的应用程序数据文件夹。<br /><br /> `CommonFilesFolder`。 当前用户的常见文件文件夹。<br /><br /> `LocalDataAppFolder`。 非漫游应用程序数据文件夹。<br /><br /> `ProgramFilesFolder`。 对于 32 位应用程序标准的 Program Files 文件夹。<br /><br /> `StartUpFolder`。 包含在系统启动时启动的所有应用程序的文件夹。<br /><br /> `SystemFolder`。 包含 32 位系统 Dll 的文件夹。<br /><br /> `WindowsFolder`。 包含 Windows 系统安装的文件夹。<br /><br /> `WindowsVolume`。 驱动器或分区包含 Windows 系统安装。|  
|`SearchDepth`|可选。 在其中进行搜索已命名的文件的子文件夹深度。 搜索不深度优先。 默认值为 0，将搜索限制为指定的顶级文件夹`SpecialFolder`和**SearchPath**。|  
  
## <a name="msiproductcheck"></a>MsiProductCheck  
 此元素为可选子元素的`InstallChecks`。 每个实例`MsiProductCheck`，引导程序将检查以确定指定的 Microsoft Windows Installer 安装是否已运行直到完成。 具体取决于该已安装产品的状态设置属性值。 正值指示已安装产品，0 或-1 指示未安装。 （请参见详细信息的 Windows Installer SDK 函数 MsiQueryFeatureState。）. 如果在计算机上未安装 Windows Installer`Property`未设置。  
  
 `MsiProductCheck`不包含任何元素，并具有以下属性。  
  
|特性|说明|  
|---------------|-----------------|  
|`Property`|必需。 要将结果存储的属性名称。 此属性可以从下一个测试引用`InstallConditions`元素，它是子节点的`Command`元素。 有关详细信息，请参阅[\<命令 > 元素](../deployment/commands-element-bootstrapper.md)。|  
|`Product`|必需。 已安装产品的 GUID。|  
|`Feature`|可选。 已安装的应用程序的特定功能的 GUID。|  
  
## <a name="registrycheck"></a>RegistryCheck  
 此元素为可选子元素的`InstallChecks`。 每个实例`RegistryCheck`，引导程序将检查以确定是否存在指定的注册表项，或是否具有指示的值。  
  
 `RegistryCheck`不包含任何元素，并具有以下属性。  
  
|特性|说明|  
|---------------|-----------------|  
|`Property`|必需。 要将结果存储的属性名称。 此属性可以从下一个测试引用`InstallConditions`元素，它是子节点的`Command`元素。 有关详细信息，请参阅[\<命令 > 元素](../deployment/commands-element-bootstrapper.md)。|  
|`Key`|必需。 注册表项的名称。|  
|`Value`|可选。 要检索的注册表值的名称。 默认值是返回默认值的文本。 `Value`必须是字符串或一个 dword 值。|  
  
## <a name="registryfilecheck"></a>RegistryFileCheck  
 此元素为可选子元素的`InstallChecks`。 每个实例`RegistryFileCheck`，引导程序检索指定文件的版本首先尝试检索到的文件的路径，从指定的注册表项。 这是特别有用，如果你想要查找指定的注册表中的值为目录中的文件。  
  
 `RegistryFileCheck`不包含任何元素，并具有以下属性。  
  
|特性|说明|  
|---------------|-----------------|  
|`Property`|必需。 要将结果存储的属性名称。 此属性可以从下一个测试引用`InstallConditions`元素，它是子节点的`Command`元素。 有关详细信息，请参阅[\<命令 > 元素](../deployment/commands-element-bootstrapper.md)。|  
|`Key`|必需。 注册表项的名称。 其值解释为文件的路径，除非`File`属性设置。 如果该键不存在，`Property`未设置。|  
|`Value`|可选。 要检索的注册表值的名称。 默认值是返回默认值的文本。 `Value`必须是字符串。|  
|`FileName`|可选。 文件的名称。 如果指定，则假定从注册表项获取的值是一个目录路径，而此名称追加到它。 如果未指定，则假定从注册表返回的值是到文件的完整路径。|  
|`SearchDepth`|可选。 在其中进行搜索已命名的文件的子文件夹深度。 搜索不深度优先。 默认值为 0，将搜索限制为指定的注册表项值的顶级文件夹。|  
  
## <a name="remarks"></a>备注  
 尽管下的元素`InstallChecks`定义要运行的测试，它们并不执行它们。 若要执行测试，必须创建`Command`元素下方`Commands`元素。  
  
## <a name="example"></a>示例  
 下面的代码示例演示`InstallChecks`作为它的元素用于中的产品文件[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。  
  
```  
<InstallChecks>  
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />  
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />  
</InstallChecks>  
```  
  
## <a name="installconditions"></a>InstallConditions  
 当`InstallChecks`是计算，它们将生成属性。 然后使用属性`InstallConditions`来确定包是否应安装、 绕过，或失败。 下表列出`InstallConditions`:  
  
|||  
|-|-|  
|`FailIf`|如果任何`FailIf`条件的计算结果为 true，包将失败。 将评估这些条件的其余部分。|  
|`BypassIf`|如果任何`BypassIf`条件的计算结果为 true，将绕过包。 将评估这些条件的其余部分。|  
  
## <a name="predefined-properties"></a>预定义的属性  
 下表列出`BypassIf`和`FailIf`元素：  
  
|属性|备注|可能的值|  
|--------------|-----------|---------------------|  
|`Version9X`|Windows 9x X 操作系统的版本号。|4.10 = Windows 98|  
|`VersionNT`|基于 Windows NT 的操作系统的版本号。|Major.Minor.ServicePack<br /><br /> 5.0 = Windows 2000<br /><br /> 5.1.0 = Windows XP<br /><br /> 5.1.2 = Windows XP Professional SP2<br /><br /> 5.2.0 = Windows Server 2003|  
|`VersionNT64`|64 位基于 Windows NT 的操作系统的版本号。|与前面提到的相同。|  
|`VersionMsi`|Windows Installer 服务的版本号。|2.0 = Windows Installer 2.0|  
|`AdminUser`|指定用户是否在基于 Windows NT 的操作系统上具有管理员权限。|0 = 没有管理员权限<br /><br /> 1 = 管理员权限|  
  
 例如，若要阻止安装运行 Windows 95 的计算机上，请使用如下代码：  
  
```  
<!-- Block install on Windows 95 -->  
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>  
```  
  
## <a name="see-also"></a>另请参阅  
 [\<命令 > 元素](../deployment/commands-element-bootstrapper.md)   
 [产品和包架构引用](../deployment/product-and-package-schema-reference.md)