---
title: "帮助查看器疑难解答 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Help Viewer 2.0, 疑难解答"
  - "疑难解答 [Help Viewer 2.0]"
ms.assetid: 461a4553-064a-4142-a2d2-058658b9ba12
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 帮助查看器疑难解答
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主题讨论问题可能会遇到“帮助查看器”。  
  
## 音频不起作用。  
 “帮助查看器”不包含音频播放器。  如果下载的内容包含音频，当点击**“播放”**时但没有播放，请安装音频播放器。  
  
## 搜索功能在 Windows Server 2008、带 SP1 的 Windows Server 2008 或 Windows Server 2008 R2 中不可用。  
 “帮助查看器”中的搜索和筛选功能要求安装并开启 Windows 搜索服务。  默认情况下，此服务在 Windows Server 2008、带 Service Pack 1 \(SP1\) 的 Windows Server 2008 和 Windows Server 2008 R2 中处于关闭状态。  
  
#### 激活 Windows 搜索服务  
  
1.  启动服务器管理器。  
  
2.  在左侧的导航窗格中，单击**“角色”**。  
  
3.  在角色摘要窗格中，单击**“添加角色”**。  
  
4.  选择文件服务角色，然后选择**“下一步”**按钮。  
  
5.  选择 Windows 搜索角色服务。  
  
## 其他资源  
 你可以通过使用以下资源获取更多信息并提供“帮助查看器”上的反馈。  
  
-   要提供反馈，请参见 Microsoft 网站上的 [Microsoft Connect](http://go.microsoft.com/fwlink/?linkid=243983) 或发送电子邮件至 [hlpfdbk@microsoft.com](mailto:hlpfdbk@microsoft.com)。  
  
-   有关详细信息，请参见 [Developer Documentation and Help System](http://go.microsoft.com/fwlink/?LinkId=232741)（开发人员文档和帮助系统）论坛以及 [The Help Guy](http://go.microsoft.com/fwlink/?LinkId=232743)（帮助）博客。  
  
## 请参阅  
 [Help Viewer 2.1 Administrator Guide](http://go.microsoft.com/fwlink/?LinkId=243985)