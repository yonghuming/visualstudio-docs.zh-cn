---
title: "源控制插件词汇表 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 251e104336d19e9f88926e5ca75a85330039fbe8
ms.lasthandoff: 02/22/2017

---
# <a name="source-control-plug-in-glossary"></a>源控制插件术语表
以下有用的术语和定义适用于源控制插件 SDK 文档。  
  
## <a name="definitions"></a>定义  
 签入  
 当用户更改的工作副本时，用户必须将更改从发送到中央源控件存储库中的工作副本。 这将创建新的修订版本可供其他用户的文件。 此过程被称为一个签入。  
  
 签出  
 从存储库，通知您的意图对其进行修改的存储库中请求的工作副本的操作。 工作副本反映了截至目前已签出项目的状态。  
  
 客户端  
 使用源代码管理系统的程序。 在本文档中，它是 Visual Studio IDE。  
  
 注释  
 描述执行源代码管理操作时，用户可以附加到修订版的更改的消息。  
  
 冲突  
 两个用户试图更改签入到同一个文件的同一个区域时所出现的情况。 通常情况下，必须执行合并。  
  
 目录  
 客户端的本地文件夹被称为一个目录。 这是用户实际进行更改的副本。 可以有多个给定的项目; 的工作副本通常，每个开发人员具有他或她自己的副本。  
  
 Get  
 Get 操作带来了用户的工作副本保持最新的存储库副本。 与不同的是签出，用户只需要最新的副本，但想要不进行任何更改时执行 get。  
  
 历史记录  
 它通常是所有签出、 签入、 更新、 标记和发行版在源代码控制存储库中完成的摘要。  
  
 IDE  
 通常是指 Visual Studio 集成开发环境。 但是，它还可以指于识别源控制插件 API 其他客户端环境。  
  
 合并  
 过程期间的两个或多个源的代码文件组合以形成新的文件，其中包含从以前的文件的所有功能。 其中两个或多个开发人员在文件上同时处理，这一概念非常重要版本控制中。  
  
 Project  
 源代码管理文件夹通常称为项目。 这在 Visual Studio 中没有与项目或解决方案的任何关系。  
  
 插件  
 一个 DLL，它通过实现源控制插件 API 提供的源代码管理功能。  
  
 存储库  
 其中一个源控制系统的主副本将存储项目的完整的修订版本历史记录。 每个项目具有恰好一个存储库。  
  
 Revision  
 文件历史记录或一组文件中已提交的更改。 修订版本是一个不断变化的项目中的快照。  
  
## <a name="see-also"></a>另请参阅  
 [源代码管理插件](../extensibility/source-control-plug-ins.md)
