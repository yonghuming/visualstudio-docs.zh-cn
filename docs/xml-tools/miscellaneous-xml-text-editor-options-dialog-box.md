---
title: "杂项，XML，文本编辑器，“选项”对话框 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fd3fff31-cddc-422d-a2f0-a5a1ef492afd
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# 杂项，XML，文本编辑器，“选项”对话框
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用此对话框可以更改“XML 编辑器”的自动完成和架构设置。可以从“工具”菜单访问“选项”对话框。  
  
> [!NOTE]
>  从**“选项”**对话框中依次选择**“文本编辑器”**文件夹、**“XML”**文件夹、**“杂项”**选项时，可使用下列设置。  
  
## 自动插入  
 **结束标记**  
 如果选中自动完成设置，则在键入右尖括号 \(\>\) 以结束开始标记时（如果该标记尚未结束），编辑器会自动添加一个结束标记。这是默认行为。  
  
 空元素的完成不依赖于自动完成设置。可通过键入反斜杠 \(\/\) 来始终自动完成空元素。  
  
 **特性引号**  
 在编写 XML 特性时，编辑器会插入 `=" "` 字符并将插入符号 \(^\) 置于双引号之间。  
  
 默认情况下选中此选项。  
  
 **命名空间声明**  
 编辑器根据需要自动插入命名空间声明。  
  
 默认情况下选中此选项。  
  
 **其他标记（注释、CDATA）**  
 自动完成注释、CDATA、DOCTYPE、处理指令和其他标记。  
  
 默认情况下选中此选项。  
  
## 网络  
 **自动下载 DTD 和架构**  
 架构和文档类型定义 \(DTD\) 自动从 HTTP 位置下载。此功能在启用自动代理服务器检测的情况下使用 System.Net。  
  
 默认情况下选中此选项。  
  
## 大纲  
 **打开文件时进入大纲模式**  
 在打开文件时启用大纲功能。  
  
 默认情况下选中此选项。  
  
## 缓存  
 **架构**  
 指定架构缓存的位置。“浏览”按钮 \(**...**\) 在当前架构缓存位置打开“目录浏览”对话框。可以选择其他目录，也可以在该对话框中选择一个文件夹，右击，然后选择“打开”查看目录中的内容。  
  
## 请参阅  
 [XML 文档属性，“属性”窗口](../xml-tools/xml-document-properties-properties-window.md)   
 [“XML 编辑器”的组件](../xml-tools/xml-editor-components.md)