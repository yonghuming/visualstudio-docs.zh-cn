---
title: "项目 &lt;name&gt; 必须转换为当前的项目格式。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.Conversion7"
  - "vs.UpgradeWarningDlg"
ms.assetid: e27d58e5-c270-468b-bb98-3163d40900bc
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 项目 &lt;name&gt; 必须转换为当前的项目格式。
你已打开了在前一个 Visual Studio 版本中创建的项目。 项目文件必须转换为当前格式，才能用你计算机上安装的 Visual Studio 版本打开和编辑项目。 你可以选择是否立即转换此项目。 格式转换不能撤消。  
  
> [!CAUTION]
>  如果项目存储在源代码管理下，而你打算重新签入转换后的项目，请首先确定是否有其他任何解决方案共享此项目。 如果最近转换的项目仍在被其他未转换的解决方案所使用，则不要签入该项目。 否则会中断这些解决方案中的依赖项，使它们不能正确打开或生成。  
  
 你可能希望在转换项目文件前先备份其副本。  
  
> [!NOTE]
>  转换某些项目类型（如 Visual C\+\+ 项目）时，以前的项目文件用文件扩展名“.old”标记并保存在项目目录中。  
  
 不能转换只读项目。 这些项目只能由具有其编辑权限的用户转换。 必须先将项目的项目文件转换为当前格式，然后才能在已转换的解决方案中使用该项目。 转换项目后，就不能再在以前版本的 Visual Studio 中编辑、生成或运行包含该项目的任何解决方案了。  
  
### 响应此消息  
  
1.  选择“是”或“否”。  
  
    -   “是”\- 如果项目是可编辑的，那么它会转换为你计算机上所安装的 Visual Studio 版本使用的格式。 如果已转换的项目存储在源代码管理下，它将被签出到本地驱动器并打开以进行编辑。  
  
    -   “否”\- 项目不会进行转换，它不会从源代码管理中签出，且不会打开。  
  
 如果你是开发团队的成员，应确保从事项目开发的所有人员在他们的本地计算机上安装相同版本的 Visual Studio。 为确保项目保持可访问状态，请定期与开发团队的其他成员进行沟通。  
  
## 请参阅  
 [Project Dependencies Dialog Box](http://msdn.microsoft.com/zh-cn/d66e48c3-3722-40dd-99b4-53d93cac128e)   
 [在 Visual Studio 中构建应用程序](../ide/compiling-and-building-in-visual-studio.md)