---
title: "有关依赖项关系图的扩展提供疑难解答 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, extension errors
- dependency diagrams, troubleshooting extensions
ms.assetid: 1fda4f8a-38b8-482b-87b8-eade1a4e5662
caps.latest.revision: 25
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 8f84f22444a5df5b9f4f4af44cd8ee9136403467
ms.openlocfilehash: 26a1992fb9c49c670740a8d4a9a992df3d0a86db
ms.lasthandoff: 02/22/2017

---
# <a name="troubleshoot-extensions-for-dependency-diagrams"></a>有关依赖项关系图的扩展提供疑难解答
本主题解决了你在创建层模型扩展时可能会遇到的一些问题。  
  
#### <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-dependency-diagrams-in-the-experimental-instance-of-includevsprvscode-qualityincludesvsprvsmdmd"></a>当我按 F5 调试我的扩展时，我的命令、 笔势处理程序、 验证扩展或自定义属性不显示在的实验实例中的依赖项关系图[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
  
1.  在的实验实例中打开你的扩展解决方案[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，然后在**生成**菜单上，单击**重新生成解决方案**。  
  
2.  按**F5**或**CTRL + F5**着手的实验实例[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 打开一个依赖项关系图并测试您的扩展。  
  
 如有必要，请继续下一个过程。  
  
#### <a name="an-old-version-of-my-extension-runs"></a>将运行我的旧版本扩展。  
  
1.  请确保没有 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 实验实例正在运行。  
  
2.  删除以下文件夹︰ %LocalAppData%\Microsoft\VisualStudio\\[version] \ComponentModelCache  
  
    > [!NOTE]
    >  %Localappdata%通常是*DriveName*: \Users\\*UserName*\AppData\Local。  
  
 如有必要，请继续下一个过程。  
  
#### <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>将出现旧版本的验证结果，或我的验证方法未被调用。  
  
1.  在实验实例中的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，请在**生成**菜单上，单击**清理解决方案**。 这将清除上一个验证分析缓存的结果。  
  
2.  请确保你的模型中的层与代码元素关联，并且在模型中有至少一个依赖项链接。 如果不存在任何验证内容，则不会调用验证。  
  
3.  常规断点可能在验证方法中不起作用，因为其运行于单独的进程中。 如果你想要逐步执行你的方法，就必须插入一个对 `System.Diagnostics.Debugger.Launch()` 的调用。  
  
4.  在**source.extension.vsixmanifest**在层验证项目中，请确保你已添加了两**MEF 组件**项和一个**自定义扩展类型**下项**内容**。  
  
## <a name="see-also"></a>另请参阅  
 [扩展依赖项关系图](../modeling/extend-layer-diagrams.md)

