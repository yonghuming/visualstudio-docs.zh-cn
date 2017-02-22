---
title: "ClickOnce 非托管 API 参考 | Microsoft Docs"
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
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "CleanOnlineAppCache [ClickOnce 非托管]"
  - "CleanOnlineAppCacheW 接口 [ClickOnce 非托管]"
  - "ClickOnce, 非托管 API"
  - "GetDeploymentDataFromManifest [ClickOnce 非托管]"
  - "LaunchApplication [ClickOnce 非托管]"
ms.assetid: ec002138-4054-456d-bcc1-79ac2f4a4fd7
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ClickOnce 非托管 API 参考
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

来自 dfshim.dll 的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 非托管公共 API。  
  
## CleanOnlineAppCache  
 从 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序缓存中清理或卸载所有的联机应用程序。  
  
### 返回值  
 如果成功，则返回 S\_OK；否则，将返回表示失败的 HRESULT。  如果发生托管异常，则返回 0x80020009 \(DISP\_E\_EXCEPTION\)。  
  
### 备注  
 如果 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 服务尚未运行，则调用 CleanOnlineAppCache 将启动该服务。  
  
## GetDeploymentDataFromManifest  
 从清单和激活 URL 中检索部署信息。  
  
### 参数  
  
|Parameter|说明|类型|  
|---------------|--------|--------|  
|`pcwzActivationUrl`|指向 `ActivationURL` 的指针。|LPCWSTR|  
|`pcwzPathToDeploymentManifest`|指向 `PathToDeploymentManifest` 的指针。|LPCWSTR|  
|`pwzApplicationIdentity`|一个指向接收以 NULL 结尾的字符串的缓冲区的指针，该字符串指定返回的完整应用程序标识。|LPWSTR|  
|`pdwIdentityBufferLength`|一个指向 DWORD 的指针，DWORD 表示 `pwzApplicationIdentity` 缓冲区的长度，以 WCHAR 为单位。  其中包括用于 NULL 终止字符的空格。|LPDWORD|  
|`pwzProcessorArchitecture`|一个指向接收以 NULL 结尾的字符串的缓冲区的指针，该字符串指定清单中的应用程序部署的处理器体系结构。|LPWSTR|  
|`pdwArchitectureBufferLength`|一个指向 DWORD 的指针，DWORD 表示 `pwzProcessorArchitecture` 缓冲区的长度，以 WCHAR 为单位。|LPDWORD|  
|`pwzApplicationManifestCodebase`|一个指向接收以 NULL 结尾的字符串的缓冲区的指针，该字符串指定清单中的应用程序清单的基本代码。|LPWSTR|  
|`pdwCodebaseBufferLength`|一个指向 DWORD 的指针，DWORD 表示 `pwzApplicationManifestCodebase` 缓冲区的长度，以 WCHAR 为单位。|LPDWORD|  
|`pwzDeploymentProvider`|一个指向接收以 NULL 结尾的字符串的缓冲区的指针，该字符串指定清单中的部署提供程序（如果存在）。  如果不存在，则将返回一个空字符串。|LPWSTR|  
|`pdwProviderBufferLength`|一个指向 DWORD 的指针，DWORD 表示 `pwzProviderBufferLength` 的长度。|LPDWORD|  
  
### 返回值  
 如果成功，则返回 S\_OK；否则，将返回表示失败的 HRESULT。  如果缓冲区太小，则返回 HRESULTFROMWIN32\(ERROR\_INSUFFICIENT\_BUFFER\)。  
  
### 备注  
 指针不得为 null。  `pcwzActivationUrl` 和 `pcwzPathToDeploymentManifest` 不得为空。  
  
 调用方负责清理激活 URL。  例如，在需要时添加转义符或移除查询字符串。  
  
 调用方负责限制输入长度。  例如，最大 URL 长度为 2KB。  
  
## LaunchApplication  
 通过使用部署 URL 来启动或安装应用程序。  
  
### 参数  
  
|Parameter|说明|类型|  
|---------------|--------|--------|  
|`deploymentUrl`|一个指向以 NULL 结尾的字符串的指针，该字符串包含部署清单的 URL。|LPCWSTR|  
|`data`|保留供将来使用。  必须为 NULL。|LPVOID|  
|`flags`|保留供将来使用。  必须为 0。|DWORD|  
  
### 返回值  
 如果成功，则返回 S\_OK；否则，将返回表示失败的 HRESULT。  如果发生托管异常，则返回 0x80020009 \(DISP\_E\_EXCEPTION\)。  
  
## 请参阅  
 <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>