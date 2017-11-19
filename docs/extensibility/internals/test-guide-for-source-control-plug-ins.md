---
title: "测试对源控件插件指南 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 55783b604e929d2e5d4cdc613befa2fbec42aec4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="test-guide-for-source-control-plug-ins"></a>为源控件插件测试指南
本部分提供用于测试你的源代码管理插件与指南[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 提供的最常见的测试区域，以及一些可能会出现问题的更复杂区域的广泛概述。 本概述不是测试用例的穷举列表。  
  
> [!NOTE]
>  某些 bug 修复和到最新改进[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 可能会发现与现有源控件的插件以以前未使用的早期版本时遇到的问题[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 强烈建议你测试你现有的源代码管理插件在此部分中，枚举的区域，即使以来的以前版本的插件进行任何更改[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="common-preparation"></a>常见的准备  
 具有的机[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]和安装，是必需的目标源代码管理插件。 同样配置第二台计算机可以用于一些打开从源代码管理的测试。  
  
## <a name="definition-of-terms"></a>术语的定义  
 在此测试指南中，使用以下术语定义：  
  
 客户端项目  
 任何项目类型中提供[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]支持源代码管理集成 (例如， [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]， [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]，或[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)])。  
  
 Web 项目  
 有四种类型的 Web 项目： 文件系统、 本地 IIS、 远程站点和 FTP。  
  
-   上的本地路径创建文件系统项目，但它们不需要 Internet 信息服务 (IIS)，因为它们通过 UNC 路径，内部访问，并将放置在从 IDE，类似于客户端项目内部的源代码管理下安装。  
  
-   本地 IIS 项目使用指向本地计算机的 URL 与程序安装在同一台计算机上访问 IIS 的工作。  
  
-   远程站点项目还将创建下一项 IIS 服务，但它们放置在 IIS 服务器计算机上而不是从源代码管理下内[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE。  
  
-   FTP 项目通过远程 FTP 服务器进行访问，但不能将它们放置在源代码管理下。  
  
 登记  
 解决方案或项目受源代码管理的另一个术语。  
  
 版本存储区  
 正在访问通过源控件插件 API 从源代码管理数据库。  
  
## <a name="test-areas-covered-in-this-section"></a>在本部分中介绍的测试环节  
  
-   [测试区域 1： 从源代码管理添加到 / 打开](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)  
  
    -   案例 1a： 将解决方案添加到源代码管理  
  
    -   案例 1b： 源代码管理中打开解决方案  
  
    -   案例 1 c： 从源代码管理中添加解决方案  
  
-   [测试区域 2：从源代码管理获取](../../extensibility/internals/test-area-2-get-from-source-control.md)  
  
-   [测试区域 3： 签出/撤消签出](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)  
  
    -   情况 3： 签出/撤消签出  
  
    -   案例 3a： 签出  
  
    -   案例 3b： 断开连接签出  
  
    -   案例 3 c： 查询编辑/查询保存 (QEQS)  
  
    -   案例三维： 无提示签出  
  
    -   案例 3e： 撤消签出  
  
-   [测试区域 4：签入](../../extensibility/internals/test-area-4-check-in.md)  
  
    -   案例 4a： 修改项目  
  
    -   案例 4b： 将文件添加  
  
    -   案例 4c： 添加项目  
  
-   [测试区域 5：更改源代码管理](../../extensibility/internals/test-area-5-change-source-control.md)  
  
    -   案例 5a： 绑定  
  
    -   案例 5b： 取消绑定  
  
    -   案例 5c： 重新绑定  
  
-   [测试区域 6：删除](../../extensibility/internals/test-area-6-delete.md)  
  
-   [测试区域 7：共享](../../extensibility/internals/test-area-7-share.md)  
  
-   [测试区域 8：插件切换](../../extensibility/internals/test-area-8-plug-in-switching.md)  
  
    -   案例 8a： 自动更改  
  
    -   案例 8b： 基于解决方案的更改  
  
## <a name="see-also"></a>另请参阅  
 [源代码管理插件](../../extensibility/source-control-plug-ins.md)