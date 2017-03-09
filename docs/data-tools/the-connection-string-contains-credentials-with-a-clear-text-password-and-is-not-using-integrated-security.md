---
title: "连接字符串包含带有明文密码的凭据并且未使用集成安全性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 连接字符串包含带有明文密码的凭据并且未使用集成安全性
是否要将此敏感信息随连接字符串一起保存到当前 DBML 文件和应用程序配置文件中?单击“否”可在保存连接字符串时不保存敏感信息。  
  
 在使用包含敏感信息（连接字符串中包含的密码）的数据连接时，可以选择将敏感信息随连接字符串一起保存到项目 DBML 文件和应用程序配置文件中，或者选择不保存敏感信息。  
  
> [!WARNING]
>  将**“连接”**属性**“应用程序设置”**属性显式设置为**“False”**可将密码添加到 DBML 文件中。  
  
### 将敏感信息随连接字符串一起保存在项目的应用程序设置中  
  
-   单击**“是”**。  
  
     连接字符串将存储为应用程序设置。连接字符串以纯文本形式包含敏感信息。DBML 文件不包含敏感信息。  
  
### 不将敏感信息随连接字符串一起保存在项目的应用程序设置中  
  
-   单击**“否”**。  
  
     连接字符串将存储为应用程序设置，但不包含密码。  
  
## 请参阅  
 [对象关系设计器（O\/R 设计器）](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [连接到 Visual Studio 中的数据](../data-tools/connecting-to-data-in-visual-studio.md)