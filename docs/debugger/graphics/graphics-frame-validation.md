---
title: "图形帧验证 |Microsoft 文档"
ms.custom: 
ms.date: 03/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9312ad8a96c5829aae21c87e78a0d5f2f0db1b35
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="graphics-frame-validation"></a>图形帧验证
<!-- VERSIONLESS -->
Visual Studio 2017 和更好的支持**帧验证**工具。  该框架验证窗口显示错误和警告事件列表与相关联。  若要查看此窗口，请选择**视图 > 帧验证**菜单。

![帧验证](media/gfx_diag_frame_validation.png)

单击**运行验证**按钮，位于左上角来启动分析。  可能需要几分钟才能完成具体取决于框架的复杂性。  它显示下面是组合来自两个源的数据： 消息该 D3D 本身发出时[SDK 层](https://msdn.microsoft.com/library/windows/desktop/ff476881(v=vs.85).aspx)启用时，和从工具自己的内部状态跟踪收集的数据。 完成后，你将看到多个列的数据：

**列**|**描述**
---|---
事件 ID | ID 映射到将项记入[事件列表](graphics-event-list.md)窗口。
严重性 | 损坏、 错误、 警告、 信息或消息。
类别 | 应用程序定义、 杂项、 初始化、 清理、 编译、 状态创建、 状态设置、 状态获取、 执行、 资源操作、 着色器，冗余，和未使用。
消息 | 与事件关联的消息。
Event | 与错误或警告关联的事件。

## <a name="see-also"></a>另请参阅  
[图形诊断 （调试 DirectX 图形）](visual-studio-graphics-diagnostics.md)   
<!-- /VERSIONLESS -->