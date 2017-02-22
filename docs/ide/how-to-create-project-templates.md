---
title: "如何：创建项目模板 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ExportTemplateWizard"
helpviewer_keywords: 
  - "项目模板, 创建"
  - "项目模板, 自定义模板位置"
  - "项目模板, 元数据文件"
  - "Visual Studio 模板, 创建项目模板"
  - "Visual Studio 模板, 项目模板"
ms.assetid: a1a6999d-a34c-48a8-b1cf-027eb5c76398
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：创建项目模板
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此过程使您可以使用**“导出模板”**向导（该向导可将模板打包成 .zip 文件）创建模板。  使用 " 导出模板向导扩展，则在提高部署的 VSIX 文件格式还可以创建模板，或使用中 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]包含的模板，也可以手动创建模板。  
  
### 使用标准导出模板向导创建自定义项目模板  
  
1.  创建一个项目。  
  
    > [!NOTE]
    >  对将成为模板的源的项目进行命名时，只能使用有效的标识符字符。  从以无效字符命名的项目导出的模板可能会导致将来基于此模板创建的项目出现编译错误。  有关有效标识符字符的更多信息，请参见[已声明的元素名称](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)。  
  
2.  编辑该项目，直至其可以作为模板导出为止。  
  
3.  根据需要编辑代码文件，以指示发生参数替换的位置。  有关参数替换的更多信息，请参见[如何：替换模板中的参数](../ide/how-to-substitute-parameters-in-a-template.md)。  
  
4.  在**“文件”**菜单上，单击**“导出模板”**。  随即打开**“导出模板”**向导。  
  
5.  单击**“项目模板”**。  
  
6.  如果当前解决方案中有多个项目，请选择要导出到模板中的项目。  
  
7.  单击**“下一步”**。  
  
8.  为模板选择图标和预览图像。  它们将出现在**“新建项目”**对话框中。  
  
9. 输入模板名称和说明。  
  
10. 单击**“完成”**。  项目将导出为一个 .zip 文件并放到指定的输出位置，而且，如果选择适当的选项，项目还会导入到 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中。  
  
     如果已安装 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]，则可以使用**“VSIX 项目”**模板来将已完成的目标包装到 .vsix 文件中用于部署。  有关更多信息，请参见[Getting Started with VSIX 项目模板](../extensibility/getting-started-with-the-vsix-project-template.md)。  
  
## 请参阅  
 [创建自定义项目和项模板](../ide/creating-project-and-item-templates.md)   
 [如何：创建项模板](../ide/how-to-create-item-templates.md)