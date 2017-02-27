---
title: "shell 命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tools.shell"
helpviewer_keywords: 
  - ".exe 文件"
  - "exe 文件"
  - "可执行文件, 从 Visual Studio 运行"
  - "shell 命令"
  - "shell, 启动 exe 文件"
  - "工具.shell 命令"
  - "Visual Studio, 可执行文件"
ms.assetid: 737fda23-b852-45c4-a9fe-41cbce6ba70f
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# shell 命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

从 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 内启动可执行程序。  
  
## 语法  
  
```  
Tools.Shell [/command] [/output] [/dir:folder] path [args]  
```  
  
## 参数  
 `path`  
 必选。  要执行的文件或要打开的文档的路径和文件名。  如果在环境变量 PATH 的某个目录中没有指定的文件，则必须使用完整路径。  
  
 `args`  
 可选。  要传递给被调用的程序的任何参数。  
  
## 开关  
 \/commandwindow \[或\] \/command \[或\] \/c \[或\] \/cmd  
 可选。  指定在**“命令”**窗口中显示可执行文件的输出。  
  
 \/dir:`folder` \[或\] \/d: `folder`  
 可选。  指定程序运行时要设置的工作目录。  
  
 \/outputwindow \[或\] \/output \[或\] \/out \[或\] \/o  
 可选。  指定在**“输出”**窗口中显示可执行文件的输出。  
  
## 备注  
 必须在 `Tools.Shell` 之后立即指定 \/dir \/o \/c。  在可执行文件名之后指定的任何内容都将作为命令行参数传给该文件。  
  
 可以使用预定义的别名 `Shell` 替换 `Tools.Shell`。  
  
> [!CAUTION]
>  如果 `path` 参数提供了目录路径和文件名，则应该将整个路径名引在原义引号 \("""\) 中，如下所示：  
  
```  
Tools.Shell """C:\Program Files\SomeFile.exe"""  
```  
  
 `Shell` 处理器将三个为一组的每组双引号 \("""\) 解释为一个双引号字符。  因此，上述示例实际上将以下路径字符串传递给 `Shell` 命令：  
  
```  
"C:\Program Files\SomeFile.exe"  
```  
  
> [!CAUTION]
>  如果您未将路径字符串引在文本引号 \("""\) 中，Windows 将只使用第一个空格前的字符串部分。  例如，如果上面的路径字符串引用不正确，则 Windows 将查找 C:\\ 根目录中的名为“Program”的文件。  如果 C:\\Program.exe 可执行文件实际可用，则即使是由非法篡改安装的，Windows 也会尝试执行该程序，而不执行所需的“c:\\Program Files\\SomeFile.exe”程序。  
  
## 示例  
 下面的命令使用 xcopy.exe 将文件 `MyText.txt` 复制到 `Text` 文件夹中。  xcopy.exe 的输出同时显示在**“命令”**窗口和**“输出”**窗口中。  
  
```  
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt  
```  
  
## 请参阅  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [“命令”窗口](../../ide/reference/command-window.md)   
 [输出窗口](../../ide/reference/output-window.md)   
 [“查找\/命令”框](../../ide/find-command-box.md)   
 [Visual Studio 命令别名](../../ide/reference/visual-studio-command-aliases.md)