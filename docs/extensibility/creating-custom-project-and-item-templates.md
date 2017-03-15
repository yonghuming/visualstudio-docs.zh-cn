---
title: "创建自定义项目和项模板 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 512014c5070e4314ad2b7d0e8c5c404c43f32cd9
ms.openlocfilehash: be53e0aa5179a38f9c2079513661607b45767a11
ms.lasthandoff: 02/22/2017

---
# <a name="creating-custom-project-and-item-templates"></a>创建自定义项目和项模板
Visual Studio SDK 包括创建自定义项目模板和自定义项模板的项目模板。 这些模板包括一些常见的参数替换，并生成以 zip 文件。 它们不会自动部署，并且这些文件不能在实验实例中。 您必须将复制 zip 文件的位置  
  
 模板创建模板，可以在更大的扩展中包含的模板。 这样可以实现上的源文件的版本控制和生成到一个 VSIX 包中的一组模板项目。  
  
 对于基本模板创建的情况下，您应该使用**导出模板**向导，它将输出到一个压缩文件。 有关创建基本模板的详细信息，请参阅[创建项目和项模板](../ide/creating-project-and-item-templates.md)。  
  
 从 Visual Studio 2017 开始，扫描自定义项目和项模板将不会再执行。 相反，该扩展插件必须提供模板的清单文件，用于描述这些模板的安装位置。 Visual Studio 2017 可用于更新您的 VSIX 扩展。 如果您部署使用 MSI 扩展插件，必须手动生成模板清单文件。 有关详细信息，请参阅[升级自定义项目和项模板的 Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md)。 中介绍了模板清单架构[Visual Studio 模板清单架构参考](../extensibility/visual-studio-template-manifest-schema-reference.md)。  
  
## <a name="creating-a-project-template"></a>创建项目模板  
  
1.  创建项目模板项目。 您可以找到中的项目模板**新项目**对话框中的，在 Visual Basic 或 Visual C#**扩展性**文件夹。  
  
     该模板生成类文件、 图标、.vstemplate 文件、 名为 ProjectTemplate.vbproj 或 ProjectTemplate.csproj，一个可编辑的项目文件和一些通常由其他项目类型中生成的文件、 resources.resx 文件、 一个程序集信息文件和.settings 文件。 每个代码文件包含公共的参数替换在适当的位置。  
  
2.  添加和移除项目根据需要为您的项目中的项。 不要删除可编辑项目文件、 程序集信息文件或.vstemplate 文件。  
  
3.  更新以反映任何添加和删除操作的.vstemplate 文件。 [项目](../extensibility/project-element-visual-studio-templates.md)元素必须包含[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)模板中包括的每个文件的元素。  
  
4.  修改您的代码文件和其他面向用户的内容，并添加适当的参数替换。  
  
5.  修改所需的生成的内容。  
  
6.  生成项目。  
  
     Visual Studio 将创建包含您的模板的.zip 文件。 未部署，并且不可用的实验实例中。  
  
## <a name="creating-an-item-template"></a>创建项模板  
  
1.  创建项模板项目。  
  
     该模板生成的类文件、 图标、.vstemplate 文件中和 AssemblyInfo 文件。 此类文件包含一些常见的参数替换。  
  
2.  添加和移除项目根据需要为您的项目中的项。  
  
3.  更新以反映任何添加和删除操作的.vstemplate 文件。 [项目](../extensibility/project-element-visual-studio-templates.md)元素必须包含[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)模板中包括的每个文件的元素。  
  
4.  修改您的代码文件和其他面向用户的内容，并添加适当的参数替换。  
  
5.  修改生成所需的内容。  
  
6.  生成项目。  
  
     Visual Studio 将创建一个压缩的文件，包含您的模板。 未部署，并且不可用的实验实例中。  
  
## <a name="deployment"></a>部署  
  
#### <a name="to-deploy-the-project-or-item-template"></a>若要部署项目或项模板  
  
1.  创建 VSIX 项目。 有关详细信息，请参阅[VSIX 项目模板](../extensibility/vsix-project-template.md)。  
  
2.  将 VSIX 项目设置为启动项目。 在**解决方案资源管理器**，选择 VSIX 项目节点，右键单击，并选择**设为启动项目**。  
  
3.  将项目模板项目设置为的 VSIX 项目的资产。 打开.vsixmanifest 文件。 转到**资产**选项卡上，单击**新建**。  
  
    1.  设置**类型**字段拖至**Microsoft.VisualStudio.ProjectTemplate**或**Microsoft.VisualStudio.ItemTemplate**。  
  
    2.  对于源，选择**当前解决方案中的项目**选项，，然后选择包含您的模板的项目。  
  
4.  生成解决方案，然后按 F5。 将显示的实验实例。  
  
5.  对于项目模板项目，您应看到您的项目模板中列出**新项目**对话框 (**文件 / 新建 / 项目**)，而是在 Visual C# 或 Visual Basic 节点。 对于一个项模板项目，您应看到您在添加新项对话框中列出的项模板 (在**解决方案资源管理器**，选择项目节点，然后单击**添加 / 新项**)。  
  
## <a name="see-also"></a>另请参阅  
 [Visual Studio 模板参考](../ide/visual-studio-template-reference.md)
