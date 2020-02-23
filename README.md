Gitalk
NPM CDNJS jsdelivr david-dm travis coveralls gzip-size

Gitalk 是一个基于 GitHub Issue 和 Preact 开发的评论插件。

特性
使用 GitHub 登录
支持多语言 [en, zh-CN, zh-TW, es-ES, fr, ru]
支持个人或组织
无干扰模式（设置 distractionFreeMode 为 true 开启）
快捷键提交评论 （cmd|ctrl + enter）
Readme 在线示例

安装
两种方式

直接引入
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.css">
  <script src="https://cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.min.js"></script>

  <!-- or -->

  <link rel="stylesheet" href="https://unpkg.com/gitalk/dist/gitalk.css">
  <script src="https://unpkg.com/gitalk/dist/gitalk.min.js"></script>
npm 安装
npm i --save gitalk
import 'gitalk/dist/gitalk.css'
import Gitalk from 'gitalk'
使用
添加一个容器：

<div id="gitalk-container"></div>
用下面的 Javascript 代码来生成 gitalk 插件：

var gitalk = new Gitalk({
  clientID: 'GitHub Application Client ID',
  clientSecret: 'GitHub Application Client Secret',
  repo: 'GitHub repo',
  owner: 'GitHub repo owner',
  admin: ['GitHub repo owner and collaborators, only these guys can initialize github issues'],
  id: location.pathname,      // Ensure uniqueness and length less than 50
  distractionFreeMode: false  // Facebook-like distraction free mode
})

gitalk.render('gitalk-container')
需要 GitHub Application，如果没有 点击这里申请，Authorization callback URL 填写当前使用插件页面的域名。

在React使用
使用以下代码引入Gitalk组件

import GitalkComponent from "gitalk/dist/gitalk-component";
按以下方式在React中使用Gitalk组件

<GitalkComponent options={{
  clientID: "...",
  // ...
  // 设置项
}} />
设置
clientID String

必须. GitHub Application Client ID.

clientSecret String

必须. GitHub Application Client Secret.

repo String

必须. GitHub repository.

owner String

必须. GitHub repository 所有者，可以是个人或者组织。

admin Array

必须. GitHub repository 的所有者和合作者 (对这个 repository 有写权限的用户)。

id String

Default: location.href.

页面的唯一标识。长度必须小于50。

number Number

Default: -1.

页面的 issue ID 标识，若未定义number属性则会使用id进行定位。

labels Array

Default: ['Gitalk'].

GitHub issue 的标签。

title String

Default: document.title.

GitHub issue 的标题。

body String

Default: location.href + header.meta[description].

GitHub issue 的内容。

language String

Default: navigator.language || navigator.userLanguage.

设置语言，支持 [en, zh-CN, zh-TW]。

perPage Number

Default: 10.

每次加载的数据大小，最多 100。

distractionFreeMode Boolean

Default: false。

类似Facebook评论框的全屏遮罩效果.

pagerDirection String

Default: 'last'

评论排序方式， last为按评论创建时间倒叙，first为按创建时间正序。

createIssueManually Boolean

Default: false.

如果当前页面没有相应的 isssue 且登录的用户属于 admin，则会自动创建 issue。如果设置为 true，则显示一个初始化页面，创建 issue 需要点击 init 按钮。

proxy String

Default: https://cors-anywhere.herokuapp.com/https://github.com/login/oauth/access_token.

GitHub oauth 请求到反向代理，为了支持 CORS。 为什么要这样?

flipMoveOptions Object

Default:

  {
    staggerDelayBy: 150,
    appearAnimation: 'accordionVertical',
    enterAnimation: 'accordionVertical',
    leaveAnimation: 'accordionVertical',
  }
评论列表的动画。 参考

enableHotKey Boolean

Default: true.

启用快捷键(cmd|ctrl + enter) 提交评论.

实例方法
render(String/HTMLElement)

初始化渲染并挂载插件。

TypeScript
已经包括了配置项和Gitalk类的类型定义，不包括React组件的类型定义。

贡献
Fork 代码仓库 并从 master 创建你的分支
如果你添加的代码需要测试，请添加测试！
如果你修改了 API，请更新文档。
确保单元测试通过 (npm test).
确保代码风格一致 (npm run lint).
提交你的代码 (git commit) 提交信息格式参考
类似项目
gitment
vssue
许可
MIT
