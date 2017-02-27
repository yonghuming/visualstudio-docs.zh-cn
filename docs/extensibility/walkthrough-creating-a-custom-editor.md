---
title: "演练: 创建自定义编辑器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，自定义的创建"
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# 演练: 创建自定义编辑器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPackage 项目模板可以在 c \+ \+ 创建一个简单的自定义编辑器。  VSPackage 项目模板不再支持 C\# 或 Visual Basic 项目。 有关详细信息，请参阅[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## 系统必备  
 要按照本演练的步骤操作，必须安装 Visual Studio SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## Visual Studio 程序包项目模板  
 在找不到 Visual Studio Package 项目模板 **新项目** c \+ \+ 扩展性文件夹中的对话框  
  
### 若要创建使用 Visual Studio Package 模板的 VSPackage  
  
1.  使用 Visual Studio Package 模板创建一个项目。  
  
2.  选择 **自定义编辑器** 选项，然后单击 **下一步**。**编辑器选项** 显示页。  
  
3.  键入您的编辑器中的名称 **编辑器名称** 框。 键入你想要将您的编辑器中与相关联的文件扩展名 **文件扩展名** 框。 您的编辑器仅供具有此扩展名的文件。 文件扩展名为注册 Visual Studio 仅，不适用于 Windows。 键入与您的编辑器中创建的新文档的默认文件名称 **默认文件名** 框。  
  
4.  单击“完成”以在指定的文件夹中创建 VSPackage。  
  
### 若要测试自定义编辑器  
  
1.  在 **文件** 菜单上，指向 **新建** ，然后单击 **文件**。  
  
2.  在 **已安装的模板** 窗格 **新文件** 对话框中，选择您刚刚注册类型在文件模板，则该文件。  
  
3.  单击 **打开** 可以查看和编辑文档。  
  
     该编辑器支持剪切和粘贴、 查找和替换和打开加载操作。  
  
## 请参阅  
 [Vspackage](../extensibility/internals/vspackages.md)