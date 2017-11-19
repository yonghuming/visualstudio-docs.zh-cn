---
title: "杂项，XML，文本编辑器，选项对话框 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd3fff31-cddc-422d-a2f0-a5a1ef492afd
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 871190deb39504a498061602b11f927832d71f35
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="miscellaneous-xml-text-editor-options-dialog-box"></a>杂项，XML，文本编辑器，“选项”对话框
使用此对话框可以更改“XML 编辑器”的自动完成和架构设置。 你可以访问**选项**对话框**工具**菜单。  
  
> [!NOTE]
>  当你选择这些设置才可用**文本编辑器**文件夹， **XML**文件夹，然后**杂项**选项从**选项**对话框。  
  
## <a name="auto-insert"></a>自动插入  
 **结束标记**  
 如果选中自动完成设置，则在键入右尖括号 (>) 以结束开始标记时（如果该标记尚未结束），编辑器会自动添加一个结束标记。 这是默认行为。  
  
 空元素的完成不依赖于自动完成设置。 可通过键入反斜杠 (/) 来始终自动完成空元素。  
  
 **特性引号**  
 在编写 XML 属性时，编辑器会插入 `=" "` 字符并将插入符号 (^) 置于双引号之间。  
  
 默认情况下选中此选项。  
  
 **命名空间声明**  
 编辑器根据需要自动插入命名空间声明。  
  
 默认情况下选中此选项。  
  
 **其他标记 （注释、 CDATA）**  
 自动完成注释、CDATA、DOCTYPE、处理指令和其他标记。  
  
 默认情况下选中此选项。  
  
## <a name="network"></a>网络  
 **自动下载 Dtd 和架构**  
 架构和文档类型定义 (DTD) 自动从 HTTP 位置下载。 此功能在启用自动代理服务器检测的情况下使用 System.Net。  
  
 默认情况下选中此选项。  
  
## <a name="outlining"></a>大纲显示  
 **打开文件时进入大纲模式**  
 在打开文件时启用大纲功能。  
  
 默认情况下选中此选项。  
  
## <a name="caching"></a>缓存  
 **架构**  
 指定架构缓存的位置。 浏览按钮 (**...**) 打开**目录浏览**对话框在当前架构缓存的位置。 你可以选择不同的目录，也可以在对话框中，选择一个文件夹右键单击，然后选择**打开**查看目录中的内容。  
  
## <a name="see-also"></a>另请参阅  
 [XML 文档属性，属性窗口](../xml-tools/xml-document-properties-properties-window.md)   
 [“XML 编辑器”的组件](../xml-tools/xml-editor-components.md)