---
title: "如何：创建项目模板 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- Visual Studio templates, creating project templates
- project templates, metadata files
- Visual Studio templates, project templates
- project templates, custom template locations
- project templates, creating
ms.assetid: a1a6999d-a34c-48a8-b1cf-027eb5c76398
caps.latest.revision: 19
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9713f09b7379b14b9362e3853a910948935c501e
ms.openlocfilehash: 279a123088308a54dccfa9abe0bfbcdb18e5aaf1
ms.contentlocale: zh-cn
ms.lasthandoff: 05/31/2017

---
# <a name="how-to-create-project-templates"></a>如何：创建项目模板
在此过程中，可以使用“导出模板”向导创建模板，将模板打包为 .zip 文件。 还可以使用导出模板向导扩展，或使用 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 中包含的模板创建 VSIX 文件格式的模板，改进部署，也可以手动创建模板。  
  
### <a name="to-create-a-custom-project-template-with-the-standard-export-template-wizard"></a>使用标准的导出模板向导创建自定义项目模板  
  
1.  创建项目。  
  
    > [!NOTE]
    >  如果命名的项目将成为模板的源，则只使用有效的标识符字符。 从采用无效字符命名的项目中导出的模板会导致在将来基于模板的项目中产生编译错误。 有关有效的标识符字符的详细信息，请参阅[已声明的元素名称](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)。  
  
2.  编辑项目，直到可以将它导出为一个模板。  
  
3.  根据需要编辑代码文件，指出应替换参数的位置。 有关参数替换的详细信息，请参阅[如何：替换模板中的参数](../ide/how-to-substitute-parameters-in-a-template.md)。  
  
4.  在“项目”菜单上，单击“导出模板”。 “导出模板”向导随即打开。  
  
5.  单击“项目模板”。  
  
6.  如果当前解决方案中具有多个项目，请选择要导出到模板中的项目。  
  
7.  单击 **“下一步”**。  
  
8.  选择模板的图标和预览图像。 这些将出现在“新建项目”对话框中。  
  
9. 输入模板名称和说明。  
  
10. 单击 **“完成”**。 项目会导出到一个 .zip 文件中，并放在指定的输出位置，还可以导入到 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]（如果选择）。  
  
     如果已安装 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]，可以使用“VSIX 项目”模板将完成的模板包装到 .vsix 文件中，供部署使用。 有关详细信息，请参阅 [VSIX 项目模板入门](../extensibility/getting-started-with-the-vsix-project-template.md)。  
  
## <a name="see-also"></a>另请参阅  
 [创建项目和项模板](../ide/creating-project-and-item-templates.md)   
 [如何：创建项模板](../ide/how-to-create-item-templates.md)

