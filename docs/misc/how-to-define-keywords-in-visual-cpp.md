---
title: "如何：在 Visual C++ 中定义关键字 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "用户关键字"
  - "保留字, 用户定义的关键字"
  - "用户定义的关键字"
  - "保留关键字, 用户定义的"
  - "usertype.dat"
  - "关键字 [C++], 用户定义的"
ms.assetid: 2dfcf343-e861-4bde-b5a4-7deb6773d9c8
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 如何：在 Visual C++ 中定义关键字
关键字是具有特殊意义的预定义保留标识符。 它们不能用作程序中的标识符。 但是，可以用 Visual C\+\+ 定义你要使用的关键字，还可以向这些关键字指定自定义语法着色。 语法着色将给出有关代码结构和状态的可视提示。  
  
### 定义你自己的 Visual C\+\+ 关键字  
  
1.  使用 Visual Studio [代码和文本编辑器](http://msdn.microsoft.com/zh-cn/508e1f18-99d5-48ad-b5ad-d011b21c6ab1)或 Notepad.exe 创建名为 `usertype.dat` 的纯文本文件。  
  
2.  在 `usertype.dat` 中，在单独的行中键入每个用户定义的关键字。  
  
3.  将 `usertype.dat` 保存到包含 devenv.exe 的目录中。 默认情况下，该目录的路径为 *\<drive\>*:\\Program Files\\[!INCLUDE[TLA#tla_visualstu](../misc/includes/tlasharptla_visualstu_md.md)] *\<major.minor version number\>*\\Common7\\[!INCLUDE[TLA2#tla_ide](../misc/includes/tla2sharptla_ide_md.md)]。 由于该目录默认为只读，因此需要管理凭据才能保存 `usertype.dat`。  
  
4.  退出 Visual Studio，然后重启它。  
  
    > [!NOTE]
    >  不能在编辑会话期间重命名或重新加载 `usertype.dat` 文件，因为在初始化期间会读取该文件。 在语法着色机制最后检查 `usertype.dat` 文件时，所有先前定义的颜色设置都是优先的。  
  
5.  在**“工具”**菜单上，单击**“选项”**。 在“选项”对话框中，依次单击“环境”和“字体和颜色”，然后在“显示项:”列表中单击“C\/C\+\+ 用户关键字”。  
  
6.  按[“选项”对话框 \-\>“环境”\-\>“字体和颜色”](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)中的说明为用于定义的关键字设置字体和颜色属性。  
  
 有关详细信息，请参阅[C\+\+ 关键字](/visual-cpp/cpp/keywords-cpp)。  
  
## 请参阅  
 [作为用户组的成员运行](/visual-cpp/top/running-as-a-member-of-the-users-group)   
 [默认键盘快捷键](../ide/default-keyboard-shortcuts-in-visual-studio.md)