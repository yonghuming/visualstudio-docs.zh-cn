---
title: "Visual Studio 中适用于 Python 的 Web 项目模板 | Microsoft Docs"
ms.custom: 
ms.date: 5/8/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 401e7725-8be5-4e67-862c-bf0690a529e3
caps.latest.revision: 11
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 20edb7a53adf400fba94556e659b4215a0060c1b
ms.contentlocale: zh-cn
ms.lasthandoff: 05/10/2017

---

# <a name="python-web-project-templates"></a>Python Web 项目模板

Visual Studio 中对 Python 的支持包括对在 Bottle、Django 和 Flask 等框架中开发 Web 项目的支持。 这包括项目模板和一个可配置来处理不同框架的调试启动程序。 但是，Visual Studio 不包括框架本身，而必须通过右键单击该项目并选择“Python”>“安装/升级框架...”来单独安装。

每个模板（通过“文件”>“新建”>“项目...”访问）在随机选择的本地端口中启动 Web 服务器、调试时打开默认浏览器，并允许直接发布到 [Microsoft Azure](http://www.azure.com)。 提供用于 Bottle、Flask 和 Django 的模板，且你可以对 Pyramid 等其他框架使用常规“Web 项目”模板。

![新建 Web 项目模板](~/docs/python/media/template-web-new-project.png)

每个 Bottle、Flask 和 Django 模板包括一个入门网站，其中包含一些页面和静态文件。 此代码足以本地运行和调试服务器（此情况下某些设置需从环境中获得），且足以部署到 Microsoft Azure（此情况下需要提供 [WSGI 应用](http://www.python.org/dev/peps/pep-3333/)对象）。

从特定于框架的模板创建项目时，将出现一个对话框，有助于使用 pip 安装所需的包。 我们还建议对 Web 项目使用[虚拟环境](python-environments.md#virtual-environments)，以便发布网站时包含正确的依赖关项：

![为项目模板安装所需包的对话框](~/docs/python/media/template-web-requirements-txt-wizard.png)

部署到 Microsoft Azure 应用服务时，需要选择一个 Python 版本作为[站点扩展](https://aka.ms/PythonOnAppService)并手动安装包。 此外，因为 Azure 应用服务从 Visual Studio 部署时**不会**自动安装 `requirements.txt` 中的包，请遵照 [aka.ms/PythonOnAppService](https://aka.ms/PythonOnAppService) 上的配置详细信息操作。

另一方面，Microsoft Azure 云服务支持 `requirements.txt` 文件。 详见 [Azure 云服务项目](template-azure-cloud-service.md)。

有关 Python Web 项目的简介，请参阅 [PTVS 入门第 6 部分：网站](https://youtu.be/FJx5mutt1uk?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)（youtube.com，3m10s）。

> [!VIDEO https://www.youtube.com/embed/FJx5mutt1uk]

## <a name="debugging"></a>调试

启动 Web 项目进行调试时，Visual Studio 在本地启动 Web 服务器，并打开默认浏览器浏览至该地址和端口。 若要指定其他选项，请右键单击项目，选择“属性”和“Web 启动器”选项卡：

  ![常规 Web 模板的 Web 启动器属性](~/docs/python/media/template-web-launcher-properties.png)

在“调试”组中：

- “搜索路径”、“脚本参数”、“解释器参数”和“解释器路径”与用于[普通调试](debugging.md)的相同
- **启动 URL**：指定将在浏览器中打开的 URL。 默认为 `localhost`。
- **端口号**：URL 中未指定端口时使用的端口（默认情况下，Visual Studio 会自动选择一个）。 这允许你替代 `SERVER_PORT` 环境变量的默认值，该变量由模板用来配置本地调试服务器侦听的端口。

“运行服务器命令”和“调试服务器命令”组（后者位于图像中所显示内容的下方）中的属性确定启动 Web 服务器的方式。 由于许多框架需要使用当前项目外的脚本，因此可在此处配置该脚本并将启动模块的名称作为参数进行传递。

- **命令**：可以是 Python 脚本（`*.py` 文件）、模块名称（例如 `python.exe -m module_name`）或一行代码（例如 `python.exe -c "code"`）。 下拉列表中的值表明这些类型中哪些适用。
- **参数**：它们将在命令后的命令行上传递。
- **环境**：指定环境变量的 `NAME=VALUE` 对的新行分隔的列表。 它们在所有可能会修改环境的属性（例如端口号和搜索路径）后进行设定，因此可能会覆盖这些值。

任何项目属性或环境变量都可以使用 MSBuild 语法进行指定，例如：`$(StartupFile) --port $(SERVER_PORT)`。
`$(StartupFile)` 是启动文件的相对路径，`{StartupModule}` 是启动文件的可导入名称。 `$(SERVER_HOST)` 和 `$(SERVER_PORT)` 是普通的环境变量，由“启动 URL”和“端口号”属性自动设定或由“环境”属性设定。

> [!Note]
> “运行服务器命令”中的值通过“调试”>“启动服务器”命令或 Ctrl-F5 使用；“调试服务器命令”组中的值通过“调试”>“启动调试服务器”命令或 F5 使用。


### <a name="sample-bottle-configuration"></a>Bottle 示例配置

Bottle Web 项目模板包括执行必要配置的 Boilerplate 代码。 导入的 Bottle 应用可能不包含此代码，但在这种情况下，以下设置将使用已安装的 `bottle` 模块启动应用：

- **运行服务器命令**组：
    - **命令**：`bottle`（模块）
    - **参数**：`--bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

- **调试服务器命令**组：
    - **命令**：`bottle`（模块）
    - **参数**：`--debug --bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

使用 Visual Studio 进行调试时，不建议使用 `--reload` 选项。

### <a name="sample-pyramid-configuration"></a>Pyramid 示例配置

Pyramid 应用当前最好使用 `pcreate` 命令行工具进行创建。 创建应用后，可使用[基于现有 Python 代码](python-projects.md#creating-a-project-from-existing-files)模板将其导入。 之后，选择“通用 Web 项目”自定义来配置选项。 这些设置假设将 Pyramid 安装到 `..\env` 处的虚拟环境。

- **调试**组：
    - **服务器端口**：6543（或 .ini 文件中配置的任何内容）

- **运行服务器命令**组：
    - 命令：`..\env\scripts\pserve-script.py`（脚本）
    - 参数：`Production.ini`

- **调试服务器命令**组：
    - 命令：`..\env\scripts\pserve-script.py`（脚本）
    - 参数：`Development.ini`

> [!Tip]
> 可能需要配置项目的“工作目录”属性，因为 Pyramid 应用通常比源树顶层要深一个目录层次。


### <a name="other-configurations"></a>其他配置

如果有针对另一个想要共享的框架的设置，或者想要为另一个框架请求设置，请[在 GitHub 上提出问题](https://github.com/Microsoft/PTVS/issues)。

## <a name="publishing-to-azure-app-service"></a>发布到 Azure 应用服务

可使用两种主要方式发布到 Azure 应用服务。 首先，如 [Azure 文档](http://azure.microsoft.com/en-us/documentation/articles/web-sites-publish-source-control/)中所述，源控件中的部署可采用与用于其他语言的相同方式进行使用。 若要直接从 Visual Studio 发布，请右键单击项目并选择“发布”：

![在项目的上下文菜单上发布命令](~/docs/python/media/template-web-publish-command.png)

选择命令后，向导将引导你完成创建网站或导入发布设置、预览修改的文件以及发布到远程服务器。

在应用服务上创建站点时，需要安装 Python 以及站点依赖的任何包。 可以首先发布站点，但它在配置 Python 前不会运行。

若要在应用程序服务上安装 Python，我们建议使用[站点扩展](http://www.siteextensions.net/packages?q=Tags%3A%22python%22) (siteextensions.net)。 它们是 Python [正式发行版](https://www.python.org)的复本，针对 Azure 应用服务进行了优化和重新打包。

可通过 [Azure 门户](https://portal.azure.com/)，使用应用服务的“开发工具”>“扩展”边栏选项卡，选择“添加”并滚动列表查找用于 Python 的扩展来部署站点扩展：

![在 Azure 门户上添加站点扩展](~/docs/python/media/template-web-site-extensions.png)

如果使用 JSON 部署模板，可以将站点扩展指定为站点的资源：

```json
{
    "resources": [
    {
        "apiVersion": "2015-08-01",
        "name": "[parameters('siteName')]",
        "type": "Microsoft.Web/sites",
        ...
    },
    "resources": [
    {
        "apiVersion": "2015-08-01",
        "name": "python352x64",
        "type": "siteextensions",
        "properties": { },
        "dependsOn": [
            "[resourceId('Microsoft.Web/sites', parameters('siteName'))]"
        ]
    },
    ...
}
```

最后，可以通过[开发控制台](https://github.com/projectkudu/kudu/wiki/Kudu-console)登录并从该处安装站点扩展。

目前，推荐在安装站点扩展并直接执行 pip 之后，使用开发控制台来安装包。 务必使用 Python 的完整路径，否则可能会执行错误的路径，且通常无需使用虚拟环境。 例如: 

```
c:\Python35\python.exe -m pip install -r D:\home\site\wwwroot\requirements.txt

c:\Python27\python.exe -m pip install -r D:\home\site\wwwroot\requirements.txt
```

部署到 Azure 应用服务时，站点将在 Microsoft IIS 之后运行。 若要使站点与 IIS 配合使用，至少需要添加一个 `web.config` 文件。 为某些常见部署目标提供有模板，通过右键单击该项目并选择“添加”>“新建项...”提供（请参见以下对话框），并且可以轻松修改它们以作他用。 请参阅 [IIS 配置引用](https://www.iis.net/configreference)，了解可用配置设置的相关信息。

![Azure 项模板](~/docs/python/media/template-web-azure-items.png)

可用的项包括：

- Azure web.config (FastCGI)：应用提供 [WSGI](https://wsgi.readthedocs.io/en/latest/) 对象以处理传入连接时添加 `web.config` 文件。
- Azure web.config (HttpPlatformHandler)：应用侦听传入连接的套接字时添加 `web.config` 文件。
- Azure 静态文件 web.config：当你具有上述任一 `web.config` 文件时，将该项添加到子目录中，使文件不被应用处理。
- Azure 远程调试 web.config：添加通过 Websocket 进行远程调试所必需的文件。
- Web 角色支持文件：包含云服务 Web 角色的默认部署脚本。
- 辅助角色支持文件：包含云服务辅助角色的默认部署和启动脚本。

如果将调试 `web.config` 模板添加到项目和计划以使用 Python 远程调试，需要在“调试”配置中发布站点。 此设置独立于当前的活动解决方案配置，且始终默认为“发布”。 若要更改，请打开“设置”选项卡，使用发布向导中的“配置”组合框（请参阅 [Azure 文档](https://azure.microsoft.com/develop/python/)，了解创建和部署到 Azure Web 应用的详细信息）：

![更改发布配置](~/docs/python/media/template-web-publish-config.png)

“转换为 Microsoft Azure 云服务项目”命令（见下图）会将云服务项目添加到解决方案。 此项目包括要使用的虚拟机和服务的部署设置和配置。 应使用云项目上的“发布”命令部署到云服务；Python 项目上的“发布”命令将仍部署到网站。 请参阅 [Azure 云服务项目](template-azure-cloud-service.md)了解详细信息。

![转换为 Microsoft Azure 云服务项目命令](~/docs/python/media/template-web-convert-menu.png)

