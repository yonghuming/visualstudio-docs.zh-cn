---
title: "如何：使用 ClickOnce 部署可在多个版本的 .NET Framework 上运行的应用程序 | Microsoft Docs"
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
  - "ClickOnce 应用程序, 多个 .NET Framework 版本"
  - "ClickOnce 部署, 多个 .NET Framework 版本"
  - "部署应用程序 [ClickOnce], 多个 .NET Framework 版本"
ms.assetid: e0a8c330-21bc-4eb2-b936-fd0f3c3221f1
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 如何：使用 ClickOnce 部署可在多个版本的 .NET Framework 上运行的应用程序
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

通过使用 ClickOnce 部署技术，可部署面向多个版本的 .NET Framework 的应用程序。  这要求生成和更新应用程序清单和部署清单。  
  
> [!NOTE]
>  在更改应用程序以面向多个版本的 .NET Framework 之前，您应确保此应用程序会与多个版本的 .NET Framework 一起运行。  公共语言运行时的版本在 [!INCLUDE[net_v40_short](../debugger/includes/net_v40_short_md.md)] 与 .NET Framework 2.0、.NET Framework 3.0 和 .NET Framework 3.5 之间是不同的。  
  
 此过程需要执行下列步骤：  
  
1.  生成应用程序清单和部署清单。  
  
2.  更改部署清单以列出多个 .NET Framework 版本。  
  
3.  更改 app.config 文件以列出兼容的 .NET Framework 运行时版本。  
  
4.  更改应用程序清单，将依赖程序集标记为 .NET Framework 程序集。  
  
5.  为应用程序清单签名。  
  
6.  更新部署清单并为其签名。  
  
### 生成应用程序清单和部署清单  
  
-   使用发布向导或项目设计器的“发布”页来发布应用程序，并生成应用程序清单文件和部署清单文件。  有关更多信息，请参见[如何：使用发布向导发布 ClickOnce 应用程序](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)或[“项目设计器”\-\>“发布”页](../ide/reference/publish-page-project-designer.md)。  
  
### 更改部署清单以列出多个 .NET Framework 版本  
  
1.  在 publish 目录中，使用 Visual Studio 中的 XML 编辑器打开部署清单。  部署清单的文件扩展名为 .application。  
  
2.  将 `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` 和 `</compatibleFrameworks>` 元素之间的 XML 代码替换为列出了您的应用程序支持的 .NET Framework 版本的 XML。  
  
     下表显示可添加到部署清单中的一些可用的 .NET Framework 版本和相应的 XML。  
  
    |.NET Framework 版本|XML|  
    |-----------------------|---------|  
    |4 Client|\<framework targetVersion\="4.0" profile\="Client" supportedRuntime\="4.0.30319" \/\>|  
    |4 Full|\<framework targetVersion\="4.0" profile\="Full" supportedRuntime\="4.0.30319" \/\>|  
    |3.5 Client|\<framework targetVersion\="3.5" profile\="Client" supportedRuntime\="2.0.50727" \/\>|  
    |3.5 Full|\<framework targetVersion\="3.5" profile\="Full" supportedRuntime\="2.0.50727" \/\>|  
    |3.0|\<framework targetVersion\="3.0" supportedRuntime\="2.0.50727" \/\>|  
  
### 更改 app.config 文件以列出兼容的 .NET Framework 运行时版本  
  
1.  在解决方案资源管理器中，使用 Visual Studio 中的 XML 编辑器打开 App.config 文件。  
  
2.  将 `<startup>` 和 `</startup>` 元素之间的 XML 代码替换为（或添加）列出了您的应用程序支持的 .NET Framework 运行时的 XML。  
  
     下表显示可添加到部署清单中的一些可用的 .NET Framework 版本和相应的 XML。  
  
    |.NET Framework 运行时版本|XML|  
    |--------------------------|---------|  
    |4 Client|\<supportedRuntime version\="v4.0.30319" sku\=".NETFramework,Version\=v4.0,Profile\=Client" \/\>|  
    |4 Full|\<supportedRuntime version\="v4.0.30319" sku\=".NETFramework,Version\=v4.0" \/\>|  
    |3.5 Full|\<supportedRuntime version\="v2.0.50727"\/\>|  
    |3.5 Client|\<supportedRuntime version\="v2.0.50727" sku\="Client"\/\>|  
  
### 更改应用程序清单，将依赖程序集标记为 .NET Framework 程序集  
  
1.  在 publish 目录中，使用 Visual Studio 中的 XML 编辑器打开应用程序清单。  部署清单的文件扩展名为 .manifest。  
  
2.  针对标记程序集（`System.Core`、`WindowsBase`、`Sentinel.v3.5Client` 和 `System.Data.Entity`），将 `group="framework"` 添加到依赖项 XML。  例如，此 XML 应类似于下面这样：  
  
    ```  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">  
    ```  
  
3.  将 Microsoft.Windows.CommonLanguageRuntime 的 `<assemblyIdentity>` 元素的版本号更新到属于最小公分母的 .NET Framework 版本号。  例如，如果应用程序面向 .NET Framework 3.5 版和 [!INCLUDE[net_v40_short](../debugger/includes/net_v40_short_md.md)]，则使用 2.0.50727.0 版本号，并且 XML 应类似于下面这样：  
  
    ```  
    <dependency>  
      <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
        <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />  
      </dependentAssembly>  
    </dependency>  
    ```  
  
### 对应用程序清单和部署清单进行更新和重新签名  
  
-   对应用程序清单和部署清单进行更新和重新签名。  有关更多信息，请参见[如何：为应用程序和部署清单重新签名](../deployment/how-to-re-sign-application-and-deployment-manifests.md)。  
  
## 请参阅  
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)   
 [\<compatibleFrameworks\> 元素](../Topic/%3CcompatibleFrameworks%3E%20Element%20\(ClickOnce%20Deployment\).md)   
 [\<dependency\> 元素](../deployment/dependency-element-clickonce-application.md)   
 [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)   
 [配置文件架构](../Topic/Configuration%20File%20Schema%20for%20the%20.NET%20Framework.md)