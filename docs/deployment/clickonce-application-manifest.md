---
title: "ClickOnce 应用程序清单 | Microsoft Docs"
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
  - "应用程序清单 [ClickOnce]"
  - "ClickOnce, 应用程序清单"
ms.assetid: 29570cec-4e53-4660-a850-abc4fa150243
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ClickOnce 应用程序清单
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

清单 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 的应用程序是使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]，描述要部署的应用程序的 XML 文件。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序清单具有以下元素和属性。  
  
|元素|说明|特性|  
|--------|--------|--------|  
|[\<assembly\> 元素](../deployment/assembly-element-clickonce-application.md)|必选。  顶级元素。|`manifestVersion`|  
|[\<assemblyIdentity\> 元素](../deployment/assemblyidentity-element-clickonce-application.md)|必选。  标识 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序的主程序集。|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language`|  
|[\<trustInfo\> 元素](../deployment/trustinfo-element-clickonce-application.md)|标识应用程序的安全要求。|无|  
|[\<entryPoint\> 元素](../deployment/entrypoint-element-clickonce-application.md)|必选。  识别应用程序代码入口点。|`name`|  
|[\<dependency\> 元素](../deployment/dependency-element-clickonce-application.md)|必选。  标识运行应用程序所需的每个依赖项。  还可以选择标识需要预安装的程序集。|无|  
|[\<file\> 元素](../Topic/%3Cfile%3E%20Element%20\(ClickOnce%20Application\).md)|可选。  标识应用程序使用的每个非程序集文件。  可以包括与该文件关联的组件对象模型 \(COM\) 隔离数据。|`name`<br /><br /> `size`<br /><br /> `group`<br /><br /> `optional`<br /><br /> `writeableType`|  
|[\<fileAssociation\> 元素](../deployment/fileassociation-element-clickonce-application.md)|可选。  标识要与应用程序关联的文件扩展名。|`extension`<br /><br /> `description`<br /><br /> `progid`<br /><br /> `defaultIcon`|  
  
## 备注  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序清单文件标识使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署的应用程序。  有关 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]的更多信息，请参见[ClickOnce 安全和部署](../deployment/clickonce-security-and-deployment.md)。  
  
## 文件位置  
 清单 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 的应用程序特定于部署的一个版本。  为此，应单独存储它们与部署清单。  约定的做法是将应用程序清单放置在继关联版本之后命名的子目录中。  
  
 必须始终在部署之前对应用程序清单进行签名。  如果手动更改应用程序清单，则必须使用清单生成工具（mage.exet）重新对应用程序清单进行签名、更新部署清单并重新签名部署清单。  有关更多信息，请参见[演练：手动部署 ClickOnce 应用程序](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。  
  
## 文件名语法  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序清单文件的名称。 `assemblyIdentity` 元素应该应用程序的全名和扩展为已标识，后接一个扩展名为 .manifest。  例如，引用 Example.exe 应用程序的应用程序清单可能使用下面的文件名语法。  
  
 `example.exe.manifest`  
  
## 示例  
 下面的代码示例演示 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序的应用程序清单。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd" manifestVersion="1.0" xmlns:asmv3="urn:schemas-microsoft-com:asm.v3" xmlns:dsig="http://www.w3.org/2000/09/xmldsig#" xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2" xmlns="urn:schemas-microsoft-com:asm.v2" xmlns:asmv1="urn:schemas-microsoft-com:asm.v1" xmlns:asmv2="urn:schemas-microsoft-com:asm.v2" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">  
  <asmv1:assemblyIdentity name="My Application Deployment.exe" version="1.0.0.0" publicKeyToken="43cb1e8e7a352766" language="neutral" processorArchitecture="x86" type="win32" />  
  <application />  
  <entryPoint>  
    <assemblyIdentity name="MyApplication" version="1.0.0.0" language="neutral" processorArchitecture="x86" />  
    <commandLine file="MyApplication.exe" parameters="" />  
  </entryPoint>  
  <trustInfo>  
    <security>  
      <applicationRequestMinimum>  
        <PermissionSet Unrestricted="true" ID="Custom" SameSite="site" />  
        <defaultAssemblyRequest permissionSetReference="Custom" />  
      </applicationRequestMinimum>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <!--  
          UAC Manifest Options  
          If you want to change the Windows User Account Control level replace the   
          requestedExecutionLevel node with one of the following.  
  
        <requestedExecutionLevel  level="asInvoker" uiAccess="false" />  
        <requestedExecutionLevel  level="requireAdministrator" uiAccess="false" />  
        <requestedExecutionLevel  level="highestAvailable" uiAccess="false" />  
  
         If you want to utilize File and Registry Virtualization for backward   
         compatibility then delete the requestedExecutionLevel node.  
    -->  
        <requestedExecutionLevel level="asInvoker" uiAccess="false" />  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
  <dependency>  
    <dependentOS>  
      <osVersionInfo>  
        <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
      </osVersionInfo>  
    </dependentOS>  
  </dependency>  
  <dependency>  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
      <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.20506.0" />  
    </dependentAssembly>  
  </dependency>  
  <dependency>  
    <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="4096">  
      <assemblyIdentity name="MyApplication" version="1.0.0.0" language="neutral" processorArchitecture="x86" />  
      <hash>  
        <dsig:Transforms>  
          <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
        </dsig:Transforms>  
        <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
        <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>  
      </hash>  
    </dependentAssembly>  
  </dependency>  
<publisherIdentity name="CN=DOMAINCONTROLLER\UserMe" issuerKeyHash="18312a18a21b215ecf4cdb20f5a0e0b0dd263c08" /><Signature Id="StrongNameSignature" xmlns="http://www.w3.org/2000/09/xmldsig#">  
…  
</Signature></r:issuer></r:license></msrel:RelData></KeyInfo></Signature></asmv1:assembly>  
```  
  
## 请参阅  
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)