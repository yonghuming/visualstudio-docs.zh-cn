---
title: "如何：升级到 LocalDB 或继续使用 SQL Server Express | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "LocalDB"
  - "SQL Server Express"
  - "SQL Server LocalDB"
  - "SQLEXPRESS"
  - "将 SQLExpress 升级到 SQLExpress"
  - "升级到 LocalDB"
ms.assetid: 14ca6f76-f80e-4926-8020-3fee2d802b75
caps.latest.revision: 33
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 如何：升级到 LocalDB 或继续使用 SQL Server Express
本主题描述您的升级数据库文件\(.mdf\)的选项卡，在安装 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 后并包含以下任务的命令:  
  
-   升级数据库文件使用LocalDB  
  
-   升级数据库文件使用SQL Server Express的一个新版本  
  
-   与 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 的数据库文件，但保留与 [!INCLUDE[ssKatmai_exp](../data-tools/includes/sskatmai_exp_md.md)]的兼容性  
  
-   创建SQL Server express默认数据库引擎  
  
 可以使用 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 打开包含使用创建SQL Server Express的旧版本中的数据库文件的项目\(.mdf\)  但是，继续开发您在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]的项目中，必须为获取版本的计算机上安装的SQL Server express和Visual Studio相同或者必须升级数据库文件添加到使用SQL Server express LocalDB。  如果升级数据库文件，您无法访问其与SQL Server Express的更早版本。  
  
 还会提示您是否升级使用创建 [!INCLUDE[sql_Denali_exp](../data-tools/includes/sql_denali_exp_md.md)] 的数据库文件，如果文件的版本不与当前安装SQL Server Express兼容的实例。  若要解决此问题，Visual Studio将提示您升级文件到SQL Server Express的新版本。  
  
> [!IMPORTANT]
>  建议您备份数据库文件，在升级之前。  
  
 在升级数据库之前，应考虑以下条件:  
  
-   如果要使用您在 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 和 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]的项目中，不要升级。  
  
-   不要升级，如果您的应用程序在使用SQL Server express而不是LocalDB的环境。  
  
-   不要升级，如果应用程序使用远程连接，因为LocalDB不接受这些更改。  
  
-   如果应用程序依赖于Internet信息服务\(IIS\)，不要升级。  
  
-   升级的考虑，如果您在沙盒环境中若要测试数据库应用程序，但不要控制数据库。  
  
### 升级数据库文件使用LocalDB  
  
1.  在 **\*\*\* 服务器资源管理器 \*\*\***，选择 **\*\*\* 连接到数据库 \*\*\*** 按钮。  
  
2.  在 **\*\*\* 添加连接 \*\*\*** 对话框中，指定以下信息:  
  
    -   **“数据源：”** Microsoft SQL Server \(SqlClient\)  
  
    -   **\*\*\* 服务器名称: \*\*\*** \(LocalDB\) \\ v11.0  
  
    -   **\*\*\* 附加数据库文件: \*\*\*** *路径*，其中 *路径* 主要是.mdf文件的物理路径。  
  
    -   **\*\*\* 逻辑名称: \*\*\*** *名称*，其中 *名称* 是要用于文件的名称。  
  
3.  选择**“确定”**按钮。  
  
4.  当提示，选择 **\*\*\* 是 \*\*\*** 按钮升级文件。  
  
 数据库中升级，附加到LocalDB数据库引擎，且不再与 [!INCLUDE[ssKatmai_exp](../data-tools/includes/sskatmai_exp_md.md)]兼容。  
  
 还可以修改SQLExpress连接是通过打开快捷菜单提供用于连接然后选择 **\*\*\* 修改连接 \*\*\***使用LocalDB。  在 **\*\*\* 修改连接 \*\*\*** 对话框中，更改服务器名称为\(LocalDB\) \\ v11.0。  在 **\*\*\* 高级属性 \*\*\*** 对话框中，确保 **\*\*\* 用户实例 \*\*\*** 设置为False。  
  
### 升级到SQL Server Express的一个新版本  
  
1.  在连接的快捷菜单与数据库，选择 **\*\*\* 修改连接 \*\*\***。  
  
2.  在 **\*\*\* 修改连接 \*\*\*** 对话框中，选择 **\*\*\* 高级 \*\*\*** 按钮。  
  
3.  在 **\*\*\* 高级属性 \*\*\*** 对话框中，选择 **\*\*\* 好 \*\*\*** 按钮，而不更改服务器名称。  
  
 数据库文件升级匹配 [!INCLUDE[sql_Denali_exp](../data-tools/includes/sql_denali_exp_md.md)]的最新版本。  
  
### 与 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 的数据库，但保留与 [!INCLUDE[ssKatmai_exp](../data-tools/includes/sskatmai_exp_md.md)]的兼容性  
  
1.  在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]，请打开项目，而无需将其升级。  
  
    -   若要运行项目，请选择F5键。  
  
    -   象在 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]，执行若要编辑该数据库，请打开在 **\*\*\* 解决方案资源管理器 \*\*\***的.mdf文件，然后展开在 **\*\*\* 服务器资源管理器 \*\*\*** 的节点与数据库一起使用。  
  
### 若要创建SQL Server中表示默认数据库引擎  
  
1.  在菜单栏上，依次选择 **\*\*\* 工具 \*\*\***，**\*\*\* 选项 \*\*\***。  
  
2.  在 **\*\*\* 选项 \*\*\*** 对话框中，展开 **\*\*\* 数据工具 \*\*\*** 选项卡，然后选择 **\*\*\* 数据连接 \*\*\*** 节点。  
  
3.  在 **\*\*\* SQL Server实例名称 \*\*\*** 文本框中，指定要使用SQL Server Express的实例的名称。  如果实例未命名，指定 `. \ SQLEXPRESS`。  
  
4.  选择**“确定”**按钮。  
  
 SQL Server express将是应用程序的默认数据库引擎。  
  
## 请参阅  
 [本地数据概述](../data-tools/local-data-overview.md)   
 [演练：连接到本地数据库文件中的数据（Windows 窗体）](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Local%20Database%20File%20\(Windows%20Forms\).md)