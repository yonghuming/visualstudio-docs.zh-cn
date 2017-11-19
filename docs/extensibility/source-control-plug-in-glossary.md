---
title: "源控件插件术语表 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dc45c47f47fe18bc857715acc3948561f06e718c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="source-control-plug-in-glossary"></a>源控件插件术语表
以下有用的术语和定义适用于源控件插件 SDK 文档。  
  
## <a name="definitions"></a>定义  
 签入  
 当用户更改工作副本时，用户必须将更改发送从工作到中央的源控件存储库中的副本。 这将创建可供其他用户的文件的新修订版本。 此过程称为签入。  
  
 签出  
 从存储库，通知你想要对其进行修改的存储库中请求的工作副本的行为。 工作副本反映自刻起已签出项目的状态。  
  
 客户端  
 使用源代码管理系统的程序。 在本文档中，它是 Visual Studio IDE。  
  
 注释  
 描述执行源代码管理操作时的用户可以将附加到的修订版本的更改的消息。  
  
 冲突  
 两个用户尝试签入到相同的文件的相同区域的更改时的情况。 通常情况下，必须执行合并。  
  
 目录  
 客户端的本地文件夹称为目录。 这是在其中的用户实际进行更改的副本。 可以有一个给定的项目; 的多个工作副本通常，每个开发人员有他或她自己的副本。  
  
 获取  
 Get 操作使用户的工作副本保持最新的存储库副本。 与不同结账时，用户只需要最新副本，但想要不进行任何更改时执行 get。  
  
 历史记录  
 它通常是所有签出、 签入、 更新、 标记和版本在源控件存储库中完成的摘要。  
  
 IDE  
 通常是指 Visual Studio 集成开发环境。 但是，还引用了其他识别源控制插件 API 的客户端环境。  
  
 合并  
 在两个或多个源过程代码文件合并以形成新的文件，其中包含从以前的文件的所有功能的过程。 这一概念是在版本控制中至关重要的其中两个或多个开发人员在文件上同时处理。  
  
 Project  
 源代码管理文件夹通常称为项目。 这在 Visual Studio 中没有与项目或解决方案的任何关系。  
  
 插件  
 一个 DLL，它通过实现源控制插件 API 提供源控件功能。  
  
 存储库  
 其中的源控件系统的主副本将存储项目的完整的修订版本历史记录。 每个项目有一个存储库。  
  
 Revision  
 文件历史记录或文件组已提交的更改。 修订都是一个持续不断变化的项目中的快照。  
  
## <a name="see-also"></a>另请参阅  
 [源代码管理插件](../extensibility/source-control-plug-ins.md)