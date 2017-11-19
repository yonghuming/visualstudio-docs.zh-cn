---
title: "如何： 更新 Visual Studio 扩展 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 098d8ca0d779b7a7877c47125017dd2cd6880445
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="how-to-update-a-visual-studio-extension"></a>如何： 更新 Visual Studio 扩展
可以通过使用你的系统上更新 Visual Studio 扩展**扩展和更新**若要安装的更新的版本。 如果你创建的扩展的更新的版本，你可以将其表示为更新的 VSIX 清单中的版本号递增。  
  
 更新安装时传入的扩展的 VSIX 清单具有相同`ID`以及安装的一个更高`Version`数。 如果`Version`数量是相同或更低时，无法安装此包。 如果`ID`值不匹配、 尚未安装的包被识别为单独的扩展。  
  
 为了帮助在开发过程中防止冲突，我们建议您卸载早期版本的进度中的扩展和也卸载或禁用可能会有冲突的任何其他扩展。  
  
### <a name="to-update-an-extension-on-your-system"></a>若要更新你的系统上的某个扩展  
  
1.  在  “工具”菜单上，单击 “扩展和更新”。  
  
2.  在左窗格中，单击**更新**。  
  
3.  在中间窗格中，单击你想要安装的更新。  
  
     更新扩展的版本号显示在右窗格中，以及其他信息。  
  
4.  在右窗格的底部，单击**更新**。  
  
### <a name="to-publish-an-update-of-an-extension"></a>若要发布的扩展更新  
  
1.  在 Visual Studio 中，打开你想要更新的扩展的解决方案。 进行更改。  
  
    > [!IMPORTANT]
    >  无符号执行不会自动更新所有的用户扩展。 始终应登录你的扩展。  
  
2.  在**解决方案资源管理器**，打开 source.extension.manifest。  
  
3.  在清单设计器中的数字的值增加**版本**字段。  
  
4.  保存解决方案并生成它。  
  
5.  （在项目的 \bin\Debug\ 文件夹） 的新.vsix 文件上载到[Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) Web 站点。  
  
     当有早期版本的扩展的用户打开**扩展和更新**，新的版本将出现在**更新**列表，前提是该工具设置为自动查找更新。  
  
     你可以启用或禁用自动检查更新底部**更新**窗格 (**启用/禁用自动检测可用的更新**)，哪些更改**检查更新**中设置**工具 / 选项 / 环境 / 扩展和更新**。  
  
    > [!NOTE]
    >  从 Visual Studio 2015 Update 2 开始，可以指定（在“工具”/“选项”/“环境”/“扩展和更新”中）是否需要为每用户扩展、所有用户扩展或两者（默认设置）进行自动更新。  
  
## <a name="see-also"></a>另请参阅  
 [VSIX 包的剖析](../extensibility/anatomy-of-a-vsix-package.md)   
 [查找和使用 Visual Studio 扩展](../ide/finding-and-using-visual-studio-extensions.md)
