---
title: "如何： 自定义 SharePoint 功能 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.RAD.FeatureDesigner.SwitchView
- VS.SharePointTools.RAD.featureDesigner.Manifest
- VS.SharePointTools.RAD.FeatureDesignerProperties
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, features
ms.assetid: e624c546-564b-4c73-9f1b-dc3675e76a55
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d81a65a8030fd77ead1362602b0e16f474ef410c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-customize-a-sharepoint-feature"></a>如何：自定义 SharePoint 功能
  你可以创建和使用 Visual Studio 中的功能设计器自定义 SharePoint 功能。 例如，你可以设置功能的作用域，并将其他功能添加为依赖关系。 默认情况下，当在解决方案资源管理器或 SharePoint 包资源管理器中添加一项新功能被打开功能设计器。  
  
## <a name="opening-the-feature-designer"></a>打开功能设计器  
 你可以添加或删除到使用功能设计器功能的 SharePoint 项目项。  
  
#### <a name="to-open-the-feature-designer"></a>若要打开功能设计器  
  
1.  在**解决方案资源管理器**，展开**功能**。  
  
2.  双击*Feature1*项，或打开的快捷菜单*Feature1*项，然后选择**视图设计器**。  
  
## <a name="viewing-the-packaged-manifest-file"></a>查看打包的清单文件  
 功能设计器可用于修改并对该功能 (feature.xml) 生成打包的清单文件。 然后，你可以在 Visual Studio 中查看此文件的 XML 代码。  
  
#### <a name="to-view-the-packaged-manifest-file"></a>若要查看打包的清单文件  
  
1.  在**功能设计器**，选择**清单**选项卡。  
  
#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>使用解决方案资源管理器查看打包的清单文件  
  
1.  在**解决方案资源管理器**，选择**显示所有文件**图标。  
  
2.  展开功能，展开 FeatureName、 展开 FeatureName.feature，然后打开*FeatureName*。模板.xml 文件。  
  
    > [!NOTE]  
    >  当你打开功能模板清单 XML 文件时，将自动验证这些文件，可以忽略在错误列表窗口中显示的警告。  
  
## <a name="changing-the-manifest-template"></a>更改清单模板  
 你可以更改在 Visual Studio XML 编辑器或清单模板窗格中的功能清单文件的 XML 代码。 对 XML 代码的任何更改都将合并到打包的清单文件的功能。 例如，你可能想要更改的清单的模板自定义功能属性。  
  
#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>若要通过使用 XML 编辑器更改清单的模板  
  
1.  在**功能设计器**，选择**清单**选项卡上，展开**编辑选项**节点，然后选择**在 XML 编辑器中打开**链接。  
  
     对 XML 的更改将合并到打包的清单文件。  
  
#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>若要使用的清单模板窗格中更改清单的模板  
  
1.  在**功能设计器**，选择**清单**选项卡上，展开**编辑选项**节点，然后再更改的清单模板窗格中显示的 XML。  
  
     对 XML 的更改出现在**预览打包的清单**窗格。  
  
## <a name="overwriting-the-packaged-manifest-file"></a>覆盖打包的清单文件  
 可以禁用功能设计器，还可以手动创建 feature.xml 文件。 第一次执行此过程中，功能设计器中的当前设置保存到功能模板 XML 文件。 然后，你可以修改或覆盖的 XML 代码。  
  
> [!NOTE]  
>  如果你添加或删除 XML 文件中的 SharePoint 项目项，在功能设计器禁用状态时，这些项目项不是一起打包。  
  
#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>通过禁用设计器覆盖打包的清单文件  
  
1.  在**功能设计器**，选择**清单**选项卡。  
  
2.  展开**编辑选项**节点，选择**XML 编辑器中的覆盖生成的 XML 和编辑清单**链接，然后再选择**是**按钮。  
  
     该模板将更新为当前打包的清单文件。  
  
## <a name="enabling-the-feature-designer"></a>启用功能设计器  
 你可以重新启用功能设计器，以自定义 feature.xml 文件。  
  
#### <a name="to-re-enable-the-designer"></a>若要重新启用设计器  
  
1.  在**功能设计器**，选择**丢弃清单编辑和重新启用设计器**链接，然后再选择**是**按钮。  
  
2.  模板刷新与原始文本，并且对 XML 的任何更改都将丢失。  
  
## <a name="see-also"></a>另请参阅  
 [打包和部署 SharePoint 解决方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  