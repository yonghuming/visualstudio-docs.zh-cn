---
title: "&lt;RelatedProducts&gt; 元素（引导程序） | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.MissingDependency"
  - "MSBuild.GenerateBootstrapper.DuplicateItems"
  - "MSBuild.GenerateBootstrapper.IncludedProductIncluded"
  - "MSBuild.GenerateBootstrapper.DependencyNotFound"
  - "MSBuild.GenerateBootstrapper.PackageFileNotFound"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<RelatedProducts> 元素 [引导程序]"
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;RelatedProducts&gt; 元素（引导程序）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`RelatedProducts` 元素定义了依赖于当前产品或包含在当前产品中的其他产品。  
  
## 语法  
  
```  
<RelatedProducts>  
    <DependsOnProduct  
        Code  
    />  
    <EitherProducts>  
        <DependsOnProduct  
            Code  
        />  
    </EitherProducts>  
    <IncludesProduct  
        Code  
    />  
</RelatedProducts>  
```  
  
## 元素和特性  
 `RelatedProducts` 元素是 `Product` 元素的子元素。  它没有特性。  
  
## DependsOnProduct  
 `DependsOnProduct` 元素表明当前产品依赖于指定的产品，并且应在安装当前产品之前安装指定的产品。  它是 `RelatedProducts` 元素的子元素。  `RelatedProducts` 元素可能有一个或多个 `DependsOnProduct` 元素。  
  
 `DependsOnProduct` 具有下列特性。  
  
|特性|说明|  
|--------|--------|  
|`Code`|所含产品的代号，由 `Product` 元素的 `ProductCode` 特性指定。  有关更多信息，请参见 [\<Product\> 元素](../deployment/product-element-bootstrapper.md)。|  
  
## EitherProducts  
 `EitherProducts` 元素定义零个或多个 `DependsOnProduct` 元素，它没有特性。  安装当前产品之前，必须至少安装此集合中的一个 `DependsOnProduct`。  一个 `RelatedProducts` 元素可以有零个或多个 `EitherProducts` 元素。  
  
## IncludesProduct  
 `IncludesProduct` 元素表明产品包含在当前安装中，不需要单独进行安装。  它是 `RelatedProducts` 元素的子元素。  `RelatedProducts` 元素可能有一个或多个 `IncludesProduct` 元素。  
  
 `IncludesProduct` 具有下列特性。  
  
|特性|说明|  
|--------|--------|  
|`Code`|所含产品的代号，由 `Product` 元素的 `ProductCode` 特性指定。  有关更多信息，请参见 [\<Product\> 元素](../deployment/product-element-bootstrapper.md)。|  
  
## 示例  
 下面的代码示例指定 Microsoft Installer 将随 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 一起安装，因此不需要单独安装。  
  
```  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## 请参阅  
 [\<Product\> 元素](../deployment/product-element-bootstrapper.md)