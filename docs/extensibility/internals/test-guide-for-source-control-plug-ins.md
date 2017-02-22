---
title: "源代码管理插件的测试指南 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "插件，源代码管理"
  - "源代码管理 [Visual Studio SDK]，测试插件"
  - "测试，源代码管理插件"
  - "测试、 源代码管理插件"
  - "源代码管理插件，测试指南"
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
caps.latest.revision: 26
caps.handback.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
---
# 源代码管理插件的测试指南
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

本节提供有关测试源代码管理插件的指导。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  ，以及一些更复杂的区域提供了最常见的测试的区域大量可能有问题的概述。  本概述不被视为是完整的列表测试用例。  
  
> [!NOTE]
>  这些 bug 修复和改进到最新 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 能找到问题的以前没有遇到，在使用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]时的早期版本中的现有源代码管理插件。  强烈建议您测试本节枚举区域的现有源代码管理插件，因此，即使更改未对插件从 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]的早期版本。  
  
## 常见准备  
 ，需要具有 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的计算机和安装的目标源代码管理插件。  与配置的第二台计算机上可用于某些打开使用从源代码管理测试。  
  
## 术语的定义  
 为测试准则的目的，请使用以下术语定义:  
  
 客户端项目  
 例如支持源代码管理集成的任何项目类型中可用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(， [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]、 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]或 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)]\)。  
  
 Web 项目  
 使 Web 项目的四种类型:文件系统、本地 IIS、远程站点和 FTP。  
  
-   文件系统项目在本地路径创建，但是，不需要 internet information services 安装 \(IIS\)，则在通过 UNC 路径在内部访问，并可以将其置于源代码管理下从 IDE 内部，这与客户端项目。  
  
-   在同一计算机上已安装并获取与点的 URL 与本地计算机与 IIS 的本地 IIS 项目工作。  
  
-   远程网站项目还会创建在下 IIS 服务，但是，其中放置在源代码管理下在 IIS 服务器计算机而不是从 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 内部。  
  
-   FTP 项目通过远程 FTP 服务器访问，但不能放在源代码管理。  
  
 登记  
 解决方案的另一个在源代码管理的术语或项目。  
  
 版本存储  
 通过源代码管理插件 API 访问的源代码管理数据库。  
  
## 本节包含的测试环节  
  
-   [测试区域 1︰ 从源代码管理添加到文件，或打开](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)  
  
    -   用例 1a:将解决方案添加到源代码管理  
  
    -   用例 1b 中:从源代码管理打开的解决方案  
  
    -   用例 1c:从源代码管理添加解决方案  
  
-   [从源代码管理获取测试的区域 2:](../../extensibility/internals/test-area-2-get-from-source-control.md)  
  
-   [测试区域 3︰ 签出\/撤消签出](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)  
  
    -   情况 3:检查\/撤消签出  
  
    -   用例 3a:检查  
  
    -   用例 3b:断开连接的签出  
  
    -   用例 3c:查询编辑器或查询保存 \(QEQS\)  
  
    -   用例三维:无提示签出  
  
    -   用例 3e:撤消签出  
  
-   [测试区域 4︰ 签入](../../extensibility/internals/test-area-4-check-in.md)  
  
    -   用例 4a:修改后的项目  
  
    -   用例 4b:添加文件  
  
    -   用例 4c:添加项目  
  
-   [测试区域 5︰ 更改源代码管理](../../extensibility/internals/test-area-5-change-source-control.md)  
  
    -   用例 5a:绑定  
  
    -   用例 5b:断开连接  
  
    -   用例 5c:Rebind  
  
-   [测试区域 6: 删除](../../extensibility/internals/test-area-6-delete.md)  
  
-   [测试区域 7: 共享](../../extensibility/internals/test-area-7-share.md)  
  
-   [测试区域 8: 插件切换](../../extensibility/internals/test-area-8-plug-in-switching.md)  
  
    -   用例 8a:自动更改  
  
    -   用例 8b:基于解决方案的更改  
  
## 请参阅  
 [源代码管理插件](../../extensibility/source-control-plug-ins.md)