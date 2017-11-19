---
title: "数据库项目、 服务器项目，和 Visual Studio 中的 DAC 项目 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing change, databases
- database features of Visual Studio, managing change
- databases, managing change
- managing change, database servers
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
caps.latest.revision: "37"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 7f538c51bd5f15f91dfae0d13a9dae8cf4f8afb1
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="database-projects-and-data-tier-applications-in-visual-studio"></a>数据库项目和 Visual Studio 中的数据层应用程序  
你可以使用数据库项目创建新数据库，新数据层应用程序 (Dac)，并更新现有数据库和数据层应用程序。 数据库项目和 DAC 项目，可以将版本控制和项目管理技术应用于数据库开发工作中，基本相同的方法将这些技术应用于托管或本机代码中。 您可以帮助开发团队管理对数据库和数据库服务器的更改通过创建*DAC 项目*，*数据库项目*，或*服务器项目*并将其放置在版本控制。 你的团队成员可以然后签出文件，以使、 生成和测试中的更改*独立的开发环境*，或沙盒之前与团队共享它们。 为了帮助确保代码质量，团队可完成和部署到生产环境所做的更改之前在过渡环境中测试的数据库的特定版本的所有更改。  
  
有关支持的数据层应用程序的数据库功能的列表，请参阅[数据层应用程序中支持的功能](http://go.microsoft.com/fwlink/?LinkId=164239)Microsoft web 站点上。 如果你使用你的数据库不支持的数据层应用程序的功能，则应改用数据库项目来管理对你的数据库的更改。  
  
## <a name="common-high-level-tasks"></a>常见的高级任务  
  
|高级任务|支持内容|  
|----------------------|------------------------|  
|**启动的数据层应用程序开发：** DAC 是随引入的新概念[!INCLUDE[sskatmai_r2](../data-tools/includes/sskatmai_r2_md.md)]，它包含用于定义[!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]数据库和支持实例程序使用的客户端-服务器或 3 层对象应用程序。 DAC 包括数据库对象，例如表和视图，以及实例的实体，例如登录名。 你可以使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]若要创建某一 DAC 项目，生成 DAC 包文件，并将该 DAC 包文件发送到实例上部署的数据库管理员[!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]数据库引擎。|-   [创建和管理数据层应用程序](http://go.microsoft.com/fwlink/?LinkId=160741)（Microsoft web 站点）<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|  
|**执行迭代数据库开发：**如果你是开发人员或测试人员，签出项目的部分的虚拟机和模板，然后在一个独立的开发环境中更新它们。 通过使用这种类型的环境，可以测试所做的更改，而不会影响团队的其他成员。 所做的更改都已完成后，你将检查文件恢复到版本控制，其他团队成员可以获取所做的更改和生成并将它们部署到测试服务器。|-   [查询和文本编辑器 (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) （Microsoft web 站点）<br />-   [TRANSACT-SQL 调试器](http://go.microsoft.com/fwlink/?LinkId=227324)（Microsoft web 站点）|  
|**原型制作验证测试结果，以及修改数据库脚本和对象：**可以使用[!INCLUDE[tsql](../data-tools/includes/tsql_md.md)]编辑器来执行这些通用任务之一。|-   [查询和文本编辑器 (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) （Microsoft web 站点）|  
  
## <a name="see-also"></a>请参阅
[适用于 NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)
