---
title: "如何：更改生成输出目录 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ccbb32b9fd035a9058812eb5a3df306ff629086f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-change-the-build-output-directory"></a>如何：更改生成输出目录
可以按项目生成的配置（调试、发布或两者）指定输出的位置。  
  
> [!NOTE]
>  如果你具有“安装”  项目，请参阅本文末尾处的注释。  
  
## <a name="changing-the-build-output-directory"></a>更改生成输出目录  
  
#### <a name="to-change-the-build-output-directory"></a>若要更改生成输出目录  
  
1.  在菜单栏上，选择 **“项目”**、 *AppName* **“属性”**。 还可以在 **“解决方案资源管理器”** 中右键单击项目节点并选择 **“属性”**。  
  
2.  如果你有 Visual Basic 项目，请选择 **“编译”** 选项卡。如果你有 Visual C# 项目，请选择 **“编译”** 选项卡。如果你具有 C++ 项目或 JavaScript 项目，请选择 **“常规”** 选项卡。  
  
3.  在顶部的配置下拉列表中，选择你想要更改其输出文件位置的配置（调试、发布或全部）。  
  
     查找输出路径条目（Visual Basic 中的**“生成输出路径”** ，Visual C++中的 **“输出目录”** ，JavaScript 和 C# 中的 **“输出路径”** ）。 指定一个相对于项目目录的新的生成输出目录。  
  
> [!NOTE]
>  在“安装”项目中，“输出文件名称”  框仅更改 Setup.exe 文件的位置，而不更改项目文件的位置。 有关详细信息，请参阅 **生成、配置属性、“部署项目属性”对话框**。  
  
## <a name="see-also"></a>另请参阅  
 [生成页、项目设计器 (C#)](../ide/reference/build-page-project-designer-csharp.md)   
 [常规属性页（项目）](/cpp/ide/general-property-page-project)   
 [编译和生成](../ide/compiling-and-building-in-visual-studio.md)