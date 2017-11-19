---
title: "ClickOnce 非托管 API 参考 |Microsoft 文档"
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
helpviewer_keywords:
- LaunchApplication [ClickOnce unmanaged]
- ClickOnce, unmanaged APIs
- CleanOnlineAppCache [ClickOnce unmanaged]
- CleanOnlineAppCacheW interface [ClickOnce unmanaged]
- GetDeploymentDataFromManifest [ClickOnce unmanaged]
ms.assetid: ec002138-4054-456d-bcc1-79ac2f4a4fd7
caps.latest.revision: "6"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 11e10800ff51abd6f95447d85204a44f8367f551
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="clickonce-unmanaged-api-reference"></a>ClickOnce 非托管 API 参考
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]从 dfshim.dll 的非托管公共 Api。  
  
## <a name="cleanonlineappcache"></a>CleanOnlineAppCache  
 清理或卸载所有联机应用程序，从[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序缓存。  
  
### <a name="return-value"></a>返回值  
 如果成功，返回，则为 S_OK;否则，返回表示失败的 HRESULT。 如果发生托管的异常，则返回 0x80020009 (DISP_E_EXCEPTION)。  
  
### <a name="remarks"></a>备注  
 调用 CleanOnlineAppCache 将启动[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]服务如果尚未运行。  
  
## <a name="getdeploymentdatafrommanifest"></a>GetDeploymentDataFromManifest  
 从清单和激活 URL 检索部署信息。  
  
### <a name="parameters"></a>参数  
  
|参数|描述|类型|  
|---------------|-----------------|----------|  
|`pcwzActivationUrl`|指向的指针`ActivationURL`。|LPCWSTR|  
|`pcwzPathToDeploymentManifest`|指向的指针`PathToDeploymentManifest`。|LPCWSTR|  
|`pwzApplicationIdentity`|指向一个缓冲区来接收指定完整的应用程序标识返回的以 NULL 结尾的字符串的指针。|LPWSTR|  
|`pdwIdentityBufferLength`|长度是一个 dword 值指向的指针`pwzApplicationIdentity`中 WCHARs 缓冲区。 这包括 NULL 终止字符的空间。|LPDWORD|  
|`pwzProcessorArchitecture`|指向一个缓冲区来接收一个以 NULL 结尾的字符串，指定应用程序部署，清单中的处理器体系结构的指针。|LPWSTR|  
|`pdwArchitectureBufferLength`|长度是一个 dword 值指向的指针`pwzProcessorArchitecture`中 WCHARs 缓冲区。|LPDWORD|  
|`pwzApplicationManifestCodebase`|指向一个缓冲区来接收一个以 NULL 结尾的字符串，指定应用程序清单，清单中的基本代码的指针。|LPWSTR|  
|`pdwCodebaseBufferLength`|长度是一个 dword 值指向的指针`pwzApplicationManifestCodebase`中 WCHARs 缓冲区。|LPDWORD|  
|`pwzDeploymentProvider`|指向要接收的以 NULL 结尾的字符串缓冲区的指针，可以指定从清单中，部署提供程序，如果存在。 否则，返回一个空字符串。|LPWSTR|  
|`pdwProviderBufferLength`|长度是一个 dword 值指向的指针`pwzProviderBufferLength`。|LPDWORD|  
  
### <a name="return-value"></a>返回值  
 如果成功，返回，则为 S_OK;否则，返回表示失败的 HRESULT。 如果缓冲区太小，则返回 HRESULTFROMWIN32(ERROR_INSUFFICIENT_BUFFER)。  
  
### <a name="remarks"></a>备注  
 指针不为 null。 `pcwzActivationUrl`和`pcwzPathToDeploymentManifest`不得为空。  
  
 它由调用方的负责清理激活 URL。 例如，添加转义字符在需要的地方，或删除的查询字符串。  
  
 它由调用方的负责将输入的长度限制。 例如，最大 URL 长度为 2 KB。  
  
## <a name="launchapplication"></a>LaunchApplication  
 启动或安装应用程序使用部署 URL。  
  
### <a name="parameters"></a>参数  
  
|参数|描述|类型|  
|---------------|-----------------|----------|  
|`deploymentUrl`|指向包含部署清单的 URL 以 NULL 结尾的字符串的指针。|LPCWSTR|  
|`data`|留待将来使用。 必须为 NULL。|LPVOID|  
|`flags`|留待将来使用。 必须为 0。|DWORD|  
  
### <a name="return-value"></a>返回值  
 如果成功，返回，则为 S_OK;否则，返回表示失败的 HRESULT。 如果发生托管的异常，则返回 0x80020009 (DISP_E_EXCEPTION)。  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>