---
title: 发布 Node.js 包
intro: 您可以将 Node.js 包发布到注册表，作为持续集成 (CI) 工作流程的一部分。
redirect_from:
  - /actions/automating-your-workflow-with-github-actions/publishing-nodejs-packages
  - /actions/language-and-framework-guides/publishing-nodejs-packages
  - /actions/guides/publishing-nodejs-packages
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
type: tutorial
topics:
  - Packaging
  - Publishing
  - Node
  - JavaScript
shortTitle: Node.js packages
ms.openlocfilehash: afa780db8d6c044d57bc2bfdb0a8ca851a32635f
ms.sourcegitcommit: dc42bb4a4826b414751ffa9eed38962c3e3fea8e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2022
ms.locfileid: '147064096'
---
{% data reusables.actions.enterprise-beta %} {% data reusables.actions.enterprise-github-hosted-runners %}

## <a name="introduction"></a>简介

本指南介绍如何创建一个工作流程，以在持续集成 (CI) 测试通过后将 Node.js 包发布到 {% data variables.product.prodname_registry %} 和 npm 注册表。

## <a name="prerequisites"></a>先决条件

建议基本了解工作流程配置选项和如何创建工作流程文件。 有关详细信息，请参阅“[了解 {% data variables.product.prodname_actions %}](/actions/learn-github-actions)”。

有关为 Node.js 项目创建 CI 工作流的详细信息，请参阅“[将 Node.js 与 {% data variables.product.prodname_actions %} 配合使用](/actions/automating-your-workflow-with-github-actions/using-nodejs-with-github-actions)。”

您可能还发现基本了解以下内容是有帮助的：

- “[使用 npm 注册表](/packages/working-with-a-github-packages-registry/working-with-the-npm-registry)”
- “[环境变量](/actions/reference/environment-variables)”
- [加密机密](/actions/reference/encrypted-secrets)
- “[工作流中的身份验证](/actions/reference/authentication-in-a-workflow)”

## <a name="about-package-configuration"></a>关于包配置

 package.json 文件中的 `name` 和 `version` 字段创建一个唯一标识符，注册表使用该标识符将包链接到注册表。 可以通过在 package.json 文件中包含一个 `description` 字段来添加软件包列表页面的摘要。 有关详细信息，请参阅 npm 文档中的“[创建 package.json 文件](https://docs.npmjs.com/creating-a-package-json-file)”和“[创建 Node.js 模块](https://docs.npmjs.com/creating-node-js-modules)”。

当本地 .npmrc 文件存在并指定了 `registry` 值时，`npm publish` 命令使用在 .npmrc 文件中配置的注册表 。 {% data reusables.actions.setup-node-intro %}

可以使用 `setup-node` 操作指定运行器上安装的 Node.js 版本。

如果在工作流中添加步骤来配置 package.json 文件中的 `publishConfig` 字段，则无需使用 `setup-node` 操作指定 registry-url，但是只能将包发布到一个注册表。 有关详细信息，请参阅 npm 文档中的“[publishConfig](https://docs.npmjs.com/files/package.json#publishconfig)”。

## <a name="publishing-packages-to-the-npm-registry"></a>发布包到 npm 注册表

每次创建新版本时，都可以触发工作流程来发布包。 以下示例中的工作流在 `release` 事件以 `created` 类型触发时运行。 如果 CI 测试通过，工作流程将包发布到 npm 注册表。

要根据工作流程中的 npm 注册表执行经过身份验证的操作，您需要将 npm 身份验证令牌作存储为密码。 例如，创建名为 `NPM_TOKEN` 的存储库机密。 有关详细信息，请参阅“[创建和使用已加密的机密](/actions/automating-your-workflow-with-github-actions/creating-and-using-encrypted-secrets)。”

默认情况下，npm 使用 package.json 文件的 `name` 字段来确定已发布包的名称。 当发布到全局命名空间时，您只需要包含包名称。 例如，将名为 `npm-hello-world-test` 的包发布到 `https://www.npmjs.com/package/npm-hello-world-test`。

如果要发布包含范围前缀的包，请在 package.json 文件的名称中包含范围。 例如，如果 npm 范围前缀是 octocat 并且包名称是 hello-world，那么 package.json 文件中的 `name` 应为 `@octocat/hello-world`。 如果 npm 包使用范围前缀并且包是公共的，则需要使用选项 `npm publish --access public`。 这是 npm 需要用来防止有人无意中发布私有包的选项。

此示例将 `NPM_TOKEN` 机密存储在 `NODE_AUTH_TOKEN` 环境变量中。 当 `setup-node` 操作创建 .npmrc 文件时，它会引用来自 `NODE_AUTH_TOKEN` 环境变量的令牌。

```yaml{:copy}
name: Publish Package to npmjs
on:
  release:
    types: [created]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: {% data reusables.actions.action-checkout %}
      # Setup .npmrc file to publish to npm
      - uses: {% data reusables.actions.action-setup-node %}
        with:
          node-version: '16.x'
          registry-url: 'https://registry.npmjs.org'
      - run: npm ci
      - run: npm publish
        env:
          NODE_AUTH_TOKEN: {% raw %}${{ secrets.NPM_TOKEN }}{% endraw %}
```

在上面的示例中，`setup-node` 操作在运行器上创建了一个具有以下内容的 .npmrc 文件：

```ini
//registry.npmjs.org/:_authToken=${NODE_AUTH_TOKEN}
registry=https://registry.npmjs.org/
always-auth=true
```

请注意，需要在 `setup-node` 中将 `registry-url` 设置为 `https://registry.npmjs.org/` 才能正确配置凭据。

## <a name="publishing-packages-to--data-variablesproductprodname_registry-"></a>发布包到 {% data variables.product.prodname_registry %}

每次创建新版本时，都可以触发工作流程来发布包。 以下示例中的工作流在类型为 `created` 的 `release` 事件发生时运行。 如果 CI 测试通过，工作流程会将包发布到 {% data variables.product.prodname_registry %}。

### <a name="configuring-the-destination-repository"></a>配置目标仓库

如果未在 package.json 文件中提供 `repository` 键，则 {% data variables.product.prodname_registry %} 会在 package.json 文件的 `name` 字段中指定的 {% data variables.product.prodname_dotcom %} 存储库中发布一个包 。 例如，名为 `@my-org/test` 的包发布到 `my-org/test` {% data variables.product.prodname_dotcom %} 存储库。

但是，如果提供了 `repository` 键，则该键中的存储库将被用作 {% data variables.product.prodname_registry %} 的目标 npm 注册表。 例如，发布以下 package.json 会导致名为 `my-amazing-package` 的包发布到 `octocat/my-other-repo` {% data variables.product.prodname_dotcom %} 存储库。

```json
{
  "name": "@octocat/my-amazing-package",
  "repository": {
    "type": "git",
    "url": "https://github.com/octocat/my-other-repo.git"
  },
```

### <a name="authenticating-to-the-destination-repository"></a>向目标仓库验证

要在工作流中对 {% data variables.product.prodname_registry %} 注册表执行经过身份验证的操作，可以使用 `GITHUB_TOKEN`。 {% data reusables.actions.github-token-permissions %}

如果要将包发布到其他仓库，您必须使用对目标仓库中的包具有写入权限的个人访问令牌 (PAT)。 有关详细信息，请参阅“[创建个人访问令牌](/github/authenticating-to-github/creating-a-personal-access-token)”和“[加密的机密](/actions/reference/encrypted-secrets)。”

### <a name="example-workflow"></a>示例工作流

此示例将 `GITHUB_TOKEN` 机密存储在 `NODE_AUTH_TOKEN` 环境变量中。 当 `setup-node` 操作创建 .npmrc 文件时，它会引用来自 `NODE_AUTH_TOKEN` 环境变量的令牌。

```yaml{:copy}
name: Publish package to GitHub Packages
on:
  release:
    types: [created]
jobs:
  build:
    runs-on: ubuntu-latest 
    permissions: 
      contents: read
      packages: write 
    steps:
      - uses: {% data reusables.actions.action-checkout %}
      # Setup .npmrc file to publish to GitHub Packages
      - uses: {% data reusables.actions.action-setup-node %}
        with:
          node-version: '16.x'
          registry-url: 'https://npm.pkg.github.com'
          # Defaults to the user or organization that owns the workflow file
          scope: '@octocat'
      - run: npm ci
      - run: npm publish
        env:
          NODE_AUTH_TOKEN: {% raw %}${{ secrets.GITHUB_TOKEN }}{% endraw %}
```

`setup-node` 操作在运行器上创建一个 .npmrc 文件。 当对 `setup-node` 操作使用 `scope` 输入时，.npmrc 文件包含范围前缀。 默认情况下，该 `setup-node` 操作会将 .npmrc 文件中的范围设置为包含该工作流文件的帐户。

```ini
//npm.pkg.github.com/:_authToken=${NODE_AUTH_TOKEN}
@octocat:registry=https://npm.pkg.github.com
always-auth=true
```

## <a name="publishing-packages-using-yarn"></a>使用 yarn 发布包

如果您使用 Yarn 包管理器，可以使用 Yarn 安装和发布包。

```yaml{:copy}
name: Publish Package to npmjs
on:
  release:
    types: [created]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: {% data reusables.actions.action-checkout %}
      # Setup .npmrc file to publish to npm
      - uses: {% data reusables.actions.action-setup-node %}
        with:
          node-version: '16.x'
          registry-url: 'https://registry.npmjs.org'
          # Defaults to the user or organization that owns the workflow file
          scope: '@octocat'
      - run: yarn
      - run: yarn publish
        env:
          NODE_AUTH_TOKEN: {% raw %}${{ secrets.NPM_TOKEN }}{% endraw %}
```
