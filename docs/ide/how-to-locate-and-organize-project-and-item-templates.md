---
title: "如何：查找和组织项目模板和项模板 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "自定义模板位置 [Visual Studio]"
  - "项模板, 位置"
  - "项目模板 [Visual Studio], 显示"
  - "项目模板 [Visual Studio], 位置"
  - "模板 [Visual Studio], 位置"
  - "Visual Studio 模板, 位置"
ms.assetid: 71f9ed52-c9c9-4818-9bce-c279ffaa0438
caps.latest.revision: 25
caps.handback.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：查找和组织项目模板和项模板
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

必须将模板文件放置在 Visual Studio 能够识别的位置，这样“新建项目”和“添加新项”对话框中才会显示这些模板。  可以为模板创建自定义子类别，以使用户界面中也显示这些子类别。  
  
## 查找模板  
 默认情况下，Visual Studio 将搜索项目和项模板的两个位置。  如果这两个位置存在包含 .vstemplate 文件的压缩文件，则“新建项目”或“添加新项”对话框中将显示一个模板。  
  
### 已安装的模板  
 默认情况下，与产品一起安装的模板位于以下位置：  
  
-   \\*VisualStudioInstallationDirectory*\\Common7\\IDE\\ItemTemplates\\*Language*\\*Locale*\\  
  
-   \\*VisualStudioInstallationDirectory*\\Common7\\IDE\\ProjectTemplates\\*Language*\\*Locale\\*  
  
 例如，以下目录包含以英语表示的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 项目模板：  
  
 C:\\*VisualStudioInstallationDirectory*\\Common7\\IDE\\ItemTemplates\\VisualBasic\\1033\\  
  
### 自定义模板  
 默认情况下，自定义模板位于以下位置：  
  
-   \\My Documents\\Visual Studio *Version*\\Templates\\ProjectTemplates\\*Language*\\  
  
-   \\My Documents\\Visual Studio *Version*\\Templates\\ItemTemplates\\*Language*\\  
  
 例如，以下目录包含自定义 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 项目模板：  
  
 C:\\Documents and Settings\\UserName\\My Documents\\\<Visual Studio version\>\\Templates\\ProjectTemplates\\Visual C\#\\  
  
 自定义模板不包含已本地化模板的子目录。  您可以在**“环境\\项目和解决方案”**下的**“选项”**对话框中更改自定义模板的默认目录。  
  
## 组织模板  
 “新建项目”和“添加新项”对话框中的类别反映存在于已安装模板位置和自定义模板位置的目录结构。  可以修改这些目录结构，以需要的方式组织模板。  
  
> [!NOTE]
>  不能在编程语言级别创建新类别。  只能在每种语言中创建新类别。  
  
 如果特定语言的已安装模板和自定义模板的目录结构不同（即一个文件夹下具有另一个文件夹下不存在的目录），则“新建项目”对话框中显示的类别集将是所有类别的合并。  
  
### 组织已安装的模板  
 可以通过在编程语言文件夹中创建子目录来组织已安装的模板。  这些子目录以每种语言内虚拟文件夹的形式显示在“新建项目”和“添加新项”对话框中。  
  
##### 如要新建已安装的项目模板类别  
  
1.  在已安装的模板目录的语言文件夹中创建一个文件夹。  例如，要为 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 项目模板创建 Office 类别，你将创建以下目录：  
  
     \\*VisualStudioInstallationDirectory*\\Common7\\IDE\\ProjectTemplates\\VisualBasic\\1033\\Office\\  
  
2.  将此类别的所有模板放入新文件夹。  
  
3.  关闭 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的所有实例。  
  
4.  在“启动”菜单上，单击“运行”，键入 **cmd**，然后单击“确定”。  
  
5.  在命令提示符处，找到包含 devenv.exe 的目录，然后键入 **devenv \/installvstemplates**。  
  
6.  运行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
7.  在**“文件”**菜单上，单击**“新建”**，然后单击**“项目”**。  
  
8.  验证确认 Office 类别显示在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 下“项目类型”窗格中的“新建项目”对话框中。  
  
 还可以将项目项模板的子集分组到自定义文件夹中。  
  
##### 如要新建已安装的项模板类别  
  
1.  在已安装的模板目录的语言文件夹中创建一个文件夹。  例如，要为 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 项模板创建 Web 类别，你将创建以下目录：  
  
     \\*VisualStudioInstallationDirectory*\\Common7\\IDE\\ItemTemplates\\CSharp\\1033\\Web\\  
  
2.  将此类别的所有模板放入新文件夹。  
  
3.  关闭 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的所有实例。  
  
4.  在“启动”菜单上，单击“运行”，键入 **cmd**，然后单击“确定”。  
  
5.  在命令提示符处，找到包含 devenv.exe 的目录，然后键入 **devenv \/setup**。  
  
6.  运行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
7.  创建项目或打开现有项目。  
  
8.  在**“项目”**菜单上，单击**“添加新项”**。  
  
9. 验证确认 Web 类别显示在“项目类型”窗格的“添加新项”对话框中。  
  
### 组织自定义模板  
 可以通过在自定义模板位置添加新文件夹，将自定义模板组织到它们自己的类别中。  “新建项目”对话框将反映出对模板类别所做的任何更改。  
  
##### 如要新建自定义项目模板类别  
  
1.  在自定义项目模板目录的语言文件夹中创建一个文件夹。  例如，要为 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 模板创建 HelloWorld 类别，你将创建以下目录：  
  
     \\My Documents\\\<Visual Studio version\>\\Templates\\ProjectTemplates\\CSharp\\HelloWorld\\  
  
2.  将此类别的所有模板放入新文件夹。  
  
3.  在**“文件”**菜单上，单击**“新建”**，然后单击**“项目”**。  
  
4.  验证确认 HelloWorld 类别显示在 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 下“项目类型”窗格中的“新建项目”对话框中。  
  
 还可以将自定义项模板的子集分组到自定义文件夹中。  
  
##### 新建自定义项模板类别  
  
1.  在自定义项模板目录的语言文件夹中创建一个文件夹。  例如，要为 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 模板创建 HelloWorld 类别，你将创建以下目录：  
  
     \\My Documents\\\<Visual Studio version\>\\Templates\\ItemTemplates\\CSharp\\HelloWorld\\  
  
2.  将此类别的所有模板放入新文件夹。  
  
3.  创建项目或打开现有项目。  
  
4.  在**“项目”**菜单上，单击**“添加新项”**。  
  
5.  验证确认 HelloWorld 类别显示在“项目类型”窗格的“添加新项”对话框中。  
  
### 在父类别中显示模板  
 可以通过使用 .vstemplate 文件中的 `NumberOfParentCategoriesToRollUp` 元素允许子类别中的模板显示在其父类别中。  对于项目模板和项模板，操作步骤相同。  
  
##### 在父类别中显示模板  
  
1.  找到包含模板的 .zip 文件。  
  
2.  解压缩 .zip 文件。  
  
3.  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中打开 .vstemplate 文件。  
  
4.  在 `TemplateData` 元素内，添加一个 `NumberOfParentCategoriesToRollUp` 元素。  例如，以下代码使模板在父类别中可见，但在更高层次结构中不可见。  
  
    ```  
    <TemplateData>  
        ...  
        <NumberOfParentCategoriesToRollUp>  
            1  
        </NumberOfParentCategoriesToRollUp>  
        ...  
    </TemplateData>  
    ```  
  
5.  保存并关闭 .vstemplate 文件。  
  
6.  选择模板中的文件，右键单击所选文件，单击“发送至”，然后单击“压缩的文件夹”。  这些文件被压缩到一个 .zip 文件中。  
  
7.  删除解压缩的模板文件和旧的 .zip 模板文件。  
  
8.  将新的 .zip 文件放入曾容纳已删除 .zip 文件的目录。  
  
## 请参阅  
 [自定义模板](../ide/customizing-project-and-item-templates.md)   
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)   
 [NumberOfParentCategoriesToRollUp（Visual Studio 模板）](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)   
 [如何：创建项目模板](../ide/how-to-create-project-templates.md)   
 [如何：创建项模板](../ide/how-to-create-item-templates.md)