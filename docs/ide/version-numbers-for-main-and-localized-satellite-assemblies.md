---
title: "主程序集和已本地化的附属程序集的版本号 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- satellite assemblies, version numbers
- SatelliteContractVersionAttribute
- version numbers, assemblies
- assemblies [Visual Studio], version numbers
- versioning, assemblies
ms.assetid: 5489aea1-57b4-4561-9bb4-24d490269602
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7e2f2e76d9dec25e6c5bf5d6deeab42364d28de8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="version-numbers-for-main-and-localized-satellite-assemblies"></a>用于主程序集和已本地化的附属程序集的版本号
<xref:System.Resources.SatelliteContractVersionAttribute> 类为通过资源管理器使用本地化资源的主程序集提供版本控制支持。 通过将 <xref:System.Resources.SatelliteContractVersionAttribute> 应用于应用程序的主程序集，可在不更新其附属程序集的情况下，更新和重新部署该程序集。 例如，可以将 <xref:System.Resources.SatelliteContractVersionAttribute> 类与不会引入新资源的服务包配合使用，而无需重新生成和重新部署附属程序集。 若要使本地化资源可用，主程序集的附属协定版本必须与附属程序集的 <xref:System.Reflection.AssemblyVersionAttribute> 类匹配。 必须在 <xref:System.Resources.SatelliteContractVersionAttribute> 中指定确切的版本号；不允许使用通配符，如“*”。 有关详细信息，请参阅 [检索资源](/dotnet/framework/resources/retrieving-resources-in-desktop-apps)。  
  
## <a name="updating-assemblies"></a>更新程序集  
 <xref:System.Resources.SatelliteContractVersionAttribute> 类允许在不更新附属程序集的情况下更新主程序集，反之亦然。 主程序集更新后，其程序集版本号也随之更新。 如果要继续使用现有附属程序集，请更改主程序集的版本号，但保持原有附属协定版本号。 例如，首次发布时，主程序集版本可能是 1.0.0.0。 附属程序集的附属协定版本和程序集版本也会是 1.0.0.0。 如果需要更新服务包的主程序集，可以将程序集版本更改为 1.0.0.1，同时将附属协定版本和附属程序集版本保持为 1.0.0.0。  
  
 如果需要更新附属程序集而不是主程序集，请更改附属程序集的 <xref:System.Reflection.AssemblyVersionAttribute>。 随附属程序集一起交付的还有策略程序集，该程序集说明新的附属程序集可与旧版附属程序集兼容。 有关策略的详细信息，请参阅[运行时如何定位程序集](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)。  
  
 下面的代码演示如何设置附属协定版本。 可以将代码放置在生成脚本或 AssemblyInfo.vb 或 AssemblyInfo.cs 文件中。  
  
```vb  
<Assembly: SatelliteContractVersionAttribute("4.3.2.1")>  
  
```  
  
```csharp  
[assembly: SatelliteContractVersionAttribute("4.3.2.1")]  
```  
  
## <a name="see-also"></a>另请参阅  
 [运行时如何定位程序集](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)   
 [设置程序集属性](/dotnet/framework/app-domains/set-assembly-attributes)   
 [安全性和已本地化的附属程序集](../ide/security-and-localized-satellite-assemblies.md)   
 [本地化应用程序](../ide/localizing-applications.md)   
 [对应用程序进行全球化和本地化](../ide/globalizing-and-localizing-applications.md)