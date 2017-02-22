---
title: "&lt;dependency&gt; 元素（ClickOnce 应用程序） | Microsoft Docs"
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
  - "urn:schemas-microsoft-com:asm.v2#osVersionInfo"
  - "urn:schemas-microsoft-com:asm.v2#os"
  - "http://www.w3.org/2000/09/xmldsig#Transform"
  - "urn:schemas-microsoft-com:asm.v2#dependency"
  - "http://www.w3.org/2000/09/xmldsig#DigestValue"
  - "urn:schemas-microsoft-com:asm.v2#assemblyIdentity"
  - "http://www.w3.org/2000/09/xmldsig#DigestMethod"
  - "http://www.w3.org/2000/09/xmldsig#Transforms"
  - "urn:schemas-microsoft-com:asm.v2#hash"
  - "urn:schemas-microsoft-com:asm.v2#dependentAssembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<dependency> 元素 [ClickOnce 应用程序清单]"
  - "清单 [ClickOnce], dependency 元素"
ms.assetid: 09d6a1e0-60f8-4fbd-843b-8e49ee3115a3
caps.latest.revision: 34
caps.handback.revision: 34
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;dependency&gt; 元素（ClickOnce 应用程序）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

标识应用程序所需的平台或程序集依赖项。  
  
## 语法  
  
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
  
## 元素和特性  
 `dependency` 元素是必需的。  在同一应用程序清单中可能有多个 `dependency` 实例。  
  
 `dependency` 元素没有特性，但包含下列子元素。  
  
### dependentOS  
 可选。  包含 `osVersionInfo` 元素。  `dependentOS` 元素和 `dependentAssembly` 元素是互斥的：对于 `dependency` 元素，只能存在其中一个元素，而不能同时存在这两个元素。  
  
 `dependentOS` 支持下列特性。  
  
|特性|说明|  
|--------|--------|  
|`supportUrl`|可选。  指定依赖平台的支持 URL。  如果找到必需的平台，此 URL 将显示给用户。|  
|`description`|可选。  以可读的形式描述 `dependentOS` 元素描述的操作系统。|  
  
### osVersionInfo  
 必选。  此元素是 `dependentOS` 元素的子元素，它包含 `os` 元素。  此元素没有特性。  
  
### os  
 必选。  此元素是 `osVersionInfo` 元素的子元素。  此元素具有下列特性。  
  
|特性|说明|  
|--------|--------|  
|`majorVersion`|必选。  指定 OS 的主版本号。|  
|`minorVersion`|必选。  指定 OS 的次版本号。|  
|`buildNumber`|必选。  指定 OS 的生成号。|  
|`servicePackMajor`|必选。  指定 OS 的 Service Pack 主版本号。|  
|`servicePackMinor`|可选。  指定 OS 的 Service Pack 次版本号。|  
|`productType`|可选。  标识产品类型值。  有效值为：`server`、`workstation` 和 `domainController`。  例如，对于 Windows 2000 Professional，此特性值为 `workstation`。|  
|`suiteType`|可选。  标识系统或系统配置类型上可用的产品套件。  有效值为 `backoffice`、`blade`、`datacenter`、`enterprise`、`home`、`professional`、`smallbusiness`、`smallbusinessRestricted` 和 `terminal`。  例如，对于 Windows 2000 Professional，此特性值为 `professional`。|  
  
### dependentAssembly  
 可选。  包含 `assemblyIdentity` 元素。  `dependentOS` 元素和 `dependentAssembly` 元素是互斥的：对于 `dependency` 元素，只能存在其中一个元素，而不能同时存在这两个元素。  
  
 `dependentAssembly` 具有下列特性。  
  
|特性|说明|  
|--------|--------|  
|`dependencyType`|必选。  指定依赖关系类型。  有效值为 `preprequisite` 和 `install`。  `install` 程序集是作为 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序的一部分安装的。  `prerequisite` 程序集必须存在于全局程序集缓存 \(GAC\) 中，之后才能安装 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序。|  
|`allowDelayedBinding`|必选。  指定是否可以通过编程方式在运行时加载程序集。|  
|`group`|可选。  如果 `dependencyType` 特性设置为 `install`，则指定一组仅按需安装的程序集。  有关更多信息，请参见 [演练：在设计器中使用 ClickOnce 部署 API 按需下载程序集](../Topic/Walkthrough:%20Downloading%20Assemblies%20on%20Demand%20with%20the%20ClickOnce%20Deployment%20API%20Using%20the%20Designer.md)。<br /><br /> 如果设置为 `framework`，且 `dependencyType` 特性设置为 `prerequisite`，则将该程序集指定为 .NET Framework 的一部分。  在 [!INCLUDE[net_v40_short](../debugger/includes/net_v40_short_md.md)] 及更高版本上安装此程序集时，不为其检查全局程序集缓存 \(GAC\) 的情况。|  
|`codeBase`|`dependencyType` 特性设置为 `install` 时为必需。  指向依赖程序集的路径。  该路径可能是绝对路径，也可能是相对于清单基本代码的路径。  此路径必须是有效 URI，程序集清单才能有效。|  
|`size`|`dependencyType` 特性设置为 `install` 时为必需。  依赖程序集的大小，以字节为单位。|  
  
### assemblyIdentity  
 必选。  此元素是 `dependentAssembly` 元素的子元素，它具有下列特性。  
  
|特性|说明|  
|--------|--------|  
|`name`|必选。  标识应用程序的名称。|  
|`version`|必选。  指定应用程序的版本号，格式如下：`major.minor.build.revision`|  
|`publicKeyToken`|可选。  指定 16 个字符的十六进制字符串，该字符串表示公钥的 `SHA-1` 哈希值的后 8 个字节。使用该公钥，可以对应用程序或程序集进行签名。  用于对目录进行签名的公钥必须至少为 2048 位。|  
|`processorArchitecture`|可选。  指定处理器。  对于 32 位 Windows，有效值为 `x86`；对于 64 位 Windows，有效值为 `I64`。|  
|`language`|可选。  标识程序集的两部分语言代码，如 EN\-US。|  
  
### hash  
 `hash` 元素是 `assemblyIdentity` 元素的可选子元素。  `hash` 元素没有任何特性。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 使用应用程序中所有文件的算法哈希运算作为一种安全检查手段，以确保部署之后没有任何文件发生更改。  如果未包含 `hash` 元素，则不会执行此检查。因此不建议省略 `hash` 元素。  
  
### dsig:Transforms  
 `dsig:Transforms` 元素是 `hash` 元素必需的子元素。  `dsig:Transforms` 元素没有任何特性。  
  
### dsig:Transform  
 `dsig:Transform` 元素是 `dsig:Transforms` 元素必需的子元素。  `dsig:Transform` 元素具有以下特性。  
  
|特性|说明|  
|--------|--------|  
|`Algorithm`|用于计算此文件的摘要的算法。  目前，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 唯一使用的值是 `urn:schemas-microsoft-com:HashTransforms.Identity`。|  
  
### dsig:DigestMethod  
 `dsig:DigestMethod` 元素是 `hash` 元素必需的子元素。  `dsig:DigestMethod` 元素具有以下特性。  
  
|特性|说明|  
|--------|--------|  
|`Algorithm`|用于计算此文件的摘要的算法。  目前，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 唯一使用的值是 `http://www.w3.org/2000/09/xmldsig#sha1`。|  
  
### dsig:DigestValue  
 `dsig:DigestValue` 元素是 `hash` 元素必需的子元素。  `dsig:DigestValue` 元素没有任何特性。  它的文本值是为指定文件计算所得的哈希值。  
  
## 备注  
 应用程序使用的所有程序集都必须具有对应的 `dependency` 元素。  依赖程序集不包括需要作为平台程序集预安装在全局程序集缓存中的程序集。  
  
## 示例  
 下面的代码示例阐释 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序清单中的 `dependency` 元素。  此代码示例摘自为 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)主题提供的一个更大示例。  
  
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
  
## 请参阅  
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)   
 [\<dependency\> 元素](../deployment/dependency-element-clickonce-deployment.md)