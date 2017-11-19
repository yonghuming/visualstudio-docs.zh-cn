---
title: "&lt;compatibleFrameworks&gt;元素 （ClickOnce 部署） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords: <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
caps.latest.revision: "15"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: bb8c31d37bd37f4e2db8415ef1815caec0ec185a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;compatibleFrameworks&gt;元素 （ClickOnce 部署）
标识此应用程序可在其上安装和运行的 .NET Framework 版本。  
  
> [!NOTE]
>  [MageUI.exe](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)不支持`compatibleFrameworks`元素保存应用程序清单时已签名证书使用[MageUI.exe](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)。 这种情况下必须使用 [Mage.exe](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)。  
  
## <a name="syntax"></a>语法  
  
```  
<compatibleFrameworks  
      SupportUrl>   
   <framework  
      targetVersion  
      profile  
      supportedRuntime  
   />   
</ compatibleFrameworks>  
```  
  
## <a name="elements-and-attributes"></a>元素和属性  
 `compatibleFrameworks`元素是必需的部署清单面向[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]运行时提供的[!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)]或更高版本。 `compatibleFrameworks`元素包含一个或多个`framework`元素，用于指定此应用程序可以在其运行的.NET Framework 版本。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]运行时将运行应用程序在第一个可用`framework`此列表中。  
  
 下表列出了该属性，`compatibleFrameworks`元素支持。  
  
|特性|描述|  
|---------------|-----------------|  
|`S` `upportUrl`|可选。 指定首选兼容的.NET Framework 版本可以下载到其中的 URL。|  
  
## <a name="framework"></a>框架  
 必需。 下表列出的属性，`framework`元素支持。  
  
|特性|说明|  
|---------------|-----------------|  
|`targetVersion`|必需。 指定的目标.NET Framework 的版本号。|  
|`profile`|必需。 指定的目标.NET Framework 的配置文件。|  
|`supportedRuntime`|必需。 指定的目标.NET Framework 与关联的运行时的版本号。|  
  
## <a name="remarks"></a>备注  
  
## <a name="example"></a>示例  
 下面的代码示例演示`compatibleFrameworks`中的元素[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署清单。 可以在上运行此部署[!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)]。 它还可以对运行[!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)]因为它是的超集[!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)]。  
  
```  
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
  <framework   
      targetVersion="4.0"   
      profile="Client"   
      supportedRuntime="4.0.30319" />  
</compatibleFrameworks>  
```  
  
## <a name="see-also"></a>另请参阅  
 [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)