---
title: "Visual Studio 中的 IPython REPL | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9bd06b0-2021-4e55-b933-8346476224a8
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
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
translationtype: Human Translation
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: 9c0c0124ed508eff8621f946a40c0dda520bc05b
ms.lasthandoff: 03/10/2017

---

# <a name="using-python-in-the-interactive-window"></a>在交互窗口中使用 Python

IPython 模式下的 Visual Studio 交互窗口是目前非常先进的用户友好交互式开发环境，具有交互式并行计算功能。 本主题介绍如何在 Visual Studio 交互窗口中使用 IPython。 要执行此操作，必须先安装 [Anaconda](https://www.continuum.io) 环境，其中包括 IPython 和必需的库。

> [!Note]
> IronPython 不支持 IPython，但事实上，你可以在交互选项窗体上选择 IPython。 如有需要，可以投票赞成[功能请求](https://github.com/Microsoft/PTVS/issues/84)或实现该请求。

1. 请转到 Python 安装目录，并在 Pylab 模式下启动 IPython，以确保正确安装 IPython 包：

  ```bash
  ipython --pylab
  ```

1. 输入以下内容：

  ```python
  x = linspace(0, 5, 10)
  y = x ** 2
  plot(x, y, 'r')
  ```

1. 如果一切配置正确，应看到类似以下示例的内容：

    ![IPython 配置输出 ](media/ipython-repl-01.png)

1. 打开 Visual Studio，切换到 Python 环境窗口（“视图”>“其他窗口”>“Python 环境”），然后选择 Python 环境。
1. 查看“pip”选项卡，确保列出 `IPython` 和 `matplotlib`。 如果没有，请在此处安装。
1. 选择“概述”选项卡，然后选择“配置交互选项”，将“交互模式”设置为 IPython，然后选择“确定”：

    ![将交互模式设置为 IPython](media/ipython-repl-02.png)

1. 选择“打开交互窗口”，在 IPython 的 PyLab 模式下打开交互窗口。 如果更改了交互模式，可能需要重置窗口：

    ![IPython 模式中的交互窗口](media/ipython-repl-03.png)

1. 输入以下代码：

  ```python
  x = linspace(0, 5, 10)
  y = x ** 2
  plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
  ```

1. 输入最后一行后，应看到一个内联关系图（可根据需要，拖动右下角重设大小）。

    ![交互窗口中的内联关系图](media/ipython-repl-04.png)

1. 可在编辑器中编写代码，然后选中，单击右键，选择“发送到交互”命令（Ctrl-E、E），而无需键入 REPL。 请将以下代码粘贴到编辑器中，使用 Ctrl-A 选中，然后发送到交互窗口。 （请注意，Visual Studio 将代码发送到交互窗口时，会将其作为一个单元发送，以免仅提供关系图的中间部分或其中一部分。）

    ```python
    from mpl_toolkits.mplot3d import Axes3D
    import matplotlib.pyplot as plt
    import numpy as np
    fig = plt.figure()
    ax = fig.add_subplot(111, projection='3d')
    for c, z in zip(['r', 'g', 'b', 'y'], [30, 20, 10, 0]):
        xs = np.arange(20)
        ys = np.random.rand(20)
        # You can provide either a single color or an array. To demonstrate this,
        # the first bar of each set will be colored cyan.
        cs = [c] * len(xs) 
        cs[0] = 'c' 
        ax.bar(xs, ys, zs=z, zdir='y', color=cs, alpha=0.8)

    ax.set_xlabel('X') 
    ax.set_ylabel('Y') 
    ax.set_zlabel('Z') 
    plt.show()
    ```

    ![将代码从编辑器发送到交互窗口](media/ipython-repl-05.png)

1. 若要查看在交互窗口之外的关系图，请运行代码，而不是使用“调试”>“启动但不调试”命令。
    
1. IPython 有很多有用的功能，如转义到系统外壳、变量替换、捕获输出等。有关详细信息，请参阅 IPython 参考指南：

    ![转义到系统外壳](media/ipython-repl-06.png)

1. 你还可以在“笔记本”模式下使用 IPython，以便将任意操作系统上的任意浏览器作为画布使用。 后端 IPython 引擎可以位于计算机本地，也可以位于远程。 Azure 支持[在 Windows 或 Linux VM 上运行 IPython](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-linux-jupyter-notebook)。 有关作为 Azure 服务的免费 Jupyter 笔记本，另请参阅 [Azure 笔记本预览版](https://notebooks.azure.com)：

    ![IPython 笔记本模式](media/ipython-repl-07.png)

