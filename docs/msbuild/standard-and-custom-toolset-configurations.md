---
title: "标准和自定义工具集配置 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, 自定义工具集配置"
  - "MSBuild, msbuild.exe.config"
ms.assetid: 15a048c8-5ad3-448e-b6e9-e3c5d7147ed2
caps.latest.revision: 31
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 31
---
# 标准和自定义工具集配置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

MSBuild 工具集包含到任务、可以使用生成应用程序项目的目标和工具的引用。  MSBuild 包括标准工具集，但是，您还可以创建自定义工具集。  有关如何确定特定工具集的信息，请参阅[工具集 \(ToolsVersion\)](../msbuild/msbuild-toolset-toolsversion.md)。  
  
## 标准工具集配置  
 MSBuild 12.0 包括下列标准工具集：  
  
|ToolsVersion|工具集路径 \(在 MSBuildToolsPath 或 MSBuildBinPath 生成中指定特性\)|  
|------------------|-----------------------------------------------------------|  
|2.0|*Windows installation path*\\Microsoft.Net\\Framework\\v2.0.50727\\|  
|3.5|*Windows installation path*\\Microsoft.NET\\Framework\\v3.5\\|  
|4.0|*Windows installation path*\\Microsoft.NET\\Framework\\v4.0.30319\\|  
|12.0|*%ProgramFiles%*\\MSBuild\\12.0\\bin|  
  
 `ToolsVersion` 值确定 Visual Studio 生成的项目应使用工具集。  在 [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] 默认值为“12.0”\(无论在项目文件中指定的版本\)，但是，您可以重写该属性使用 **\/toolsversion** 切换到命令提示。  有关此特性和其他方式指定 `ToolsVersion`的信息，请参见 [重写 ToolsVersion 设置](../msbuild/overriding-toolsversion-settings.md)。  
  
 如果 `ToolsVersion` 未指定，注册表项 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSBuild\\\<Version Number\>\\DefaultToolsVersion 定义 `ToolsVersion`，始终为 2.0。  
  
 下列寄存器表项指定 MSBuild.exe 安装路径。  
  
|注册表项|键名|字符串键值|  
|----------|--------|-----------|  
|\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSBuild\\ToolsVersions\\2.0\\|MSBuildToolsPath|.NET Framework 2.0 安装路径|  
|\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\ MSBuild\\ToolsVersions\\3.5\\|MSBuildToolsPath|.NET Framework 3.5 安装路径|  
|\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\ MSBuild\\ToolsVersions\\4.0\\|MSBuildToolsPath|.NET Framework 4 安装路径|  
|\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\ MSBuild\\ToolsVersions\\12.0\\|MSBuildToolsPath|MSBuild 安装路径|  
  
### 子工具集  
 如果上一个表中的注册表项有一个子级，则MSBuild 使用它确定子工具集的路径，这样可能会覆盖父工具集的路径。  下面的子键是一个示例：  
  
 \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSBuild\\ToolsVersions\\12.0\\12.0  
  
 如果任何属性在基本工具集与选定的子工具集均有定义，则使用在子工具集的属性定义。  例如，MSBuild 4.0 工具集定义 `SDK40ToolsPath` 指向 7.0A SDK，但是MSBuild 4.0\\11.0 工具集定义同一个属性来指向 8.0A SDK。  如果 `VisualStudioVersion` 未设置，`SDK40ToolsPath` 将指向7.0A，但是如果 `VisualStudioVersion` 设置为 11.0，属性将指向 8.0A。  
  
 `VisualStudioVersion` 生成属性指示子工具集是否变为活动状态。  例如，`VisualStudioVersion` 值“12.0”指定 MSBuild 12.0 子工具集。  有关更多信息，请参阅[工具集 \(ToolsVersion\)](../msbuild/msbuild-toolset-toolsversion.md)的子工具集一节。  
  
> [!NOTE]
>  建议您避免更改这些设置。  不过，您还是可以添加自己的设置，定义计算机范围内的自定义工具集定义，这将在下一节中进行介绍。  
  
## 自定义工具集定义  
 当标准的工具集不能满足您的生成要求时，您可以创建自定义工具集。  例如，您可能拥有一套实验方案，在这里您必须为生成 [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] 项目设置一个单独的系统。  通过使用自定义工具集，那么，当您创建项目或运行 MSBuild.exe 时，可以指定自定义值设置为 `ToolsVersion` 属性。  这样，也可以使用 `$(MSBuildToolsPath)` 属性从该目录导入 .targets 文件，以及定义可用于所有项目使用该工具集您的自定义工具集属性。  
  
 在 MSBuild.exe （或者承载MSBuild引擎的自定义工具如果您在使用的话）的配置文件中指定自定义工具集。  例如，如果希望重写 ToolsVersion 值默认行为 12.0，MSBuild.exe 的配置文件可以包含以下工具集定义。  
  
```  
<msbuildToolsets default="12.0">  
   <toolset toolsVersion="12.0">  
      <property name="MSBuildToolsPath"   
        value="C:\SpecialPath" />  
   </toolset>  
</msbuildToolsets>  
```  
  
 在配置文件还必须定义`<msbuildToolsets>`，如下所示。  
  
```  
<configSections>  
   <section name="msbuildToolsets"         
       Type="Microsoft.Build.BuildEngine.ToolsetConfigurationSection,   
       Microsoft.Build.Engine, Version=12.0.0.0, Culture=neutral,   
       PublicKeyToken=b03f5f7f11d50a3a"  
   </section>  
</configSections>  
```  
  
> [!NOTE]
>  为了能正确读取，`<configSections>` 必须位于 `<configuration>` 部分的第一小节。  
  
 `ToolsetConfigurationSection` 是一个可由自定义配置的任意MSBuild宿主使用的自定义配置节。  如果使用自定义工具集，则宿主除了提供配置文件项外，无需再执行任何其他操作便可初始化生成引擎。  通过在注册表中定义这些项，您可以指定计算机范围内的、适用于 MSBuild.exe、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 及所有MSBuild宿主的工具集。  
  
> [!NOTE]
>  如果先在注册表中定义了 `ToolsVersion` 的设置，而后又在配置文件中对其进行了定义，则这两个定义并不会合并。  配置文件中的定义会具有较高的优先级，而注册表中的`ToolsVersion` 设置则会被忽略。  
  
 下列属性特定于项目中所用的 `ToolsVersion`值：  
  
-   **$\(MSBuildBinPath\)** \- MSBuildBinPath 被设置为`ToolsPath`值，该值在定义`ToolsVersion` 的注册表或配置文件中指定。  注册表或配置文件中的 `$(MSBuildToolsPath)` 设置用于指定核心进程和目标的位置。  在项目文件中，此值映射到 $\(MSBuildBinPath\) 属性和 $\(MSBuildToolsPath\) 属性。  
  
-   `$(MSBuildToolsPath)` 是一个由在配置文件中指定的 MSBuildToolsPath 属性提供的保留属性。（此属性取代了 `$(MSBuildBinPath)`。  但是，`$(MSBuildBinPath)` 是为实现向前兼容性而承载的。）除非它们具有相同的值，自定义工具集必须定义 `$(MSBuildToolsPath)` 或 `$(MSBuildBinPath)`，但不能同时包含二者。  
  
 您还可以使用添加 MSBuildToolsPath 属性时所用的语法在配置文件中添加特定于 ToolsVersion 的自定义属性。  如果要在项目文件中使用这些自定义属性，只需使用与配置文件中所指定的值相同的名称。  您可以在配置文件中定义工具集但不能定义子工具集。  
  
## 请参阅  
 [工具集 \(ToolsVersion\)](../msbuild/msbuild-toolset-toolsversion.md)