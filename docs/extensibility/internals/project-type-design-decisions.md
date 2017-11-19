---
title: "项目类型的设计决策 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a3e0216161669e12c245484da3ca6e4de63c6a48
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="project-type-design-decisions"></a>项目类型的设计决策
在创建新的项目类型之前，你必须进行一些设计决策，有关你的项目类型。 你必须决定要将哪些类型的项将包含你的项目、 如何将保持项目文件，以及哪些承诺模型。  
  
## <a name="project-items"></a>项目项  
 将你的项目使用文件或抽象对象？ 如果使用的文件，它们将是基于引用的或基于目录的文件？ 是否要为本地或远程的文件或接下来的抽象对象？  
  
 项目中的项可以是文件，或它们可以是 Internet 更抽象的对象，如数据库存储库或数据连接中的对象。 如果该项为文件，项目可以是基于引用的或基于目录的项目。  
  
 在基于引用的项目中，项可以出现在多个项目。 但是，一项表示的实际文件位于仅限一个目录中。 在基于目录的项目中，所有项目项的目录结构中都存在。 有关详细信息，请参阅[NIB： 项管理项目中](http://msdn.microsoft.com/en-us/762e606b-7f44-4b66-97a1-e30a703654a0)。  
  
 本地项存储在其中安装应用程序的相同计算机上。 在本地网络中，单独服务器上或 Internet 上的其他地方，可以存储远程项。  
  
## <a name="project-file-persistence"></a>项目文件持久性  
 将数据存储在常见的平面文件系统，或在结构化存储？ 将通过使用标准编辑器中或特定于项目的编辑器中打开文件？  
  
 若要保存其数据，大多数应用程序将其数据保存在文件中，，然后读取它时用户必须查看或更改的信息。  
  
 多个组件对象模型 (COM) 对象需要将其持久化的数据存储在单个文件时，通常使用结构化的存储，也称为复合文件。 使用结构化存储若干不同软件组件可以共享单个磁盘文件。  
  
 你有若干选项需要注意的有关你的项目中的项的持久性。 你可以执行以下选项之一：  
  
-   已更改时，请单独保存每个文件。  
  
-   捕获在一次的很多事务**保存**操作。  
  
-   保存文件进行本地，然后发布到服务器或使用另一种方法保存项目项，该项表示与远程对象的数据连接时。  
  
 有关持久性的详细信息，请参阅[项目持久性](../../extensibility/internals/project-persistence.md)和[打开和保存项目项](../../extensibility/internals/opening-and-saving-project-items.md)。  
  
## <a name="project-commitment-model"></a>项目承诺模型  
 将打开持久化的数据对象中直接模式或事务处理的模式？  
  
 当在直接模式下打开数据对象时，对数据所做的更改会合并立即或用户手动保存该文件时。  
  
 当通过使用事务处理的模式中打开数据对象时，更改保存到内存中的临时位置，并在用户手动选择保存文件之前不提交。 在那时，必须一起出现的所有更改，或将进行任何更改。  
  
## <a name="see-also"></a>另请参阅  
 [清单： 创建新项目类型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [NIB： 项管理项目中](http://msdn.microsoft.com/en-us/762e606b-7f44-4b66-97a1-e30a703654a0)   
 [打开和保存项目项](../../extensibility/internals/opening-and-saving-project-items.md)   
 [项目持久性](../../extensibility/internals/project-persistence.md)   
 [项目模型的元素](../../extensibility/internals/elements-of-a-project-model.md)   
 [项目模型核心组件](../../extensibility/internals/project-model-core-components.md)   
 [创建项目类型](../../extensibility/internals/creating-project-types.md)