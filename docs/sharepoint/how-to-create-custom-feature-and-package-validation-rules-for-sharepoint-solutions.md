---
title: "如何： 为 SharePoint 解决方案创建自定义功能和包验证规则 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
- SharePoint development in Visual Studio, validation rules
ms.assetid: 17e818f8-0f3a-4a96-a6fc-1634ddb4825d
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7a4b2c9bb828fb8c8b55829a4a6a295bb8324361
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions"></a>如何：为 SharePoint 解决方案创建自定义功能和包验证规则
  你可以创建自定义验证规则来验证解决方案包生成的 Visual Studio。 可以在整个功能或包上执行完全验证，通过选择**验证**包或中的新功能的上下文菜单中**PackagingExplorer**。 当将新 SharePonit 项目项或功能添加到项目中以确定包或功能将能处于有效状态，将执行部分验证。  
  
### <a name="to-create-a-custom-package-validation-rule"></a>若要创建自定义包验证规则  
  
1.  创建类库项目。  
  
2.  添加对下列程序集的引用：  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  创建一个类以实现以下接口之一：  
  
    -   若要创建包验证规则，实现<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>接口。  
  
    -   若要创建功能验证规则，实现<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>接口。  
  
4.  添加<xref:System.ComponentModel.Composition.ExportAttribute>到类。 此属性使 Visual Studio 发现和加载你的验证规则。 传递<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>或<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>给特性构造函数的类型。  
  
## <a name="example"></a>示例  
 下面的代码示例演示如何创建自定义功能验证规则。  
  
 [!code-vb[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb#1)]
 [!code-csharp[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs#1)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要引用以下程序集：  
  
-   Microsoft.VisualStudio.SharePoint。  
  
-   System.ComponentModel.Composition。  
  
## <a name="deploying-the-extension"></a>部署扩展  
 若要部署的扩展，创建[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]扩展 (VSIX) 包的程序集和你想要随此扩展分发的任何其他文件。 有关详细信息，请参阅[部署 Visual Studio 中的 SharePoint 工具扩展](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另请参阅  
 [扩展 SharePoint 打包和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  