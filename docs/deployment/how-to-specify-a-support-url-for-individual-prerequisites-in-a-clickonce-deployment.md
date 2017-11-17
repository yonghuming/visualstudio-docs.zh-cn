---
title: "如何： 为 ClickOnce 部署中的各个系统必备项指定一个支持 URL |Microsoft 文档"
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
- ClickOnce deployment, prerequisites
- ClickOnce deployment, URLs
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
caps.latest.revision: "10"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 2335c0279c8e7a23e1b514a8264651e73fedebfc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>如何：为 ClickOnce 部署中的各个系统必备项指定一个支持 URL
A[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署可以为大量的系统必备组件，必须在客户端计算机上可测试[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]要运行应用程序。 其中包括所需的最低版本[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]，以及操作系统，必须预先安装在全局程序集缓存 (GAC 中) 的任何程序集的版本。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]但是，无法安装任何这些系统必备组件然后重试。如果未找到系统必备组件，它只需暂停安装并显示一个对话框，以解释安装失败的原因。  
  
 有两种方法来安装系统必备组件。 你可以安装它们使用的引导程序应用程序。 或者，你可以指定各个系统必备项，如果找不到到系统必备组件到在对话框中的用户显示的支持 URL。 该 URL 所引用的页可以包含用于安装必备组件的说明的链接。 如果应用程序未指定一个单独的必备组件，支持 URL[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]显示作为一个整体，应用程序的部署清单中指定的支持 URL，如果已定义。  
  
 虽然[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，Mage.exe 和 MageUI.exe 所有可用来生成[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署，这些工具的任何直接支持指定各个系统必备项的支持 URL。 本文档介绍如何修改部署的应用程序清单和部署清单，以包括这些支持 Url。  
  
### <a name="specifying-a-support-url-for-an-individual-prerequisite"></a>指定一个单独的必备组件的支持 URL  
  
1.  打开应用程序清单 （.manifest 文件） 你[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]在文本编辑器应用程序。  
  
2.  对于操作系统系统必备组件，添加`supportUrl`属性设为`dependentOS`元素：  
  
    ```  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3.  对于某一版本的公共语言运行时的先决条件，添加`supportUrl`属性设为`dependentAssembly`条目指定了公共语言运行时依赖项：  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4.  对于必须预先安装在全局程序集缓存程序集的先决条件，设置`supportUrl`为`dependentAssembly`指定所需的程序集的元素：  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5.  可选。 对于面向.NET Framework 4 中，应用程序打开部署清单 （.application 文件） 的你[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]在文本编辑器应用程序。  
  
6.  对于.NET Framework 4 系统必备组件，添加`supportUrl`属性设为`compatibleFrameworks`元素：  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7.  一旦您手动更改了应用程序清单，必须使用数字证书，应用程序清单重新签名，然后更新并且重新签名的部署清单。 你必须使用 Mage.exe 或 MageUI.exe SDK 工具来完成此任务中的，重新生成使用这些文件作为[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]清除你手动更改。 有关使用 Mage.exe 清单进行重新签名的详细信息，请参阅[如何： 重新签名的应用程序和部署清单](../deployment/how-to-re-sign-application-and-deployment-manifests.md)。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 如果应用程序被标记为在部分信任中运行时，支持 URL 不被显示在对话框中。  
  
## <a name="see-also"></a>另请参阅  
 [Mage.exe（清单生成和编辑工具）](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [演练：手动部署 ClickOnce 应用程序](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<compatibleFrameworks > 元素](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [ClickOnce 和 Authenticode](../deployment/clickonce-and-authenticode.md)   
 [应用程序部署必备](../deployment/application-deployment-prerequisites.md)