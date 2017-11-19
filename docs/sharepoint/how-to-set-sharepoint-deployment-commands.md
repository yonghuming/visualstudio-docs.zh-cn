---
title: "如何： 设置 SharePoint 部署命令 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, deploying
ms.assetid: 289c8c33-a603-434e-889f-a0d0a1736ecb
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 65c67972dddedcd05338d793883b2dcba0789d48
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>如何：设置 SharePoint 部署命令
  通过设置预先部署脚本和后期部署命令，你可以自定义部署过程。 调试从 Visual Studio 的 SharePoint 解决方案时，这些命令运行之前和之后的其他部署操作。  
  
### <a name="to-add-a-pre-deployment-command"></a>若要添加预先部署命令  
  
1.  在菜单栏上，选择**项目**， *ProjectName***属性**。  
  
2.  选择**SharePoint**选项卡。  
  
3.  在**预先部署命令行**文本框中，输入 MS-DOS 或 MSBuild 命令，以自定义此步骤。  
  
     例如，若要在部署完成之前，请列出目录内容，请输入**dir**。  
  
### <a name="to-add-a-post-deployment-command"></a>若要添加后期部署命令  
  
1.  在菜单栏上，选择**项目**， *ProjectName***属性**。  
  
2.  选择**SharePoint**选项卡。  
  
3.  在**后期部署命令行**文本框中，输入 MS-DOS 或 MSBuild 命令，以自定义此步骤。  
  
     例如，若要列出目录内容部署完成后，输入**dir**。 若要使用 MSBuild 变量的程序集复制从生成目录，输入**复制 $ （targetpath) c:\DeploymentDirectory**。  
  
## <a name="see-also"></a>另请参阅  
 [打包和部署 SharePoint 解决方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  