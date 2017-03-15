---
title: "&lt;entryPoint&gt; 元素（ClickOnce 应用程序） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#commandLine"
  - "urn:schemas-microsoft-com:asm.v2#entryPoint"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<entryPoint> 元素 [ClickOnce 应用程序清单]"
  - "清单 [ClickOnce], entryPoint 元素"
ms.assetid: 10ad3083-10c1-4189-a870-9bba2eab244f
caps.latest.revision: 33
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 33
---
# &lt;entryPoint&gt; 元素（ClickOnce 应用程序）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

标识在客户端计算机上运行此 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序时应该执行的程序集。  
  
## 语法  
  
```  
  
      <entryPoint  
   name  
>  
   <assemblyIdentity  
      name  
      version  
      processorArchitecture  
      language  
   />  
   <commandLine  
      file  
      parameters  
   />  
   <customHostRequired />  
   <customUX />  
</entryPoint>  
```  
  
## 元素和特性  
 `entryPoint` 元素是必需的，它位于 `urn:schemas-microsoft-com:asm.v2` 命名空间中。  一个应用程序清单中可能只定义了一个 `entryPoint` 元素。  
  
 `entryPoint` 元素具有下列特性。  
  
|特性|说明|  
|--------|--------|  
|`name`|可选。  .NET Framework 不使用此值。|  
  
 `entryPoint` 具有下列元素。  
  
## assemblyIdentity  
 必选。  `assemblyIdentity` 及其特性的作用在 [\<assemblyIdentity\> 元素](../deployment/assemblyidentity-element-clickonce-application.md)中定义。  
  
 此元素的 `processorArchitecture` 特性与应用程序清单中其他地方的 `assemblyIdentity` 中定义的 `processorArchitecture` 特性必须匹配。  
  
## commandLine  
 必选。  必须是 `entryPoint` 元素的子元素。  它不包含任何子元素，但具有下列特性。  
  
|特性|说明|  
|--------|--------|  
|`file`|必选。  对 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序的启动程序集的本地引用。  此值不能包含正斜杠 \(\/\) 或反斜杠 \(\\\) 路径分隔符。|  
|`parameters`|必选。  描述要通过入口点执行的操作。  唯一的有效值为 `run`；如果提供空白字符串，则假定值为 `run`。|  
  
## customHostRequired  
 可选。  如果包括，则指定此部署包含将在自定义宿主内部署的组件，并且不是独立应用程序。  
  
 如果此元素存在，则 `assemblyIdentity` 和 `commandLine` 元素也必须存在。  如果这两个元素存在，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 将在安装期间引发验证错误。  
  
 此元素没有特性，也没有子级。  
  
## customUX  
 可选。  指定通过自定义安装程序安装和维护应用程序，并且不会创建一个“开始”菜单项、快捷方式或“添加或删除程序“项。  
  
```  
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />  
```  
  
 包括 customUX 元素的应用程序必须提供使用 <xref:System.Deployment.Application.InPlaceHostingManager> 类执行安装操作的自定义安装程序。  采用此元素的应用程序无法通过双击其清单或 setup.exe 必备组件引导程序安装。  自定义安装程序可以创建开始菜单项、快捷方式和添加或删除程序项。  如果自定义安装程序没有创建“添加或删除程序”项，则它必须存储由 <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> 属性提供的订阅标识符，并使用户能够通过调用 <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A> 方法在以后卸载该应用程序。  有关更多信息，请参见[演练：为 ClickOnce 应用程序创建自定义安装程序](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md)。  
  
## 备注  
 此元素标识 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序的程序集和入口点。  
  
 运行时，不能使用 `commandLine` 将参数传递到应用程序中。  可以从该应用程序的 <xref:System.AppDomain> 访问 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署的查询字符串参数。  有关更多信息，请参见[如何：在联机 ClickOnce 应用程序中检索查询字符串信息](../Topic/How%20to:%20Retrieve%20Query%20String%20Information%20in%20an%20Online%20ClickOnce%20Application.md)。  
  
## 示例  
 下面的代码示例阐释 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序的应用程序清单中的 `entryPoint` 元素。  此代码示例摘自为 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)主题提供的一个更大示例。  
  
```  
<!-- Identify the main code entrypoint. -->  
<!-- This code runs the main method in an executable assembly. -->  
  <entryPoint>  
    <assemblyIdentity   
      name="MyApplication"   
      version="1.0.0.0"  
      language="neutral"  
      processorArchitecture="x86" />  
    <commandLine file="MyApplication.exe" parameters="" />  
  </entryPoint>  
```  
  
## 请参阅  
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)