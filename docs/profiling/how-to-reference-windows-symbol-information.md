---
title: "如何：引用 Windows 符号信息 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "性能工具, 符号服务器"
  - "服务器, 符号服务器"
  - "分析工具, 符号服务器"
  - "符号服务器"
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：引用 Windows 符号信息
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio 分析工具使用符号 \(.pdb\) 文件来解析符号名称，例如，程序二进制文件中的函数名称。  可以按照以下步骤为本地计算机上的 Windows 版本自动下载和更新正确的 .pdb 文件。  
  
> [!NOTE]
>  此设置不会影响现有报告。  只有在指定符号服务器以后创建的报告才会有符号信息。  
  
 有关详细信息，请参阅[指定符号 \(.pdb\) 和源文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。  
  
### 使用 Microsoft 符号服务器  
  
1.  创建用于包含符号文件信息的文件夹，如 C:\\SymbolCache。  
  
2.  在**“工具”**菜单上，单击**“选项”**。  
  
     这将显示**“选项”**对话框。  
  
3.  展开**“调试”**树，然后单击**“符号”**。  
  
4.  在 **符号文件 \(.pdb\) 位置**中，选择 **Microsoft 符号服务器**  
  
5.  在**“将符号从符号服务器缓存到此目录”**中，键入在第 1 步中创建的文件夹的路径，例如：  
  
     C:\\SymbolCache  
  
     您还可以单击省略号按钮 \(**...**\)。然后从 **浏览文件夹** 对话框的目录。  
  
## 请参阅  
 [配置性能会话](../profiling/configuring-performance-sessions.md)   
 [如何：序列化符号信息](../profiling/how-to-serialize-symbol-information.md)