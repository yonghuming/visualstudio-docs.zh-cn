---
title: "如何：从命令行指定符号文件位置 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：从命令行指定符号文件位置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

为了显示函数名称和行号等符号信息，VSPerfReport 命令行工具要求访问被分析组件的符号 \(.pdb\) 文件以及 Windows 系统文件。  编译组件时将创建符号文件。  有关详细信息，请参阅[VSPerfReport](../profiling/vsperfreport.md)。  VSPerfReport 自动搜索以下位置的符号文件：  
  
-   **\/SymbolPath** 选项中或 **\_NT\_SYMBOL\_PATH** 环境变量中指定的路径。  
  
-   从中编译组件的准确本地路径。  
  
-   分析数据（.vsp 或 .vsps）文件所在的目录。  
  
 Microsoft 在符号服务器上联机提供其许多产品的 .pdb 文件。  如果用于报告的计算机与 Internet 相连，则 VSPerfReport 将连接到联机符号服务器自动查找符号信息，并将文件保存到本地存储区。  
  
 可以通过以下方式指定符号文件以及 Microsoft 符号服务器存储区的位置：  
  
-   设置 **\_NT\_SYMBOL\_PATH** 环境变量。  
  
-   向 VSPerfReport 命令行添加 **\/SymbolPath** 选项。  
  
 还可以同时使用这两种方法。  
  
> [!NOTE]
>  如果本地计算机上安装了 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，则可能已指定了 Windows 符号文件的位置。  有关详细信息，请参阅[如何：引用 Windows 符号信息](../profiling/how-to-reference-windows-symbol-information.md)。  仍必须配置 VSPerfReport 才能使用位置和服务器，如本主题后面所述。  
  
## 指定 Windows 符号文件  
  
#### 配置 Windows 符号服务器的使用  
  
1.  如有必要，请创建一个目录，在本地存储符号文件。  
  
2.  使用以下语法设置 **\_NT\_SYMBOL\_PATH** 环境变量或 VSPerfReport \/SymbolPath 选项：  
  
     **srv\*** *LocalStore* **\*http:\/\/msdl.microsoft.com\/downloads\/symbols**  
  
     其中 *LocalStore* 是您创建的本地目录的路径。  
  
## 指定组件符号文件  
 分析工具会搜索组件的 .pdb 文件，您想在这些文件在组件中存储的原始位置或包含分析数据文件的文件夹中对其进行分析。  可通过向 **\_NT\_SYMBOL\_PATH** 或向 **\/SymbolPath** 选项中添加一个或多个路径指定要搜索的其他位置。  各个路径之间用英文分号分隔。  
  
## 示例  
 以下命令行将 **\_NT\_SYMBOL\_PATH** 环境变量设置为 Windows 符号服务器，并将本地目录设置为 **C:\\Symbols**。  
  
 **set  \_NT\_SYMBOL\_PATH\=srv\*C:\\symbols\*http:\/\/msdl.microsoft.com\/downloads\/symbols**  
  
 通过使用 **\/SymbolPath** 选项，以下 VSPerfReport 命令行向搜索路径添加 C:\\Projects\\Symbols 目录。  
  
 **VSPerfReport**  *MyApp* **.exe \/SymbolPath:C:\\Projects\\Symbols \/summary:all**