---
title: "&lt;依赖项&gt;元素 （ClickOnce 应用程序） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#osVersionInfo
- urn:schemas-microsoft-com:asm.v2#os
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#dependency
- http://www.w3.org/2000/09/xmldsig#DigestValue
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
- urn:schemas-microsoft-com:asm.v2#dependentAssembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- manifests [ClickOnce], dependency element
- <dependency> element [ClickOnce application manifest]
ms.assetid: 09d6a1e0-60f8-4fbd-843b-8e49ee3115a3
caps.latest.revision: "34"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 7a0604113161fed432219f84ac6c4d8a6a4d7666
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ltdependencygt-element-clickonce-application"></a>&lt;依赖项&gt;元素 （ClickOnce 应用程序）
标识所需的应用程序的平台或程序集依赖项。  
  
## <a name="syntax"></a>语法  
  
```  
  
      <dependency>  
   <dependentOS  
      supportURL  
      description  
   >  
      <osVersionInfo>  
         <os  
            majorVersion  
            minorVersion  
            buildNumber  
            servicePackMajor  
            servicePackMinor  
            productType  
            suiteType  
         />   
      </osVersionInfo>  
   </dependentOS>  
   <dependentAssembly  
      dependencyType  
      allowDelayedBinding  
      group  
      codeBase  
      size  
   >  
      <assemblyIdentity  
         name  
         version  
         processorArchitecture  
         language  
      >  
         <hash>  
            <dsig:Transforms>  
               <dsig:Transform  
                  Algorithm  
            />  
            </dsig:Transforms>  
            <dsig:DigestMethod />  
            <dsig:DigestValue>  
            </dsig:DigestValue>  
    </hash>  
  
      </assemblyIdentity>  
   </dependentAssembly>  
</dependency>  
```  
  
## <a name="elements-and-attributes"></a>元素和属性  
 `dependency`元素是必需的。 可能存在的多个实例`dependency`相同的应用程序清单中。  
  
 `dependency`元素没有属性，并包含以下子元素。  
  
### <a name="dependentos"></a>dependentOS  
 可选。 包含`osVersionInfo`元素。 `dependentOS`和`dependentAssembly`元素是互相排斥： 一个或另一个必须存在`dependency`元素，但不是两者。  
  
 `dependentOS`支持以下属性。  
  
|特性|描述|  
|---------------|-----------------|  
|`supportUrl`|可选。 指定的依赖平台的支持 URL。 如果找到所需的平台，将向用户显示此 URL。|  
|`description`|可选。 中的可读的窗体中，描述所描述的操作系统`dependentOS`元素。|  
  
### <a name="osversioninfo"></a>osVersionInfo  
 必需。 此元素是 `dependentOS` 元素的子元素，并且包含 `os` 元素。 此元素没有属性。  
  
### <a name="os"></a>操作系统  
 必需。 此元素是 `osVersionInfo` 元素的子元素。 此元素具有以下属性。  
  
|特性|说明|  
|---------------|-----------------|  
|`majorVersion`|必需。 指定的操作系统的主版本号。|  
|`minorVersion`|必需。 指定的操作系统的次版本号。|  
|`buildNumber`|必需。 指定的操作系统的生成号。|  
|`servicePackMajor`|必需。 指定服务包的操作系统的主版本号。|  
|`servicePackMinor`|可选。 指定服务包的操作系统的次版本号。|  
|`productType`|可选。 标识的产品类型值。 有效值为 `server`、`workstation` 和 `domainController`。 例如，对于 Windows 2000 Professional，此属性的值是`workstation`。|  
|`suiteType`|可选。 标识系统或系统的配置类型上可用的产品套件。 有效值为`backoffice`， `blade`， `datacenter`， `enterprise`， `home`， `professional`， `smallbusiness`， `smallbusinessRestricted`，和`terminal`。 例如，对于 Windows 2000 Professional，此属性的值是`professional`。|  
  
### <a name="dependentassembly"></a>dependentAssembly  
 可选。 包含`assemblyIdentity`元素。 `dependentOS`和`dependentAssembly`元素是互相排斥： 一个或另一个必须存在`dependency`元素，但不是两者。  
  
 `dependentAssembly`具有以下属性。  
  
|特性|说明|  
|---------------|-----------------|  
|`dependencyType`|必需。 指定的依赖关系类型。 有效值为 `preprequisite` 和 `install`。 `install`作为的一部分安装的程序集[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序。 A`prerequisite`程序集必须位于全局程序集缓存 (GAC) 之前[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]可以安装应用程序。|  
|`allowDelayedBinding`|必需。 指定是否能以编程方式在运行时加载程序集。|  
|`group`|可选。 如果`dependencyType`属性设置为`install`，指定该仅按需安装的一组命名的程序集。 有关详细信息，请参阅[演练：在设计器中使用 ClickOnce 部署 API 按需下载程序集](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md)。<br /><br /> 如果设置为`framework`和`dependencyType`属性设置为`prerequisite`，将程序集指定为.NET Framework 的一部分。 全局件缓存 (GAC) 时不会检查此程序集上安装[!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)]及更高版本。|  
|`codeBase`|需要时`dependencyType`属性设置为`install`。 依赖程序集的路径。 可能是绝对路径，或者是相对该清单的代码路径基。 此路径必须是有效的 URI 中的程序集清单的顺序才能有效。|  
|`size`|需要时`dependencyType`属性设置为`install`。 依赖程序集，以字节为单位的大小。|  
  
### <a name="assemblyidentity"></a>assemblyIdentity  
 必需。 此元素是 `dependentAssembly` 元素的子元素，并且包含下列元素。  
  
|特性|说明|  
|---------------|-----------------|  
|`name`|必需。 标识应用程序的名称。|  
|`version`|必需。 采用以下格式指定应用程序的版本号：`major.minor.build.revision`|  
|`publicKeyToken`|可选。 指定的 16 个字符的十六进制字符串表示的最后 8 个字节`SHA-1`的应用程序集签名的公钥的哈希值。 用于对目录进行签名的公钥必须是 2048 位或的详细信息。|  
|`processorArchitecture`|可选。 指定处理器。 有效值为`x86`适用于 32 位 Windows 和`I64`适用于 64 位 Windows。|  
|`language`|可选。 标识由两部分语言代码，例如 EN-US，程序集。|  
  
### <a name="hash"></a>hash  
 `hash`元素是可选的子`assemblyIdentity`元素。 `hash`元素没有任何特性。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]使用应用程序中的所有文件的哈希算法作为一种安全检查，以确保部署之后的任何文件发生更改。 如果`hash`元素不包含，则不会执行此检查。 因此，省略`hash`元素不建议。  
  
### <a name="dsigtransforms"></a>dsig:Transforms  
 `dsig:Transforms`元素是必需的子`hash`元素。 `dsig:Transforms`元素没有任何特性。  
  
### <a name="dsigtransform"></a>dsig:Transform  
 `dsig:Transform`元素是必需的子`dsig:Transforms`元素。 `dsig:Transform`元素具有以下属性。  
  
|特性|描述|  
|---------------|-----------------|  
|`Algorithm`|用来计算此文件的摘要的算法。 当前使用的唯一值[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]是`urn:schemas-microsoft-com:HashTransforms.Identity`。|  
  
### <a name="dsigdigestmethod"></a>dsig:DigestMethod  
 `dsig:DigestMethod`元素是必需的子`hash`元素。 `dsig:DigestMethod`元素具有以下属性。  
  
|特性|描述|  
|---------------|-----------------|  
|`Algorithm`|用来计算此文件的摘要的算法。 当前使用的唯一值[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]是`http://www.w3.org/2000/09/xmldsig#sha1`。|  
  
### <a name="dsigdigestvalue"></a>dsig:DigestValue  
 `dsig:DigestValue`元素是必需的子`hash`元素。 `dsig:DigestValue`元素没有任何特性。 其文本值是指定的文件的计算哈希。  
  
## <a name="remarks"></a>备注  
 应用程序使用的所有程序集必须具有相应`dependency`元素。 依赖程序集不包括程序集必须预先安装在全局程序集缓存中作为平台程序集。  
  
## <a name="example"></a>示例  
 下面的代码示例阐释了`dependency`中的元素[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序清单。 此代码示例摘自更大的示例为提供[ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)主题。  
  
```  
<dependency>  
  <dependentOS>  
    <osVersionInfo>  
      <os   
        majorVersion="4"   
        minorVersion="10"   
        buildNumber="0"   
        servicePackMajor="0" />  
    </osVersionInfo>  
  </dependentOS>  
</dependency>  
<dependency>  
  <dependentAssembly  
    dependencyType="preRequisite"  
    allowDelayedBinding="true">  
    <assemblyIdentity  
      name="Microsoft.Windows.CommonLanguageRuntime"  
      version="4.0.20506.0" />  
  </dependentAssembly>  
</dependency>  
  
<dependency>  
  <dependentAssembly  
    dependencyType="install"  
    allowDelayedBinding="true"  
    codebase="MyApplication.exe"  
    size="4096">  
    <assemblyIdentity  
      name="MyApplication"  
      version="1.0.0.0"  
      language="neutral"  
      processorArchitecture="x86" />  
    <hash>  
      <dsig:Transforms>  
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
      </dsig:Transforms>  
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
      <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>  
    </hash>  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="see-also"></a>另请参阅  
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)   
 [\<依赖项 > 元素](../deployment/dependency-element-clickonce-deployment.md)