---
title: "如何： 使用 MSBuild 任务创建 SharePoint 解决方案包 |Microsoft 文档"
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
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, packages
ms.assetid: c3880bdd-f0a1-4d53-9a97-5767cb3f7b8e
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3cfe26fde4dd2d2b6617a008769fd535bb3e2cbb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>如何：使用 MSBuild 任务创建 SharePoint 解决方案包
  你可以生成、 清除和验证 SharePoint 包 (.wsp) 的开发计算机上使用命令行的 MSBuild 任务。 你还可以使用这些命令通过在生成计算机上使用 Team Foundation Server 自动化生成过程。  
  
## <a name="building-a-sharepoint-package"></a>生成 SharePoint 包  
  
#### <a name="to-build-a-sharepoint-package"></a>若要生成 SharePoint 包  
  
1.  在 Windows**启动**菜单上，选择**所有程序**，**附件**，**命令提示符**。  
  
2.  将更改为 SharePoint 项目所在的目录。  
  
3.  输入以下命令以创建项目的包。 替换*ProjectFileName*与项目的名称。  
  
    ```  
    msbuild /t:Package ProjectFileName  
    ```  
  
     例如，你可以运行以下命令以打包一个名为 ListDefinition1 的 SharePoint 项目之一。  
  
    ```  
    msbuild /t:Package ListDefinition1.vbproj  
    msbuild /t:Package ListDefinition1.csproj  
    ```  
  
## <a name="cleaning-a-sharepoint-package"></a>清理 SharePoint 包  
  
#### <a name="to-clean-a-sharepoint-package"></a>若要清理 SharePoint 包  
  
1.  打开命令提示符窗口。  
  
2.  将更改为 SharePoint 项目所在的目录。  
  
3.  输入以下命令来清理项目的包。 替换*ProjectFileName*与项目的名称。  
  
    ```  
    msbuild /t:CleanPackage ProjectFileName  
    ```  
  
     例如，你可以运行以下命令以清除一个名为 ListDefinition1 的 SharePoint 项目之一。  
  
    ```  
    msbuild /t:CleanPackage ListDefinition1.vbproj  
    msbuild /t:CleanPackage ListDefinition1.csproj  
    ```  
  
## <a name="validating-a-sharepoint-package"></a>验证 SharePoint 包  
  
#### <a name="to-validate-a-sharepoint-package"></a>若要验证 SharePoint 包  
  
1.  打开命令提示符窗口。  
  
2.  将更改为 SharePoint 项目所在的目录。  
  
3.  输入以下命令以验证该项目的包。 替换*ProjectFileName*与项目的名称。  
  
    ```  
    msbuild /t:ValidatePackage ProjectFileName  
    ```  
  
     例如，你可以运行以下命令以验证一个名为 ListDefinition1 的 SharePoint 项目之一。  
  
    ```  
    msbuild /t:ValidatePackage ListDefinition1.vbproj  
    msbuild /t:ValidatePackage ListDefinition1.csproj  
    ```  
  
## <a name="setting-properties-in-a-sharepoint-package"></a>在 SharePoint 包中设置属性  
  
#### <a name="to-set-a-property-in-a-sharepoint-package"></a>在 SharePoint 包中设置属性  
  
1.  打开命令提示符窗口。  
  
2.  将更改为 SharePoint 项目所在的目录。  
  
3.  输入以下命令以设置包项目的属性。 替换*PropertyName*与你想要设置的属性。  
  
    ```  
    msbuild /property:PropertyName=Value  
    ```  
  
     例如，你可以运行以下命令以设置警告等级。  
  
    ```  
    msbuild /property:WarningLevel = 2  
    ```  
  
## <a name="see-also"></a>另请参阅  
 [创建 SharePoint 功能](../sharepoint/creating-sharepoint-features.md)   
 [如何： 自定义 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [如何：在 SharePoint 功能中添加和删除项](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
  