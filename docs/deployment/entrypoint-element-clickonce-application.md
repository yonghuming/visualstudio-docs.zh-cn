---
title: "&lt;入口点&gt;元素 （ClickOnce 应用程序） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#commandLine
- urn:schemas-microsoft-com:asm.v2#entryPoint
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <entryPoint> element [ClickOnce application manifest]
- manifests [ClickOnce], entryPoint element
ms.assetid: 10ad3083-10c1-4189-a870-9bba2eab244f
caps.latest.revision: "33"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: eb280684f0c06391bc6c0596093c01f260f685d3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ltentrypointgt-element-clickonce-application"></a>&lt;入口点&gt;元素 （ClickOnce 应用程序）
标识应为程序集时执行此[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]客户端计算机上运行应用程序。  
  
## <a name="syntax"></a>语法  
  
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
  
## <a name="elements-and-attributes"></a>元素和属性  
 `entryPoint` 元素是必需的，它位于 `urn:schemas-microsoft-com:asm.v2` 命名空间中。 可能仅有一个`entryPoint`应用程序清单中定义的元素。  
  
 `entryPoint`元素具有以下属性。  
  
|特性|描述|  
|---------------|-----------------|  
|`name`|可选。 .NET Framework 不使用此值。|  
  
 `entryPoint`具有以下元素。  
  
## <a name="assemblyidentity"></a>assemblyIdentity  
 必需。 角色`assemblyIdentity`中定义其属性和[ \<assemblyIdentity > 元素](../deployment/assemblyidentity-element-clickonce-application.md)。  
  
 `processorArchitecture`此元素的属性和`processorArchitecture`中定义特性`assemblyIdentity`在其他位置在应用程序清单必须匹配。  
  
## <a name="commandline"></a>命令行  
 必需。 必须为的子级`entryPoint`元素。 它不包含任何子元素，并具有以下属性。  
  
|特性|说明|  
|---------------|-----------------|  
|`file`|必需。 启动程序集的本地引用[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序。 此值不能包含正斜杠 （/） 或反斜杠 (\\) 路径分隔符。|  
|`parameters`|必需。 描述要使用的入口点执行的操作。 唯一有效的值是`run`; 如果提供的空白字符串，则`run`假定。|  
  
## <a name="customhostrequired"></a>customHostRequired  
 可选。 如果包含，则指定此部署包含将在自定义主机，内部部署的组件，并不是独立的应用程序。  
  
 如果此元素已存在，`assemblyIdentity`和`commandLine`元素必须还不存在。 如果它们，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]将在安装过程中引发验证错误。  
  
 此元素具有任何属性，也没有子级。  
  
## <a name="customux"></a>customUX  
 可选。 指定应用程序安装和维护的自定义安装程序，并不创建开始菜单项、 快捷方式或添加或删除程序条目。  
  
```  
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />  
```  
  
 包括 customUX 元素的应用程序必须提供自定义安装程序，则使用<xref:System.Deployment.Application.InPlaceHostingManager>类来执行安装操作。 此元素的应用程序无法通过双击其清单或 setup.exe 先决条件引导程序安装。 开始菜单项、 快捷方式和添加或删除程序条目，可以创建自定义安装程序。 如果自定义安装程序不会创建的添加或删除程序项，它必须存储提供的订阅标识符<xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A>属性，并使用户更高版本卸载该应用程序，通过调用<xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A>方法。 有关详细信息，请参阅[演练： 为 ClickOnce 应用程序创建自定义安装程序](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md)。  
  
## <a name="remarks"></a>备注  
 此元素标识的程序集和入口点[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序。  
  
 不能使用`commandLine`地将参数传递给你的应用程序在运行时。 你可以访问的查询字符串参数[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]从应用程序的部署<xref:System.AppDomain>。 有关详细信息，请参阅[如何： 在联机 ClickOnce 应用程序中检索查询字符串信息](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)。  
  
## <a name="example"></a>示例  
 下面的代码示例阐释了`entryPoint`的应用程序清单中的元素[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序。 此代码示例摘自更大的示例为提供[ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)主题。  
  
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
  
## <a name="see-also"></a>另请参阅  
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)