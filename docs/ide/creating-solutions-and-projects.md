---
title: "创建解决方案和项目 | Microsoft Docs"
ms.custom: 
ms.date: 03/21/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.openprojectfromweb
- vs.newproject
- VS.ToolsOptionsPages.Projects.General
- SolutionItemsProject
helpviewer_keywords:
- solutions [Visual Studio], deleting
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
ms.assetid: 836f8ca0-3fc9-4f4b-9090-45f2e4d2e9c8
caps.latest.revision: 46
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 9a4b04dc59c409a5c68ad1fb376abb33b3859ff6
ms.contentlocale: zh-cn
ms.lasthandoff: 05/24/2017

---

# 创建解决方案和项目
<a id="create-solutions-and-projects" class="xliff"></a>

项目是生成应用程序所需的所有内容的逻辑容器。 依次选择主菜单上的“文件”、“新建”和“项目”创建项目时，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 会创建将项目包含在内的解决方案。 如有必要，可以继续向解决方案添加更多新项目或现有项目。 可以从现有代码文件创建项目，也可创建在使用完毕后删除的临时项目（仅 .NET）。

> [!NOTE]
>  本主题中的说明基于 Visual Studio Community 版。 您看到的对话框和菜单命令可能与此处描述的有所不同，这取决于您的设置或 Visual Studio 版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。

## 从已安装项目模板创建项目
<a id="create-a-project-from-an-installed-project-template" class="xliff"></a>  
 依次选择主菜单上的“文件”、“新建”和“项目”，调出“新建项目”对话框。 在左侧窗格的“已安装”下，依次选择“模板”、编程语言和平台或技术，然后从中间窗格的可用模板中进行选择。  

 在 **“新建项目”** 对话框中，选择 **“解决方案”** 下拉列表中提供的选项，在新解决方案、现有解决方案或 Visual Studio 的新实例中创建新项目。  

## 从现有代码文件创建项目
<a id="create-a-project-from-existing-code-files" class="xliff"></a>  
 如果有一系列松散源文件，则可以轻松创建一个包含它们的项目。 依次选择“文件”、“新建”和“从现有代码创建项目”，启动“从现有代码文件创建项目”向导，然后按提示操作。  

> [!TIP]
>  此选项最适合各组相对简单的文件。  

## 创建临时项目（C# 和 Visual Basic）
<a id="create-a-temporary-project-c-and-visual-basic" class="xliff"></a>
 使用临时项目时，你可以在不指定磁盘位置的情况下创建和试验 .NET 项目。 创建项目时，只需在 **“新建项目”** 对话框中选择项目类型和模板，并指定名称。 使用临时项目时，你可以随时保存或放弃它。  

## 创建面向 .NET Framework 特定版本的 .NET 项目
<a id="create-a-net-project-that-targets-a-specific-version-of-the-net-framework" class="xliff"></a>  
 通过使用 **“新建项目”** 对话框顶部的 **“.NET Framework”** 版本下拉菜单，您可以创建面向 .Net Framework 早期版本的项目。 在选择项目模板之前设置此值，因为只有与该 .NET Framework 版本兼容的模板将出现在列表中。  

 您必须在您的系统上安装 .NET Framework 3.5，这样可以访问 framework 4.0 以前的版本。  

## 下载示例解决方案
<a id="download-sample-solutions" class="xliff"></a>  
 可以使用 Visual Studio 下载和安装 [MSDN 代码库](http://go.microsoft.com/fwlink/?LinkId=254185)和 Git 存储库等其他源中的示例解决方案。

 您可单独下载示例，也可以下载包含共享技术或主题的相关示例的示例包。 在为下载的任何示例发布源代码更改时，您将收到通知。  

 有关详细信息，请参阅 [Visual Studio 示例](../ide/visual-studio-samples.md)。  

## 在解决方案一级添加单个文件
<a id="add-single-files-at-the-solution-level" class="xliff"></a>  
 有时，一个文件可能会被多个项目引用，或者包含在逻辑上属于解决方案级而非特定项目下的文本或各种数据。  向解决方案添加单个项：  

- 右键单击“解决方案资源管理器”中的解决方案节点，然后依次选择“添加”和“新建项”，或依次选择“添加”和“现有项”。  

## 创建空的解决方案
<a id="create-empty-solutions" class="xliff"></a>  
 尽管项目驻留在解决方案中，也可以创建不包含任何项目的解决方案。 还可以打开代码项目，而无需创建解决方案。

#### 创建空解决方案
<a id="to-create-an-empty-solution" class="xliff"></a>  

1.  在“文件”菜单上，依次选择“新建”和“新建项目”。  

2.  在左侧窗格中，依次选择展开列表中的“已安装”、“其他项目类型”和“Visual Studio 解决方案”。  

3.  在中间窗格中，选择“空白解决方案”。  

4.  设置解决方案的“名称”和“位置”值，然后选择“确定”。  

创建空白解决方案后，可以选择“项目”菜单上的“添加新项”或“添加现有项”，将新的或现有的项目或项添加到解决方案中。

### 删除解决方案
<a id="delete-solutions" class="xliff"></a>  
 您可以永久性删除解决方案，但不能使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]来删除解决方案。 在删除解决方案前，把您要再次使用的任何项目移动到其他解决方案中。 然后，使用文件资源管理器删除包含 .sln 和 .suo 解决方案文件的目录。  

> [!NOTE]
>  .suo 文件是隐藏文件，在默认的文件资源管理器设置下不会显示。  

##### 要删除解决方案
<a id="to-delete-a-solution" class="xliff"></a>  

1.  在“解决方案资源管理器”中，在要删除的解决方案的上下文（右键单击）菜单中，选择“在文件资源管理器中打开文件夹”。

2.  在文件资源管理器中，导航到上一级。

3.  选择包含解决方案的目录，然后按 DELETE 键。

## 另请参阅
<a id="see-also" class="xliff"></a>  
 [解决方案和项目](../ide/solutions-and-projects-in-visual-studio.md)   

