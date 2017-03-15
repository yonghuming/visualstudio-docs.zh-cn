---
title: "Creating and Managing Databases and Data-tier Applications in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing change, databases"
  - "database features of Visual Studio, managing change"
  - "databases, managing change"
  - "managing change, database servers"
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
caps.latest.revision: 37
caps.handback.revision: 35
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Creating and Managing Databases and Data-tier Applications in Visual Studio
> [!IMPORTANT]
>  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的早期版本中包括的数据库项目。[!INCLUDE[sql_Denali_long](../data-tools/includes/sql_denali_long_md.md)] 工具现在提供。  有关更多信息，请参见 [SQL Server开发人员工具](http://go.microsoft.com/fwlink/?LinkId=228126)。  
  
 您可以使用数据库项目来创建新数据库、新数据层应用程序 \(DAC\)，以及更新现有数据库和数据层应用程序。  利用数据库项目和 DAC 项目，您都可以将版本控制和项目管理技术应用于数据库开发工作，采用的方式与将这些技术应用于托管代码或本机代码大致相同。  您可以帮助开发团队管理对数据库和数据库服务器的更改，方法是创建 DAC 项目、数据库项目或服务器项目，并将其置于版本控制之下。  然后，团队的成员将能够签出文件，以便在独立开发环境（或沙盒）中进行更改、生成更改和测试更改，之后再与团队共享这些更改。  为了帮助确保代码质量，您的团队可以针对临时环境中的特定数据库版本完成和测试所有更改，之后您再将这些更改部署到生产。  
  
 有关由数据层应用程序支持的数据库功能的列表，请参见 [在数据层应用程序支持的功能](http://go.microsoft.com/fwlink/?LinkId=164239) Microsoft网站上。  如果您在数据库中使用数据层应用程序不支持的功能，则应改为使用数据库项目管理对数据库的更改。  
  
## 常见高级任务  
  
|高级任务|支持内容|  
|----------|----------|  
|**开始开发数据层应用程序：**DAC 是随 [!INCLUDE[sskatmai_r2](../data-tools/includes/sskatmai_r2_md.md)] 引入的一个新概念，它包含 [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] 数据库的定义，以及由客户端\/服务器应用程序或 3 层应用程序使用的支持实例对象。  DAC 包括数据库对象（例如表和视图）以及实例实体（例如登录名）。  您可以使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 来创建 DAC 项目、生成 DAC 数据包文件，以及将该 DAC 数据包文件发送到数据库管理员以便部署到 [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] 数据库引擎的实例上。|-   [创建和管理数据层应用程序](http://go.microsoft.com/fwlink/?LinkId=160741)（Microsoft 网站）<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|  
|**执行迭代数据库开发：**如果您是开发人员或测试人员，则可以签出项目的一部分，然后在独立开发环境中对它们进行更新。  通过使用这种类型的环境，可以测试更改，而不会影响团队的其他成员。  完成更改后，可将文件重新签入到版本控制中，其他团队成员可在其中获取更改，并生成更改然后将它们部署到测试服务器。|-   [查询和文本编辑器\(SQL Server Management Studio\)](http://go.microsoft.com/fwlink/?LinkId=227327) \(Microsoft网站\)<br />-   [Transact\-SQL调试器](http://go.microsoft.com/fwlink/?LinkId=227324) \(Microsoft网站\)|  
|**建立原型、验证测试结果并修改数据库脚本和对象：**您可以使用 [!INCLUDE[tsql](../data-tools/includes/tsql_md.md)] 编辑器来执行这些常见任务中的任何一个。|-   [查询和文本编辑器\(SQL Server Management Studio\)](http://go.microsoft.com/fwlink/?LinkId=227327) \(Microsoft网站\)|