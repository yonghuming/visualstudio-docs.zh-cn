---
title: "如何：为 ClickOnce 部署中的各个系统必备项指定一个支持 URL | Microsoft Docs"
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
  - "ClickOnce 部署, 系统必备"
  - "ClickOnce 部署, URL"
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 如何：为 ClickOnce 部署中的各个系统必备项指定一个支持 URL
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署可以测试必须在客户端计算机上可用以便 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序可以运行的许多系统必备组件。  这些系统必备组件包括所需的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 最低版本、操作系统版本以及必须预先安装在全局程序集缓存 \(GAC\) 中的任何程序集。  但是，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 自身无法安装任何这些系统必备组件；如果未找到系统必备组件，则它仅停止安装并显示一个对话框来解释安装失败的原因。  
  
 安装系统必备有两种方法。  您可以使用引导程序应用程序来安装它们。  或者，可以为个别系统必备指定支持 URL；如果未找到系统必备，将在对话框上向用户显示该 URL。  该 URL 引用的页面可以包含有关安装必需的系统必备说明的链接。  如果应用程序没有为单个系统必备组件指定支持 URL，则 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 会显示部署清单中为整个应用程序指定的支持 URL（若已定义的话）。  
  
 虽然 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、Mage.exe 和 MageUI.exe 均可用于生成 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署，但这些工具都不直接支持为个别系统必备组件指定支持 URL。  本文档描述了如何修改部署的应用程序清单和部署清单以包含这些支持 URL。  
  
### 为单个系统必备指定支持 URL  
  
1.  在文本编辑器中，打开 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序的应用程序清单（.manifest 文件）。  
  
2.  对于操作系统必备，请将 `supportUrl` 特性添加到 `dependentOS` 元素中：  
  
    ```  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3.  对于特定版本的公共语言运行时的系统必备，请将 `supportUrl` 特性添加到指定公共语言运行时依赖项的 `dependentAssembly` 项中：  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4.  对于必须预先安装在全局程序集缓存中的程序集的系统必备，请设置指定必需程序集的 `dependentAssembly` 元素的 `supportUrl`：  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5.  可选。  对于面向 .NET Framework 4 的应用程序，在文本编辑器中打开 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序的部署清单（.application 文件）。  
  
6.  对于 .NET Framework 4 系统必备组件，请将 `supportUrl` 特性添加到 `compatibleFrameworks` 元素中：  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7.  手动修改应用程序清单后，必须使用数字证书对应用程序清单进行重新签名，然后更新部署清单并重新签名。  由于使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 重新生成这些文件会清除手动更改，因此，必须使用 Mage.exe 或 MageUI.exe SDK 工具来完成此项任务。  有关使用 Mage.exe 对清单重新签名的更多信息，请参见[如何：为应用程序和部署清单重新签名](../deployment/how-to-re-sign-application-and-deployment-manifests.md)。  
  
## .NET Framework 安全性  
 如果应用程序被标记为以部分信任运行，则对话框中不显示支持 URL。  
  
## 请参阅  
 [Mage.exe（清单生成和编辑工具）](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [演练：手动部署 ClickOnce 应用程序](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<compatibleFrameworks\> 元素](../Topic/%3CcompatibleFrameworks%3E%20Element%20\(ClickOnce%20Deployment\).md)   
 [ClickOnce 和 Authenticode](../deployment/clickonce-and-authenticode.md)   
 [应用程序部署必备](../deployment/application-deployment-prerequisites.md)