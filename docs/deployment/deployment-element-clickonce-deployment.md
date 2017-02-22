---
title: "&lt;deployment&gt; 元素（ClickOnce 部署） | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#subscription"
  - "urn:schemas-microsoft-com:asm.v2#beforeApplicationStartup"
  - "urn:schemas-microsoft-com:asm.v2#deploymentProvider"
  - "urn:schemas-microsoft-com:asm.v2#update"
  - "urn:schemas-microsoft-com:asm.v2#deployment"
  - "urn:schemas-microsoft-com:asm.v2#expiration"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<deployment> 元素 [ClickOnce 部署清单]"
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
caps.latest.revision: 30
caps.handback.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;deployment&gt; 元素（ClickOnce 部署）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

标识用来部署更新并向系统公开的特性。  
  
## 语法  
  
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
  
## 元素和特性  
 `deployment` 元素是必需的，它位于 `urn:schemas-microsoft-com:asm.v1` 命名空间中。  它具有下列特性。  
  
|特性|说明|  
|--------|--------|  
|`install`|必选。  指定此应用程序是否在 Windows**“开始”**菜单和“控制面板”**“添加或删除程序”**应用程序中定义存在性。  有效值是 `true` 和 `false`。  如果为 `false`，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 将始终通过网络运行此应用程序的最新版本，但不识别 `subscription` 元素。|  
|`minimumRequiredVersion`|可选。  指定可以在客户端上运行的此应用程序的最低版本。  如果该应用程序的版本号低于部署清单中提供的版本号，将不会运行该应用程序。  版本号必须以 `N.N.N.N` 格式指定，其中，`N` 是无符号的整数。  如果 `install` 特性为 `false`，则不得设置 `minimumRequiredVersion`。|  
|`mapFileExtensions`|可选。  默认为 `false`。  如果为 `true`，部署中的所有文件都应具有 .deploy 的扩展名。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 将在从 Web 服务器下载这些文件之后立即去除它们的这个扩展名。  如果使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 发布应用程序，它将自动向所有文件添加此扩展名。  此参数允许从阻止传输以“不安全”扩展名（例如 .exe）结尾的文件的 Web 服务器下载 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署中的所有文件。|  
|`disallowUrlActivation`|可选。  默认为 `false`。  如果为 `true`，则阻止通过单击 URL 或在 Internet Explorer 中输入 URL 启动已安装的应用程序。  如果 `install` 特性不存在，则忽略此特性。|  
|`trustURLParameters`|可选。  默认为 `false`。  如果为 `true`，则允许 URL 包含要传入应用程序的查询字符串参数，非常类似于将命令行变量传递给命令行应用程序。  有关更多信息，请参见[如何：在联机 ClickOnce 应用程序中检索查询字符串信息](../Topic/How%20to:%20Retrieve%20Query%20String%20Information%20in%20an%20Online%20ClickOnce%20Application.md)。<br /><br /> 如果 `disallowUrlActivation` 特性为 `true`，则必须从清单中排除 `trustUrlParameters` 或将其显式设置为 `false`。|  
  
 `deployment` 元素还包含下列子元素。  
  
## Subscription — 订阅  
 可选。  包含 `update` 元素。  `subscription` 元素没有任何特性。  如果 `subscription` 元素不存在，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序将永远不检查更新。  如果 `deployment` 元素的 `install` 特性为 `false`，将会忽略 `subscription` 元素，因为通过网络启动的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序始终使用最新版本。  
  
## update  
 必选。  此元素是 `subscription` 元素的子元素，它包含 `beforeApplicationStartup` 元素或 `expiration` 元素。  不能在同一部署清单中同时指定 `beforeApplicationStartup` 和 `expiration`。  
  
 `update` 元素没有任何特性。  
  
## beforeApplicationStartup  
 可选。  此元素是 `update` 元素的子元素，它没有特性。  如果 `beforeApplicationStartup` 元素存在，那么当客户端处于联机状态时，应用程序将在 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 检查更新时被阻止。  如果此元素不存在，则 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 将首先根据为 `expiration` 元素指定的值检查更新。  不能在同一部署清单中同时指定 `beforeApplicationStartup` 和 `expiration`。  
  
## expiration  
 可选。  此元素是 `update` 元素的子元素，并且没有子元素。  不能在同一部署清单中同时指定 `beforeApplicationStartup` 和 `expiration`。  发生更新检查并检测到更新的版本时，新版本会在现有版本运行的情况下进行缓存。  然后新版本安装 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序的下一次启动。  
  
 `expiration` 元素支持下列特性。  
  
|特性|说明|  
|--------|--------|  
|`maximumAge`|必选。  标识当前更新的使用期限，超过此期限后，应用程序将执行更新检查。  时间单位由 `unit` 特性决定。|  
|`unit`|必选。  标识 `maximumAge` 的时间单位。  有效单位是 `hours`、`days` 和 `weeks`。|  
  
## deploymentProvider  
 对于 .NET Framework 2.0 而言，部署清单包含 `subscription` 节时需要此元素。  对于 .NET Framework 3.5 及更高版本而言，此元素是可选的，并且默认值将为在其中发现部署清单的服务器和文件路径。  
  
 此元素是 `deployment` 元素的子元素，它具有以下特性。  
  
|特性|说明|  
|--------|--------|  
|`codebase`|必选。  以统一资源标识符 \(URI\) 的形式标识用来更新 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序的部署清单的位置。  此元素还可以用来转发光盘安装的更新位置。  必须是有效的 URI。|  
  
## 备注  
 可以将 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序配置为在启动时检查更新、在启动后检查更新或永不检查更新。  若要在启动时检查更新，请确保 `update` 元素下面存在 `beforeApplicationStartup` 元素。  若要在启动后检查更新，请确保 `update` 元素下面存在 `expiration` 元素，并且提供了更新间隔。  
  
 若要禁止检查更新，请移除 `subscription` 元素。  当在部署清单中指定了永不检查更新时，仍然可以使用 <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> 方法手动检查更新。  
  
 有关 deploymentProvider 与更新有何关系的更多信息，请参见[选择 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)。  
  
## 示例  
 下面的代码示例阐释了 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署清单中的 `deployment` 元素。  该示例使用 `deploymentProvider` 元素指示首选的更新位置。  
  
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
  
## 请参阅  
 [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)