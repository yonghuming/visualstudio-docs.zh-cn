---
title: "“选项”对话框 -&gt;“环境”-&gt;“自动恢复” | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPag.Environment.AutoRecover"
  - "VS.DialogAutoRestore"
  - "VS.ToolsOptionsPages.Environment.AutoRecover"
  - "VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore"
helpviewer_keywords: 
  - "文件，恢复"
  - "自动恢复页"
  - "保存文件，自动"
  - "文件，自动保存"
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# “选项”对话框 -&gt;“环境”-&gt;“自动恢复”
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

使用“选项”对话框中的该页可以指定是否自动备份文件。  通过该页，还可以指定在集成开发环境 \(IDE\) 意外关闭时是否还原已修改的文件。  您可以通过依次选择**“工具”**菜单、**“选项”**、**“环境”**文件夹，然后选择**“自动恢复”**页来访问该对话框。  如果此页未出现在列表中，请在**“选项”**对话框中选择**“显示所有设置”**。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于您现用的设置或版本。  若要更改设置，请在“工具”菜单上选择“导入和导出设置”。  有关更多信息，请参见 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
 **保存自动恢复信息的时间间隔: \<n\> 分钟**  
 使用此选项可以自定义在编辑器中自动保存文件的频率。  对于以前保存的文件，文件副本保存在 \\...  \\My Documents\\Visual Studio \<*版本*\>\\Backup Files\\\<*项目名称*\>。  如果文件是新的，且尚未手动保存过，则使用一个随机生成的文件名来自动保存该文件。  
  
 **保留自动恢复信息的天数: \<n\> 天**  
 使用此选项可以指定 Visual Studio 对于为自动恢复创建的文件保留多长时间。  
  
## 请参阅  
 [“选项”对话框](../../ide/reference/options-dialog-box-visual-studio.md)