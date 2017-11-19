---
title: "MSSCCPRJ。SCC 文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b61478b482ed10aba61ea9ce412dc0fe0725b0bd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ。SCC 文件
Visual Studio 解决方案或项目置于受源代码管理使用 IDE 后，IDE 会从源代码管理插件中字符串的形式接收两个关键信息。 两个字符串，"AuxPath"和"ProjName"是不透明的 IDE 中，但它们用于由该插件在版本控制中找到解决方案或项目。 IDE 通常获取这些字符串首次通过调用[SccGetProjPath](../extensibility/sccgetprojpath-function.md)，它然后将它们保存在解决方案或项目文件中以便将来调用[SccOpenProject](../extensibility/sccopenproject-function.md)。 当嵌入的解决方案和项目文件中，"AuxPath"和"ProjName"字符串不会自动更新用户分支，分叉，或将复制解决方案和项目版本控制中的文件时。 若要确保解决方案和项目文件指向它们在版本控制中的正确位置，用户必须手动更新的字符串。 由于字符串要作为不透明，它可能不始终会清除它们的更新方式。  
  
 源代码管理插件可避免此问题，通过将"AuxPath"和"ProjName"字符串存储在名为 MSSCCPRJ 特殊文件。SCC 文件。 它是本地的客户端的文件拥有和维护由该插件。 此文件永远不会放置在源代码管理下，但生成的每个包含受源代码管理文件的目录的插件。 若要确定哪些文件是 Visual Studio 解决方案和项目文件，源代码管理插件可以比较根据标准的或用户提供的列表的文件扩展名。 一旦 IDE 检测到插件支持 MSSCCPRJ。SCC 文件，它将停止嵌入"AuxPath"和"ProjName"字符串到解决方案和项目文件，并且它从 MSSCCPRJ 读取这些字符串。SCC 文件相反。  
  
 源代码管理插件支持 MSSCCPRJ。SCC 文件必须遵循以下指导原则：  
  
-   只能有一个 MSSCCPRJ。每个目录的 SCC 文件。  
  
-   MSSCCPRJ。SCC 文件中，对于在给定目录中的源代码管理下的多个文件都可以包含的"AuxPath"和"ProjName"。  
  
-   "AuxPath"字符串不能有其内部的引号。 它允许包含用括号括起来它作为分隔符 （例如，一对双引号括起来可以用于指示一个空字符串）。 从 MSSCCPRJ 读取它时，IDE 将条带"AuxPath"字符串中的所有引号。SCC 文件。  
  
-   MSSCCPRJ 中的"ProjName"字符串。SCC 文件必须从返回的字符串完全匹配`SccGetProjPath`函数。 如果该函数返回的字符串具有在其 MSSCCPRJ 中的字符串周围的引号。SCC 文件必须具有引号括起来，反之亦然。  
  
-   MSSCCPRJ。SCC 文件创建或更新只要文件放置在源代码管理下。  
  
-   如果检测到 MSSCCPRJ。SCC 文件被删除，提供程序应重新生成其下一次执行有关该目录的源代码管理操作。  
  
-   MSSCCPRJ。SCC 文件必须严格遵循定义的格式。  
  
## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>举例说明了 MSSCCPRJ。SCC 文件格式  
 以下是 MSSCCPRJ 一个示例。SCC 文件格式 （仅提供作为指南，和不应在文件正文中包含的行号）：  
  
 [第 1 行]`SCC = This is a Source Code Control file`  
  
 [第 2 行]  
  
 [第 3 行]`[TestApp.sln]`  
  
 [第 4 行]`SCC_Aux_Path = "\\server\vss\"`  
  
 [第 5 行]`SCC_Project_Name = "$/TestApp"`  
  
 [第 6 行]  
  
 [第 7 行]`[TestApp.csproj]`  
  
 [第 8 行]`SCC_Aux_Path = "\\server\vss\"`  
  
 [第 9 行]`SCC_Project_Name = "$/TestApp"`  
  
 第一个行状态的文件的用途，并且用作此类型的所有文件的签名。 此行应显示在所有 MSSCCPRJ 完全一样。SCC 文件：  
  
 `SCC = This is a Source Code Control file`  
  
 下面是由方括号中的文件名称标记的每个文件的设置的节。 对跟踪每个文件重复此部分。 此行是一个示例文件名称，也就是说， `[TestApp.csproj]`。 IDE 需要以下两行。 但是，它未定义的样式定义的值。 这些变量就`SCC_Aux_Path`和`SCC_Project_Name`。  
  
 `SCC_Aux_Path = "\\server\vss\"`  
  
 `SCC_Project_Name = "$/TestApp"`  
  
 到此部分没有结束分隔符。 Scc.h 标头文件中定义的文件，以及在文件中，显示的所有文本的名称。 有关详细信息，请参阅[字符串用作密钥用于查找源代码管理插件](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)。  
  
## <a name="see-also"></a>另请参阅  
 [源控件插件](../extensibility/source-control-plug-ins.md)   
 [作为用于查找源代码管理插件的密钥的字符串](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)