---
title: "Visual Studio SDK 术语表 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d9bf6b39d74e88289d9521216f98aa3195e30d6d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="visual-studio-sdk-glossary"></a>Visual Studio SDK 术语表
此术语表提供有关在中使用的术语定义[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]文档。  
  
## <a name="terms"></a>术语  
 Add-in — 外接程序  
 实用工具应用程序、 驱动程序或添加到主应用程序的其他软件。 在 Visual Studio 集成的开发环境 (IDE) 中外, 接程序是基于自动化的应用程序扩展 IDE 的功能。  
  
 自动化模型  
 自动化模型，在以前版本的 Visual Studio 扩展性模型中，是一个编程接口，使你的基础例程 IDE 该驱动器访问。 外接程序、 向导和宏使用控件的自动化模型中的对象或扩展 IDE 功能。  
  
 命令 UI 上下文  
 关联的 GUID，UI 命令或元素如工具栏的可见性。 命令 UI 上下文是与所选内容上下文不同，因为它未附加到窗口。  
  
 命令 UI 上下文可用于：  
  
-   将 GUID 分配给特定窗口被激活时显示的工具栏。  
  
-   将 GUID 分配给命令的可用性，而无需加载或运行 VSPackage。  
  
-   将分配一个 GUID 以影响活动的键绑定。  
  
-   将分配一个 GUID 以开启宏录制。  
  
-   分配的 GUID 以激活调试模式，或若要设计和在编辑器中的运行的模式之间切换。  
  
 组件  
 一种软件，可以不具有任何预先存在信息。 有关软件的实现该应用程序建立应用程序的功能的一部分。 组件和应用程序之间的通信是仅通过 OLE 样式接口。  
  
 组件管理器  
 服务， `SOleComponentManager`，其提供为顶级组件的非用户界面协调服务。 `SOleComponentManager`服务实现`IOleComponentManager`接口。  
  
 组件 UI 管理器  
 服务， `SOleComponentUIManager`，这可提供用户界面协调服务。 `SOleComponentUIManager`服务实现`IOleComponentUIManager`和`IOleInPlaceComponentUIManager`接口。  
  
 上下文包  
 `IVsUserContext`对象 （COM 对象） 附加到环境组件。 此对象包含查找关键字、 F1 关键字，以及与组件相关的属性。 上下文包此外指向链接到其任何子上下文包。  
  
 上下文提供程序  
 IDE 具有与之关联的上下文包中的组件。 此类组件包括工具窗口、 编辑器或项目层次结构。  
  
 设计器  
 一个编程接口，允许用户操作 UI （窗体、 按钮和其他控件） 的元素。  
  
 DocData  
 COM 对象封装基础数据世界中的文档的文档/视图分离的情况 （例如，在文本编辑器的情况下，它是基础所有文本编辑器视图的文本缓冲区）。 如果 EditorFactory 未提供此对象，IDE 将制造一个代表它。 此对象的职责是管理数据暂留和多个共享的语义通过查看只包含此相同`DocData`。 如果`DocData`对象支持`IOleCommandTarget`接口，它将包含在 UIShell 命令路由。  
  
 DocObject  
 用于承载在宿主所提供的范围内的用户界面的技术。 更具体地说，此术语是指支持任何嵌入`IOleDocument`和相关的接口。 此技术都有许多潜在应用程序，如实现的 COM 文档的详细信息、 在 Visual Basic 5.0 中的工具窗口、 ActiveX 设计器在 Visual Basic 6.0 中，依次类推。  
  
 文档  
 用于引用常规于整个文档-同时`DocData`和`DocView`。 例如，DocumentFrame 包含`DocView`，但它还会保留对引用`DocData`来处理持久性。  
  
 DocView  
 在用户查看和操作基础交互 DocObject/Embedding/窗格`DocData`。 请注意，用户不需要利用是的一部分的文档/视图分离`DocObject`接口设计。 用户使用整个 DocObject 充当而不是使用名为的基础数据的更抽象 （和较低正式） 的概念视图`DocData`。 `DocView`与在 IDE 的文档框架对象 （MDI 子窗口） 始终嵌入对象。  
  
 DTE  
 `DTE` （开发工具扩展性） 对象是在 Visual Studio 自动化模型中，允许你以编程方式自动化和扩展 IDE 的最顶层的访问点。  
  
 “动态帮助”窗口   
 工具窗口由 IDE，并显示查找关键字或 F1 帮助主题的列表。  
  
 编辑器  
 实现的代码 （类，CLSID） `DocView`。 它还实现`DocData`如果支持的视图/数据分离。  
  
 扩展  
 一种修改、 自定义，或将添加到 IDE 功能。 在创建使用自动化模型或 Vspackage 的扩展。  
  
 外部编辑器  
 一个编辑器，并不特定于 IDE 中，Microsoft Word 等。 它已注册通过其自己的机制，并可以在 IDE 外部使用。 如果可以嵌入此编辑器，它会在 IDE 中的窗口中显示。 如果它不能嵌入，将创建一个单独的顶级窗口。  
  
 层次结构  
 树的节点，每个节点与一组属性关联。  
  
 独立的顶级组件  
 一个组件，使用一个无模式的顶级窗口和作为独立应用程序窗口中，可以有效地运行，但作为中进程的对象实现。 因此，独立的顶级组件必须协调模式和使用 IDE 的消息循环服务。 进程内的对象不具有其自己的消息循环。  
  
 信息提供程序  
 信息提供程序是一个模块，可以查找关键字并返回主题中的一个列表中的窗体`IVsUserContextItem`对象。 若要提供 F1 和查找关键字项信息提供程序，注册已编译的帮助文件 (。HxS) 与系统。 这些文件中的帮助主题用于提供的主题显示在动态帮助窗口中，显示用户是否按下 f1 键列表。  
  
 就地组件  
 实现的 VSPackage 对象`IOleInPlaceComponent`界面来管理直观地包含在拥有 IDE 的文档窗口的窗口。 就地组件不参与标准 OLE 菜单合并;而是它们将其用户界面元素集成到 IDE。  
  
 有两种就地组件类型： 硬编码的就地组件和组件控件。  
  
 硬编码的就地组件具有菜单、 工具栏和紧密集成到 IDE 中，显示为如果它们已直接内置到 IDE 的用户界面的命令。  
  
 组件控件不具有任何集成到 IDE; 其自身用户界面元素相反，它们使用 IDE 的菜单、 命令和工具栏。 例如，无法使用以粗体显示的命令为加粗内多信息文本控件在窗体中嵌入的所选的字。 但是，组件控件可以请求，会显示动态已安装的特定于组件的 UI 元素。  
  
 语言服务  
 一组对象，允许 VSPackage 开发人员实现的计算机的语言代码编辑器，如文本标记和着色功能。  
  
 杂项文件项目  
 用于存储不在任何项目的打开文件的项目。 此项目中的项列表不会保存。  
  
 项目  
 项目由组成的层次结构对象或 COM 对象实现`IVsHierarchy`接口。  
  
 特定于项目的设计器或编辑器  
 独立于项目类型不能使用设计器。 在注册表中，所有特定于项目的设计器必须都输入他们编辑器工厂的信息。 IDE 然后可以实例化设计器每次在特定项目中打开特定文件类型。  
  
 项目类型窗口  
 一个不断从全局选择上下文跟踪的当前处于活动状态的项目层次结构和项的窗口。 项目类型 windows 使用`SVsTrackSelectionEx`服务警报更改 IDE，并向用户显示反馈。 解决方案资源管理器是一种项目类型窗口。  
  
 “属性”窗口  
 以前属性浏览器。  
  
 基于引用的项目  
 不需要相同的目录中的项目文件的项目。 相反，对文件从其他不相关的目录的引用进行存储和维护由项目本身。  
  
 正在运行的文档表  
 依据 IDE 维护的所有当前打开的文档列表的内部结构。 此列表包括所有打开的文档，而不考虑是否当前正在编辑文档的内存中。 文档是包括在一个编辑器，项目中的文件或主项目文件 （例如，*.vcproj 文件） 中打开的存储的过程的保存任何项。  
  
 选择上下文  
 是在 IDE 中的每个窗口的详细信息的一部分，用于跟踪活动选择的数据。 选择上下文组成：  
  
-   指向`IVsHierarchy`接口的项目层次结构  
  
-   项目项的项标识符。  
  
-   指向`ISelectionContainer`接口提供对属性的活动对象的访问权限。  
  
-   元素的值的数组。  
  
 服务  
 功能的协定，一组位于单个 COM 对象的 COM 接口。 当你创建一个服务，它由 GUID 标识，你将定义服务所执行 COM 接口的集。 COM 对象使用服务相互通信。  
  
 解决方案  
 组的用户的工作的相关项目。  
  
 标准的设计器  
 一个设计器，可以使用独立于项目类型。 在注册表中，所有标准的设计器必须输入他们编辑器工厂的信息。 IDE 然后可以实例化设计器每次打开具有特定扩展名的文件。 数据必须保存到文件。  
  
 标准编辑器  
 可以使用独立于任何特定项目类型的编辑器。 此类编辑器都有 EditorFactories 在注册表中注册。 这使 IDE 以找到和调用编辑器。  
  
 标准操作系统编辑器  
 嵌入不是 Visual Studio 特定。 使用已知的 Win32 键进行注册 （例如，Win32 资源管理器知道如何调用）。 如果可以嵌入此类编辑器，编辑器将仍显示在其在 IDE 中的位置。 否则，为此类编辑器创建一个单独的顶级窗口。  
  
 子上下文包  
 `IVsUserContext`对象链接到上下文包。 此对象包含查找关键字、 F1 关键字，以及选择的 IDE 组件中的属性。 子上下文的示例中的工具窗口中或在编辑器中的关键字包括命令。  
  
 任务列表  
 工具窗口，通过 IDE 实现，并显示活动任务的列表。  
  
 文本缓冲区  
 对象的公用名`VSTextBuffer`。  
  
 文本视图  
 对象的公用名`VSTextView`。  
  
 工具顶级组件  
 一个组件，作为无模式的弹出窗口中，与 IDE 的用户界面紧密协作运行。 独立的顶级组件，如模式和使用 IDE 的消息循环服务，必须还将协调工具顶级组件。  
  
 顶级组件  
 VSPackage 对象，用于管理一个无模式的顶级窗口，而不是一个 IDE 窗口的工作区。 顶级组件实现`IOleComponent`接口以利用到空闲时间的消息循环服务，例如访问。  
  
 UI 活动  
 VSPackage 对象是可见且当前具有焦点。  
  
 UI 层次结构  
 COM 对象实现`IVsUIHierarchy`接口以允许层次结构的显示。 UI 层次结构窗口实现`ISelectionContainer`接口更新属性窗口; 其他项目类型 windows 可以使用此实现中，如果需要。  
  
 VSCT  
 Visual Studio 命令表。 .Vsct 文件包含有关布局和菜单、 工具栏和 XML 格式的命令的行为的信息。  
  
 VSPackage  
 可安装的一种软件，它通过参与一个或多个以下扩展 Visual Studio IDE： 用户界面、 服务、 项目类型或编辑器 / 设计器。 VSPackage 包含 COM 对象实现`IVsPackage`接口和一个或多个其他 COM 对象实现其他接口以支持选择和其他功能。 此外，VSPackage 具有特定的注册要求。