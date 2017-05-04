---
title: "Windows 脚本接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c750627-6797-4857-9f5e-e5f54371f83c
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Windows 脚本接口
Microsoft Windows 脚本接口为应用程序添加脚本和 OLE 自动化提供一种方法。  依赖于 windows 脚本的脚本宿主可以使用多个源和供应商的脚本引擎管理脚本组件之间。  脚本自身语言，语法，持久性格式，执行模型的实现，等等\) 留给脚本供应商联系。  
  
 windows 脚本文档分为以下几节：  
  
 [Windows 脚本主机](../winscript/windows-script-hosts.md)  
  
 [Windows 脚本引擎](../winscript/windows-script-engines.md)  
  
 [活动脚本调试概述](../winscript/active-script-debugging-overview.md)  
  
 [活动脚本分析概述](../winscript/active-script-profiling-overview.md)  
  
 [Windows 脚本接口参考](../winscript/reference/windows-script-interfaces-reference.md)  
  
## windows 脚本背景  
 windows 脚本界面分为两类：windows 脚本宿主和 windows 脚本引擎。  宿主在引擎创建一个脚本引擎并调用运行脚本。  windows 脚本宿主的示例包括：  
  
-   Microsoft Internet Explorer  
  
-   创作工具的 Internet  
  
-   shell  
  
 windows 脚本引擎可以为所有语言或运行时环境中开发，包括：  
  
-   Microsoft Visual Basic Scripting Edition \(vbscript\)  
  
-   Perl  
  
-   口齿  
  
 若要使实现宿主相同灵活尽可能，提供 windows 脚本的一个 OLE 自动化包装。  但是，使用该包装对象实例化脚本引擎的宿主没有程度访问运行时命名空间，持久性设计的控件，等等，它会，则使用窗口直接脚本。  
  
 windows 脚本界面元素在一个创作环境中只需要的设计隔离，以便 nonauthoring 的宿主 \(例如浏览器和浏览器\)，并且脚本引擎 \(例如，VBScript\) 中保持更轻巧。  
  
## windows 脚本基本结构  
 下图演示 windows 脚本宿主之间的交互和 windows 脚本引擎。  
  
 在宿主和引擎之间的交互所涉及的步骤在以下给定列表。  
  
1.  创建一个项目。  宿主加载项目或文档。  \(此步骤不是特定的到窗口的完整性脚本，但是，包括在此处。\)  
  
2.  创建 windows 脚本引擎。  宿主调用 `CoCreateInstance` 创建一个新的 windows 脚本引擎，指定选件类标识符 \(以捕获特定脚本引擎使用。  例如，Internet Explorer HTML 浏览器将 HTML \<OBJECT\> 标记的 CLSID\= 属性接收脚本引擎的选件类标识符。  
  
3.  加载该脚本。  如果脚本内容保存，宿主调用脚本引擎的 `IPersist*::Load` 方法提供该脚本存储、流或属性包。  否则，宿主使用 `IPersist*::InitNew` 或 [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) 方法创建一个空脚本。  维护一个脚本的宿主，当文本可以使用 [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) 提供脚本引擎该脚本的文本，在调用 `IActiveScriptParse::InitNew`之后。  
  
4.  添加名为的项目。  对于每个顶级命名项 \(如页和窗体\) 导入脚本引擎的命名空间，宿主在引擎的命名空间调用 [IActiveScript::AddNamedItem](../winscript/reference/iactivescript-addnameditem.md) 方法创建项。  此步骤不是必需的顶级命名项是否已为该脚本的持久状态部分以加载的第 3. 步。  宿主不使用 `IActiveScript::AddNamedItem` 添加分段命名项 \(如 HTML 页的控件\);相反，使用宿主的 `ITypeInfo` 和 `IDispatch` 接口，引擎间接从顶级项的分段项目。  
  
5.  运行该脚本。  宿主会使引擎启动运行该脚本通过将 [IActiveScript::SetScriptState](../winscript/reference/iactivescript-setscriptstate.md) 方法的 SCRIPTSTATE\_CONNECTED 标志。  这在方法调用可以将执行所有脚本引擎生成工作，包括静态绑定，在事件 \(下文\) 并执行代码，与一个为其编写脚本的 `main()` 功能。  
  
6.  获取项信息。  每次脚本引擎需要将符号与一个顶级项，它调用 [IActiveScriptSite::GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md) 方法，它返回有关该特定项的信息。  
  
7.  挂钩事件。  在启动实际脚本之前，脚本引擎连接到任何相关对象事件通过 `IConnectionPoint` 接口。  
  
8.  调用属性和方法。  当脚本运行，脚本引擎会注意到对方法和属性在名为对象。`IDispatch::Invoke` 或其他标准 OLE 绑定机制。  
  
## windows 脚本术语  
 此列表包含用于此的脚本相关的术语的定义文档。  
  
|术语|定义|  
|--------|--------|  
|代码对象|与一个名为项，例如在窗体后的模块在 Visual Basic 或 c. c\+\+ 选件类与命名项目的脚本引擎创建的实例。  更好地，这是一个支持 OLE 自动化，因此宿主或其他非脚本实体可以操作代码对象的 OLE 组件对象模型 \(COM\) 对象。|  
|命名的项目|一 OLE COM 对象 \(支持 OLE 自动化\) 主机被视为有趣到该脚本的最好是一。  示例在浏览器中包括 HTML 页和浏览器和文档和对话框 Microsoft Word。|  
|字符集|组成程序的脚本引擎在的数据。  脚本可以是任何连续可执行数据，包括文本部分，块 `pcode`，甚至相关单个计算机的可执行字节代码。  宿主加载一个脚本。脚本引擎将一 `IPersist*` 接口或者通过 [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) 接口。|  
|脚本引擎|处理脚本的 OLE 对象。  一个脚本引擎实现 [IActiveScript](../winscript/reference/iactivescript.md)，因此，选择，[IActiveScriptParse](../winscript/reference/iactivescriptparse.md) 接口。|  
|脚本宿主|拥有 windows 脚本引擎的应用程序或程序。  宿主实现 [IActiveScriptSite](../winscript/reference/iactivescriptsite.md)，因此，选择，[IActiveScriptSiteWindow](../winscript/reference/iactivescriptsitewindow.md) 接口。|  
|Scriptlet|获取脚本的部分附加到对象。[IActiveScriptParse](../winscript/reference/iactivescriptparse.md) 接口。  scriptlets 的复合集合为该脚本。|  
|脚本语言|脚本编写的语言 \(例如 VBScript，\) 和该语言语义。|  
  
## 请参阅  
 [Windows Script Interfaces](../winscript/windows-script-interfaces.md)