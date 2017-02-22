---
title: "&lt;dependency&gt; 元素（ClickOnce 部署） | Microsoft Docs"
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
  - "<dependency> 元素 [ClickOnce 部署清单]"
ms.assetid: 9b4d2082-0347-4922-ac70-85f11b913039
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;dependency&gt; 元素（ClickOnce 部署）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

标识要安装的应用程序的版本以及应用程序清单的位置。  
  
## 语法  
  
```  
  
      <dependency>   
   <dependentAssembly  
      preRequisite  
      visible  
      dependencyType  
      codeBase  
      size  
   >   
      <assemblyIdentity   
         name   
         version   
         publicKeyToken   
         processorArchitecture   
         language  
         type  
      />   
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
  
   </dependentAssembly>   
</dependency>  
```  
  
## 元素和特性  
 `dependency` 元素是必需的。  它没有特性。  部署清单可以有多个 `dependency` 元素。  
  
 `dependency` 元素通常表示主应用程序中依赖于 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序内包含的程序集的项。  如果您的 Main.exe 应用程序使用名为 DotNetAssembly.dll 的程序集，则该程序集必须在依赖项节中列出。  但是，dependency 也可以表示其他类型的依赖项，如特定版本的公共语言运行时的依赖项、全局程序集缓存 \(GAC\) 中的程序集的依赖项或 COM 对象的依赖项。  由于它是一项无人参与的部署技术，因此 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 无法启动下载和安装这些类型的依赖项，但是，如果一个或多个指定的依赖项不存在，则它会阻止应用程序运行。  
  
## dependentAssembly  
 必选。  此元素包含 `assemblyIdentity` 元素。  下表显示了 `dependentAssembly` 支持的特性。  
  
|特性|说明|  
|--------|--------|  
|`preRequisite`|可选。  指定此程序集应当预先存在于 GAC 中。  有效值是 `true` 和 `false`。  如果为 `true`，并且指定的程序集不存在于 GAC 中，则应用程序将无法运行。|  
|`visible`|可选。  标识顶级应用程序标识，包括其依赖项。  由 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 在内部使用，以管理应用程序存储和激活。|  
|`dependencyType`|必选。  此依赖项和应用程序之间的关系。  有效值为：<br /><br /> -   `install`。  组件表示独立于当前应用程序的单独安装。<br />-   `preRequisite`。  组件是当前应用程序所必需的。|  
|`codebase`|可选。  应用程序清单的完整路径。|  
|`size`|可选。  应用程序清单的大小，以字节为单位。|  
  
## assemblyIdentity  
 必选。  此元素是 `dependentAssembly` 元素的子元素。  `assemblyIdentity` 的内容必须与 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序清单中描述的内容相同。  下表显示了 `assemblyIdentity` 元素的特性。  
  
|特性|说明|  
|--------|--------|  
|`Name`|必选。  标识应用程序的名称。|  
|`Version`|必选。  指定应用程序的版本号，格式如下：`major.minor.build.revision`|  
|`publicKeyToken`|必选。  指定 16 个字符的十六进制字符串，该字符串表示公钥的 SHA\-1 哈希值的后 8 个字节。使用该公钥，可以对应用程序或程序集进行签名。  用于签名的公钥必须至少为 2048 位。|  
|`processorArchitecture`|必选。  指定微处理器。  对于 32 位 Windows，有效值为 `x86`；对于 64 位 Windows，有效值为 `IA64`。|  
|`Language`|可选。  标识程序集的两部分语言代码。  例如，EN\-US 代表英语（美国）。  默认值为 `neutral`。  此元素在 `asmv2` 命名空间中。|  
|`type`|可选。  用于与 Windows 并行安装技术的向后兼容性。  唯一允许的值是 `win32`。|  
  
## hash  
 `hash` 元素是 `file` 元素的可选子元素。  `hash` 元素没有任何特性。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 使用应用程序中所有文件的算法哈希运算作为一种安全检查手段，以确保部署之后没有任何文件发生更改。  如果未包含 `hash` 元素，则不会执行此检查。因此不建议省略 `hash` 元素。  
  
## dsig:Transforms  
 `dsig:Transforms` 元素是 `hash` 元素必需的子元素。  `dsig:Transforms` 元素没有任何特性。  
  
## dsig:Transform  
 `dsig:Transform` 元素是 `dsig:Transforms` 元素必需的子元素。  下表显示了 `dsig:Transform` 元素的特性。  
  
|特性|说明|  
|--------|--------|  
|`Algorithm`|用于计算此文件的摘要的算法。  目前，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 唯一使用的值是 `urn:schemas-microsoft-com:HashTransforms.Identity`。|  
  
## dsig:DigestMethod  
 `dsig:DigestMethod` 元素是 `hash` 元素必需的子元素。  下表显示了 `dsig:DigestMethod` 元素的特性。  
  
|特性|说明|  
|--------|--------|  
|`Algorithm`|用于计算此文件的摘要的算法。  目前，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 唯一使用的值是 `http://www.w3.org/2000/09/xmldsig#sha1`。|  
  
## dsig:DigestValue  
 `dsig:DigestValue` 元素是 `hash` 元素必需的子元素。  `dsig:DigestValue` 元素没有任何特性。  它的文本值是为指定文件计算所得的哈希值。  
  
## 备注  
 部署清单通常只有一个 `assemblyIdentity` 元素，该元素标识应用程序清单的名称和版本。  
  
## 示例  
 下面的代码示例演示 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署清单中的 `dependency` 元素。  
  
```  
<!-- Identify the assembly dependencies -->  
<dependency>  
  <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="16384">  
    <assemblyIdentity name="MyApplication" version="0.0.0.0" cultural="neutral" processorArchitecture="msil" />  
    <hash>  
      <dsig:Transforms>  
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
      </dsig:Transforms>  
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
       <dsig:DigestValue>YzXYZJAvj9pgAG3y8jXUjC7AtHg=</dsig:DigestValue>  
    </hash>  
  </dependentAssembly>  
</dependency>  
```  
  
## 示例  
 下面的代码示例指定了 GAC 中已安装的程序集的依赖项。  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />  
  </dependentAssembly>  
</dependency>  
```  
  
## 示例  
 下面的代码示例指定了特定版本的公共语言运行时的依赖项。  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50215.0" />  
  </dependentAssembly>  
</dependency>  
```  
  
## 示例  
 下面的代码示例指定了操作系统依赖项。  
  
```  
<dependency>  
   <dependentOS supportUrl="http://www.microsoft.com" description="Microsoft Windows Operating System">  
      <osVersionInfo>  
         <os majorVersion="4" minorVersion="10" />  
      </osVersionInfo>  
   </dependentOS>  
</dependency>  
```  
  
## 请参阅  
 [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)   
 [\<dependency\> 元素](../deployment/dependency-element-clickonce-application.md)