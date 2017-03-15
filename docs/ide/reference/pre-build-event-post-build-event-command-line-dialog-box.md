---
title: "预生成事件/生成后事件命令行对话框 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cs.ProjectPropertiesBuildEventsBuilder"
  - "vb.ProjectPropertiesBuildEventsBuilder"
helpviewer_keywords: 
  - "$(SolutionExt)"
  - "$(ProjectDir)"
  - "$(TargetPath)"
  - "$(ProjectExt)"
  - "$(TargetFileName)"
  - "$(PlatformName)"
  - "$(SolutionName)"
  - "宏，生成事件"
  - "$(SolutionPath)"
  - "$(ProjectPath)"
  - "$(ProjectFileName)"
  - "$(DevEnvDir)"
  - "$(TargetName)"
  - "$(TargetDir)"
  - "$(SolutionDir)"
  - "$(TargetExt)"
  - "$(OutDir)"
  - "$(ConfigurationName)"
  - "$(SolutionFileName)"
  - "$(ProjectName)"
  - "生成事件，宏"
ms.assetid: d49b2c57-24bf-4fb2-8351-5c4b6cca938f
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# 预生成事件/生成后事件命令行对话框
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

可以直接在编辑框中键入 [“项目设计器”\-\>“生成事件”页 \(C\#\)](../../ide/reference/build-events-page-project-designer-csharp.md) 的预先生成和后期生成事件，也可以从可用宏列表中选择预先生成和后期生成宏。  
  
> [!NOTE]
>  如果项目是最新的且没有触发任何生成，则不会运行预生成事件。  
  
## UI 元素列表  
 **命令行编辑框**  
 包含要为预先生成或后期生成运行的事件。  
  
> [!NOTE]
>  在运行 .bat 文件的所有后期生成命令之前添加一个 `call` 语句。  例如，`call C:\MyFile.bat` 或 `call C:\MyFile.bat call C:\MyFile2.bat`。  
  
 **宏**  
 展开编辑框，显示要插入命令行编辑框中的宏列表。  
  
 **宏表**  
 列出可用的宏及其值。  有关每个宏的说明，请参见下面的“宏”。  一次只能选择将一个宏插入命令行编辑框中。  
  
 **Insert**  
 将在宏表中选择的宏插入命令行编辑框中。  
  
### 宏  
 可以使用以下任意宏来指定文件位置，或在存在多重选择的情况下获取输入文件的实际名称。  这些宏不区分大小写。  
  
|宏|描述|  
|-------|--------|  
|`$(ConfigurationName)`|当前项目配置的名称（如“Debug”）。|  
|`$(OutDir)`|输出文件目录的路径，相对于项目目录。  这解析为“输出目录”属性的值。  它包括尾部的反斜杠“\\”。|  
|`$(DevEnvDir)`|Visual Studio 安装目录 \(定义与驱动器和路径\);包括尾部的反斜杠“\\”。|  
|`$(PlatformName)`|当前目标平台的名称。  例如“AnyCPU”。|  
|`$(ProjectDir)`|项目的目录（定义为驱动器 \+ 路径）；包括尾部的反斜杠“\\”。|  
|`$(ProjectPath)`|项目的绝对路径名（定义为驱动器 \+ 路径 \+ 基本名称 \+ 文件扩展名）。|  
|`$(ProjectName)`|项目的基名称。|  
|`$(ProjectFileName)`|项目的文件名（定义为基本名称 \+ 文件扩展名）。|  
|`$(ProjectExt)`|项目的文件扩展名。  它在文件扩展名的前面包括“.”。|  
|`$(SolutionDir)`|解决方案的目录（定义为驱动器 \+ 路径）；包括尾部的反斜杠“\\”。|  
|`$(SolutionPath)`|解决方案的绝对路径名（定义为驱动器 \+ 路径 \+ 基本名称 \+ 文件扩展名）。|  
|`$(SolutionName)`|解决方案的基名称。|  
|`$(SolutionFileName)`|解决方案的文件名（定义为基本名称 \+ 文件扩展名）。|  
|`$(SolutionExt)`|解决方案的文件扩展名。  它在文件扩展名的前面包括“.”。|  
|`$(TargetDir)`|生成的主输出文件的目录（定义为驱动器 \+ 路径）。  它包括尾部的反斜杠“\\”。|  
|`$(TargetPath)`|生成的主输出文件的绝对路径名（定义为驱动器 \+ 路径 \+ 基本名称 \+ 文件扩展名）。|  
|`$(TargetName)`|生成的主输出文件的基本名称。|  
|`$(TargetFileName)`|生成的主输出文件的文件名（定义为基本名称 \+ 文件扩展名）。|  
|`$(TargetExt)`|生成的主输出文件的文件扩展名。  它在文件扩展名的前面包括“.”。|  
  
## 请参阅  
 [在 Visual Studio 中指定自定义生成事件](../../ide/specifying-custom-build-events-in-visual-studio.md)   
 [“项目设计器”\-\>“生成事件”页 \(C\#\)](../../ide/reference/build-events-page-project-designer-csharp.md)   
 [如何：指定生成事件 \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md)   
 [如何：指定生成事件 \(C\#\)](../../ide/how-to-specify-build-events-csharp.md)