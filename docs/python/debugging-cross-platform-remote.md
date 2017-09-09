---
title: "Visual Studio 中的 Python 跨平台远程调试 | Microsoft Docs"
ms.custom: 
ms.date: 7/12/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa667357-763f-4ce6-8e47-48f9337658a8
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: b18efd1fb488c0d07b9a0ffa41f9b4e3613ef17c
ms.contentlocale: zh-cn
ms.lasthandoff: 07/18/2017

---

# <a name="remotely-debugging-python-code-on-linux"></a>在 Linux 上远程调试 Python 代码

Visual Studio 可在 Windows 计算机本地和远程启动和调试 Python 应用程序（请参阅[远程调试](../debugger/remote-debugging.md)）。 它还可使用 [ptvsd 库](https://pypi.python.org/pypi/ptvsd)在其他操作系统、设备或除 CPython 外的 Python 实现中进行远程调试。

使用 ptvsd 时，进行调试的 Python 代码将承载 Visual Studio 可附加到的调试服务器。 此承载要求对代码稍作修改以导入并启用服务器，且可能需要远程计算机上的网络或防火墙配置允许 TCP 连接。

有关远程调试的介绍，请参阅[深入了解：跨平台远程调试](https://youtu.be/y1Qq7BrV6Cc)（youtube.com，6 分 22 秒）。

> [!VIDEO https://www.youtube.com/embed/y1Qq7BrV6Cc]

## <a name="setting-up-a-linux-computer"></a>设置 Linux 计算机

执行本演练需满足以下各项：

- 在操作系统（如 Mac OSX 或 Linux）上运行 Python 的远程计算机。
- 该计算机防火墙上的 5678 端口（入站）处于开启状态，这是远程调试的默认设置。

你可以轻松[在 Azure 中创建 Linux 虚拟机](https://docs.microsoft.com/azure/virtual-machines/linux/creation-choices)，并[使用 Windows 远程桌面访问虚拟机](https://docs.microsoft.com/azure/virtual-machines/linux/use-remote-desktop)。 使用适用于 VM 的 Ubuntu 会非常方便，因为默认安装了 Python；否则，请查看[安装所选的 Python 解释器](python-environments.md#selecting-and-installing-python-interpreters)中的列表，获取有关其他 Python 下载位置的信息。

有关为 Azure VM 创建防火墙规则的详细信息，请参阅[在 Azure 中使用 Azure 门户打开 VM 的端口](https://docs.microsoft.com/azure/virtual-machines/windows/nsg-quickstart-portal)。

## <a name="preparing-the-script-for-debugging"></a>准备调试脚本

1. 在远程计算机上，使用下面的代码创建名为 `guessing-game.py` 的 Python 文件：

  ```python
    import random

    guesses_made = 0
    name = input('Hello! What is your name?\n')
    number = random.randint(1, 20)
    print('Well, {0}, I am thinking of a number between 1 and 20.'.format(name))

    while guesses_made < 6:
    guess = int(input('Take a guess: '))
    guesses_made += 1
    if guess < number:
        print('Your guess is too low.')
    if guess > number:
        print('Your guess is too high.')
    if guess == number:
        break
    if guess == number:
    print('Good job, {0}! You guessed my number in {1} guesses!'.format(name, guesses_made))
    else:
    print('Nope. The number I was thinking of was {0}'.format(number))
  ```
 
1. 使用 `pip3 install ptvsd` 将 `ptvsd` 包安装到环境中。 （请注意：建议记录安装的 ptvsd 版本，以防需要进行故障排除；[ptvsd 列表](https://pypi.python.org/pypi/ptvsd)也显示了可用版本。）

1. 将以下代码添加到 `guessing-game.py` 中其他代码前的最早可能点处，启用远程调试。 （虽然不是严格要求，但不能调试调用 `enable_attach` 函数前生成的任何后台线程。）

   ```python
   import ptvsd
   ptvsd.enable_attach('my_secret')
   ```

   传递给 `enable_attach` 的第一个参数（称为“机密”）会限制对运行中脚本的访问，附加远程调试器时，需要输入该机密。 （虽然不推荐，但是你可以通过使用 `enable_attach(secret=None)` 允许任何人连接。）

1. 保存文件并运行 `python3 guessing-game.py`。 另外，当你与程序进行交互时，对 `enable_attach` 的调用将在后台运行并等待传入连接。 需要时，可在 `enable_attach` 后调用 `wait_for_attach` 函数以阻止程序，直到附加调试器。

> [!Tip]
> 除了 `enable_attach` 和 `wait_for_attach`，ptvsd 还提供了一个帮助程序函数 `break_into_debugger`，如果已附加调试器，它将作为编程断点。 如果已附加调试器，还有返回 `True` 的 `is_attached` 函数（请注意，无需在调用任何其他 `ptvsd` 函数前检查此结果）。

## <a name="attaching-remotely-from-python-tools"></a>从 Python 工具远程附加

在这些步骤中，我们将设置简单断点以停止远程进程。

1. 在本地计算机上创建远程文件的副本，然后在 Visual Studio 中打开它。 文件位置并不重要，但其名称应与远程计算机上的脚本名称匹配。

1. （可选）若要在本地计算机上安装适用于 ptvsd 的 IntelliSense，请将 ptvsd 包安装到 Python 环境中。

1. 选择“调试”>“附加到进程”。

1. 在出现的“附加到进程”对话框中，将“连接类型”设置为“Python 远程(ptvsd)”。 （在旧版本的 Visual Studio 中，这些命令被称为“传输”和“Python 远程调试”。）

1. 在“连接目标”字段（旧版本中为“限定符”）中，输入 `tcp://<secret>@<ip_address>:5678`，其中 `<secret>` 是 Python 代码中传递给 `enable_attach` 的字符串，`<ip_address>` 是远程计算机（可以是显式地址或名称，如 myvm.cloudapp.net），而 `:5678` 是远程调试的端口号。

    > [!Warning]
    > 如果要连接公共 Internet，应改用 `tcps`，并按照以下有关[使用 SSL 保护调试器连接](#securing-the-debugger-connection-with-ssl)的说明操作。

1. 按 Enter 填充该计算机上可用 ptvsd 进程的列表：

    ![输入连接目标并列出进程](media/remote-debugging-qualifier.png)

    如果在填写此列表后碰巧在远程机器上启动了另一个程序，请选择“刷新”按钮。

1. 选择要调试的进程，然后选择“附加”，或双击该进程。

1. Visual Studio 将切换为调试模式，而脚本继续在远程计算机上运行，并提供所有常用[调试](debugging.md)功能。 例如，在 `if guess < number:` 行上设置断点，然后切换到远程计算机上，输入其他猜测。 执行此操作后，本地计算机上的 Visual Studio 将在该断点处停止、显示局部变量等：

    ![触发断点](media/remote-debugging-breakpoint-hit.png)

1. 停止调试后，Visual Studio 将与远程计算机上继续运行的程序分离。 ptvsd 还会继续侦听附加调试器，因此可以随时重新附加到该进程。

### <a name="connection-troubleshooting"></a>连接疑难解答

1. 请确保针对“连接类型”选择“Python 远程(ptvsd)”（在旧版本中，对应为“传输”和“Python 远程调试”。）
1. 检查“连接目标”（或“限定符”）中的机密是否与远程代码中的机密完全匹配。
1. 检查“连接目标”（或“限定符”）中的 IP 地址是否与远程计算机中的 IP 地址相匹配。
1. 检查是否打开了远程计算机上的远程调试端口，并且已在连接目标值中添加了端口后缀，如 `:5678`。
    - 如果需要使用其他端口，可以使用 `address` 参数在 `enable_attach` 调用中指定端口，如 `ptvsd.enable_attach(secret = 'my_secret', address = ('0.0.0.0', 8080))`。 在这种情况下，将在防火墙中打开指定的端口。
1. 检查由 `pip3 list` 返回的远程计算机上安装的 ptvsd 版本是否与下表中 Visual Studio 使用的 Python 工具版本所用的 ptvsd 版本相匹配。 如有必要，请更新远程计算机上的 ptvsd。

    | Visual Studio 版本 | Python 工具/ptvsd 版本 |
    | --- | --- |
    | 2017 | 3.0.0 |
    | 2015 | 2.2.6 |
    | 2013 | 2.2.2 |
    | 2012, 2010 | 2.1 |


## <a name="securing-the-debugger-connection-with-ssl"></a>使用 SSL 保护调试器连接

默认情况下，仅采用机密保护 ptvsd 远程调试服务器的连接，所有数据均以纯文本形式传递。 对于更安全的连接，ptvsd 支持 SSL，可按以下方式进行设置：

1. 在远程计算机上，使用 openssl 生成单独的自签名证书和密钥文件：
    
    ```bash
    openssl req -new -x509 -days 365 -nodes -out cert.cer -keyout cert.key
    ```

    出现提示时，如果是 openssl 提示，请使用主机名或 IP 地址（任选一个用于连接）作为“公用名”。

    （有关详细信息，请参阅 Python `ssl` 模块文档中的[自签名证书](http://docs.python.org/3/library/ssl.html#self-signed-certificates)。 请注意，这些文档中的命令仅生成单个合并文件。）

1. 在代码中，修改对 `enable_attach` 的调用，使其包含 `certfile` 和 `keyfile` 参数（这些参数使用文件名作为值，其含义与标准 `ssl.wrap_socket` Python 函数中的含义相同）：

    ```python
    ptvsd.enable_attach(secret='my_secret', certfile='cert.cer', keyfile='cert.key')
    ```
    
    此外，还可以在本地计算机上的代码文件中进行相同的更改，但由于实际上并不会运行此代码，所以严格上来将，不必进行此更改。    

1. 在远程计算机上重启 Python 程序，使其做好调试准备。

1. 使用 Visual Studio 将证书添加到 Windows 计算机上受信任的根 CA 以保护信道：

    1. 将证书文件从远程计算机复制到本地计算机。
    1. 打开控制面板，导航到“管理工具”>“管理计算机证书”。
    1. 在出现的窗口中，展开左侧的“受信任的根证书颁发机构”，右键单击“证书”，然后选择“所有任务”>“导入...”。
    1. 导航到从远程计算机复制的 `.cer` 文件，并将其选中，然后单击对话框以完成导入。

1. 在 Visual Studio 中重复如前所述的附加进程，现在使用 `tcps://` 作为“连接目标”或（“限定符”）的协议。

    ![选择使用 SSL 进行远程调试传输](media/remote-debugging-qualifier-ssl.png)

### <a name="warnings"></a>警告

使用 SSL 连接时，Visual Studio 将提示潜在的证书问题，如下所述。 可以忽略这些警告并继续操作，但是，虽然信道会加密以防止窃听，该信道仍然可能会受到中间人攻击。

1. 如果看到下面的“远程证书不是受信任的证书”警告，则表示未正确地将证书添加到受信任根 CA。 请检查相关步骤并重试。

    ![SSL 证书信任警告](media/remote-debugging-ssl-warning.png)

1. 如果看到下面的“远程证书名称与主机名不匹配”警告，则表示创建证书时，未使用适当的主机名或 IP 地址作为“公用名”。

    ![SSL 证书主机名警告](media/remote-debugging-ssl-warning2.png)

> [!Warning]
> 目前，如果忽略这些警告，Visual Studio 2017 会挂起。 请务必在尝试连接之前更正所有问题。
