---
title: "“编辑并继续”错误和警告 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ENC2001"
  - "ENC1006"
  - "ENC2008"
  - "ENC1009"
  - "ENC1002"
  - "ENC2002"
  - "ENC1011"
  - "ENC1003"
  - "ENC1004"
  - "ENC1008"
  - "ENC1013"
  - "ENC2005"
  - "ENC1010"
  - "ENC2004"
  - "ENC1007"
  - "ENC1005"
  - "ENC2006"
  - "ENC1001"
  - "ENC2007"
  - "ENC2003"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "编辑并继续 [C++], 错误和警告"
  - "错误 [C++], 编辑并继续"
  - "错误 [调试器], 编辑并继续"
ms.assetid: b5c5e25c-7ca4-4ca9-b91e-e8882de44dae
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "susanno"
manager: "douge"
---
# “编辑并继续”错误和警告 (C++)
利用 [!INCLUDE[cpp_current_short](../misc/includes/cpp_current_short_md.md)] 的“编辑并继续”，您可以在中断模式下停止程序执行，对执行代码进行更改，然后继续执行包含新纳入更改的程序。  
  
 通常情况下，影响类的公共结构的声明性代码编辑是禁止的，但对类内部的方法、属性体或私有声明进行某些编辑是允许的。  “编辑并继续”会尽可能将不可编辑的代码标记为浅灰色并显示错误消息。  有关 [!INCLUDE[cpp_current_short](../misc/includes/cpp_current_short_md.md)] 的“编辑并继续”中不支持的编辑的详细信息，请参阅[编辑并继续 \(Visual C\+\+\)](../debugger/edit-and-continue-visual-cpp.md)。  
  
 可以通过以下方式之一解决“编辑并继续”错误和警告：  
  
|解决方法|错误和警告消息编号|  
|----------|---------------|  
|停止调试，重新应用您的更改，然后继续调试。|1001、1002、1003、1004、1005、1006、1007、1008、1010、1013、2003、2005 有关此类别中的错误和警告消息的列表，请参阅[重新启动调试消息](../misc/edit-and-continue-errors-and-warnings-cpp.md#BKMK_RestartDebuggingMessages)。|  
|在**“编辑”** 菜单上，选择**“撤消”**，然后使用未更改的代码继续调试。<br /><br /> \- 或 \-<br /><br /> 停止调试，重新应用您的更改，然后继续调试。|1009、1011 有关此类别中的错误和警告消息的列表，请参阅[撤消或停止消息](../misc/edit-and-continue-errors-and-warnings-cpp.md#BKMK_UndoOrStopMessages)。|  
|继续调试。  当首次命中代码时，您的更改将会忽略，但在后续调用中会应用。|2001, 2002, 2004.  有关此类别中的错误和警告消息的列表，请参阅[在下一次调用时应用消息](../misc/edit-and-continue-errors-and-warnings-cpp.md#BKMK_ApplyAtNextCallMessages)。|  
|执行一些其他操作，如使用最新版本的 [!INCLUDE[cpp_current_short](../misc/includes/cpp_current_short_md.md)] 重置断点或重新生成模块。|2007, 2008.  有关此类别中的错误和警告消息的列表，请参阅[需要其他操作消息](../misc/edit-and-continue-errors-and-warnings-cpp.md#BKMK_OtherActionRequiredMessages)|  
  
##  <a name="BKMK_RestartDebuggingMessages"></a> 重新启动调试消息  
 必须通过以下方式来解析以下错误消息：停止当前正在调试的会话，重新应用执行过的编辑，然后重新启动调试会话。  
  
|||  
|-|-|  
|1001|无法更新符号的形式转换\(thunk\): *symbol* \(位置: *location*，形式转换: *address*\)|  
|1002|数据符号已经更改: symbol \(*symbol*\)|  
|1003|无法为新的函数映射形式转换\(thunk\): *function*|  
|1004|无法打开 PDB 进行类型封装: *pdb* \(pdb\)|  
|1005|重命名、移除或修改了符号: *symbol*|  
|1006|添加、重命名、移除了一个全局或静态变量，或者更改了数据类型或进行了初始化: *symbol*\(由 *module* 引用\)|  
|1007|未定义符号: *symbol* \(由 *module* 引用\)|  
|1008|无法执行在编辑过程中所加载的对象所需要的运行时初始化: *module*|  
|1010|已添加静态或全局变量: *variable referenced in file*|  
|1013|调试器在应用代码更改时内存不足|  
|2003|代码位置更改可能引起异常处理或变量析构错误: *function*|  
|2005|新的源分配给代码。  调试器的行号信息可能会受到影响: function \(*function*\)|  
  
##  <a name="BKMK_UndoOrStopMessages"></a> 撤消或停止消息  
 可通过以下方式来解析以下错误消息：停止当前正在调试的会话，重新应用执行过的编辑，然后重新启动调试会话。  
  
-   在“编辑”菜单上，单击“撤消”。  您可以继续调试，但不会应用您的编辑。  
  
     \- 或 \-  
  
-   停止调试，重新应用更改，然后重新启动调试。  
  
|||  
|-|-|  
|1009|已删除静态或全局变量: *variable referenced in file*|  
|1011|已更改静态或全局变量: *variable referenced in file*|  
  
##  <a name="BKMK_ApplyAtNextCallMessages"></a> 在下一次调用时应用消息  
 在显示以下警告消息之一时，您可以继续调试会话。  编辑后首次调用代码时，您的编辑不会应用；这些编辑将在对代码的所有后续调用中应用。  
  
|||  
|-|-|  
|2001|无法找到局部变量或更改的变量数据类型: symbol \(*symbol*\)|  
|2002|已删除的变量或新的局部变量需要构造或析构: symbol \(*symbol*\)|  
|2004|无法对使用已经定义了一次以上的名称的局部变量进行添加或删除处理: symbol \(*symbol*\)|  
  
##  <a name="BKMK_OtherActionRequiredMessages"></a> 需要其他操作消息  
 解析这些消息所需的操作在消息文本中有述。  
  
|||  
|-|-|  
|2007|未能移动某些在反汇编窗口中设置的断点。<br /><br /> 若要解决此问题，请重置受影响的断点。|  
|2008|未能在模块 *module* 中为文件 *file* 加载调试符号。<br /><br /> 若要解决此问题，请使用最新版本的 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 重新生成指定的模块。|  
  
## 请参阅  
 [编辑并继续 \(Visual C\+\+\)](../debugger/edit-and-continue-visual-cpp.md)   
 [编辑并继续](../debugger/edit-and-continue.md)