---
title: "如何： 更改图形诊断播放机 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35b8eb174ea8e0ca238bafe5a05dfbba54855cda
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>如何：更改图形诊断播放机
通过使用本地计算机，或通过使用远程计算机或设备，你可以播放图形信息。  
  
## <a name="choosing-a-playback-machine"></a>选择播放机  
 播放计算机是计算机或用于播放图形日志中的图形事件的设备。 通常情况下，本地计算机是最方便的选项，但具有不同的硬件或驱动程序版本与计算机中捕获它; 计算机上的呈现问题可能不会重现在此情况下，你可以选择更好地再现该问题的远程播放计算机，并仍使用你的开发计算机进行诊断。  
  
#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>若要使用本地计算机来播放图形信息  
  
1.  在图形日志文档窗口上，选择**播放机**链接。 **远程调试器连接**对话框随即出现。  
  
2.  下**手动配置**中**地址**属性，输入`localhost`。  
  
3.  设置**身份验证模式**属性**无**。  
  
4.  选择**选择**按钮。  
  
#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>若要使用远程计算机播放图形信息  
  
1.  在图形日志文档窗口上，选择**播放机**链接。 **远程调试器连接**对话框随即出现。  
  
2.  下**手动配置**中**地址**属性，输入的 Windows 域名或 IP 地址的计算机或你想要用于播放图形信息的设备。  
  
3.  指定你想要用于保护与播放计算机的连接的授权的类型。  
  
    -   对于 Windows 身份验证设置**身份验证模式**属性**Windows**。  
  
    -   不进行身份验证，设置**身份验证模式**属性**无**。  
  
4.  选择**选择**按钮。  
  
> [!NOTE]
>  **远程调试器连接**对话框也可能显示直接连接到你的开发计算机或者位于同一子网上的远程调试目标。 你可以使用这些远程调试目标之一作为图形诊断播放机而无需手动配置它。 在**远程调试器连接**对话框框中，选择你想，然后选择目标**选择**按钮。  
  
## <a name="see-also"></a>另请参阅  
 [图形日志文档](graphics-log-document.md)