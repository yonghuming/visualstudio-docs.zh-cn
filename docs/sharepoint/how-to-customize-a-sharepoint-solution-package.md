---
title: "如何： 自定义 SharePoint 解决方案包 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerAdvanced
- VS.SharePointTools.RAD.PackageDesigner.Manifest
- VS.SharePointTools.RAD.PackageDesignerProperties
- VS.SharePointTools.RAD.PackageDesigner.SwitchView
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, packages
ms.assetid: fd365f8c-8a80-4ce8-8e28-c0eb609f12f3
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d07f03c1aed1c2e85e65bd10a89bd62138d571c7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-customize-a-sharepoint-solution-package"></a>如何：自定义 SharePoint 解决方案包
  在包设计器可用于创建和自定义包 (.wsp)。 例如，你可以添加 SharePoint 项目项和功能，指定是否 Web 服务器是重置部署解决方案时，并将设置部署服务器类型。  
  
## <a name="opening-the-package-designer"></a>打开在包设计器  
  
#### <a name="to-open-the-package-designer"></a>若要打开在包设计器  
  
-   在**解决方案资源管理器**，双击**包**，或选择**视图设计器**的快捷菜单上**包**。  
  
## <a name="viewing-the-packaged-manifest-file"></a>查看打包的清单文件  
 在包设计器可用于修改并生成打包的清单文件。 然后，你可以在 Visual Studio 中查看此文件的 XML 代码。  
  
#### <a name="to-view-the-xml-source-file"></a>若要查看 XML 源文件  
  
1.  在**包设计器**，选择**清单**。  
  
#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>使用解决方案资源管理器查看打包的清单文件  
  
1.  在**解决方案资源管理器**，选择**显示所有文件**。  
  
2.  展开包，展开包，然后打开 Package.Template.xml 文件。  
  
    > [!NOTE]  
    >  当打开包模板的清单 XML 文件时，将自动验证这些文件，，你可以忽略在错误列表窗口中显示的警告。  
  
## <a name="changing-the-manifest-template"></a>更改清单模板  
 你可以更改在 Visual Studio XML 编辑器或清单模板窗格中打包的清单文件的 XML 代码。 对 XML 代码的任何更改将合并到包的打包清单文件。  
  
#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>若要通过使用 XML 编辑器更改清单的模板  
  
1.  在**包设计器**，选择**清单**选项卡上，展开**编辑选项**节点，然后选择**在 XML 编辑器中打开**链接。  
  
     对 XML 的更改将合并到打包的清单文件。  
  
#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>若要使用的清单模板窗格中更改清单的模板  
  
1.  在**包设计器**，选择**清单**选项卡上，展开**编辑选项**节点，然后再更改的清单模板窗格中显示的 XML。  
  
     对 XML 的更改出现在**预览打包的清单**窗格。  
  
## <a name="overwriting-the-packaged-manifest-file"></a>覆盖打包的清单文件  
 你可以禁用在包设计器和手动创建的清单 xml 文件。 第一次执行此过程中，在包设计器中的当前设置保存到包模板 XML 文件。 然后，你可以修改或覆盖的 XML 代码。  
  
> [!NOTE]  
>  如果你在添加或删除 SharePoint 项目项和功能的 XML 文件在包设计器禁用状态时，这些项目项和功能不打包。  
  
#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>通过禁用设计器覆盖打包的清单文件  
  
1.  在**包设计器**，选择**清单**选项卡。  
  
2.  .  
  
3.  展开**编辑选项**节点，选择**XML 编辑器中的覆盖生成的 XML 和编辑清单**链接，然后再选择**是**按钮。  
  
     该模板将更新为当前打包的清单文件。  
  
## <a name="enabling-the-package-designer"></a>启用在包设计器  
 你可以重新启用自定义的清单 xml 文件在包设计器。  
  
#### <a name="to-re-enable-the-designer"></a>若要重新启用设计器  
  
1.  在**包设计器**，选择**丢弃清单编辑和重新启用设计器**链接，然后再选择**是**按钮。  
  
     模板刷新与原始文本，并且对 XML 的任何更改都将丢失。  
  
## <a name="see-also"></a>另请参阅  
 [打包和部署 SharePoint 解决方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  