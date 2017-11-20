---
title: "如何： 在 ClickOnce 应用程序包含一个数据文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- deploying applications [ClickOnce], data files
- data access, ClickOnce applications
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
caps.latest.revision: "15"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: b03083ce6e9fe7fcebdad0b82373bee41221bbb5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>How to: Include a Data File in a ClickOnce Application
每个[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]你安装的应用程序分配应用程序可以在其中管理其自己的数据的目标计算机的本地磁盘上的数据目录。 数据文件可以包含任何类型的文件： 文本文件、 XML 文件或甚至 Microsoft Access 数据库 (.mdb) 文件。 下面的过程演示如何将添加到任何类型的数据文件你[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序。  
  
### <a name="to-include-a-data-file-by-using-mageexe"></a>若要通过使用 Mage.exe 包含的数据文件  
  
1.  将数据文件添加到你的应用程序目录与你的应用程序文件的其余部分。  
  
     通常情况下，你的应用程序目录将标记为部署的当前版本的目录-例如，版本 1.0.0.0。  
  
2.  到列表的数据文件中更新你的应用程序清单。  
  
     **mage-u v1.0.0.0\Application.manifest-FromDirectory 版本 1.0.0.0**  
  
     执行此任务将重新创建你的应用程序清单中的文件列表，并还会自动生成的哈希签名。  
  
3.  在你首选的文本或 XML 编辑器中打开应用程序清单并找到`file`最近添加的文件的元素。  
  
     如果你添加一个名为的 XML 文件`Data.xml`，该文件将类似于下面的代码示例。  
  
 `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  将属性添加`type`到此元素，并将其提供值为`data`。  
  
 `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  通过使用你的密钥对或证书，你应用程序清单进行重新签名，然后重新登录你的部署清单。  
  
     因为应用程序清单其哈希已更改，必须重新登录你的部署清单。  
  
     **mage-s 应用程序清单-cf cert_file-pwd 密码**  
  
     **mage-u 部署清单 appm 应用程序清单**  
  
     **mage-s 部署清单-cf certfile-pwd 密码**  
  
2.  
  
### <a name="to-include-a-data-file-by-using-mageuiexe"></a>若要通过使用 MageUI.exe 包含的数据文件  
  
1.  将数据文件添加到你的应用程序目录与你的应用程序文件的其余部分。  
  
2.  通常情况下，你的应用程序目录将标记为部署的当前版本的目录-例如，版本 1.0.0.0。  
  
3.  上**文件**菜单上，单击**打开**以打开应用程序清单。  
  
4.  选择**文件**选项卡。  
  
5.  在选项卡顶部的文本框中，输入包含你的应用程序文件的目录，然后单击**填充**。  
  
     你的数据文件将显示在网格中。  
  
6.  设置**文件类型**值的数据文件的**数据**。  
  
7.  将应用程序清单中，保存，然后重新对该文件。  
  
     MageUI.exe 将提示你重新对文件进行签名。  
  
8.  部署清单重新签名  
  
     因为应用程序清单其哈希已更改，必须重新登录你的部署清单。  
  
## <a name="see-also"></a>另请参阅  
 [在 ClickOnce 应用程序中访问本地数据和远程数据](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)