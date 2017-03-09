---
title: "How to: Add, Update, or Remove a WCF Data Service Reference | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "service references [Visual Studio]"
  - "WCF Data Service reference"
  - "WCF data service references"
  - "ADO.NET service references"
  - "ADO.NET Data Service reference"
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Add, Update, or Remove a WCF Data Service Reference
利用服务引用，项目可访问一个或多个 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]。  使用**“添加服务引用”**对话框可在当前解决方案中、在本地、在局域网中或在 Internet 上搜索 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## 添加服务引用  
  
#### 添加对外部服务的引用  
  
1.  在**“解决方案资源管理器”**中，右击要添加服务的项目的名称，然后单击**“添加服务引用”**。  
  
     将出现**“添加服务引用”**对话框。  
  
2.  在**“地址”**框中，输入服务的 URL，然后单击**“前往”**搜索该服务。  如果此服务实现了用户名和密码安全性，系统可能会提示您输入用户名和密码。  
  
    > [!NOTE]
    >  只应引用来自受信任源的服务。  添加来自不受信任源的引用可能会降低安全性。  
  
     还可以从**“地址”**列表中选择 URL，此列表存储了前 15 个在其中找到了有效服务元数据的 URL。  
  
     执行搜索时将显示一个进度栏。  随时都可以通过单击**“停止”**来停止搜索。  
  
3.  在**“服务”**列表中，展开要使用的服务的节点，并选择一个实体集。  
  
4.  在**“命名空间”**框中，输入要用于引用的命名空间。  
  
5.  单击**“确定”**以将此引用添加到项目。  
  
     将生成一个服务客户端（代理），并且描述此服务的元数据将添加到 app.config 文件中。  
  
#### 添加对当前解决方案中的服务的引用  
  
1.  在**“解决方案资源管理器”**中，右击要添加服务的项目的名称，然后单击**“添加服务引用”**。  
  
     将出现**“添加服务引用”**对话框。  
  
2.  单击**“发现”**。  
  
     当前解决方案中的所有服务（[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]和 WCF 服务）都将添加到**“服务”**列表中。  
  
3.  在**“服务”**列表中，展开要使用的服务的节点，并选择一个实体集。  
  
4.  在**“命名空间”**框中，输入要用于引用的命名空间。  
  
5.  单击**“确定”**以将此引用添加到项目。  
  
     将生成一个服务客户端（代理），并且描述此服务的元数据将添加到 app.config 文件中。  
  
## 更新服务引用  
 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]的实体数据模型有时会发生更改。  如果此情况发生，则必须更新服务引用。  
  
#### 更新服务引用  
  
-   在**“解决方案资源管理器”**中，右击服务引用，然后单击**“更新服务引用”**。  
  
     在从引用的原始位置更新该引用的过程中将显示一个进度对话框，并且会重新生成服务客户端以反映元数据中的任何更改。  
  
## 移除服务引用  
 如果不再使用服务引用，则可将其从解决方案中移除。  
  
#### 移除服务引用  
  
-   在**“解决方案资源管理器”**中，右击服务引用，然后单击**“删除”**。  
  
     该服务客户端将从解决方案中移除，并且描述该服务的元数据也将从 app.config 文件中移除。  
  
    > [!NOTE]
    >  引用该服务引用的任何代码将需要手动移除。  
  
## 请参阅  
 [Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md)