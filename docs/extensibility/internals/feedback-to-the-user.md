---
title: "向用户的反馈 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "用户模型反馈"
  - "环境中上下文"
  - "IDE、 上下文"
  - "IDE 中，用户反馈"
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# 向用户的反馈
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 集成开发环境中 \(IDE\)，有关可用功能的可视反馈根据用户的当前选定内容和全局选择上下文。  下表列出了可用在不同的选择上下文的功能。  
  
|选择上下文|可用的功能|  
|-----------|-----------|  
|IDE|Global|  
|设置的当前产品|产品特殊化|  
|有效的层次结构|层次结构类型特定|  
|有效的层次结构项目|层次结构特定于项目类型的|  
|活动文档|文件类型特定|  
|最顶层请多文档界面 \(mdi\) \(MDI\) 窗口|窗口类型特定|  
|当前选定内容上下文|选择特定于上下文|  
  
 如果只图面功能的用户需求和顺序提供一致的选择和环境上下文反馈，则会降低 IDE 的复杂性。  下列规则适用，只要窗口在 IDE 中打开:  
  
-   如果窗口更改其选择上下文，选择反馈在窗口中清楚地指示，并且，，因此，如果显示，更新动态帮助 " 窗口反映当前上下文。  
  
-   如果窗口更改全局选择上下文，更新所有特定于上下文菜单、有效的层次结构 " 窗口和应用程序的标题栏反映当前上下文。  
  
-   窗口应图面当前选择的属性。 **属性** 窗口和可选的，因此，如果显示， **属性页** 对话框。  
  
-   如果窗口不图面属性或更改全局选择上下文，选择反馈在窗口不应该保持，当不再是在 IDE 中活动窗口。  
  
-   所有文档工具窗口应顺序反映活动文档。  
  
-   菜单、工具栏和应用程序的标题栏应反映最顶层多文档界面 \(mdi\) \(MDI\) 客户端窗口。  
  
 例如，在中，打开后 Web 窗体的 HTML 视图在 Visual Basic Web 应用程序项目中，并且用户选择一 `<td>` 标记，按以下方式提供反馈:  
  
-   选择在活动窗口在 **属性** 窗口指示以及反射。  
  
-   更新文档特定 **工具箱** 反映活动文档。  
  
-   **编辑** 工具栏和 **表** 显示菜单和标题栏更新以反映 Web 窗体窗口。  
  
-   有效的层次结构 " 窗口，通常是 **解决方案资源管理器**和其标题栏更新以反映当前上下文的和上下文相关 **项目** 菜单命令现在应用于活动的 Web 应用程序项目。  
  
## 请参阅  
 [所选内容和在 IDE 中的货币](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [选择上下文对象](../../extensibility/internals/selection-context-objects.md)   
 [层次结构和所选内容](../../extensibility/internals/hierarchies-and-selection.md)