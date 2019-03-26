# WEB & Others

#### 谈谈你对 WEB 标准的理解

> WEB 标准不是某一个标准，而是一系列标准的合集。网页主要是由三部分组成：结构，表现和行为。所以相对应的标准也有三种。html,css,js(dom+es)。  
> WEB 标准（结构、表现、行为分离） 
>为了能让web发展的更‘健康’，开发者遵循统一的标准，降低开发难度，开发成本，SEO也会更好做，也不会因为滥用代码导致各种BUG、安全问题，最终提高网站易用性。

- 易于维护：只需要更改 CSS 文件，就可以改  变整站的样式
- 页面响应快：HTML 文件体积变小，响应时间短
- 可访问性：语义化的 HTML 编写的网页文件，更容易被屏幕阅读器识别
- 设备兼容性：不同的样式表可以让网页在不同的设备上呈现不同的样式
- 搜索引擎：语义化的 HTML 更能容易被搜索引擎解析，提升排名

#### 请说说你对 WEB 性能优化的理解

答：1. 从用户角度而言，优化能够让页面加载得更快、对用户的操作响应得更及时，能够给用户提供更为友好的体验。

2. 从服务商角度而言，优化能够减少页面请求数、或者减小请求所占带宽，能够节省可观的源。

   - WEB 性能优化可以从四个方面开始：

     - 内容方面：

       减少 HTTP 请求  
        减少 DOM 元素数量  
        使得 Ajax 可缓存（将获取的结果存入变量或缓存中）

     - 针对 CSS：

       把 CSS 放到代码页上端  
        从页面中剥离 JavaScript 与 CSS  
        精简 JavaScript 与 CSS  
        避免 CSS 表达式（不设置动态的 css 属性）

     - 针对 JavaScript ：

       脚本放到 HTML 代码页底部  
        从页面中剥离 JavaScript 与 CSS  
        精简 JavaScript 与 CSS  
        移除重复脚本

     - 面向图片(Image)：

       优化图片  
        不要在 HTML 中使用缩放图片  
        使用恰当的图片格式（颜色较多使用 JPG，颜色较少使用 PNG 等等）  
        使用 CSS Sprites 技巧对图片优化（精灵图，雪碧图）

#### 浏览器输入网址后的加载过程？

1. 加载过程

- 浏览器根据 DNS 服务器得到域名的 IP 地址
- 向这个 IP 的机器发送 HTTP 请求
- 服务器收到、处理并返回 HTTP 请求
- 浏览器得到返回内容

2. 渲染过程

- 根据 HTML 结构生成 DOM 树
- 根据 CSS 生成 CSSOM
- 将 DOM 和 CSSOM 整合形成 RenderTree
- 根据 RenderTree 开始渲染和展示
- 遇到`<script>`时，会执行并阻塞渲染


#### 如何预防 CSRF 攻击？

答：CSRF(Cross-site request forgery)跨站请求伪造，是一种对网站的恶意攻击。是在受害者毫不知情的情况下，以受害者名义伪造请求发送给受攻击站点，从而在受害者并未授权的情况下执行受害者权限下的各种操作。

CSRF 攻击的原理：

- 攻击的条件
  - 正常网站 A，存在 CSRF 漏洞；恶意网站 B，含有攻击性代码，用来对网站 A 进行攻击。
  - 正常网站 A，有两个用户：user01（受害者）和 user02（攻击者）。
  - user02（攻击者）清楚地了解网站 A，并创建了具有攻击性的网站 B。
  - user01（受害者）登录了网站 A 后，在自身的 session 未失效的情况下，访问了恶意网站 B。

CSRF 攻击的过程：

- 攻击的过程
  - 用户 user01 通过浏览器访问正常网站 A，输入用户名和密码请求登录验证。
  - 登录验证通过后，网站 A 保存 user01 的 session，并将对应的 cookie 返回给 user01 的浏览器。这样， user01 就可以在网站 A 执行自身权限下的各种请求（操作），比如取款、发表文章、发表评论等。
  - 假如， user01 还未退出网站 A，在同一浏览器中，访问了恶意网站 B。
  - 网站 B 是 user02 创建的，user02 清楚地知道网站 A 的工作模式。网站 B 通过攻击性代码访问网站 A（携带的是 user01 的 cookie），执行某些并非 user01 授意的操作。
  - 网站 A 却并不知道这个恶意请求是从网站 B 发出的，因此，就会根据 user01 在网站 A 中具备的相关权限，执行权限下的各种操作。这样，就在 user01 不知情的情况下，user02 假冒 user01，执行了具备 user01 用户身份的操作。

防范 CSRF 的几种策略：

- 验证 HTTP Referer 字段 （根据 HTTP 协议，在 HTTP 头中有一个字段叫 Referer，它记录了该 HTTP 请求的来源地址。）
- 在请求地址中添加 token 并验证
- 在 HTTP 头中自定义属性并验证  

#### 理解 `MVC`, `MVVM`, `Flux` 的区别  

 MVC模式是MVP,MVVM模式的基础，这两种模式更像是MVC模式的优化改良版,他们三个的MV即Model，view相同，不同的是MV之间的纽带部分。
1. MVC：（单向绑定）如果前端没有框架，只使用原生的html+js，MVC模式可以这样理解。将html看成view;js看成controller，负责处理用户与应用的交互，响应对view的操作（对事件的监听），调用Model对数据进行操作，完成model与view的同步（根据model的改变，通过选择器对view进行操作）;将js的ajax当做Model，也就是数据层，通过ajax从服务器获取数据。  

2. MVVM：（双向绑定）MVVM与MVC最大的区别就是：它实现了View和Model的自动同步，也就是当Model的属性改变时，我们不用再自己手动操作Dom元素，来改变View的显示，而是改变属性后该属性对应View层显示会自动改变。  

3. Flux：（数据的单向流动）  
  * 用户访问 View（视图层）
  * View 发出用户的 Action （动作）
  * Dispatcher（派发器） 收到 Action，要求 Store 进行相应的更新
  * Store（数据层） 更新后，发出一个"change"事件
  * View 收到"change"事件后，更新页面  

    ![flux图](./img/flux.png)


