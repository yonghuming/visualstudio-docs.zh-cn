---
title: "Visual Studio 命令表 (。Vsct) 文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ace754b9d6ddb220b3647b281011d3763810987c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="visual-studio-command-table-vsct-files"></a>Visual Studio 命令表 (。Vsct) 文件
命令表配置文件是介绍 VSPackage 包含的命令集的文本文件。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]命令表 (VSCT) 编译器将基于 XML 的配置文件 （.vsct 文件） 编译为二进制命令表输出 (.cto) 文件。 生成.cto 文件是通过使用命令表 (CTC) 编译器编译.ctc 配置文件创建的那些相同。 但是，基于 XML 的.vsct 文件具有一些优点，包括 XML 编辑器和 XML IntelliSense 等。  
  
 若要了解有关语法和语义的.vsct 文件的详细信息，请参阅[设计 XML 命令表 (。Vsct) 文件](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
  
## <a name="in-this-section"></a>本节内容  
 [设计 XML 命令表格 (.Vsct) 文件](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
 描述如何设计.vsct 文件。  
  
 [如何：创建 .Vsct 文件](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)  
 比较用于创建.vsct 文件的方法。 介绍手动创建一个新的.vsct 文件的过程。  
  
## <a name="related-sections"></a>相关章节  
 [VSCT XML 架构参考](../../extensibility/vsct-xml-schema-reference.md)  
 提供有关每个部分的命令表 XML 配置文件的详细信息。  
  
 [命令表配置 (。Ctc) 文件](http://msdn.microsoft.com/en-us/3413dda1-f372-4669-bcf0-c64d3463842c)  
 不推荐使用的.ctc 文件格式概述提供。  
  
 [VSPackage 如何添加用户界面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 描述命令表格式规范。  
  
 [Vspackage 中的资源](../../extensibility/internals/resources-in-vspackages.md)  
 描述如何在托管的 Vspackage 中使用托管和非托管资源。  
  
 [命令、菜单和工具栏](../../extensibility/internals/commands-menus-and-toolbars.md)  
 说明如何创建包含菜单、工具栏和命令组合框的 UI。