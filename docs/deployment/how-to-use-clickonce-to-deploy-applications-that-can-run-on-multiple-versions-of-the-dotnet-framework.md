---
title: "如何： 使用 ClickOnce 来部署可在多个版本的.NET Framework 运行的应用程序 |Microsoft 文档"
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
- ClickOnce applications, multiple .NET Framework versions
- ClickOnce deployment, multiple .NET Framework versions
- deploying applications [ClickOnce], multiple .NET Framework versions
ms.assetid: e0a8c330-21bc-4eb2-b936-fd0f3c3221f1
caps.latest.revision: "17"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: d634d320df50dafc203ea1b1b4c8366ae3e24a41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-use-clickonce-to-deploy-applications-that-can-run-on-multiple-versions-of-the-net-framework"></a>如何：使用 ClickOnce 部署可在多个版本的 .NET Framework 上运行的应用程序
你可以部署通过使用 ClickOnce 部署技术面向.NET Framework 的多个版本的应用程序。 这要求你生成并更新应用程序和部署清单。  
  
> [!NOTE]
>  更改要面向的.NET framework 的多个版本的应用程序之前，应确保你的应用程序运行使用.NET framework 的多个版本。 版本的公共语言运行时之间的差异[!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)]与.NET Framework 2.0、.NET Framework 3.0 和.NET Framework 3.5。  
  
 此过程需要执行下列步骤：  
  
1.  生成应用程序和部署清单。  
  
2.  更改部署清单以列出的多个.NET Framework 版本。  
  
3.  更改 app.config 文件以列出兼容的.NET Framework 运行时版本。  
  
4.  更改要标记为.NET Framework 程序集的依赖程序集的应用程序清单。  
  
5.  对应用程序清单进行签名。  
  
6.  更新和部署清单进行签名。  
  
### <a name="to-generate-the-application-and-deployment-manifests"></a>若要生成应用程序和部署清单  
  
-   使用发布向导或项目设计器的发布页面发布应用程序并生成应用程序和部署清单文件。 有关详细信息，请参阅[如何： 发布 ClickOnce 应用程序使用发布向导](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)或[发布页上，项目设计器](../ide/reference/publish-page-project-designer.md)。  
  
### <a name="to-change-the-deployment-manifest-to-list-the-multiple-net-framework-versions"></a>若要更改部署清单以列出的多个.NET Framework 版本  
  
1.  在发布目录中，通过使用 Visual Studio 中的 XML 编辑器中打开部署清单。 部署清单具有.application 文件扩展名。  
  
2.  将 XML 代码之间`<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">`和`</compatibleFrameworks>`列出你的应用程序支持的.NET Framework 版本的 xml 元素。  
  
     下表显示了一些可用的.NET Framework 版本以及可以添加到部署清单的相应 XML。  
  
    |.NET Framework 版本|XML|  
    |----------------------------|---------|  
    |4 客户端|\<framework targetVersion ="4.0"profile ="客户端"supportedRuntime ="4.0.30319"/ >|  
    |4 完整|\<framework targetVersion ="4.0"profile = 完全 supportedRuntime ="4.0.30319"/ >|  
    |3.5 客户端|\<framework targetVersion ="3.5"profile ="客户端"supportedRuntime ="2.0.50727"/ >|  
    |3.5 完整|\<framework targetVersion ="3.5"profile = 完全 supportedRuntime ="2.0.50727"/ >|  
    |3.0|\<framework targetVersion ="3.0"supportedRuntime ="2.0.50727"/ >|  
  
### <a name="to-change-the-appconfig-file-to-list-the-compatible-net-framework-runtime-versions"></a>若要更改 app.config 文件，若要列出兼容的.NET Framework 运行时版本  
  
1.  在解决方案资源管理器，通过使用 Visual Studio 中的 XML 编辑器中打开 App.config 文件。  
  
2.  替换 （或添加） 之间的 XML 代码`<startup>`和`</startup>`与列出的受支持的.NET Framework 运行时，你的应用程序的 XML 元素。  
  
     下表显示了一些可用的.NET Framework 版本以及可以添加到部署清单的相应 XML。  
  
    |.NET framework 运行时版本|XML|  
    |------------------------------------|---------|  
    |4 客户端|\<supportedRuntime 版本 ="v4.0.30319"sku ="。NETFramework，Version = v4.0，配置文件 = 客户端"/ >|  
    |4 完整|\<supportedRuntime 版本 ="v4.0.30319"sku ="。NETFramework，Version = v4.0"/ >|  
    |3.5 完整|\<supportedRuntime version="v2.0.50727"/ >|  
    |3.5 客户端|\<supportedRuntime 版本 ="v2.0.50727"sku ="客户端"/ >|  
  
### <a name="to-change-the-application-manifest-to-mark-dependent-assemblies-as-net-framework-assemblies"></a>若要更改要标记为.NET Framework 程序集的依赖程序集的应用程序清单  
  
1.  在发布目录中，通过使用 Visual Studio 中的 XML 编辑器中打开应用程序清单。 部署清单具有.manifest 文件扩展名。  
  
2.  添加`group="framework"`到 sentinel 程序集的依赖项 XML (`System.Core`， `WindowsBase`， `Sentinel.v3.5Client`，和`System.Data.Entity`)。 例如，XML 应如下所示：  
  
    ```  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">  
    ```  
  
3.  更新的版本号`<assemblyIdentity>`Microsoft.Windows.CommonLanguageRuntime 元素是最小公分.NET Framework 的版本编号。 例如，如果该应用程序面向.NET Framework 3.5 和[!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)]，使用 2.0.50727.0 版本号和 XML 应如下所示：  
  
    ```  
    <dependency>  
      <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
        <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />  
      </dependentAssembly>  
    </dependency>  
    ```  
  
### <a name="to-update-and-re-sign-the-application-and-deployment-manifests"></a>更新并重新对签名的应用程序和部署清单  
  
-   更新并对应用程序和部署清单重新签名。 有关详细信息，请参阅[如何： 重新签名的应用程序和部署清单](../deployment/how-to-re-sign-application-and-deployment-manifests.md)。  
  
## <a name="see-also"></a>另请参阅  
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)   
 [\<compatibleFrameworks > 元素](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [\<依赖项 > 元素](../deployment/dependency-element-clickonce-application.md)   
 [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)   
 [配置文件架构](/dotnet/framework/configure-apps/file-schema/index)