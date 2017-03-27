---
title: "使用针对 Visual Studio 的 Python 工具进行跨平台远程调试 | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa667357-763f-4ce6-8e47-48f9337658a8
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
ms.openlocfilehash: 7634da4bdc2b0186f410acb4eaf57a70ddea3e91
ms.lasthandoff: 03/10/2017

---

# <a name="remotely-debugging-python-code"></a>远程调试 Python 代码

针对 Visual Studio 的 Python 工具 (PTVS) 可在 Windows 计算机本地和远程启动和调试 Python 应用程序（请参阅[远程调试](../debugger/remote-debugging.md)）。 它还可使用 [ptvsd 库](https://pypi.python.org/pypi/ptvsd)在其他操作系统、设备或除 CPython 外的 Python 实现中进行远程调试。

使用 ptvsd 时，进行调试的 Python 代码将承载 Visual Studio 可附加到的调试服务器。 这要求对代码稍作修改以导入并启用服务器，且可能需要远程计算机上的网络或防火墙配置允许 TCP 连接。

有关远程调试的介绍，请参阅[深入了解：跨平台远程调试](https://youtu.be/y1Qq7BrV6Cc)（youtube.com，6 分 22 秒）。

> [!VIDEO https://www.youtube.com/embed/y1Qq7BrV6Cc]

## <a name="preparing-the-script-for-debugging"></a>准备调试脚本

1. 使用下面的代码在远程计算机上创建 Python 文件：

  ```python
  import random

  guesses_made = 0
  name = raw_input('Hello! What is your name?\n')
  number = random.randint(1, 20)
  print 'Well, {0}, I am thinking of a number between 1 and 20.'.format(name)

  while guesses_made < 6:
      guess = int(raw_input('Take a guess: '))
      guesses_made += 1
      if guess < number:
          print 'Your guess is too low.'
      if guess > number:
          print 'Your guess is too high.'
      if guess == number:
          break
  if guess == number:
      print 'Good job, {0}! You guessed my number in {1} guesses!'.format(name, guesses_made)
  else:
      print 'Nope. The number I was thinking of was {0}'.format(number)
  ```
 
1. 使用 `pip install ptvsd` 将 `ptvsd` 包安装到环境中。

1. 通过将以下代码添加到脚本中其他代码前的最早可能点处启用远程调试。 （虽然不是严格要求，但不能调试调用 `enable_attach` 函数前生成的任何后台线程。）

   ```python
   import ptvsd
   ptvsd.enable_attach(secret='my_secret')
   ```

   传递给 `enable_attach` 的 `secret` 参数用于限制对运行中脚本的访问。 附加时，必须在 Visual Studio 指定它，否则将拒绝连接。 若要禁用此功能并允许任何人都可以连接，请使用 `enable_attach(secret=None)`。

1. 保存文件并在远程计算机上启动脚本。 请注意，对 `enable_attach` 的调用在后台运行并等待传入连接。 需要时，可在 `enable_attach` 后调用 `wait_for_attach` 函数以阻止程序，直到附加调试器。

除了 `enable_attach` 和 `wait_for_attach`，ptvsd 还提供了一个帮助程序函数 `break_into_debugger`，如果已附加调试器，它将作为编程断点。 如果已附加调试器，还有返回 `True` 的 `is_attached` 函数（请注意，无需在调用任何其他 `ptvsd` 函数前检查此结果）。

## <a name="attaching-remotely-from-python-tools"></a>从 Python 工具远程附加

在这些步骤中，我们将设置简单断点以停止远程进程。

1. 在本地计算机上创建远程文件的副本，然后在 Visual Studio 中打开它。 文件位置并不重要，但其名称应与将附加到的远程计算机上的脚本名称匹配。

1. 选择“调试”>“附加到进程”以打开“附加到进程”对话框。

1. 将“传输”设为“Python 远程调试”。

1. 在“限定符”字段中输入远程计算机的地址，然后按 Enter。 这样应该会列出该计算机上的可用进程：

![输入限定符并列出进程](media/remote-debugging-qualifier.png)

1. 此阶段的错误通常表示密钥不匹配，`ptvsd` 版本不匹配 PTVS 所用的版本，或者无法建立连接。 连接失败的常见原因之一是远程计算机的防火墙正在阻止打开调试服务器端口（默认值为 5678）。 你可以重新配置防火墙，也可以使用其他端口；通过在 `address` 参数中指定对 `enable_attach` 的调用进行显式指定可以使用其他端口，例如：

  ```python
  ptvsd.enable_attach(secret = 'my_secret', address = ('0.0.0.0', 8080))
  ```

  地址格式与 `AF_INET` 类型的套接字的标准 Python 模块套接字所用的格式相同；有关详细信息，请参阅其[文档](http://docs.python.org/3/library/socket.html#socket-families)。 

1. 进程出现在列表中后，双击它即可附加。 Visual Studio 在脚本继续运行时会打开其调试工具。 对于上面所示的示例脚本，输入数字将导致触发该断点：

    ![触发断点](media/remote-debugging-breakpoint-hit.png)

1. 此时，可以使用所有常用的 PTVS 调试功能。 

1. 停止调试后，Visual Studio 将从你的脚本分离，但该脚本将继续在远程计算机上运行。 调试服务器也将在其后台线程上继续运行，因此稍后可使用相同的步骤重新附加到进程中。


## <a name="securing-the-debugger-connection-with-ssl"></a>使用 SSL 保护调试器连接

默认情况下，未采用任何方式保护 PTVS 远程调试服务器的连接；具有密钥的任何人均可连接，且所有数据均以纯文本形式传递。 因此，网络上的其他人均可以侦听数据甚至执行中间人 (MITM) 攻击。 为了防止在通过不受保护的网络或 Internet 进行调试时发生此攻击，调试服务器需要支持 SSL。 

为了使用 SSL 保护通道，你需要 SSL 证书。 你可以自行生成自签名证书，如 [Python 标准模块文档`ssl`](http://docs.python.org/3/library/ssl.html#self-signed-certificates)中所述。 为了防止 MITM 攻击，此类生成的证书还须添加到运行 PTVS 的 Windows 计算机上的 CA 根存储。 如 [How do I export certificates and/or private keys?](https://answers.microsoft.com/en-us/windows/forum/windows_10-security/how-do-i-export-certificates-andor-private-keys/7722900a-e848-4076-bc50-9e2f5e3c66ac)（我如何导出证书和/或私钥）中所述，通过使用证书管理器 (certmgr.msc) 可实现此操作。 请注意，你需要具有单独的证书文件（未与单个文件中的私钥合并）才能导入。 

生成并注册证书和私钥文件后，需要在脚本中更新对 `enable_attach` 的调用以便于使用。 通过 `certfile` 和 `keyfile` 参数可实现此操作，这些参数具有与标准 Python 函数 `ssl.wrap_socket` 相同的含义。 例如，如果证书文件称为 `my_cert.cer`，则密钥文件称为 `my_cert.key`，使用： 

```python
ptvsd.enable_attach(secret='my_secret', certfile='my_cert.cer', keyfile='my_cert.key')
```

附加过程与前面所述的完全相同，不同之处在于，没有在限定符中使用 `tcp://` 方案，而是使用 `tcps://`： 

![选择使用 SSL 进行远程调试传输](media/remote-debugging-qualifier-ssl.png)

如果没有将证书添加到 CA 的根存储，你将收到一条警告消息： 

![SSL 证书警告](media/remote-debugging-ssl-warning.png)

你可能选择忽略然后继续调试；通道仍将加密以防止窃听，但忽略警告可能导致 MITM 攻击。

