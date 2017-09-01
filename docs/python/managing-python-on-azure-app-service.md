---
title: "在 Azure App Service 上管理 Python | Microsoft Docs"
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
ms.assetid: e56b5d55-6e6b-48af-af40-5172c768cabc
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: c00adbbabf0d3b82acb17f4a269dfc693246bc69
ms.openlocfilehash: 56fccdd5e103cf29c8ea4a93ab80de7187275642
ms.contentlocale: zh-cn
ms.lasthandoff: 08/01/2017

---

# <a name="managing-python-on-azure-app-service"></a>在 Azure App Service 上管理 Python

[Azure App Service](https://azure.microsoft.com/services/app-service/) 是适用于 Web 应用的平台即服务产品/服务，这些应用包括通过浏览器访问的站点、用户自己的客户端使用的 REST API 或事件触发的处理过程。 应用服务完全支持使用 Python 实现应用。

Azure App Service 上的 Python 支持的提供方式是作为一组应用服务站点扩展来提供，其中每个扩展均包含特定版本的 Python 运行时。 建议使用最新版本的 Python 3，但也可以根据需要选择较旧版本。 本主题说明如何安装和配置站点扩展以及任何所需的包。

> [!Note]
> 本文所述的过程会随时更改，尤其是出于改进目的。 将在 [Microsoft 博客上的 Python 工程](https://blogs.msdn.microsoft.com/pythonengineering/)中发布更改。

## <a name="choosing-a-python-version-through-the-azure-portal"></a>通过 Azure 门户选择 Python 版本

如果站点已部署且正在 Azure App Service 上运行，请导航到“应用服务”边栏选项卡，滚动到“开发工具”部分，然后选择“扩展”>“添加”。 滚动列表，找到适用于所需 Python 版本的特定扩展。 （不足之处是，此列表不可排序，因此不同的版本通常在列表中零散分布：）

![显示 Python 扩展的 Azure 门户](media/python-on-azure-extensions.png)

## <a name="choosing-a-python-version-through-the-azure-resource-manager"></a>通过 Azure 资源管理器选择 Python 版本

如果要使用 Azure 资源管理器模板部署站点，请将站点扩展添加为资源。 此扩展显示为站点的一个嵌套资源，其类型为 `siteextensions`，名称来源于 [siteextensions.net](https://www.siteextensions.net/packages?q=Tags%3A%22python%22)。

例如，添加对 `python361x64` (Python 3.6.1 x64) 的引用后，模板外观可能如下所示：

```json
  "resources": [
    {
      "apiVersion": "2015-08-01",
      "name": "[parameters('siteName')]",
      "type": "Microsoft.Web/sites",
      ...
      "resources": [
        {
          "apiVersion": "2015-08-01",
          "name": "python361x64",
          "type": "siteextensions",
          "properties": { },
          "dependsOn": [
            "[resourceId('Microsoft.Web/sites', parameters('siteName'))]"
          ]
        },
      ...
```

## <a name="configuring-your-site"></a>配置站点

安装站点扩展（通过门户或 Azure 资源管理器模板）后，Python 安装路径将类似于 `d:\home\python361x64\python.exe`。 若要查看具体路径，请在为应用服务显示的列表中选中该扩展，打开其说明页面，其中包含路径：

![Azure App Service 上的扩展列表](media/python-on-azure-extension-list.png)

![Azure App Service 上的扩展详细信息](media/python-on-azure-extension-detail.png)

下一步要为 FastCGI 和 Http 平台请求处理程序引用站点的 `web.config` 文件中的 Python 安装。

### <a name="using-the-fastcgi-handler"></a>使用 FastCGI 处理程序

FastCGI 是在请求级别工作的接口。 IIS 接收传入的连接，并将每个请求转发到在一个或多个持久 Python 进程中运行的 WSGI 应用。 [Wfastcgi 包](https://pypi.io/project/wfastcgi)是使用每个 Python 站点扩展进行预安装和配置的，因此可通过在 `web.config` 中包含以下代码轻松启用此包：

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <appSettings>
    <add key="PYTHONPATH" value="D:\home\site\wwwroot"/>
    <add key="WSGI_HANDLER" value="app.wsgi_app"/>
    <add key="WSGI_LOG" value="D:\home\LogFiles\wfastcgi.log"/>
  </appSettings>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule" scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py" resourceType="Unspecified" requireAccess="Script"/>
    </handlers>
  </system.webServer>
</configuration>
```

`<appSettings>` 可作为环境变量供应用使用：
- `PYTHONPATH` 的值可以自由扩展，但必须包括你的站点的根目录。
- `WSGI_HANDLER` 必须指向可从你的站点导入的 WSGI 应用。
- `WSGI_LOG` 可选，但建议在调试站点时使用。 

在 `<handlers>` 下，请确保 `<add>` 元素中的 `scriptProcessor` 属性包含指向特定安装的正确路径。 此路径同样显示在扩展的详细信息边栏选项卡中。

### <a name="using-the-http-platform-handler"></a>使用 Http 平台处理程序

HttpPlatform 模块将套接字连接直接传递到独立的 Python 进程。 借助此传递可根据需要运行任何 Web 服务器，但需要用于运行本地 Web 服务器的启动脚本。 在 `<httpPlatform>` 元素中指定脚本，其中 `processPath` 属性指向 Python，`arguments` 属性指向脚本和想提供的任何参数：

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="httpPlatformHandler" resourceType="Unspecified"/>
    </handlers>
    <httpPlatform processPath="D:\home\Python361x64\python.exe"
                  arguments="D:\home\site\wwwroot\runserver.py --port %HTTP_PLATFORM_PORT%"
                  stdoutLogEnabled="true"
                  stdoutLogFile="D:\home\LogFiles\python.log"
                  startupTimeLimit="60"
                  processesPerApplication="16">
      <environmentVariables>
        <environmentVariable name="SERVER_PORT" value="%HTTP_PLATFORM_PORT%" />
      </environmentVariables>
    </httpPlatform>
  </system.webServer>
</configuration>
```

当然，配置中指向 `python.exe` 的路径特定于安装的版本。

代码中显示的 `HTTP_PLATFORM_PORT` 环境变量包含本地服务器用来侦听来自 localhost 的连接的端口。 此示例还演示如何根据需要创建其他环境变量，本示例中为 `SERVER_PORT`。

## <a name="installing-packages"></a>安装包

由于应用可能依赖于各种包，因此需要确保通过以下三种方法之一在应用服务上的 Python 环境中安装这些包：

- Azure 门户上的 Azure App Service 控制台
- Kudu REST API
- 将每个库复制到应用源代码

### <a name="kudu-console"></a>Kudu 控制台

使用 [Kudu 控制台](https://github.com/projectkudu/kudu/wiki/Kudu-console)可直接以提升的命令行访问应用服务服务器及其文件系统。 它不仅是重要的调试工具，还可用于基于 CLI 的配置。

从“应用服务”边栏选项卡访问 Kudu，方法是：选择“开发工具”>“高级工具”，然后选择“前往”导航到一个 URL，它与应用服务基 URL 基本相同，只是其中插入了 `.scm`。 例如，如果基 URL 是 `https://vspython-test.azurewebsites.net/`，则 Kudu 位于 `https://vspython-test.scm.azurewebsites.net/`：

![Azure App Service 的 Kudu 控制台](media/python-on-azure-console01.png)

选择“调试控制台”>“CMD”以打开控制台，在其中可导航到 Python 安装，并查看现已有哪些库。

安装单个包：

1. 导航到想在其中安装包的 Python 安装文件夹，如 `d:\home\python361x64`。
1. 使用 `python.exe -m pip install <package_name>` 安装包。

![示例：通过 Azure App Service 的 Kudu 控制台安装 matplotlib](media/python-on-azure-console02.png)

从 `requirements.txt` 安装包（推荐）：

1. 导航到想在其中安装包的 Python 安装文件夹，如 `d:\home\python361x64`。
1. 使用 `python.exe -m pip install --upgrade -r d:\home\site\wwwroot\requirements.txt` 安装包。

建议使用 requirements.txt，因为这样可以轻松在本地和服务器上重新生成完全一样的包集。

> [!Note]
> Web 服务器上没有 C 编译器，因此需要使用本机扩展模块为所有包安装滚轮。 许多常用包本身附带滚轮。 对于不附带滚轮的包，请在本地开发计算机上使用 `pip wheel <package_name>`，然后将滚轮上传到站点。 有关示例，请参阅[管理所需的包](python-environments.md#managing-required-packages)

### <a name="kudu-rest-api"></a>Kudu REST API

将命令发布到 `https://yoursite.scm.azurewebsites.net/api/command`，即可通过 Kudu REST API 远程运行命令，而无需通过 Azure 门户使用 Kudu 控制台。 例如，若要安装 `matplotlib` 包，则需将以下 JSON 发布到 `/api/command`：

```json
{
    "command": 'python.exe -m pip install matplotlib',
    "dir": '\home\python361x64'
}
```

有关命令和身份验证的信息，请参阅 [Kudu 文档](https://github.com/projectkudu/kudu/wiki/REST-API)。 还可以使用 Azure CLI 中的 [`az webapp deployment list-publishing-profiles command`](https://docs.microsoft.com/cli/azure/webapp/deployment#list-publishing-profiles) 查看凭据。 [GitHub 上还提供](https://github.com/lmazuel/azure-webapp-publish/blob/master/azure_webapp_publish/kudu.py#L42)发布 Kudu 命令的帮助程序库。


### <a name="copying-libraries-into-app-source-code"></a>将库复制到应用源代码

可将库复制到自己的源代码中，并将其当作应用的一部分进行部署，而无需直接在服务器上安装包。 此方法可能是有效执行当前部署的最简单方法，具体取决于拥有的依赖项数量及其更新频率。

需要注意的是，这些库必须与服务器上的 Python 版本完全匹配，否则部署后会出现奇怪的错误。 但由于应用服务站点扩展中的 Python 版本与 python.org 上发布的版本完全相同，因此可以轻松获取兼容版本进行本地开发。

### <a name="avoiding-virtual-environments"></a>避免使用虚拟环境

虽然在本地虚拟环境中进行操作有助于全面了解站点所需的依赖项，但不建议在应用服务上使用虚拟环境。 相反，只需将库安装到主 Python 文件夹，然后使用应用部署库即可避免存在冲突依赖项。

