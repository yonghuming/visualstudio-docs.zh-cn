---
title: "Visual Studio 命令表 (。Vsct) 文件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT 文件概述"
  - "Visual Studio 命令表配置文件 (VSCT)、 概述"
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
---
# Visual Studio 命令表 (。Vsct) 文件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

命令表配置文件是文本文件，介绍的 VSPackage 包含的命令集。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 表 \(VSCT\) 编译器将基于 XML 的配置文件 \(.vsct 文件\) 编译为二进制命令表输出 \(.cto\) 文件的命令。 结果.cto 文件并通过使用命令表 \(CTC\) 编译器进行编译.ctc 配置文件创建的那些相同。 但是，基于 XML 的.vsct 文件有一些优点，例如 XML 编辑器和 XML IntelliSense。  
  
 若要了解有关语法和语义.vsct 文件的详细信息，请参阅 [设计 XML 命令表 \(。Vsct\) 文件](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
  
## 本节内容  
 [设计 XML 命令表 \(。Vsct\) 文件](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
 介绍如何设计.vsct 文件。  
  
 [如何: 创建。Vsct 文件](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)  
 将创建.vsct 文件的方法进行比较。 介绍手动创建一个新的.vsct 文件的过程。  
  
## 相关章节  
 [VSCT XML 架构参考](../../extensibility/vsct-xml-schema-reference.md)  
 提供有关每个部分的命令表 XML 配置文件的详细信息。  
  
 [Command Table Configuration \(.Ctc\) Files](http://msdn.microsoft.com/zh-cn/3413dda1-f372-4669-bcf0-c64d3463842c)  
 不推荐使用的.ctc 文件格式概述提供。  
  
 [Vspackage 如何添加用户界面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 描述命令表格式规范。  
  
 [在 Vspackage 中的资源](../../extensibility/internals/resources-in-vspackages.md)  
 描述如何在托管的 VSPackages 中使用托管和非托管资源。  
  
 [命令、 菜单和工具栏](../../extensibility/internals/commands-menus-and-toolbars.md)  
 说明如何创建一个用户界面，包括菜单、 工具栏和命令组合框。