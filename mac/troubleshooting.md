---
title: "疑难解答"
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: CE860D79-E29E-4B93-B094-BE74B35FC1C2
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: a820423704b6f656b55b7e33f15d1c7880d2e27d
ms.contentlocale: zh-cn
ms.lasthandoff: 08/11/2017

---

# <a name="troubleshooting"></a>疑难解答

## <a name="viewing-logs-in-visual-studio-for-mac"></a>查看 Visual Studio for Mac 中的日志
 
可通过浏览到“帮助”>“打开日志目录” 菜单项查看日志，如下所示：

![打开日志目录菜单项](media/troubleshooting-image1.png)

## <a name="viewing-exceptions"></a>查看异常

捕获到异常时，会出现一个异常气泡。 若要查看更多详细信息，请选择“查看详细信息” 按钮：

![查看更多关于异常的详细信息](media/troubleshooting-image2.png)

这将显示“显示详细信息”对话框，提供更多关于异常的信息：

![](media/troubleshooting-image3.png)

该对话框的重要部分（上述编号部分）的详细信息如下所示：

1. 异常类型 - 显示观察到的异常类型的全名。
2. 异常消息 - 显示异常对象的消息属性值。
3. 内部异常类型 - 显示内部异常树状视图中当前选中的异常的异常类型的全名。
4. 内部异常消息 - 显示内部异常树状视图中选中的异常的消息属性值。
5. StackTrace 视图。 可通过公开箭头折叠，包含堆栈帧条目。
6. 非用户代码条目的示例。
7. 用户代码条目的示例。
8. 属性视图 - 显示异常的所有属性和字段。 可通过公开箭头折叠。
9. 内部异常树状视图。 通过键盘向上键/向下键或使用鼠标或触控板选择此视图中的内部异常。
10. 默认情况下，此设置与调试程序设置中“调仅试项目代码”选项的设置结果相同。 选择此框将导致所有非用户代码折叠到 StackTrace 中的一行中。
11. 复制按钮 - 将 `exception.ToString()` 输出复制到剪贴板。

请注意某些部分只有在异常属于内部异常时可见。
