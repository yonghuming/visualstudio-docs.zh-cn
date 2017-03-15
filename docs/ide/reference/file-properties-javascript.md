---
title: "文件属性，JavaScript | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "javascript.project.property.expandedsdknode.fileversion"
  - "javascript.project.property.expandedsdknode.uri"
  - "javascript.project.property.expandedsdknode.filename"
  - "javascript.project.property.reference.description"
  - "javascript.project.property.reference.specificversion"
  - "javascript.project.property.reference.identity"
  - "javascript.project.property.fullpath"
  - "javascript.project.property.packageaction"
  - "javascript.project.property.reference.package"
  - "javascript.project.property.copytooutputdirectory"
  - "javascript.project.property.expandedsdknode.sdkpath"
  - "javascript.project.property.reference.filetype"
  - "javascript.project.property.reference.culture"
  - "javascript.project.property.filename"
  - "javascript.project.property.reference.resolvedpath"
  - "javascript.project.property.reference.version"
ms.assetid: 085913b8-a97b-45f7-85fa-bbb0902f3ee9
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# 文件属性，JavaScript
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

可以使用文件属性指示项目系统应对文件执行什么操作。  例如，可以设置文件属性指示是否应将文件添加到包作为资源文件。  
  
 可以在解决方案资源管理器中选择任何文件，然后在“属性”窗口中检查其属性。  JavaScript 文件有四个属性：**复制到输出目录**、**包操作**、**文件名**和 **文件路径**。  
  
## 文件属性  
 本节描述共有的属性 JavaScript 文件。  
  
### “复制到输出目录”属性  
 此属性指定将选定的源文件复制到输出目录所依据的条件。  如果文件从未复制到输出目录中，则选择**“不复制”**。  如果文件总是复制到输出目录中，则选择**“始终复制”**。  如果仅在此文件比输出目录中与其名称相同的现有文件更新时复制，则选择**“如果较新则复制”**。  
  
### 包操作  
 **包操作** 属性指示 Visual Studio 对文件，在生成时。  **包操作** 可以有多个值之一：  
  
-   **无** \-文件包清单中不包括。  例如包含文档的文本文件，如自述文件。  
  
-   **内容** \-文件包清单中包含。  例如，设置为 .htm、.js、.css、图像、音频或视频文件的默认值。  
  
-   **清单** –文件包清单中不包括。  相反，那么，当生成清单时，的包文件为输入使用。  这是 package.appxmanifest 文件的默认值。  
  
-   **资源** \-文件包清单中不包括。  相反，文件的内容在输入包清单的包资源索引 \(PRI\) 索引。  此设置通常用于资源文件。  
  
 **包操作** 的默认值取决于添加到解决方案中的文件的扩展名。  
  
### “文件名“属性  
 显示文件名作为只读属性的值。  若要重命名文件，则在解决方案资源管理器必须右击并选择 **重命名**。  
  
### 完整路径属性  
 显示完整路径文件为只读值。  若要更改文件的路径，可以拖放在解决方案资源管理器中的文件。  
  
## 引用文件属性  
 本节描述共有的属性从 [!INCLUDE[win8_app_js](../../ide/reference/includes/win8_app_js_md.md)]引用的文件。  如果选择某个引用例如 .winmd 文件时，SDK 引用，项目到项目的引用，或程序集在解决方案资源管理器在"属性"窗口中引用，其他属性可以显示，根据文件类型。  
  
### 区域性  
 显示该语言与引用。  
  
### 文件类型  
 所引用的文件类型。  
  
### 文件版本  
 所引用的文件版本。  
  
### 标识  
 显示在项目，存储在项目文件中引用的标识。  
  
### Package  
 显示名称的程序包清单与引用。  
  
### 解决的路径  
 显示路径。在项目的引用。  
  
### SDK 路径  
 显示路径引用的 SDK 文件。  
  
### Uri  
 公开项目的 HTML 或 JavaScript 文件必须包括文件作为源文件的 URI。  
  
### 版本  
 所引用的版本。  
  
## 请参阅  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/zh-cn/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)