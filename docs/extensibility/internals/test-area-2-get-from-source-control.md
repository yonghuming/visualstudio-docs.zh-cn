---
title: "测试区域 2： 获取从源代码管理 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, getting items from source control
- source control [Visual Studio SDK], getting items from
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3d436ef99907556c93f48c55bea315ae66e6218e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="test-area-2-get-from-source-control"></a>测试区域 2： 获取从源代码管理
此测试区域介绍用于从通过 Get 命令的版本存储区中检索项的测试用例。 可以应用于这些测试用例，这两个本地以及 Web 项目。  
  
## <a name="command-menu-access"></a>命令菜单访问  
 以下[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]集成的开发环境菜单路径使用的测试用例。  
  
##### <a name="get-latest-version"></a>获取最新版本：  
  
-   **文件**，**源代码管理**，**获取最新版本**。  
  
-   **文件**，**获取最新版本**。  
  
-   快捷菜单上，**获取最新版本**。  
  
-   Get:**文件**，**源代码管理**，**获取**。  
  
## <a name="expected-behavior"></a>预期的行为  
  
##### <a name="get-latest-version"></a>获取最新版本：  
 从版本存储区执行无提示 (无 UI) 检索的项的最新版本。  
  
##### <a name="get"></a>获取：  
 显示**获取**对话框中，并允许用户对将检索，以及修改会影响如何检索文件的选项的文件集进行更改。  
  
## <a name="test-cases"></a>测试用例  
  
|操作|测试步骤|若要验证的预期的结果|  
|------------|----------------|--------------------------------|  
|获取不存在本地文件的最新版本|1.创建项目。<br />2.向项目添加项。<br />3.将源代码管理中的项目。<br />4.删除项的本地副本。<br />5.获取项的最新版本 (快捷菜单上，**获取最新版本**)。|本地检索项文件。|  
|获取不存在本地文件|1.创建项目。<br />2.向项目添加项。<br />3.将源代码管理中的项目。<br />4.删除项的本地副本。<br />5.获取的项 (**文件**，**源代码管理**，**获取**\<项 >)。|本地检索项文件。|  
|获取已以独占方式签出和修改本地文件|1.创建项目。<br />2.向项目添加项。<br />3.将源代码管理中的项目。<br />4.以独占方式签出项目项。<br />5.修改本地副本。<br />6.获取项的最新版本 (**文件**，**获取最新版本的**\<项 >)。 如果此步骤成功，则继续下一步。<br />7.单击**替换**在警告对话框中的按钮。|**步骤 6 中 reResult**`:`<br /><br /> 警告对话框中指示该文件已签出。<br /><br /> **ReResult 来自步骤 7:**<br /><br /> 修改后的本地文件替换为从版本存储的原始版本。<br /><br /> 文件是读/写。|  
|获取，并将文件签出、 共享的并且本地修改|1.创建新项目。<br />2.向项目添加项。<br />3.将源代码管理中的项目。<br />4.签出作为共享的项目项。<br />5.修改本地副本。<br />6.获取项的最新版本 (**文件**，**获取最新版本的**\<项 >)。 如果此步骤成功，则继续下一步。<br />7.单击**替换**在警告对话框中。|**来自步骤 6:**<br /><br /> 警告对话框中指示该文件已签出。<br /><br /> **来自步骤 7:**<br /><br /> 修改后的本地文件替换为从版本存储的原始版本。<br /><br /> 文件是读/写。|  
|获取本地存在的文件版本存储区中的最新版本相同|1.创建新项目。<br />2.向项目添加项。<br />3.将源代码管理中的项目。<br />4.获取的项 (**文件**，**源代码管理**，**获取**\<项 >)。|本地文件保持不变。|  
|获取具有一个项目的解决方案|1.与一个项目中创建一个解决方案。<br />2.将放置在源代码管理下的解决方案。<br />3.删除所有项目文件本地。<br />4.获取解决方案 (**文件**，**源代码管理**，**获取**)。|将本地还原所有已删除的文件。|  
  
## <a name="see-also"></a>另请参阅  
 [源代码管理插件的测试指南](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)