---
title: "如何：将数据文件包括到 ClickOnce 应用程序中 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce 部署, 数据"
  - "数据访问, ClickOnce 应用程序"
  - "部署应用程序 [ClickOnce], 数据文件"
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 如何：将数据文件包括到 ClickOnce 应用程序中
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

安装的每个 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序在目标计算机的本地磁盘中都指定有一个数据目录，应用程序可以在其中管理自己的数据。  数据文件可以包括任何类型的文件，如文本文件、XML 文件，甚至 Microsoft Access 数据库 \(.mdb\) 文件。  下面的过程演示如何向 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序添加任何类型的数据文件。  
  
### 使用 Mage.exe 包括数据文件  
  
1.  将数据文件与其余的应用程序文件一起添加到应用程序目录中。  
  
     通常，应用程序目录是一个标有部署的当前版本（如 v1.0.0.0）的目录。  
  
2.  更新应用程序清单以列出数据文件。  
  
     **mage \-u v1.0.0.0\\Application.manifest \-FromDirectory v1.0.0.0**  
  
     执行此任务会重新创建应用程序清单中的文件列表，还会自动生成哈希签名。  
  
3.  在首选的文本或 XML 编辑器中打开应用程序清单，然后在 `file` 元素中找到最近添加的文件。  
  
     如果添加名为 `Data.xml` 的 XML 文件，该文件将类似于下面的代码示例。  
  
 `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  向此元素添加 `type` 特性，并为其提供 `data` 值。  
  
 `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  通过使用密钥对或证书对应用程序清单重新签名，然后对部署清单重新签名。  
  
     必须对部署清单重新签名，因为其应用程序清单哈希已更改。  
  
     **mage \-s app manifest \-cf cert\_file \-pwd password**  
  
     **mage \-u deployment manifest \-appm app manifest**  
  
     **mage \-s deployment manifest \-cf certfile \-pwd password**  
  
### 使用 MageUI.exe 包括数据文件  
  
1.  将数据文件与其余的应用程序文件一起添加到应用程序目录中。  
  
2.  通常，应用程序目录是一个标有部署的当前版本（如 v1.0.0.0）的目录。  
  
3.  在**“文件”**菜单上，单击**“打开”**，以打开应用程序清单。  
  
4.  选择**“文件”**选项卡。  
  
5.  在该选项卡顶部的文本框中，输入包含应用程序文件的目录，然后单击**“填充”**。  
  
     数据文件将出现在网格中。  
  
6.  将数据文件的**“文件类型”**值设置为**“数据”**。  
  
7.  保存应用程序清单，然后对该文件重新签名。  
  
     MageUI.exe 将提示您重新对文件进行签名。  
  
8.  对部署清单重新签名  
  
     必须对部署清单重新签名，因为其应用程序清单哈希已更改。  
  
## 请参阅  
 [在 ClickOnce 应用程序中访问本地数据和远程数据](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)