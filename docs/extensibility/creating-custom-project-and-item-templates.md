---
title: "创建自定义项目和项模板 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e99505c0d3c4ee59f6e07a5b38d5d95533ab879f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="creating-custom-project-and-item-templates"></a>创建自定义项目和项模板
Visual Studio SDK 包括创建自定义项目模板和自定义项模板的项目模板。 这些模板包括一些常用的参数替换字符，并生成以 zip 文件。 它们不会自动部署，并且它们不能在实验实例中。 必须将复制 zip 文件的位置  
  
 模板创建模板，可以将模板包含更大的扩展中。 这样可以实现上的源文件的版本控制和生成到一个 VSIX 包中的一组的模板项目。  
  
 对于基本模板创建方案，应使用**导出模板**向导，将输出到压缩文件。 有关创建基本模板的详细信息，请参阅[创建项目和项模板](../ide/creating-project-and-item-templates.md)。  
  
 从 Visual Studio 2017 年 1 开始，扫描自定义项目和项模板将无法再执行。 相反，扩展必须提供模板清单文件描述这些模板的安装位置。 你可以使用 Visual Studio 2017 更新 VSIX 扩展。 如果在部署你使用 MSI 的扩展，你必须手动生成模板清单文件。 有关详细信息，请参阅[升级自定义项目和项模板为 Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md)。 模板清单架构记录在[Visual Studio 模板清单架构参考](../extensibility/visual-studio-template-manifest-schema-reference.md)。  
  
## <a name="creating-a-project-template"></a>创建项目模板  
  
1.  创建一个项目模板项目。 你可以查找中的项目模板**新项目**对话框中的，在 Visual Basic 或 Visual C#**扩展性**文件夹。  
  
     该模板会生成一个类文件、 图标、.vstemplate 文件、 一个名为 ProjectTemplate.vbproj 或 ProjectTemplate.csproj 的可编辑项目文件以及通常都由其他项目类型，此类 resources.resx 文件，AssemblyInfo 某些文件文件和.settings 文件。 每个代码文件包含常用的参数替换字符，在适当的位置。  
  
2.  添加和删除项从根据需要为你的项目的项目。 不要删除可编辑项目文件、 AssemblyInfo 文件或.vstemplate 文件。  
  
3.  更新以反映任何添加和删除的.vstemplate 文件。 [项目](../extensibility/project-element-visual-studio-templates.md)元素必须包含[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)模板中包含的每个文件的元素。  
  
4.  修改代码文件和其他面向用户的内容，并添加适当的参数替换项。  
  
5.  修改作为所需的生成的内容。  
  
6.  生成项目。  
  
     Visual Studio 将创建包含你的模板的.zip 文件。 未部署，并且不可在实验实例中。  
  
## <a name="creating-an-item-template"></a>创建项模板  
  
1.  创建项模板项目。  
  
     该模板会生成一个类文件、 图标、.vstemplate 文件以及 AssemblyInfo 文件。 类文件包含一些常见的参数替换。  
  
2.  添加和删除项从根据需要为你的项目的项目。  
  
3.  更新以反映任何添加和删除的.vstemplate 文件。 [项目](../extensibility/project-element-visual-studio-templates.md)元素必须包含[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)模板中包含的每个文件的元素。  
  
4.  修改代码文件和其他面向用户的内容，并添加适当的参数替换项。  
  
5.  可以修改所需的生成的内容。  
  
6.  生成项目。  
  
     Visual Studio 将创建一个压缩的文件，包含你的模板。 未部署，并且不可在实验实例中。  
  
## <a name="deployment"></a>部署  
  
#### <a name="to-deploy-the-project-or-item-template"></a>若要部署项目或项模板  
  
1.  创建 VSIX 项目。 有关详细信息，请参阅[VSIX 项目模板](../extensibility/vsix-project-template.md)。  
  
2.  将 VSIX 项目设置为启动项目。 在**解决方案资源管理器**，选择 VSIX 项目节点，右键单击，并选择**设为启动项目**。  
  
3.  将项目模板项目设置的 VSIX 项目的资产。 打开的.vsixmanifest 文件。 转到**资产**选项卡，单击**新建**。  
  
    1.  设置**类型**字段**Microsoft.VisualStudio.ProjectTemplate**或**Microsoft.VisualStudio.ItemTemplate**。  
  
    2.  对于源，选择**当前解决方案中的项目**选项，然后再选中包含你的模板的项目。  
  
4.  生成解决方案，然后按 F5。 实验实例中出现。  
  
5.  对于项目模板项目，你应看到项目模板中列出**新项目**对话框 (**文件 / 新建 / 项目**)，而是在 Visual C# 或 Visual Basic 节点。 对于项模板项目，你应看到添加新项对话框中列出项模板 (在**解决方案资源管理器**，选择项目节点，然后单击**添加 / 新项**)。  
  
## <a name="see-also"></a>另请参阅  
 [Visual Studio 模板参考](../ide/visual-studio-template-reference.md)