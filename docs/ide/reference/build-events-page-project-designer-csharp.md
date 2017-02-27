---
title: "“项目设计器”-&gt;“生成事件”页 (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cs.ProjectPropertiesBuildEvents"
helpviewer_keywords: 
  - "生成事件"
  - "项目设计器，“生成事件”页"
  - "生成前事件"
  - "生成后事件"
ms.assetid: 3fff9ae5-213c-46ea-a660-1d70acb6c922
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# “项目设计器”-&gt;“生成事件”页 (C#)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

使用**“项目设计器”**的**“生成事件”**页来指定生成配置说明。  还可以指定运行任何后期生成事件的条件。  有关更多信息，请参见[如何：指定生成事件 \(C\#\)](../../ide/how-to-specify-build-events-csharp.md)和[如何：指定生成事件 \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md)。  
  
## UIElement 列表  
 **配置**  
 此控件在此页面中不可编辑。  有关此控件的说明，请参见[“项目设计器”\-\>“生成”页 \(C\#\)](../../ide/reference/build-page-project-designer-csharp.md)。  
  
 **平台**  
 此控件在此页面上不可编辑。  有关此控件的说明，请参见[“项目设计器”\-\>“生成”页 \(C\#\)](../../ide/reference/build-page-project-designer-csharp.md)。  
  
 **预先生成事件命令行**  
 指定在开始生成之前要执行的任何命令。  若要键入长命令，请单击**“编辑预先生成事件”**以显示 [预生成事件\/生成后事件命令行对话框](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)。  
  
> [!NOTE]
>  如果项目是最新的且没有触发任何生成，则不会运行预生成事件。  
  
 **后期生成事件命令行**  
 指定在生成结束之后要执行的任何命令。  若要键入长命令，请单击**“编辑后期生成事件”**以显示**“预先生成事件\/后期生成事件命令行”**对话框。  
  
> [!NOTE]
>  在运行 .bat 文件的所有后期生成命令之前添加一个 `call` 语句。  例如，`call C:\MyFile.bat` 或 `call C:\MyFile.bat call C:\MyFile2.bat`。  
  
 **运行后期生成事件**  
 要使后期生成事件能够运行，请指定以下条件（如下表中所示）。  
  
|选项|结果|  
|--------|--------|  
|**始终**|无论生成是否成功，都将运行生成后事件。|  
|**生成成功时**|如果生成成功，将运行生成后事件。  因此，即使是最新的项目，只要生成成功，就会运行该事件。|  
|**当生成更新项目输出时**|仅当编译器的输出文件（.exe 或 .dll）不同于以前的编译器输出文件时，才会运行后期生成事件。  因此，如果项目是最新的，则不会运行后期生成事件。|  
  
## 请参阅  
 [如何：指定生成事件 \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md)   
 [如何：指定生成事件 \(C\#\)](../../ide/how-to-specify-build-events-csharp.md)   
 [项目属性引用](../../ide/reference/project-properties-reference.md)   
 [在 Visual Studio 中构建应用程序](../../ide/compiling-and-building-in-visual-studio.md)