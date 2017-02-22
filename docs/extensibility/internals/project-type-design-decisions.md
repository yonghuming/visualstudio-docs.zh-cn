---
title: "项目类型的设计决策 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "项目类型中，项目文件持久性"
  - "项目类型中，承诺机制"
  - "项目类型中项"
  - "项目类型中，设计决策"
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# 项目类型的设计决策
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在创建新的项目类型之前，您必须作出有关项目类型的若干设计决策。  您必须决定哪种类型的项目项将包含，项目文件如何将保留，，以及提交模型将使用。  
  
## 项目项  
 该项是否将使用文件或抽象对象?  如果您使用文件，它们是否引用基于或基于目录的文件?  文件或抽象对象是本地或远程?  
  
 项目中的项可以是文件，也可以是抽象对象 \(如数据库储存库的对象或在 Internet 上的数据连接。  如果项目是文件，该项目可以是基于引用的或基于目录的项目。  
  
 在基于引用的项目时，项目可显示在多个项目。  但是，项表示的物理文件仅位于一个目录。  在基于目录的项目，所有项目项存在于目录结构。  有关更多信息，请参见[NIB:Item Management in Projects](http://msdn.microsoft.com/zh-cn/762e606b-7f44-4b66-97a1-e30a703654a0)。  
  
 本地项目在安装应用程序的同一台计算机上存储。  远程项目可以存储在单独的服务器在本地网络或在其他地方在 Internet。  
  
## 项目文件持久性  
 数据是否将存储在常见的平面文件系统，或者在结构化存储?  通过使用标准编辑或一个项目特定版本，文件是否将打开?  
  
 ，当用户必须查看或更改信息时，为了保留它们的数据，大多数应用程序保存其文件中的数据，然后读取该 cookie。  
  
 结构化存储，当若干组件对象模型 \(com\) 对象在一个文件时，需要存储其 \(COM\)保留的数据，也称为复合文件，通常使用。  结构化存储，几种不同的软件组件可共享一个磁盘文件。  
  
 有考虑若干的选项看待项目的持久性在项目。  您可以执行以下任一选项:  
  
-   ，当更改时，可以单独保存每个文件它。  
  
-   获取在单个 **保存** 操作的许多事务。  
  
-   ，当项目表示与远程对象时，的数据连接保存文件，本地发布到服务器或然后使用另一种方法来保存的项目项。  
  
 有关持久性的更多信息，请参见 [项目持久性](../../extensibility/internals/project-persistence.md) 和 [打开和保存项目项](../../extensibility/internals/opening-and-saving-project-items.md)。  
  
## 项目承诺模型  
 保存数据对象是否将打开在直接方式或事务模式下?  
  
 当数据对象直接在模式中打开，对数据所做的更改会立即合并或，当用户手动保存文件。  
  
 使用事务模式时，数据对象中打开，更改保存到一个临时位置在内存中并不会提交，直到用户手动选择保存文件。  此时，任何更改必须一起发生或更改不会对。  
  
## 请参阅  
 [清单︰ 创建新的项目类型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [NIB:Item Management in Projects](http://msdn.microsoft.com/zh-cn/762e606b-7f44-4b66-97a1-e30a703654a0)   
 [打开和保存项目项](../../extensibility/internals/opening-and-saving-project-items.md)   
 [项目持久性](../../extensibility/internals/project-persistence.md)   
 [项目模型的元素](../../extensibility/internals/elements-of-a-project-model.md)   
 [项目模型核心组件](../../extensibility/internals/project-model-core-components.md)   
 [创建项目类型](../../extensibility/internals/creating-project-types.md)