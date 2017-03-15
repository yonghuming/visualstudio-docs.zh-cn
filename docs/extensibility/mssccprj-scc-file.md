---
title: "MSSCCPRJ。源代码管理文件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "源代码管理插件、 MSSCCPRJ。源代码管理文件"
  - "MSSCCPRJ。源代码管理文件"
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# MSSCCPRJ。源代码管理文件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

当 Visual Studio 解决方案或项目放在 IDE 中使用的源代码管理下时，IDE 会从源代码管理插件中字符串的形式接收两个关键信息。 这些字符串，"AuxPath"和"ProjName"是不透明的 IDE 中，但不用于该插件在版本控制中找到的解决方案或项目。 IDE 一般能获得这些字符串第一次通过调用 [SccGetProjPath](../extensibility/sccgetprojpath-function.md), ，它然后将它们保存在解决方案或项目文件中为未来调用 [SccOpenProject](../extensibility/sccopenproject-function.md)。 当嵌入到解决方案和项目文件中，"AuxPath"和"ProjName"字符串会不自动更新用户分支，分叉，或将复制位于版本控制中的解决方案和项目文件时。 若要确保解决方案和项目文件指向其在版本控制的正确位置，用户必须手动更新这些字符串。 因为这些字符串应该是不透明，它可能始终不清除更新方式。  
  
 源代码管理插件可以通过调用 MSSCCPRJ 的特殊文件中存储的"AuxPath"和"ProjName"字符串来避免此问题。源代码管理文件。 它是一个本地客户端的文件拥有和维护该插件。 此文件永远不会置于源代码管理下，但生成的每个包含受源代码管理文件的目录的插件。 若要确定哪些文件是 Visual Studio 解决方案和项目文件，源代码管理插件可以比较根据标准或用户提供的列表的文件扩展名。 一旦 IDE 检测到插件支持 MSSCCPRJ。源代码管理文件，它将停止要嵌入"AuxPath"并且"ProjName"将字符串读入解决方案和项目文件从 MSSCCPRJ 读取这些字符串。SCC 改为文件。  
  
 源代码管理插件支持 MSSCCPRJ。源代码管理文件必须遵循以下准则:  
  
-   只能有一个 MSSCCPRJ。每个目录的源代码管理文件。  
  
-   MSSCCPRJ。源代码管理文件中，对于给定目录中的源代码管理下的多个文件都可以包含"AuxPath"和"ProjName"。  
  
-   "AuxPath"字符串不能在其内部引号。 它允许包含用括号括起来它作为分隔符 \(例如，一对双引号来分隔可以用于指示一个空字符串\)。 从 MSSCCPRJ 中读取时，IDE 会去除所有的报价单"AuxPath"字符串。源代码管理文件。  
  
-   MSSCCPRJ 中的"ProjName"字符串。源代码管理文件必须从返回的字符串完全匹配 `SccGetProjPath` 函数。 如果该函数返回的字符串具有引号，MSSCCPRJ 中的字符串。源代码管理文件必须具有引号括起来，反之亦然。  
  
-   MSSCCPRJ。源代码管理文件创建或更新时的文件将位于源代码管理下。  
  
-   如果检测到 MSSCCPRJ。源代码管理文件，将会删除，提供程序应重新生成下一次执行源代码管理操作，有关该目录。  
  
-   MSSCCPRJ。源代码管理文件必须严格遵循定义的格式。  
  
## 举例说明了 MSSCCPRJ。源代码管理文件格式  
 下面是 MSSCCPRJ 的示例。SCC 文件格式 \(仅作为指南，提供和不应在文件正文中包含的行号\):  
  
 \[第 1 行\] `SCC = This is a Source Code Control file`  
  
 \[第 2 行\]  
  
 \[第 3 行\] `[TestApp.sln]`  
  
 \[第 4 行\] `SCC_Aux_Path = "\\server\vss\"`  
  
 \[第 5 行\] `SCC_Project_Name = "$/TestApp"`  
  
 \[第 6 行\]  
  
 \[第 7 行\] `[TestApp.csproj]`  
  
 \[第 8 行\] `SCC_Aux_Path = "\\server\vss\"`  
  
 \[第 9 行\] `SCC_Project_Name = "$/TestApp"`  
  
 第一行指出文件的用途，并可作为此类型的所有文件的签名。 此行应显示在所有 MSSCCPRJ 一样。SCC 文件:  
  
 `SCC = This is a Source Code Control file`  
  
 下面是由方括号中的文件名称标记每个文件的设置的一部分。 该节被重复的每个文件进行跟踪。 该行是一个示例的文件名，即 `[TestApp.csproj]`。 IDE 需要以下两行。 但是，它不定义的样式定义的值。 这些变量就 `SCC_Aux_Path` 和 `SCC_Project_Name`。  
  
 `SCC_Aux_Path = "\\server\vss\"`  
  
 `SCC_Project_Name = "$/TestApp"`  
  
 到本节没有结束分隔符。 Scc.h 标头文件中定义的文件，以及在文件中，显示的所有文本的名称。 有关详细信息，请参阅[字符串用作键用于查找源代码管理插件](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)。  
  
## 请参阅  
 [源代码管理插件](../extensibility/source-control-plug-ins.md)   
 [字符串用作键用于查找源代码管理插件](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)