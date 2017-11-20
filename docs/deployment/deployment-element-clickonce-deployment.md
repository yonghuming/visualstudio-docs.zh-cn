---
title: "&lt;部署&gt;元素 （ClickOnce 部署） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#subscription
- urn:schemas-microsoft-com:asm.v2#beforeApplicationStartup
- urn:schemas-microsoft-com:asm.v2#deploymentProvider
- urn:schemas-microsoft-com:asm.v2#update
- urn:schemas-microsoft-com:asm.v2#deployment
- urn:schemas-microsoft-com:asm.v2#expiration
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords: <deployment> element [ClickOnce deployment manifest]
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
caps.latest.revision: "30"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: ddcdc96095775f5957fbc9db872b51396798ba52
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;部署&gt;元素 （ClickOnce 部署）
标识用于部署更新并向系统公开的特性。  
  
## <a name="syntax"></a>语法  
  
```  
  
      <deployment   
   install  
   minimumRequiredVersion  
   mapFileExtensions  
   disallowUrlActivation  
   trustUrlParameters  
>   
   <subscription>   
         <update>   
            <beforeApplicationStartup/>   
            <expiration  
               maximumAge  
               unit  
            />  
         </update>    
   </subscription>   
   <deploymentProvider   
      codebase   
   />   
</deployment>  
```  
  
## <a name="elements-and-attributes"></a>元素和属性  
 `deployment` 元素是必需的，它位于 `urn:schemas-microsoft-com:asm.v1` 命名空间中。 元素具有以下属性。  
  
|特性|说明|  
|---------------|-----------------|  
|`install`|必需。 指定此应用程序是否在 Windows 上定义存在性**启动**菜单和控制面板中**添加或删除程序**应用程序。 有效值为 `true` 和 `false`。 如果`false`，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]始终将从网络中，运行此应用程序的最新版本并将无法识别`subscription`元素。|  
|`minimumRequiredVersion`|可选。 指定可在客户端运行此应用程序的最低版本。 如果应用程序的版本号小于部署清单中提供的版本号，将不会运行该应用程序。 版本号必须指定格式`N.N.N.N`，其中`N`是无符号的整数。 如果`install`属性是`false`，`minimumRequiredVersion`不能设置。|  
|`mapFileExtensions`|可选。 默认为 `false`。 如果`true`，部署中的所有文件必须都具有.deploy 扩展名。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]将关闭这些文件中剥离此扩展，只要它从 Web 服务器下载它们。 如果使用发布你的应用程序[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，它自动将此扩展添加到的所有文件。 此参数允许内的所有文件[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署从筛选器阻止传输文件等.exe"不安全的"扩展中的 Web 服务器下载。|  
|`disallowUrlActivation`|可选。 默认为 `false`。 如果`true`，阻止从正在通过单击的 URL 或 Internet 资源管理器中输入 URL 来启动已安装应用程序。 如果`install`属性不存在，则忽略此属性。|  
|`trustURLParameters`|可选。 默认为 `false`。 如果`true`、 允许 URL 包含到应用程序传递的查询字符串参数、 多 like 的命令行自变量传递给命令行应用程序。 有关详细信息，请参阅[如何： 在联机 ClickOnce 应用程序中检索查询字符串信息](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)。<br /><br /> 如果`disallowUrlActivation`属性是`true`，`trustUrlParameters`必须为排除从清单，或者显式设置为`false`。|  
  
 `deployment`元素还包含以下子元素。  
  
## <a name="subscription"></a>订阅  
 可选。 包含`update`元素。 `subscription`元素没有任何特性。 如果`subscription`元素不存在，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序将永远不会扫描更新。 如果`install`属性`deployment`元素是`false`、`subscription`元素被忽略，因为[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]始终启动从网络应用程序使用的最新版本。  
  
## <a name="update"></a>更新  
 必需。 此元素是的子级`subscription`元素，它包含`beforeApplicationStartup`或`expiration`元素。 `beforeApplicationStartup`和`expiration`无法同时指定相同的部署清单中。  
  
 `update`元素没有任何特性。  
  
## <a name="beforeapplicationstartup"></a>beforeApplicationStartup  
 可选。 此元素是的子级`update`元素且不具有特性。 当`beforeApplicationStartup`元素存在，该应用程序将被阻止时[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]检查更新，如果客户端处于联机状态。 如果此元素不存在，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]将根据为指定的值的更新会先扫描`expiration`元素。 `beforeApplicationStartup`和`expiration`无法同时指定相同的部署清单中。  
  
## <a name="expiration"></a>过期  
 可选。 此元素是的子级`update`元素，并没有任何子级。 `beforeApplicationStartup`和`expiration`无法同时指定相同的部署清单中。 后，就会执行更新检查检测到更新的版本，最新版本将缓存的现有版本运行时。 在下一步启动然后安装新版本[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序。  
  
 `expiration`元素支持下列属性。  
  
|特性|说明|  
|---------------|-----------------|  
|`maximumAge`|必需。 标识如何旧当前的更新超过此期限后应用程序执行更新检查。 时间单位由`unit`属性。|  
|`unit`|必需。 标识的时间单位`maximumAge`。 有效的单位为`hours`， `days`，和`weeks`。|  
  
## <a name="deploymentprovider"></a>deploymentProvider  
 .NET Framework 2.0，此元素是必需的部署清单包含如果`subscription`部分。 .NET Framework 3.5 及更高版本，此元素是可选的并且将默认为服务器和发现的部署清单的文件路径。  
  
 此元素是 `deployment` 元素的子元素，并且包含以下元素。  
  
|特性|说明|  
|---------------|-----------------|  
|`codebase`|必需。 标识的位置，作为统一资源标识符 (URI)，用于更新的部署清单[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序。 此元素还允许转发基于 CD 的安装的更新位置。 必须是有效的 URI。|  
  
## <a name="remarks"></a>备注  
 你可以配置你[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序启动时，更新扫描后启动时，扫描更新或从不检查更新。 若要扫描上启动的更新，确保`beforeApplicationStartup`元素下存在`update`元素。 若要在启动后检查更新，请确保`expiration`元素下存在`update`元素，并提供了更新间隔。  
  
 若要禁用检查更新，删除`subscription`元素。 当你在要永远不会扫描更新的部署清单中指定时，可以仍手动检查更新通过使用<xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A>方法。  
  
 DeploymentProvider 如何与更新相关的详细信息，请参阅[选择 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)。  
  
## <a name="examples"></a>示例  
 下面的代码示例阐释了`deployment`中的元素[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署清单。 该示例使用`deploymentProvider`元素以指示首选的更新位置。  
  
```  
<deployment install="true" minimumRequiredVersion="2.0.0.0" mapFileExtension="true" trustUrlParameters="true">  
    <subscription>  
      <update>  
        <expiration maximumAge="6" unit="hours" />  
      </update>  
    </subscription>  
    <deploymentProvider codebase="http://www.adatum.com/MyApplication.application" />  
  </deployment>  
```  
  
## <a name="see-also"></a>另请参阅  
 [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)