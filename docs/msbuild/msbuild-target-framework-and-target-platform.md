---
title: "MSBuild 目标 Framework 和目标平台 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
caps.latest.revision: "10"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: cdfbe126e8a647cda4c8e29e50591a1aa229df80
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="msbuild-target-framework-and-target-platform"></a>MSBuild 目标 Framework 和目标平台
可以生成要在目标框架（.NET Framework 的一个特定版本）和目标平台（一种特定的软件体系结构）上运行的项目。  例如，可将一个应用程序的目标设定为在与 802x86 处理器系列 (“x86”) 兼容的 32 位平台上的 .NET Framework 2.0 上运行。 目标框架与目标平台的组合称为“目标上下文”。  
  
## <a name="target-framework-and-profile"></a>目标框架和配置文件  
 目标框架是特定版本的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]生成的项目将在其上运行。 需要规范目标框架，因为它将启用专用于该框架版本的编译器功能和程序集引用。  
  
 目前，以下版本的 .NET Framework 可供使用：  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0（包含在 Visual Studio 2005 中）  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.0（包含在 [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] 中）  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.5（包含在 [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] 中）  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4（包含在 Visual Studio 2010 中）  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.5（包含在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 中）  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.5.1（包含在 [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] 中）  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.5.2  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.6（包含在 [!INCLUDE[vs_dev14](../misc/includes/vs_dev14_md.md)] 中）  
  
 在可供引用的各程序集的列表中，.NET Framework 的版本各不相同。 例如，不能生成 Windows Presentation Foundation (WPF) 应用程序，除非项目面向 .NET Framework 3.0 或更高版本。  
  
 目标框架是在项目文件中的 `TargetFrameworkVersion` 属性中指定的。 可通过在 Visual Studio 集成开发环境 (IDE) 中使用项目属性页来更改项目的目标框架。 有关详细信息，请参阅[如何：面向 .NET Framework 的某个版本](../ide/how-to-target-a-version-of-the-dotnet-framework.md)。 `TargetFrameworkVersion` 的可用值包括 `v2.0`、`v3.0`、`v3.5`、`v4.0`、`v4.5`、`v4.5.1`、`v4.5.2` 和 `v4.6`。  
  
```xml  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
```  
  
 目标概况是目标框架的一个子集。 例如，.NET Framework 4 客户端配置文件不包括对 MSBuild 程序集的引用。  
  
 目标配置文件是在项目文件中的 `TargetFrameworkProfile` 属性中指定的。 可通过在 IDE 中使用项目属性页中的目标框架控件来更改目标概况。 有关详细信息，请参阅[如何：面向 .NET Framework 的某个版本](../ide/how-to-target-a-version-of-the-dotnet-framework.md)。  
  
```xml  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
<TargetFrameworkProfile>Client</TargetFrameworkProfile>  
```  
  
## <a name="target-platform"></a>目标平台  
 平台是定义特定运行时环境的硬件和软件的组合。 例如，  
  
-   `x86` 指定在 Intel 80x86 处理器或等效处理器上运行的 32 位 Windows 操作系统。  
  
-   `Xbox` 指定 Microsoft Xbox 360 平台。  
  
 目标平台是指将在其上运行生成项目的特定平台。 目标平台是在项目文件中的 `Platform` 生成属性中指定的。 可通过在 IDE 中使用项目属性页或**配置管理器**来更改目标平台。  
  
```xml  
<PropertyGroup>  
   <Platform>x86</Platform>  
</PropertyGroup>  
  
```  
  
 目标配置是目标平台的一个子集。 例如，`x86``Debug` 配置不包括大多数代码优化项。 目标配置是在项目文件中的 `Configuration` 生成属性中指定的。 可通过使用项目属性页或**配置管理器**来更改目标配置。  
  
```xml  
<PropertyGroup>  
   <Platform>x86</Platform>  
   <Configuration>Debug</Configuration>  
<PropertyGroup>  
  
```  
  
## <a name="see-also"></a>另请参阅  
 [多定向](../msbuild/msbuild-multitargeting-overview.md)