---
title: "如何： 将依赖项添加到 VSIX 包 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d3f3b54e19d8418f35a733b73ea0616b53bd42ce
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>如何： 将依赖项添加到 VSIX 包
你可以将用于安装尚不存在于目标计算机上的任何依赖关系的 VSIX 包部署设置。 若要实现此目的，包括对 source.extension.vsixmanifest 文件中的 VSIX 依赖关系。  
  
#### <a name="to-add-a-dependency"></a>添加依赖关系  
  
1.  打开 source.extension.vsixmanifest 文件中的**设计**视图。 转到**依赖关系**选项卡，单击**新建**。  
  
2.  若要添加已安装的扩展： 在**添加新依赖关系**对话框中，选择**安装扩展**，然后针对**名称**，选择列表中的扩展。  
  
3.  若要添加另一个未安装的 VSIX:: 在**添加新依赖关系**对话框中，选择**文件系统上的文件**，然后使用**浏览**按钮以选择 VSIX。  
  
## <a name="see-also"></a>另请参阅  
 [VSIX 扩展架构 1.0 引用](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [VSIX 包的剖析](../extensibility/anatomy-of-a-vsix-package.md)   
 [准备 Windows Installer 部署的扩展](../extensibility/preparing-extensions-for-windows-installer-deployment.md)