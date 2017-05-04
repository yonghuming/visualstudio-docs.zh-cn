---
title: "How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint development in Visual Studio, extending deployment"
  - "SharePoint development in Visual Studio, validation rules"
ms.assetid: 17e818f8-0f3a-4a96-a6fc-1634ddb4825d
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions
  您可以创建自定义验证规则来验证 Visual Studio 生成的解决方案包。  可通过在**“打包资源管理器”**中从包或功能的上下文菜单中选择**“验证”**，对整个功能或包执行完全验证。  当您向项目中添加新的 SharePonit 项目项或功能时，将执行部分验证来确定包或功能是否将处于有效的状态。  
  
### 创建自定义包验证规则  
  
1.  创建一个类库项目。  
  
2.  添加对下列程序集的引用：  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  创建实现以下接口之一的类：  
  
    -   若要创建包验证规则，请实现 <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> 接口。  
  
    -   若要创建功能验证规则，请实现 <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> 接口。  
  
4.  将 <xref:System.ComponentModel.Composition.ExportAttribute> 添加到该类中。  此特性使 Visual Studio 能够发现并加载您的验证规则。  将 <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> 或 <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> 类型传递到特性构造函数。  
  
## 示例  
 下面的代码示例演示如何创建自定义功能验证规则。  
  
 [!code-csharp[SPExtensibility.FeatureValidation#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.featurevalidation/cs/extension/customfeaturevalidationrule.cs#1)]
 [!code-vb[SPExtensibility.FeatureValidation#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.featurevalidation/vb/extension/customvalidationrule.vb#1)]  
  
## 编译代码  
 此示例需要对以下程序集的引用：  
  
-   Microsoft.VisualStudio.SharePoint。  
  
-   System.ComponentModel.Composition。  
  
## 部署扩展  
 若要部署扩展，请为要随此扩展分发的程序集和任何其他文件创建 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 扩展 \(VSIX\) 包。  有关更多信息，请参见[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 请参阅  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  