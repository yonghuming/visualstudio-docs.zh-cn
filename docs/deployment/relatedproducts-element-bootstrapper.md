---
title: "&lt;RelatedProducts&gt;元素 （引导程序） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MSBuild.GenerateBootstrapper.MissingDependency
- MSBuild.GenerateBootstrapper.DuplicateItems
- MSBuild.GenerateBootstrapper.IncludedProductIncluded
- MSBuild.GenerateBootstrapper.DependencyNotFound
- MSBuild.GenerateBootstrapper.PackageFileNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords: <RelatedProducts> element [bootstrapper]
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
caps.latest.revision: "12"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 4fa304f787c954b9ee89878e792e6f543f344f60
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;RelatedProducts&gt;元素 （引导程序）
`RelatedProducts`元素定义取决于或当前产品中包括的其他产品。  
  
## <a name="syntax"></a>语法  
  
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
  
## <a name="elements-and-attributes"></a>元素和属性  
 `RelatedProducts`元素是的子`Product`元素。 它具有任何属性。  
  
## <a name="dependsonproduct"></a>DependsOnProduct  
 `DependsOnProduct`元素表示当前产品取决于指定的产品，和的命名的产品，应安装在当前之前。 它是的子级`RelatedProducts`元素。 A`RelatedProducts`元素可能具有一个或多`DependsOnProduct`元素。  
  
 `DependsOnProduct`具有以下属性。  
  
|特性|描述|  
|---------------|-----------------|  
|`Code`|包括的产品，按指定的代码名称`ProductCode`属性`Product`元素。 有关详细信息，请参阅[\<产品 > 元素](../deployment/product-element-bootstrapper.md)。|  
  
## <a name="eitherproducts"></a>EitherProducts  
 `EitherProducts`元素定义零个或多`DependsOnProduct`元素，且不具有特性。 至少一个`DependsOnProduct`在这一组之前，必须安装当前产品。 A`RelatedProducts`元素可包含零个或多`EitherProducts`元素。  
  
## <a name="includesproduct"></a>IncludesProduct  
 `IncludesProduct`元素表示一种产品包含在当前的安装，并不需要单独安装。 它是的子级`RelatedProducts`元素。 A`RelatedProducts`元素可能具有一个或多`IncludesProduct`元素。  
  
 `IncludesProduct`具有以下属性。  
  
|特性|描述|  
|---------------|-----------------|  
|`Code`|包括的产品，按指定的代码名称`ProductCode`属性`Product`元素。 有关详细信息，请参阅[\<产品 > 元素](../deployment/product-element-bootstrapper.md)。|  
  
## <a name="example"></a>示例  
 下面的代码示例指定随 Microsoft 安装程序[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]，，因此不需要单独安装。  
  
```  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## <a name="see-also"></a>另请参阅  
 [\<产品 > 元素](../deployment/product-element-bootstrapper.md)