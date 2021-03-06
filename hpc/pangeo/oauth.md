[toc]

# Apps

## Github App

GitHub应用程序代表它自己，通过API直接使用它自己的身份进行操作，这意味着你不需要作为一个单独的用户来维护一个机器人或服务账户。

GitHub应用程序可以直接安装在组织和用户账户上，并被授予访问特定repository的权限。它们带有内置的webhook和狭窄、特定的权限。在设置GitHub应用程序时，可以选择希望它访问的代码仓库。例如，您可以设置一个名为MyGitHub的应用程序，它在octocat仓库中写入issue，并且只在octocat仓库中写入issue。要安装GitHub应用程序，您必须是组织所有者或在仓库中具有管理权限。

默认情况下，只有组织所有者才能管理组织中GitHub应用程序的设置。要允许其他用户管理组织中的GitHub应用程序，所有者可以授予他们GitHub应用程序管理器权限。GitHub应用程序是需要在某处托管的应用程序。

要改进工作流，您可以创建一个包含多个脚本或整个应用程序的GitHub应用程序，然后将该应用程序连接到许多其他工具。例如，您可以将GitHub应用程序连接到GitHub、Slack、您可能拥有的其他内部应用程序、电子邮件程序或其他api。在创建GitHub应用程序时，请记住以下几点:：

- 用户或组织最多可以拥有100个GitHub应用
- GitHub应用应该独立于用户采取行动
- 确保GitHub应用程序与特定的仓库集成
- GitHub应用程序应该连接到一个个人账户或一个组织
- 不要期望GitHub应用知道用户能做的所有事情
- 如果你只需要“使用GitHub登录”服务，就不要使用GitHub应用。但是GitHub应用程序可以使用user identification flow来记录用户并做其他事情
- 如果你只想做GitHub的用户，做所有用户能做的事情，那就不要开发GitHub应用

## OAuth App

 OAuth2是一种协议，它允许外部应用程序在不访问用户的密码的情况下请求授权到用户的GitHub帐户中的私有细节。这比基本身份验证更可取，因为令牌可以限制于特定类型的数据，并且可以由用户在任何时候撤销。

OAuth应用程序使用GitHub作为身份提供程序，对授权访问该应用程序的用户进行身份验证。这意味着，当用户授予OAuth应用程序访问权限时，他们将向其帐户中有权访问的所有仓库授予权限，也向未阻止第三方访问的所属组织授予权限。需要注意一下几点：

- 如果您希望应用程序处理单个仓库，那么不要构建OAuth应用程序。使用repo OAuth作用域，OAuth应用程序可以处理所有经过身份验证的用户的仓库
- 不要构建OAuth应用程序来充当团队或公司的应用程序。OAuth应用程序作为单个用户进行身份验证，因此，如果一个人创建了一个供公司使用的OAuth应用程序，然后离开公司，其他人将无法访问它

创建一个OAuth App：https://developer.github.com/apps/building-oauth-apps/creating-an-oauth-app/