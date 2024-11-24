# 应用开发说明

<p align="center"><b> 中文  </a>  </b></p>

> Serverless Devs 应用开发需要严格遵守 [Serverless Package Model](../../spec/zh/0.0.2/serverless_package_model/readme.md) 中的 [应用模型规范](../../spec/zh/0.0.2/serverless_package_model/3.package_model.md#应用模型规范)。在[应用模型规范](../../spec/zh/0.0.2/serverless_package_model/3.package_model.md#应用模型规范)中有关于[应用模型元数据](../../spec/zh/0.0.2/serverless_package_model/3.package_model.md#应用模型元数据)的说明。

> 使用流水线推荐 使用 GitHub


此时，选择`Application Scaffolding`，并按回车，即可完成一个完整的 Serverless Devs 的 Application 项目的初始化，可以通过命令查看文件树：

```shell script
$ find . -print | sed -e 's;[^/]*/;|____;g;s;____|; |;g'
.
|____readme.md
|____version.md
|____publish.yaml
|____readme_en.md
|____src
| |____s.yaml
| |____code
| | |____index.js
| |____readme.md
```

这其中：

| 目录         | 含义                                                     |
| ------------ | -------------------------------------------------------- |
| readme.md    | 对该组件的描述，或帮助文档信息                           |
| version.md   | 版本的描述，例如当前版本的更新内容等                     |
| publish.yaml | 项目所必须的文件，Serverless Devs Package 的开发识别文档 |
| src          | 应用所在目录，需要包括`s.yaml`和相关的应用代码等         |

此时，开发者可以在 src 下完成应用的开发，并对项目进行`publish.yaml`文件的编写。完成之后，即可通过以下几个步骤发布项目：

- 更改 `publish.yaml` 里的 `Version` 字段。确保版本号比现有最高版本号大 1，例如：1.0.0 -> 1.0.1。

  > 您可以使用固定的 dev 版本用于持续发布测试版本

- 首次发布需要通过 [registry](https://docs.serverless-devs.com/serverless-devs/command/registry) 命令先登录 Serverless Devs Registry。

  ```shell script
  s registry login
  ```

  随后浏览器会跳出登陆窗口，根据提示进行操作即可。

- 后续直接执行 `s registry publish` 即可进行发布

- 测试应用

  如果您使用 dev 版本进行了应用的发布， 假设您的应用名字为 start-application-v3, 那么您可以使用：

  - 本地终端执行: `s init start-application-v3@dev`
  - 浏览器打开: https://fcnext.console.aliyun.com/applications/create?template=start-bitwarden-v3@dev 进行测试
