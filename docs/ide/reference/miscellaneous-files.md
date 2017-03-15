---
title: "杂项文件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.newfile"
  - "VS.OpenWith"
  - "MiscellaneousFilesProject"
helpviewer_keywords: 
  - "解决方案, 杂项文件"
  - "生成 [Visual Studio], 杂项文件"
  - "独立文件"
  - "解决方案资源管理器, 杂项文件"
  - "“杂项文件”文件夹"
  - "文件 [Visual Studio], 容器外部"
  - "文件 [Visual Studio], “杂项文件”文件夹"
ms.assetid: 5b96640b-8efe-48a4-8d0a-1ae3f9587e44
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# 杂项文件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

可能需要使用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 编辑器独立于项目或解决方案来处理文件。  打开某个解决方案后，可以打开和修改文件，而不必将其添加到解决方案或项目中。  要独立于容器来处理的文件称为杂项文件。  杂项文件位于解决方案和项目的外部，不包括在生成中，而且无法包括在受源代码管理的解决方案中。  
  
 由于各种原因，独立于容器打开文件很有用。  您可能有一个需要在开发基于项目的解决方案时查看的文件，但它对于解决方案的开发并非必不可少。  通用示例包括开发说明或指令、数据库架构和代码剪辑。  此外，您可能还需要创建独立文件。  
  
 ![解决方案项目](../../ide/reference/media/projects_solutions_misc.gif "Projects\_Solutions\_Misc")  
  
 如果启用了相应的文件夹选项，则解决方案资源管理器可为这类文件显示一个“杂项文件”文件夹。  可从[“选项”对话框 \-\>“环境”\-\>“文档”](../../ide/reference/documents-environment-options-dialog-box.md)中设置这些选项。  关闭某个杂项文件后，该文件与任何特定解决方案或项目都不相关，除非也启用了使之相关的选项。  
  
 “杂项文件”文件夹将文件表示为链接。  尽管此文件夹不是解决方案的一部分，但当打开某解决方案时，上次关闭该解决方案时打开的部分或全部杂项文件重新打开，这具体取决于该文件夹的设置。  
  
> [!NOTE]
>  有些没有在“杂项文件”文件夹中显示的文件是不能在 IDE 中修改的文件，例如 .zip 和 .doc 文件。  IDE 不会跟踪那些只能通过外部编辑器修改的文件。  
  
## IDE 中的可用命令  
 根据打开的文件的格式，它们包括的菜单、工具栏和命令会发生变化。  例如，打开一个文本文件时，出现“文本编辑器”工具栏而且其命令可用。  如果接着打开“XML 架构”文件，则出现“XML 架构”工具栏。  编辑“XML 架构”时，“文本编辑器”工具栏的命令（或该工具栏本身）不可用。  “XML 架构”是活动窗口，因此具有当前选定内容上下文。  当从项目文件切换到杂项文件时，所有与项目相关的命令消失，仅显示那些直接与杂项文件相关的命令。  
  
## 文件夹显示选项  
 可以设置“杂项文件夹”的显示选项，以便即使未打开任何“杂项文件”时也显示该文件夹。  解决方案文件不永久管理杂项文件列表。  它使用一个可选功能，该功能使它记住每个用户最近使用过 \(MRU\) 的一组文件。  
  
## 请参阅  
 [解决方案和项目](../../ide/solutions-and-projects-in-visual-studio.md)   
 [“选项”对话框 \-\>“环境”\-\>“文档”](../../ide/reference/documents-environment-options-dialog-box.md)