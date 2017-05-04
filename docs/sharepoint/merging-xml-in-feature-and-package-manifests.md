---
title: "合并功能和包清单中的 XML | Microsoft Docs"
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
  - "Visual Studio 中的 SharePoint 开发, 打包"
ms.assetid: fc1cbd2a-0166-4f2f-a81b-4dac2fa7b0f3
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# 合并功能和包清单中的 XML
  功能和包是通过 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 清单文件定义的。  这些打包的清单是设计器中生成的数据与用户在清单模板中输入的自定义 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 的组合。  在打包时，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 会将自定义 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 语句与设计器提供的 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 合并，以组成打包的 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 清单文件。  会将类似的元素（例外情况稍后在“合并例外情况”中说明）加以合并，以便在将文件部署到 SharePoint 之后避免 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 验证错误，并使清单文件更小并更有效。  
  
## 修改清单  
 在禁用功能或包设计器之前，您无法直接修改打包的清单文件。  不过，您可以通过功能和包设计器或 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 编辑器向清单模板中手动添加自定义 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 元素。  有关更多信息，请参见[如何：自定义 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)和[如何：自定义 SharePoint 解决方案包](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)。  
  
## 功能和包清单合并过程  
 在将自定义元素与设计器提供的元素合并在一起时，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 使用以下过程。  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 将检查每个元素是否有唯一的键值。  如果元素没有唯一的键值，则会将其追加到打包的清单文件。  同样，具有多个键的元素也无法合并。  因此，会将它们追加到清单文件。  
  
 如果元素有唯一的键，则 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 将比较设计器和自定义键的值。  如果这些值匹配，则它们将合并为单个值。  如果这些值不同，则会丢弃设计器键值，并使用自定义键值。  还会合并集合。  例如，如果设计器生成的 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 和自定义 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 都包含程序集集合，则打包的清单将只包含一个程序集集合。  
  
## 合并例外情况  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 会将大多数设计器 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 元素与类似的自定义 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 元素合并在一起，只要它们具有单个唯一的标识特性。  但是，某些元素缺少进行 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 合并所需的唯一标识符。  这些元素称为“合并例外情况”。  在这些情况下，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 不会将自定义 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 元素与设计器提供的 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 元素合并在一起，而是会将它们追加到打包的清单文件。  
  
 下面列出了功能和包 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 清单文件的合并例外情况。  
  
|设计器|XML 元素|  
|---------|------------|  
|功能设计器|ActivationDependency|  
|功能设计器|UpgradeAction|  
|包设计器|SafeControl|  
|包设计器|CodeAccessSecurity|  
  
## 功能清单元素  
 下表列出了可合并的所有功能清单元素，以及这些元素的用于匹配的唯一键。  
  
|元素名称|唯一键|  
|----------|---------|  
|Feature（所有特性）|*特性名称Attribute Name*（功能元素的每个特性名称都是唯一键。）|  
|ElementFile|位置|  
|ElementManifests\/ElementManifest|位置|  
|Properties\/Property|键|  
|CustomUpgradeAction|名称|  
|CustomUpgradeActionParameter|名称|  
  
> [!NOTE]  
>  由于只能在自定义 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 编辑器中修改 CustomUpgradeAction 元素，因此不合并的影响不大。  
  
## 包清单元素  
 下表列出了可合并的所有包清单元素，以及这些元素的用于匹配的唯一键。  
  
|元素名称|唯一键|  
|----------|---------|  
|Solution（所有特性）|*特性名称Attribute Name*（Solution 元素的每个特性名称都是唯一键。）|  
|ApplicationResourceFiles\/ApplicationResourceFile|位置|  
|Assemblies\/Assembly|位置|  
|ClassResources\/ClassResource|位置|  
|DwpFiles\/DwpFile|位置|  
|FeatureManifests\/FeatureManifest|位置|  
|Resources\/Resource|位置|  
|RootFiles\/RootFile|位置|  
|SiteDefinitionManifests\/SiteDefinitionManifest|位置|  
|WebTempFile|位置|  
|TemplateFiles\/TemplateFile|位置|  
|SolutionDependency|SolutionID|  
  
## 手动添加部署的文件  
 某些清单元素（例如 ApplicationResourceFile 和 DwpFiles）指定其中包括文件名的位置。  但是，在将文件名项添加到清单模板时，并不会将基础文件添加到包中。  您必须将文件添加到项目以将其包括在包中，并相应地设置其“部署类型”属性。  
  
## 请参阅  
 [打包和部署 SharePoint 解决方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [生成和调试 SharePoint 解决方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  