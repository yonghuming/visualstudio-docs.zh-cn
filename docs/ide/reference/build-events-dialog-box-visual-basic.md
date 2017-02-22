---
title: "“生成事件”对话框 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesBuildEvents"
helpviewer_keywords: 
  - "生成事件"
  - "生成事件，指定"
  - "生成前事件"
  - "“生成事件”对话框"
  - "生成后事件"
ms.assetid: 3a81a7c7-39f9-47a8-ba5a-b351227f380e
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# “生成事件”对话框 (Visual Basic)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

使用**“生成事件”**对话框可指定生成配置说明。  也可以指定运行任何预先生成事件或后期生成事件所依据的条件。  有关更多信息，请参见 [如何：指定生成事件 \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md)。  
  
 **预先生成事件命令行**  
 指定在开始生成之前要执行的任何命令。  若要键入长命令，请单击**“编辑预先生成事件”**以显示 [预生成事件\/生成后事件命令行对话框](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)。  
  
> [!NOTE]
>  如果项目是最新的，且未触发生成，将不会运行预先生成事件。  
  
 **后期生成事件命令行**  
 指定在生成结束之后要执行的任何命令。  若要键入长命令，请单击**“编辑后期生成事件”**以显示**“预先生成事件\/后期生成事件命令行”**对话框。  
  
> [!NOTE]
>  在运行 .bat 文件的所有后期生成命令之前添加一个 `call` 语句。  例如，`call C:\MyFile.bat` 或 `call C:\MyFile.bat call C:\MyFile2.bat`。  
  
 **运行后期生成事件**  
 指定使后期生成事件运行所需的条件，如下表中所示。  
  
|选项|结果|  
|--------|--------|  
|**始终**|无论生成是否成功，都将运行后期生成事件。|  
|**生成成功时**|如果生成成功，将运行生成后事件。  即使是最新的项目，只要生成成功，就会运行该事件。  此设置为默认设置。|  
|**当生成更新项目输出时**|仅当编译器的输出文件（.exe 或 .dll）不同于以前的编译器输出文件时，才会运行后期生成事件。  如果项目是最新的，则不会运行后期生成事件。|  
  
## 请参阅  
 [“编译”页, 项目设计器 \(Visual Basic\)](../../ide/reference/compile-page-project-designer-visual-basic.md)   
 [如何：指定生成事件 \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md)   
 [预生成事件\/生成后事件命令行对话框](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)