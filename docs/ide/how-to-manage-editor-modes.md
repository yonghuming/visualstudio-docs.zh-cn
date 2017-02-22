---
title: "如何：管理编辑器模式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "代码编辑器, modes"
  - "代码编辑器, 查看和显示选项"
  - "字体和大小"
  - "全屏显示模式"
  - "行号"
  - "行号, 显示"
  - "视图, 更改模式"
  - "视图, 创建新窗口"
  - "视图, 行号"
  - "视图, 大纲显示"
  - "视图, 拆分"
  - "视图, 虚拟空间"
  - "视图, 字回绕"
  - "虚拟空间模式"
  - "自动换行"
ms.assetid: 1fb48027-d870-439f-8b72-4a0321390748
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：管理编辑器模式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可以显示 Visual Studio 代码编辑器的各种显示模式。  
  
> [!NOTE]
>  您看到的对话框和菜单命令可能会与 " 帮助 " 中的描述不同具体取决于您现用的设置或版本。  若要更改设置，请选择在 **工具** 菜单的 **导入和导出设置** 。  有关更多信息，请参见 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 启用 " 全屏 " 模式  
 可以选择隐藏所有工具窗口，而视图是通过初始化 **全屏显示** 架构只文档窗口。  
  
#### 启用 " 全屏 " 模式  
  
-   按 ALT\+SHIFT\+ENTER 进入或退出 **全屏显示** 模式。  
  
     \-\-或\-\-  
  
-   发出在 **命令** 窗口的命令 `View.Fullscreen` 。  
  
## 启用 " 虚空格 " 模式  
 在 **虚拟空间** 模式下，空格插入到每行代码的结尾。  选择此选项将注释定位在代码旁的一致位置。  
  
#### 启用 " 虚空格 " 模式  
  
1.  选择 **选项** 从 **工具** 菜单。  
  
2.  外接 **文本编辑器** 文件夹，然后选择 **所有语言** 全局设置此选项或选择一个特定的语言文件夹。  \(例如，打开行只想在 Visual Basic 中，选择基本，文本编辑器选项。\)  
  
3.  选择 **常规** 选项卡，在 **设置**，选择下的 **启用虚空格**。  
  
    > [!NOTE]
    >  **虚拟空间** 在 **列选择** 模式下启用。  当 **虚拟空间** 未启用模式时，插入点从一行末尾的直接移到第一个字符下。  
  
## 请参阅  
 [自定义编辑器](../ide/customizing-the-editor.md)   
 [如何：排列和停靠窗口](../misc/how-to-arrange-and-dock-windows.md)   
 [“选项”对话框 \-\>“环境”\-\>“字体和颜色”](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)