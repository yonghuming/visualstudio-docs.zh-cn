---
title: "实现智能宿主帮助程序接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "智能宿主帮助程序接口, 实现"
ms.assetid: b9c44246-4d4d-469e-91be-00c8f5796fa5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 实现智能宿主帮助程序接口
因为它用于许多接口提供实现所需的智能承载，[IDebugDocumentHelper 接口](../winscript/reference/idebugdocumenthelper-interface.md) 接口极大地简化了创建有效的调试一个智能宿主任务。  
  
 使用 `IDebugDocumentHelper`，若要是一个智能宿主，宿主应用程序只必须执行下列三种操作：  
  
1.  `CoCreate` 进程调试管理器，并使用 [IProcessDebugManager 接口](../winscript/reference/iprocessdebugmanager-interface.md) 接口向应用程序添加到可调试应用程序列表中。  
  
2.  使用 [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md) 方法，创建调试文档每个脚本对象的帮助器，。  确保文档名称，父文档，文本，并且，脚本块定义。  
  
3.  实现对象的 [IActiveScriptSiteDebug 接口](../winscript/reference/iactivescriptsitedebug-interface.md) 接口实现Active脚本是必需的\)的 [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) 界面\(ui\)。  在 `IActiveScriptSiteDebug` 接口完全委托的唯一重要方法帮助器。  
  
 或者，宿主可以实现 [IDebugDocumentHost 接口](../winscript/reference/idebugdocumenthost-interface.md) 接口，如果需要使用语法颜色的其他控件，文档上下文创建和其他扩展功能。  
  
 在智能宿主帮助器的主要限制是它可以内容更改或缩小仅的处理文档，并在添加之后\(尽管文档中展开\)。  对于许多智能宿主，但是，它提供的功能正是必需的。  
  
 以下各节将更详细地说明了每个步骤。  
  
## 创建一个应用程序对象  
 才能使用智能宿主帮助器，创建 [IDebugApplication 接口](../winscript/reference/idebugapplication-interface.md) 对象表示您在调试器的应用程序是必需的。  
  
#### 创建应用程序对象  
  
1.  创建处理例程调试使用 `CoCreateInstance`管理器的。  
  
2.  调用 [IProcessDebugManager::CreateApplication](../winscript/reference/iprocessdebugmanager-createapplication.md)。  
  
3.  使用 [IDebugApplication::SetName](../winscript/reference/idebugapplication-setname.md)，将应用程序的名称。  
  
4.  使用 [IProcessDebugManager::AddApplication](../winscript/reference/iprocessdebugmanager-addapplication.md)，向可调试应用程序中列出的应用程序对象。  
  
     在下面的代码概括了处理，但是，它不包含错误检查或其他可靠编程技术。  
  
    ```  
    CoCreateInstance(CLSID_ProcessDebugManager, NULL,  
          CLSCTX_INPROC_SERVER | CLSCTX_INPROC_HANDLER  
          | CLSCTX_LOCAL_SERVER,  
    IID_IProcessDebugManager, (void **)&g_ppdm);  
    g_ppdm->CreateApplication(&g_pda);  
    g_pda->SetName(L"My cool application");  
    g_ppdm->AddApplication(g_pda, &g_dwAppCookie);  
    ```  
  
## 使用IDebugDocumentHelper  
  
#### 使用帮助器\(步骤最少的顺序\)  
  
1.  对于每个主机文档，创建使用 [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md)的帮助器。  
  
2.  调用帮助器的 [IDebugDocumentHelper::Init](../winscript/reference/idebugdocumenthelper-init.md)，为该名称，文档属性，依此类推。  
  
3.  调用与父帮助器 [IDebugDocumentHelper::Attach](../winscript/reference/idebugdocumenthelper-attach.md) 文档\(或NULL中，如果文档是根\)定义文档的位置在树并使其可见到调试器。  
  
4.  调用 [IDebugDocumentHelper::AddDBCSText](../winscript/reference/idebugdocumenthelper-adddbcstext.md) 或 [IDebugDocumentHelper::AddUnicodeText](../winscript/reference/idebugdocumenthelper-addunicodetext.md) 定义文档中的文本。  \(这些可多次调用，则文档增量下载，以免浏览器。\)  
  
5.  调用 [IDebugDocumentHelper::DefineScriptBlock](../winscript/reference/idebugdocumenthelper-definescriptblock.md) 定义每个脚本块的大小和关联的脚本引擎。  
  
## 实现IActiveScriptSiteDebug  
 若要实现 [IActiveScriptSiteDebug::GetDocumentContextFromPosition](../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)，获取帮助器与给定站点相对应，获取开始然后文档特定源上下文的偏移量，如下所示：  
  
```  
pddh->GetScriptBlockInfo(dwSourceContext, NULL, &ulStartPos, NULL);  
```  
  
 接下来，使用帮助器创建特定字符的新文档上下文偏移量：  
  
```  
pddh->CreateDebugDocumentContext(ulStartPos + uCharacterOffset, cChars, &pddcNew);  
```  
  
 若要实现 [IActiveScriptSiteDebug::GetRootApplicationNode](../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)，请调用 `IDebugApplication::GetRootNode` \(继承自 [IRemoteDebugApplication::GetRootNode](../winscript/reference/iremotedebugapplication-getrootnode.md)\)。  
  
 若要实现 [IDebugDocumentHelper::GetDebugApplicationNode](../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md)，则返回最初创建使用进程内调试管理器的 `IDebugApplication`。  
  
## 选项IDebugDocumentHost接口  
 宿主可提供 [IDebugDocumentHost 接口](../winscript/reference/idebugdocumenthost-interface.md) 的实现使用 [IDebugDocumentHelper::SetDebugDocumentHost](../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md) 为其提供给帮助器的其他控件。  这是宿主接口允许您所做的一些主要操作：  
  
-   添加文本使用 [IDebugDocumentHelper::AddDeferredText](../winscript/reference/idebugdocumenthelper-adddeferredtext.md)，以便宿主无需立即提供实际字符。  当字符实际上是必需的，帮助程序将调用宿主的 [IDebugDocumentHost::GetDeferredText](../winscript/reference/idebugdocumenthost-getdeferredtext.md)。  
  
-   重写帮助器提供默认值的语法着色。  如果宿主返回 `E_NOTIMPL`，帮助器调用 [IDebugDocumentHost::GetScriptTextAttributes](../winscript/reference/idebugdocumenthost-getscripttextattributes.md) 确定字符范围的着色，转而依赖于其默认实现。  
  
-   提供控件未知对于文档帮助器创建的上下文通过实现 [IDebugDocumentHost::OnCreateDocumentContext](../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md)。  这允许宿主重写默认值的功能文档上下文实现。  
  
-   提供文档提供在文件系统的路径名称。  一些调试用户界面使用这允许用户编辑和保存到文档的更改。  在文档保存后，[IDebugDocumentHost::NotifyChanged](../winscript/reference/idebugdocumenthost-notifychanged.md) 调用以通知宿主。  
  
## 请参阅  
 [活动脚本调试概述](../winscript/active-script-debugging-overview.md)