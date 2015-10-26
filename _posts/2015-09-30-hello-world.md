

The Definitive Ionic Starter Guide
Ionic入门权威指南

[Ionic][1] is a powerful tool for building mobile apps using HTML, CSS, and JavaScript. This starter guide focuses on getting up and running with a realistic mobile app and learning about the primary features of Ionic. You will see many features of Ionic with a complete app example. You will end this guide with a strong command of Ionic and how it enables you to build beautiful, functional mobile apps.
[Ionic][1] 对于用 HTML、CSS 和 JavaScript 构建移动 APP 是一个强大的工具。本教程将以完成一个实际的完整移动 APP 的过程为例，讲授 ionic 的主要特性。最终，你将很好地掌握 ionic，从而构建漂亮而功能丰富的移动 APP。

Ionic is build on Angular and I will assume you are at least moderately familiar with Angular and the basics of web applications. If you need some help with Angular, I recommend reading up from Todd Motto's post [AngularJS Tutorial: A Comprehensive 10,000 Word Guide][2]. It is also assumed you have NodeJS installed.
Ionic 是基于 Angular 框架的，本教程针对熟悉 Angular 并且有一定 Web 应用开发基础的人员。如果你需要了解Angular相关知识，推荐你阅读Todd Motto的文章 [《AngularJS Tutorial: A Comprehensive 10,000 Word Guide》][2]，该文章假设读者已有NodeJS的相关知识。

During this guide you will learn how to build a stock tracking app. You can [preview the completed app here][3] and see the whole project on GitHub at [gnomeontherun/ionic-definitive-guide][4]. You can resize the browser to see how it would appear on mobile, or if you are using Chrome you can use the [device emulator feature][5].
在本教程中你将会学习如何构建一个股票报价应用。你可以在 [这里预览完整地应用][3]，并且可以在GitHub工程  [gnomeontherun/ionic-definitive-guide][4] 看到整个项目的源码。你可以通过改变浏览器的大小或者使用 Chrome 浏览器的 [模拟设备特性][5] 提前看看这个应用在移动设备上的表现。

## Ionic, the missing hybrid app SDK
Ionic，期盼已久的混合应用开发SDK

Ionic is built for [hybrid apps][6], which are mobile apps that are written with HTML, CSS, and JavaScript instead of the native platform languages (Java for Android, Swift for iOS). When building a native app, you have access to the SDK which includes interface components such as [tabs][7] and [complex lists][8]. These are the interface controls that you are familiar with from using mobile apps, and Ionic provides a comprehensive set of components for building hybrid apps.
Ionic 是用来构建使用 HTML、CSS 和 JavaScript 开发的 [混合应用][6] 的，而不是原生语言（安卓使用Java语言，iOS使用Swift语言）。开发原生应用的时候，可以 使用带有界面组件的 SDK，比如 [标签页][7] 和 [复合列表][8]。这些都是使用移动应用熟悉的界面控件，而 Ionic 正提供了一整套控件去构建混合移动应用。

However, Ionic is really more than just interface components. It also:

* provides a fantastic CLI utility for managing projects.
* leverages SASS to easily customize components.
* is built and maintained by a professional team, with a strong community behind it.
* incorporates a pluggable architecture for including 'ions' (additional components and features).
* has a large set of icons.

然而，Ionic绝不仅仅只是一些界面组件。它还：

* 提供强大的命令行工具去管理项目。
* 通过使用 SASS 技术，便捷地定制化用户界面。
* 由专业团队发起和维护，有强大的社区支持。
* 集成了灵活的“ ions ”结构（额外的组件和功能）。
* 包含一整套图标。

In addition, Ionic has a whole platform of services to support your apps, such as [Creator][9] for a visual drag/drop design experience, [View][10] for sharing a preview/beta version of your app with anyone, and [Push][11] for easily setting up push notifications. Recently added were [Deploy][12] and [Analytics][13] which are currently in alpha. You can expect Ionic to expand into a complete platform to serve the needs of app developers.
另外，Ionic 有一整个完整的服务平台来支持移动应用的开发，比如 [Creator][9] 提供了可视化拖拽/拖放设计模式，[View][10] 可以发布APP预览/测试版本给大众，[Push][11] 可以十分简便的添加推送消息通知。最近，Ionic增加了 [Deploy][12] 和 [Analytics][13]，目前还在内部测试阶段。你完全可以认为 Ionic 一个能够提供给 APP 开发人员完整服务功能的平台。

## Setup for Ionic
安装Ionic

First things first, we need to get Ionic setup. For this tutorial we will be previewing in a browser, not on a mobile device (though you could if you follow the [Ionic guide][14] for details on emulating and loading to a device). You need to have [Node][15] installed on your system before you can install Ionic (Note: io.js may not work properly). Run this command in the terminal/command line prompt:
首先，我们需要安装 Ionic。在本教程中，我们将会在浏览器里预览，而不是在移动设备上（不过你可以根据 [Ionic 开发文档][14] 上的详细步骤，在移动设备上运行程序）。在安装Ionic之前，你的系统需要安装  [Node][15]。（注意：io.js 可能运行不正确）。在命令行终端运行以下命令：

    $ npm install -g ionic
    
Here the Node Package Manager (NPM) will download and install the Ionic CLI. This is essential for building Ionic apps, and we'll use it to setup, preview, and build our app. Let's cover the primary types of features in Ionic.
这里，Node 包管理器（ NPM ）会下载并安装 Ionic 命令行工具。它是构建 Ionic 应用的基础，并且我们后面还会用来创建、预览、构建应用。现在，我们来浏览Ionic的几个主要特性。

## Ionic components & services
Ionic components & services

Before we jump into building our app, I wanted to give you a quick overview of Ionic's primary features. Ionic provides two primary features: components and services.
在构建我们自己的APP之前，我们将会快速浏览Ionic的主要特性。Inoic 提供了两个主要特性：components 和 services。

### Ionic Components
Ionic Components

Components are the user interface elements you declare using markup and CSS classes such as tabs, headers, slideshows, side menus, and more. These components either just CSS classes (like CSS frameworks like Bootstrap) or Angular directives. Some of the CSS components (`input`, `card`, `button`) don't provide additional features, but Ionic provides nicer styling that works well on mobile. The directive components (`sidemenu`, `list`, `slidebox`) are available as HTML tags. 
Components 是使用标签和 CSS 类标识的用户界面元素，比如标签页、标题栏、幻灯片、侧滑菜单等等。这些组件要么是 CSS 类（比如 CSS 框架 Bootstrap ），要么使用 Angular 指令实现。一些 CSS 组件（`input`、`card`、`button`）没有提供额外的功能，但是 Ionic 提供了更好的样式展现使其能在移动设备上表现的更好。指令组件（`sidemenu`、`list`、`slidebox`）是可以像 HTML 标签一样使用的。


    <!-- Card: CSS Component Example -->
    <div class="list card">
      <div class="item">Basic card!</div>
    </div>
    
    <!-- SlideBox: Directive Component Example -->
    <ion-slide-box slide-interval="10000" does-continue="true">
      <ion-slide>Slide 1</ion-slide>
      <ion-slide>Slide 2</ion-slide>
    </ion-slide-box>

In the two examples above, the first is a visual card like you might see in many apps like Google Now. It is created simply by using the CSS classes. The second is a slide box, which is a directive and declared using HTML tags. The slide box example could also include attributes, like `slide-interval` which provide configuration to the slide box (in this case sets the length of time for each slide to display).
在上面的两个例子中，第一个是现在在很多 google 应用中可以看到的卡片效果。仅仅是用 CSS 类就可以将样式做出效果。第二个是一个滑动框，用指令和 HTML 标签配合实现。在侧滑框的例子中还包括了一些属性，比如 `slide-interval` 指定了滑动框的配置（在这个例子中指定了每个滑动框展示的时间间隔）。

### Ionic Services
Ionic Services

Services are programmatic user interface elements that are declared in JavaScript, and are provided using Angular's services architecture. These are typically used in your controllers, and provide interface elements that have a limited display time (such as modals, popups, loaders). Just like Angular services, Ionic services all start with a `$` and are very clearly named like you see in this example.
Services 是在 JavaScript 中声明来操作用户界面元素的，通过了 Angular 的 Service 结构来提供。通常用在控制器中，提供有显示时间限制的界面元素（比如弹出窗口、弹出对话框、进度条）。就和 Angular 的 services 一样，Ionic 的 services 全部以 `$` 开头，而且在下面的例子中，你可以看到 services 都是根据功能来准确地命名。


    function Controller($scope, $ionicSlideBoxDelegate) {
      $scope.next = function() {
        $ionicSlideBoxDelegate.next();
      }
      $scope.previous = function() {
        $ionicSlideBoxDelegate.previous();
      }
    }

In this controller, there are two scope methods that control the slide box using the service (any services that manage a component are delegate services). This would allow any custom button to change the slide, such as these two buttons.
在这个控制器中，作用域下有两个方法使用 service 来控制滑动框（任何管理组件的 services 都叫做代理 services ）。这样开发人员就可以让任意的按钮去更改滑动框中的内容，比如下面两个按钮。

    <button ng-click="next()">Next</button>
    <button ng-click="previous()">Previous</button>

Other services create a new visual experience, such as the loader. These will inject content into the current view as needed to create the desired effect, in this case a loading screen will overlay with a message, and after 2 seconds it will automatically hide.
其他的 services 可以用来创建一个新的可视化的内容，比如加载提示框。这将在当前视图中注入需要添加的内容以创建所需的效果，在这个例子中我们添加了一个覆盖整个屏幕的加载提示信息，并在2秒钟之后自动隐藏。

    function Controller($timeout, $ionicLoading) {
      $ionicLoading.show({
        template: 'Loading'
      });
      $timeout(function() {
        $ionicLoading.hide();
      }, 2000);
    }

Now let's get a new project started and see these things in action. If at any point you want to see the entire codebase, check out the [gnomeontherun/ionic-definitive-guide][16] GitHub project.
现在，我们就来创建一个工程，然后动手实践这些内容。如果任何时候你想查看工程源码，都可以去 GitHub 上查看 [gnomeontherun/ionic-definitive-guide][17]。

## Starting the Ionic project
新建一个Ionic工程

Let the fun begin! The first thing is to generate a new project. The Ionic CLI we installed before will help us do this.
让我们愉快地开始吧！第一件事就是新建一个工程。我们之前安装的 Ionic 命令行工具就可以派上用场了。

    $ ionic start stocks https://github.com/ionic-in-action/starter
    
    $ cd stocks
    
    $ ionic serve

This will create a new blank app called `stocks` based on the starter app I created for my book [Ionic in Action][18]. This starter app is blank, and is ideal for new projects. The `ionic serve` command should have opened up the new app in your browser, and it will be just a blank page. Have no fear, we shall fix that now.
这个命令可以创建一个空白的叫做 `stocks` 的 APP  工程，基于我在我的书 [《动手学习Ionic》][18] 中创建的 starter APP 工程。这个空白的 starter APP 对于新建工程是个理想的选择。`ionic serve` 命令可以在浏览器中打开刚刚新建的 app，但它仅仅是一个空白的页面。不要担心，我们现在就来把它补充完整。

## Setting up Sass for styling
安装 Sass 做样式

Ionic comes with a very helpful feature for customizing the default components and color presets using [Sass][19]. It is also recommended that you write any custom styles in the same way to take advantage of the variables and auto-generation provided by Ionic.
Ionic 一个十分有用的特性就是可以使用 [Sass][20] 定制化默认组件和预制颜色。官方推荐你以同样地方式利用 Ionic 提供的变量和自动生成器写你自己的样式表。

Sass support is not enabled by default in a new project. The following command will setup your project with Sass support.
新工程不会默认支持 Sass。运行一以下命令，可以让工程支持 Sass。

    $ ionic setup sass

This command will generate a new CSS file based on the the scss/ionic.app.scss file, and output it to css/ionic.app.css. Then it will update the index.html file to load the new CSS file instead. Lastly, it enables Ionic commands to automatically regenerate the styles when you build the app, so you can't forget.
这行命令将会根据 scss/ionic.app.scss 文件生成一个新的 CSS 文件，放在 css/ionic.app.css。然后 index.html 会加重新生成的 CSS 文件。最后，当你构建 app 的时候，它会使 Ionic 命令自动生成样式文件，所以你一定要记住这一点。

This app needs some styling, so you'll need to replace the contents of scss/ionic.app.scss file with the following.
我们教程中的 app 需要一些样式，所以你需要把 scss/ionic.app.scss 中内容改为以下内容。

    // Override variables
    $light: #eee;
    
    $lighter: #fff;
    
    $darker: #363636;
    
    $assertive: #B33F33;
    
    $balanced: #70AB23;
    
    $positive: #366091;
    
    // The path for our ionicons font files, relative to the built CSS in www/css
    $ionicons-font-path: "../lib/ionic/fonts" !default;
    
    // Include all of Ionic
    @import "www/lib/ionic/scss/ionic";
    
    // Dark theme for backgrounds.
    .view, .pane, .modal {
      background: $darker;
    }
    
    // Style the form inside of the footer bar
    .bar-search {
      padding: 0;
    
      form {
        display: block;
        width: 100%;
      }
    
      .item {
        padding: 3.75px 10px;
      }
    }
    
    // Make the item-dark style default by extending it back on top of item
    .item {
      @extend .item-dark;
    }
    
    //
    .item-reorder .button.icon {
      color: $light;
    }
    
    // Make inputs nicer on dark
    .item-input {
    
      input {
        margin-right: 30px;
        padding-left: 5px;
        background: $darker;
        color: $light;
      }
      .input-label {
        color: $light;
      }
    }
    .item-input-wrapper {
      background: $darker;
    
      input {
        color: $lighter;
      }
    }
    
    // Make toggler nicer on dark
    .toggle .track {
      background-color: $dark;
      border-color: $darker;
    }
    .toggle input:checked + .track {
      background-color: $positive;
      border-color: $positive;
    }
    
    // Remove a bottom border
    .tabs-striped .tabs {
      border-bottom: 0;
    }
    
    // Allow the tabs to be as wide as needed
    .tab-item {
      max-width: none;
    }
    
    // Styles for the quote component
    .quote {
      background: $darker;
      padding: 5px;
      border-radius: 4px;
      display: block;
      position: absolute;
      top: 1px;
      right: 16px;
      text-align: center;
      width: 90px;
      height: 50px;
      color: $lighter;
    
      .spinner svg {
        margin-top: 6px;
      }
    
      &.positive {
        background: $balanced;
        color: $light;
      }
    
      &.negative {
        background: $assertive;
        color: $light;
      }
    
      .quote-change {
        font-size: 0.8em;
        color: $light;
      }
    }

At the top of these styles, several of the Ionic variables are overridden with some custom colors (so it doesn't appear with the same colors as default Ionic). The rest of the styles are commented, and it will be easier to review all of the styles when the app is completed.
在这个样式文件最上面，是用自定义的颜色重写了 Ionic 变量（我们的应用的不会出现和 Ionic 默认样式一样的颜色）。样式文件空白处都添加了注释，当我们完成了这个 app，再回过头来看会更容易。

This will setup all of the styles for the app. It is best to start a project setting up Sass in your project at the start, though you can do it anytime. Next you will start getting the base navigation setup.
这将会建立 app 全部的样式文件。尽管在项目任何阶段都可以构建 Sass，但是最好在项目开始时就以这一步开始。接下来，将会开始建立起页面导航的基础。

## Add Ionic's navigation components
添加 Ionic 的页面导航组件

Navigation is core to all apps, and Ionic provides several components that can be useful for navigation. In this example, you will use the `ionTabs` and `ionNavViewcomponents` to have tabs at the bottom to navigate between views. The `ionSideMenuscomponent` is often used as well to expose a list of links for navigation.
导航是所有 app 的核心，Ionic 提供了一些功能强大的 components 用来导航。在本例中，你将会使用到 `ionTabs` 和 `ionNavView` components 去生成页面底部的标签页，实现不同页面的之间的导航。而 `ionSideMenus` component 通常用来展示一组可以导航的链接。

Ionic is built using the popular ui-router project, which is an enhanced replacement for Angular's core ngRoute component. Ionic adds another layer of enhancements on top of ui-router, which is baked into the Ionic components and services. It leverages the idea of declaring states, which is a place in the app that describes the associated controller, view, template, and possibly other details. It will become more clear as we see some examples.
Ionic 使用了目前流行的 ui-router 项目做路由，它比 Angular 内核自带的 ngRouter 功能更强大。Ionic 在 ui-router 基础上封装了一项增强功能，就是将其放入 Ionic 的 components 和 services 中。这决定了根据 states 确定路由的方式，它是一个在 app 中描述了如何将控制器、视图、模板和一些其他细节联系以来的地方。这一点我们看过一些例子之后会更加清楚。

The `ionNavView` component is typically the center of an Ionic app's navigation, and works with several other components to allow you to craft intuitive navigation. Open up the www/index.html file, and update the body of the HTML file with the following.
`ionNavView` component 通常位于 Ionic app 导航的中心位置，通过和一些其他组件配合工作，可以让你手动直观地实现导航。打开 www/index.html 文件，将 body 标签下的内容修改为以下内容。

    <body ng-app="App">
      <!-- The ionNavBar updates the title and buttons as the application state changes -->
      <ion-nav-bar class="bar-positive">
        <!-- The ionNavBackButton knows when to show or hide based on current state -->
        <ion-nav-back-button></ion-nav-back-button>
      </ion-nav-bar>
      <!-- Primary ionNavView which will load the views -->
      <ion-nav-view></ion-nav-view>
    </body>

Here you see three components,`ionNavView, ionNavBar`, and `ionNavBackButton`. The `ionNavBar` will contain our header content, such as the `ionNavBackButton` and a title of the state. Navbars are very common in apps, and it will automatically update the title as the user navigates between views, and conditionally show the `ionNavBackButton` when a user is allowed to go back in the history.
这里我们看到了三个 components，`ionNavView`, `ionNavBar` 和 `ionNavBackButton`。`ionNavBar` 包含了页面顶部内容，比如 `ionNavBackButton` 返回按钮和 state 标题。导航栏在 app 中是很常见的，用户在不同视图间导航时，它能够自动更新标题，并且在用户可以返回历史页面的时候显示返回按钮。

Now if you save these changes and look at the browser, you'll now see a blue navbar along the top. The `ionNavBar`  is gray by default, but with the class `bar-positive` added it adopts a new color. There is a set of color presets that many components can adopt, and you'll see them sprinkled in throughout the example.
现在如果你保存了这些更改，返回看浏览器，会回看到一个蓝色的导航条在页面顶部。`ionNavBar` 默认是灰色的，但是我们通过增加 `bar-positive` 类选择器，它采用了另一种颜色。这里有一系列预制颜色供不同的组件使用，并且你会在整个例子中看到它们。

This app isn't very impressive yet, because we haven't defined any states to actually load (hence the blank screen). Let's get the first state setup.
这个例子目前还是不能使用的，因为我们还没有定义任何 states 去实际加载内容（因此是一个空白页面）。让我们来建立第一个 state 吧！

## Add the tabs state
添加标签页 state

It is time to add the tabs state's template. You will declare the template which will contain the tabs component with two tabs for the `tabs.quotes`  and `tabs.portfolio`  states. You'll need to create a new file at www/views/tabs/tabs.html and add the following markup.
现在我们来添加标签页 state 的模板。你需要定义模板，包含了标签页 component   `tabs.quotes` 和 `tabs.portfolio` 两种 states。你需要创建文件 www/views/tabs/tabs.html，并加入下面的代码。

    <!-- ionTabs wraps the ionTab directives -->
    <ion-tabs class="tabs-icon-top tabs-dark tabs-striped">
      <!-- Quotes tab -->
      <ion-tab title="Quotes" icon-on="ion-ios-pulse-strong" icon-off="ion-ios-pulse" ui-sref="tabs.quotes">
        <!-- ionNavView for the quotes tab -->
        <ion-nav-view name="quotes"></ion-nav-view>
      </ion-tab>
      <!-- Portfolio tab -->
      <ion-tab title="Portfolio" icon-on="ion-ios-paper" icon-off="ion-ios-paper-outline" ui-sref="tabs.portfolio">
        <!-- ionNavView for the portfolio tab -->
        <ion-nav-view name="portfolio"></ion-nav-view>
      </ion-tab>
    </ion-tabs>

Here the `ionTabs` component contains two `ionTab` components, which will display two tabs. The attributes declare icons for when the tab is active and inactive, as well as a link to a particular state using the `ui-sref` attribute. Inside of each `ionTab` are `ionNavView` components, which must have a name. You can only have on  `ionNavView` that is unnamed, and that is in the index.html (which acts as the default).
这里的 `ionTabs` 包括两个 `ionTab` components，这样将会显示两个标签。属性声明了当前tab页面展示选中和不选中的图标样式，`ui-sref` 属性表示它将链接到某个页面。每个 `ionTab` 里包含了一个 `ionNavView` component，它必须有名字。只可以有一个 `ionNavView` 可以没有名字，他就是在 index.html 中的那个（默认展示的）。

Later, when you create the tab states you will declare the states to match these specific `ionNavViews`. This is done so that each tab can have its own, independent navigation history, which will be demonstrated in depth later.
接下来，当你创建完标签，就需要定义 states 分别去匹配这几个页面。这样做可以使每一个标签有自己独立的导航历史，这点在以后会有更进一步的展示。

Now create www/views/tabs/tabs.js and add the following JavaScript that declares the 'tabs' state. Be sure to also add a script tag to the index.html file after the app.js file to load this file.
现在来创建文件 www/views/tabs/tabs.js，并加入下面的 JavaScript 代码，其中定义了 “tabs” state。

    angular.module('App')
    
    .config(function($stateProvider) {
      $stateProvider
        .state('tabs', {
          abstract: true,
          url: '/tabs',
          templateUrl: 'views/tabs/tabs.html'
        });
    });

The `tabs` view is `abstract`, which is unique to properly support nested `ionNavView` components like you see inside of the tabs. This simply means you will never go directly to just the `tabs` state, but in fact you will always go to a child state. Or in other words, it means you always go directly to one of the two tabs because it doesn't make sense to navigate to the tabs without one of them being selected.
`tabs` 是 `abstract`（抽象）的，就像你在标签中看到的，它是唯一支持嵌套的`ionNavView` components。这意味着你永远不能直接跳转到 `tabs`  state，但是事实上你一直在它的子页面 state 下。换句话说，这表示你总是会直接跳转到两个tab页下的某一个，因为只有选中某个导航标签才是有意义的。

Sadly, yet again, the screen is blank. Remember, the tabs view is `abstract`  so you can only see it when you navigate to a child tab state. That means the next step is to create the first child tab state, so the tabs will appear and some very interesting things will start to happen.
可是到目前为止，屏幕上还是空白的。记住，`tabs` state 设置为 `abstract`，所以只有当它导航至子页面 state 中你才能看到界面。这意味着下一步我们要创建第一个子页面 state，那么我们就可以看到tab页面和一些非常有意思的事情发生了。

## Add the services
添加services

But wait! You will need some Angular services to help manage data for this app, and I don't want to spend a lot of time on them. You can look through the comments to see how they work, and they should be familiar to Angular developers. The first is a simple service to help manage data in localStorage, and the second is a service to load stock quotes from Yahoo! Finance. If you are not familiar with Angular and creating services, it is best to take a moment and review the [Angular services documentation][21].
但是，等等！你需要一些 Angular services 知识来帮助管理这个 app，而这里我不打算花太多时间在这上面。你可以浏览注释看它们是怎么工作的，从事 Angular 的开发人员应该是非常熟悉的。第一个 service 是用来管理 localStorage 中的数据，第二个 service 是用来从雅虎金融加载股票报价数据的。如果你不熟悉 Angular 或怎样创建 service ，最好花一些时间看看 Angular service 的文档说明。

First create the file www/js/localstorage.js with the content in the code below. Be sure to add a script tag to index.html.
首先创建文件 www/js/localstorage.js，并添加以下代码。一定要在 index.html 引用这个文件。

    angular.module('App')
    .factory('LocalStorageService', function() {
      // Helper methods to manage an array of data through localstorage
      return {
        // This pulls out an item from localstorage and tries to parse it as JSON strings
        get: function LocalStorageServiceGet(key, defaultValue) {
          var stored = localStorage.getItem(key);
          try {
            stored = angular.fromJson(stored);
          } catch(error) {
            stored = null;
          }
          if (defaultValue && stored === null) {
            stored = defaultValue;
          }
          return stored;
        },
        // This stores data into localstorage, but converts values to a JSON string first
        update: function LocalStorageServiceUpdate(key, value) {
          if (value) {
            localStorage.setItem(key, angular.toJson(value));
          }
        },
        // This will remove a key from localstorage
        clear: function LocalStorageServiceClear(key) {
          localStorage.removeItem(key);
        }
      };
    });

Now create another file at www/js/quotes.js with the following code. Again, make sure to add a script tag to the index.html.
现在来创建另一个文件 www/js/quotes.js，并添加以下代码。再一次声明，一定要在 index.html 文件中对这个文件添加引用。

    angular.module('App')
    
    .factory('QuotesService', function($q, $http) {
      // Create a quotes service to simplify how to load data from Yahoo Finance
      var QuotesService = {};
      QuotesService.get = function(symbols) {
        // Convert the symbols array into the format required for YQL
        symbols = symbols.map(function(symbol) {
          return "'" + symbol.toUpperCase() + "'";
        });
        // Create a new deferred object
        var defer = $q.defer();
        // Make the http request
        $http.get('https://query.yahooapis.com/v1/public/yql?q=select * from yahoo.finance.quotes where symbol in (' + symbols.join(',') + ')&format=json&env=http://datatables.org/alltables.env').success(function(quotes) {
          // The API is funny, if only one result is returned it is an object, multiple results are an array. This forces it to be an array for consistency
          if (quotes.query.count === 1) {
            quotes.query.results.quote = [quotes.query.results.quote];
          }
          // Resolve the promise with the data
          defer.resolve(quotes.query.results.quote);
        }).error(function(error) {
          // If an error occurs, reject the promise with the error
          defer.reject(error);
        });
        // Return the promise
        return defer.promise;
      };
    
      return QuotesService;
    });

Ok, now it is time to create the quotes state, which leverages these two services.
好了，现在是时候创建使用了上面的两个 services 的 quotes state 了。

## Add the quotes state
添加 quotes state

It's time to jump into high gear. The quotes tab is able to display a list of stocks that you wish to follow, show details about the current bids, allow you to lookup new quotes and add them, and even sort the list. This is an awful lot of functionality, but only requires about 30 lines of HTML and about 70 lines of JavaScript.
是时候更进一步了。quotes 页面用来展示你要关注的股票列表，显示当前报价的细节，查找别的股票报价并添加他们，还可以进行排序。这看上去有很多复杂的功能，但是只需要 30 行 Html 代码和 70 行 JavaScript 代码。

You'll first add all of the code for this state, and then we'll review how each part works individually. Create a new file at www/views/quotes/quotes.html and add the following markup.
首先你需要添加这个 state 下的所有代码，然后我们回过头来分别看看每个部分是如何工作的。创建一个新文件 www/views/quotes/quotes.html， 添加以下的代码。

    <ion-view view-title="Market Quotes">
      <!-- Add a nav button to the primary location -->
      <ion-nav-buttons side="primary">
        <button class="button button-clear" ng-click="state.reorder = !state.reorder">Reorder</button>
      </ion-nav-buttons>
      <!-- ionContent is used to wrap scrollable content -->
      <ion-content>
        <!-- ionRefresher activates when the user pulls down and calls getQuotes() -->
        <ion-refresher on-refresh="getQuotes()"></ion-refresher>
        <!-- ionList allows us to make a complex list with swipe buttons, reordering, and more -->
        <ion-list show-reorder="state.reorder">
          <!-- Repeat over each quote, to display the current details and name -->
          <ion-item ng-repeat="stock in quotes" class="item-dark">
            <div class="quote" ng-class="quoteClass(stock)">
              <div class="quote-price">{{stock.LastTradePriceOnly | currency:'$'}}</div>
              <div class="quote-change">{{stock.Change}}</div>
            </div>
            {{stock.symbol}}
            <!-- Option and reorder button for list items -->
            <ion-option-button class="button-assertive" ng-click="remove($index)">Remove</ion-option-button>
            <ion-reorder-button class="ion-navicon" on-reorder="reorder(stock, $fromIndex, $toIndex)">
          </ion-item>
        </ion-list>
      </ion-content>
      <!-- Footer sits above the tabs and sticks -->
      <ion-footer-bar class="bar-search">
        <!-- Form to input a quote to add to the list -->
        <form ng-submit="add()" class="list">
          <div class="item item-input-inset">
              <label class="item-input-wrapper">
                <input type="search" placeholder="Symbol" ng-model="form.query">
              </label>
              <input type="submit" class="button button-small button-positive" value="Add" />
          </div>
        </form>
      </ion-footer-bar>
    </ion-view>

Now create another file at www/views/quotes/quotes.js and add the following JavaScript. Also be sure to add the script tag to this file in the www/index.html file.
现在创建文件 www/views/quotes/quotes.js 并且添加以下 JavaScript 代码。同样地，要在 www/index.html 文件中加入引用的 script 标签。

    angular.module('App')
    
    .config(function($stateProvider) {
      // Declare the state for the quotes, with the template and controller
      $stateProvider
        .state('tabs.quotes', {
          url: '/quotes',
          views: {
            quotes: {
              controller: 'QuotesController',
              templateUrl: 'views/quotes/quotes.html'
            }
          }
        });
    })
    
    .controller('QuotesController', function($scope, $ionicPopup, $ionicLoading, LocalStorageService, QuotesService) {
    
      // Get symbols from localstorage, set default values
      $scope.symbols = LocalStorageService.get('quotes', ['YHOO', 'AAPL', 'GOOG', 'MSFT', 'FB', 'TWTR']);
      $scope.form = {
        query: ''
      };
      $scope.state = {
        reorder: false
      };
      // Function to update the symbols in localstorage
      function updateSymbols() {
        var symbols = [];
        angular.forEach($scope.quotes, function(stock) {
          symbols.push(stock.Symbol);
        });
        $scope.symbols = symbols;
        LocalStorageService.update('quotes', symbols);
      }
      // Method to handle reordering of items in the list
      $scope.reorder = function(stock, $fromIndex, $toIndex) {
        $scope.quotes.splice($fromIndex, 1);
        $scope.quotes.splice($toIndex, 0, stock);
        updateSymbols();
      };
      // Method to load quotes, or show an alert on error, and finally close the loader
      $scope.getQuotes = function() {
        QuotesService.get($scope.symbols).then(function(quotes) {
          $scope.quotes = quotes;
        }, function(error) {
          $ionicPopup.alert({
            template: 'Could not load quotes right now. Please try again later.'
          });
        }).finally(function() {
          $ionicLoading.hide();
          $scope.$broadcast('scroll.refreshComplete');
        });
      };
      // Method to load a quote's data and add it to the list, or show alert for not found
      $scope.add = function() {
        if ($scope.form.query) {
          QuotesService.get([$scope.form.query]).then(function(results) {
            if (results[0].Name) {
              $scope.symbols.push($scope.form.query);
              $scope.quotes.push(results[0]);
              $scope.form.query = '';
              updateSymbols();
            } else {
              $ionicPopup.alert({
                title: 'Could not locate symbol.'
              });
            }
          });
        }
      };
      // Method to remove a quote from the list
      $scope.remove = function($index) {
        $scope.symbols.splice($index, 1);
        $scope.quotes.splice($index, 1);
        updateSymbols();
      };
      // Method to give a class based on the quote price vs closing
      $scope.quoteClass = function(quote) {
        if (quote.PreviousClose < quote.LastTradePriceOnly) {
          return 'positive';
        }
        if (quote.PreviousClose > quote.LastTradePriceOnly) {
          return 'negative';
        }
        return '';
      };
      // Start by showing the loader the first time, and request the quotes
      $ionicLoading.show();
      $scope.getQuotes();
    });

At this point, if `ionic serve` is still running your app should be loaded in the browser. Go to  [http://localhost:8100/#/tabs/quote][22]  and this new view will appear with the list of current stock quotes.
现在，如果 `ionic serve` 还在运行，那么刚才修改的文件在浏览器中已经可以看到效果了。在浏览器输入 http://localhost:8100/#/tabs/quote ，这个带有股票报价列表的新页面就会显示出来。

If you look at the controller, you will see that there are a number of methods that you might see in any Angular app, such as the `quoteClass()` method which determines if the quote box should be green or red or `getQuotes()` which handles the loading of data. Several methods will be called by Ionic components, such as `remove()` and `reorder()` by the Ionic List component.
如果你看了控制器的代码，会看到里面有很多方法，你可能在其他任何 Angular app 中看到，比如 `quoteClass()` 这个方法决定了报价框的颜色是绿色还是红色的，`getQuotes()` 这个方法加载了数据进来。一些方法被 Ionic components 调用，比如 Ionic 列表 component 的 `remove()` 和 `reorder()`。

Now let's take a look at the Ionic components and services that make this view work.
现在，我们一起来看看让这个页面工作起来的 Ionic components 和 service。

### Ionic View, Nav Buttons, and Content Components
Ionic 视图，导航按钮和内容 Components

The foundation of our view is the `ionView` component, which is used to wrap a template. The `view-title` attribute allows the view to set the title in the `ionNavBar`, and other attributes are available to control other aspects of the navbar (such as if the view should be cached or if it should show the back button). Every view will have the `ionView` component wrapping the rest of the content.
视图的基础就是可以包含模板的 `ionView` component。它的 `view-title` 属性可以页面标题栏上添加标题，其他的属性用来控制标题栏的其他的属性（比如视图是否需要缓存，是否需要显示返回按钮）。每个视图都需要 `ionView` 组件包含其内容。

Inside of the `ionView` is the `ionNavButtons` component. This will add buttons to the navbar when this view is active, and you are able to declare which side they appear. In this example, it use `side="primary"` which allows the buttons to be placed on the primary location for buttons based on the platform. In iOS that is on the left, and for Android that is right, and demonstrates how Ionic has many features that are 'platform aware'. This button uses the `ngClick` directive to run an expression, which will be covered in the list component.
`ionView` 里包含了有 `ionNavButtons` component。当这个页面显示的时候，就会在标题栏上添加一些按钮，并且你可以定义它在标题栏的哪边显示。在这个例子中，使用了  `side="primary"` 让按钮放在与原生平台相应地的位置。在 iOS 平台就是在左边，但是在 Android 平台就是在右边，这也证实了 Ionic 的许多特性是平台相关的。这个作用于列表 component 的按钮使用了 `ngClick` 指令去运行表达式。

Then you see the `ionContent` component. Think of this as the content wrapper, and it has a number of benefits.
你可以看到 `ionContent` component。它除了可以包含内容在里面，还有以下几个优点。

1.	It sizes the content area to the available space.
2.	It automatically ensures content will scroll vertically if it is taller than the viewport.
3.	It is aware of other components, such as the navbar, tabs, and footer, and will resize to allow room for those components.
4.	It allows the Ionic Refresher component to work seemlessly with your content.
5.	It is very configurable, and allows you to set values for features such as padding, scrolling direction, scroll locking.
1. 它可以根据可用的空间的大小排列内容。
2. 如果要显示的内容高度超过了可视范围，它自动保证内容可以在垂直方向上滚动查看。
3. 它可以监视其他控件的存在，比如标题栏、标签页、页底，并且可以根据这些控件重新排列要显示的内容。
4. 它允许 Ionic 刷新 component 去完美的展示内容。
5. 它是可配置的，允许你去设置一些属性值，比如内边距、滚动方向或是否禁止滚动。

You will use `ionContent` to wrap your content in most of your views, and most of the time with only the default settings.
在大部分页面中，你需要使用 `ionContent` 包含你的内容，并且大部分时候只需要默认的设置。

These several components work together to provide the primary container structure for our view, and you'll see them again in the next view since they are quite common.
这些 components 协同工作，为我们的页面提供主要的容器结构，在后面的视图中你还会看到他们，因为他们相当常见。

### Ionic Loading Service
Ionic 加载 service

The Ionic Loading service overlays the screen with a configurable loading message until the content has loaded, so it prevents the user from interacting with the view until its ready. From a usability perspective, this should be reserved for when the interface can only work once data has loaded. In this example, it only will appear the first time the app has to load the data.
Ionic 加载 service 用一个可以配置加载消息的界面覆盖了整个屏幕，直到页面内容加载完才消失，所以这保证了直到页面加载完用户才可以看到。从可用性的角度来说，在只有数据加载完页面才可以使用的情况下，这中做法是必要的。在这个例子中，只有 app 第一次加载数据的时候才会出现加载页面。

When the controller is first loaded, the `$ionicLoading.show()` method is called. This triggers the loading indicator to appear, and it will remain until the `$ionicLoading.hide()` method is called. Right after the  `show()` method, the controller call `$scope.getQuotes()` which handles loading the data. You can see the `hide()` is called in the `finally()` promise callback to hide the loader after the data request has finished.
当控制器第一次加载的时候，`$ionicLoading.show()` 方法被调用。它触发了加载进度条出现，一直到 `$ionicLoading.hide()` 这个方法被调用加载进度条才会消失。就在 `show()` 方法后面，控制器调用了 `$scope.getQuotes()` 来加载数据。你可以看到在数据请求完成之后， `hide()` 方法在 `finally()` 的 promise 中被调用，以隐藏加载进度条。 

You might think the loader could auto hide when the data has loaded, but the loader requires you to call the `hide()` method because it cannot know exactly when everything is ready for the view. The loader is also like a singleton, meaning there is only ever one loader on the screen. If you call `show()` multiple times, it will still only take one call the `hide()` to hide it.
你可能会想，加载显示器应该在数据加载完之后自动隐藏起来，但是加载显示器需要你去调用 `hide()` 方法，这是因为它并不能准确地知道什么时候页面需要的一切都准备好去显示了。加载显示器就像是一个独行侠，仅仅表示这里有一个在屏幕上显示的加载提示。即便你多次调用 `show()` 方法，也只需要调用一次 `hide()` 来隐藏它。

### Ionic Refresher Component
Ionic 刷新 Component

The Ionic Refresher is a component you put inside of a view that allows the user to pull down to refresh the view. As the user pulls down, an icon slides down and if they pull far enough and let go it triggers the refresh. You've likely seen this in many apps that allow you to reload the data, such as an app showing sports scores or (like this example) stock quotes. It is a common pattern that uses the pull down gesture instead of a button.
Ionic Refresher 是一个在页面内部可以容用户下拉刷新整个页面的 component。当用户下拉时，一个向下箭头出现，如果你下拉足够距离再放开的话，就会触发刷新。你可能会在很多app中看到这样的效果以重新加载数据，比如一个显示运动得分的应用，或者（像本例一样）股票报价。使用下拉手势而不是一个按钮去刷新是一种常见的设计模式。

The component is just a directive called `ionRefresher`, and has a single attribute `on-refresh` that accepts an expression to evaluate when the user releases the pull. In this case, it calls the `getQuotes()` method, which reloads the data and update the view. Similarly to the Loading service, we use the `finally()` callback to broadcast an event `$scope.$broadcast('scroll.refreshComplete');` that will tell the Refresher the reload is complete and to hide itself.
这个 component 是一个叫做 `ionRefresher` 的指令，它只有一个属性 `on-refresh` 可以接受一个表达式，当用户释放下拉的时候执行。在这个例子中，它调用了 `getQuotes()` 方法，去加载数据并更新视图。同样地在加载的 service 时，我们使用 `finally()` 回调去广播事件  `$scope.$broadcast('scroll.refreshComplete');` 这将会通知 Refersher ，重新加载已经完成了，要隐藏自己。

The primary key to making the Refresher component work is to ensure that you have a single scope method that (re)loads the data in the view. Since the Refresher is a component and not a service (like the Loader), it listens for the `scroll.refreshComplete` event to know when to hide. If you forget to call this, the Refresher will display forever.
让刷新 component 正常工作的关键是要确保有一个独立的作用域方法去（重新）加载视图中的数据。因为 Refresher 是一个 component 而不是 service（像加载器那样），他会监听 `scroll.refreshComplete` 事件从而得知什么时候应该隐藏。如果你忘记了调用，那刷新控件将会一直显示。

### Ionic Popup Service
Ionic Popup service

The Ionic Popup service is used to display an overlay for the user to acknowledge or interact with. It will block the current view and overlay a box with a message and button. There are several built in types of popups and you can also build your own.
Ionic Popup（弹出窗口） service 用于展示信息或者和用户交互。他将会暂停当前的视图，显示一个带有提示信息和按钮的对话框。这里有几种类型的弹出框，你也可以构建自己的弹出框。

* Alert: Shows a simple message and button to clear. Useful to inform users of something such as an error.
* 警告：显示提示信息和关闭提示的按钮。用来提示用户一些信息，比如错误提示。
* Confirm: Shows a simple message and two buttons to either confirm or cancel. Useful to confirm an action such as deleting an item.
* 确认框：显示提示信息和确认、取消两个按钮。用于确认一个行为，比如是否删除一个列表项。
* Prompt: Shows a simple message, an input field, and an OK and Cancel button. Useful when you need additional details, such as a password.
* 提示框：显示提示信息、输入框、确定和取消按钮。用于当你需要更多地细节信息的时候，比如密码。

The Popup service is `$ionicPopup` and when you create one of the types of a popup it is returned as a promise. When you create a new popup, it will appear and you use the promise API to handle the callback when a button is selected. It is also possible to programmatically close the popup using the `close()` method.
Popup service 用 `$ionicPopup` 显示，当你创建某种类型的弹出框时，它会返回一个 promise。你一旦创建一个新弹出框，它就会显示并且当它的某个按钮被选择的时候，你需要用 promise 模式的 API 去处理结果。也可以在程序中调用 `close()` 方法来关闭弹出框。

In this view, the Popup service is used to help alert to errors in loading data. In the `getQuotes()`  method, if the request promise is resolved with an error it will alert that it could not load the quotes. Likewise, when the user tries to add a quote that doesn't exist, it will alert that the symbol was not found. In this example you are not waiting for the popup promise to be resolved (with the alert is closed), it simply just closes and allows the user to continue using the app.
在这个例子中，Popup service 用于提示用户加载数据时出错了。在 `getQuotes()` 这个方法中，如果请求的 promise 返回结果是错误，它就会警告这里不能够加载股票信息。同样地，当用户视图去加载不存在的股票报价时，它会警告该代码没有找到。在这个例子中，你不需要等待弹出框的 promise 被执行了（警告框被关闭的时候），它仅仅是被关闭了，并且用户可以继续使用这个应用。

Popups can be easily abused from a usability standpoint. Much like an alert/confirm window you see in JavaScript, it blocks the interface and requires the user to interact to continue. Using Popups should be limited to situations when the user needs to acknowledge or respond to the Popup to continue. You could argue that this example could use a different method to give feedback to the user.
根据可用性的观点，弹出框很容易被滥用。很多你在 JavaScript 代码中看到的警告框或者确认框，他阻断了界面并且需要用户交互使其继续下去。应该限制在一些情景下使用弹出框，当用户需要确认或者回应弹出框以继续使用 app。你应该可以指出，这个例子可以使用不同的方法去给予用户反馈。

### Ionic List Component
Ionic List Component

The Ionic List component is a powerful user interface component, which is really a combination of several different directives that work together. Lists are a very common and clean way to display content, as mobile content has limited space. Android and iOS have introduced many features to lists that users have become accustomed to using, such as the ability to reorder items, swiping to show additional buttons, and deleting items. So much of the data shown in apps are really just lists, such as lists of news articles, emails, locations visited, and more.
Ionic List（列表） Component 是强大的用于界面显示的 component，它实际上是一些不同的指令共同起作用的结果。由于移动设备空间有限，列表是一种常见且整齐的展示内容的方式。 Android 和 iOS 已经介绍了很多用户已经习惯使用的列表特性，比如可以给列表项排序，滑动显示更多按钮，以及删除列表项。在应用程序中，大量的数据都是通过列表显示的，比如新闻文章列表、邮件列表、轨迹定位列表等等。

In this app, the List component supports reordering and deleting of items. The `ionList` component is used to wrap the `ionItem` components. The `ionItem`s have a `ngRepeat`  so it will display the entire list of quotes that are stored (or the default list from the localStorage service). Then, each `ionItem` displays the quote and price.
在这个应用中，列表 component 支持排序和删除列表项。`ionList` 控件包括了若干个 `ionItem` 控件。 `ionItems` 使用了 `ngRepeat` 指令，它会显示存储的全部股票报价（或者默认是从  localStorage service 中获取的列表）。然后，每个 `ionItem` 都会显示出一支股票报价和价格。

The `ionList` has several attributes that control when the list is in a 'reorder' mode, which is a boolean that is evaluated. The `ionItem` contains a `ionReorderButton` to power this feature. When the `state.reorder` model is true, the reorder button (which is a stacked three lines icon) will slide into view and allow you to tap and drag the list items. When the item is released, it will call the `reorder()` method that was declared by the `on-reorder`  attribute. It passes three items, the item, the index value of the item originally, and the new index after it was released. The `reorder()` method takes these values and moves the item in the `$scope.quote` array.
当 `ionList` 处于重新排序的模式下，有几个布尔型的的属性值可以控制它的行为。`ionItem` 包含了一个 `ionReorderButton` 按钮去增强这个功能。当 `state.reorder` model 为真时，排序按钮（有三个横线排列起来的）将会滑入列表并且你可以选中并拖拽某个列表项。当你释放列表项的时候，它会根据属性 `on-reorder` 的定义去调用 `reorder()` 方法。它有三个参数，当前列表项、列表项原来的序列号和排序后列表项的序列号。`reorder()` 方法得到这些值然后移动数据项，给 `$scope.quote` 数组中排好序。

The last feature is the `ionOptionButton`, which is a button that appears when the user swipes left on an item. This option button is designed to act like a delete button, so if the user taps on the button it will call the `remove()` method to remove that item from the list. You could make buttons for other purposes, such as to edit or share an item.
最后要说的一个特性就是  `ionOptionButton`，当用户左划列表项时，在列表上会出现的一个按钮。这个选项按钮被设计成一个删除按钮的样式，所以如果用户点击了它，它会调用 `remove()` 方法去删除列表中的这一项。你也可以让这个按钮实现别的功能，比如编辑或者分享一个列表项。

Ionic Lists are quite powerful, and very intuitive for users to manage lists. They are used so often, I would even suggest you can't use it too often. Anything that is a collection of items is probably ideal for a list. Ionic Lists can also be styled in many ways with default Ionic CSS classes, found in the documentation. Some common styles include lists with an avatar or icon to the side, large images like cover art, or cards style that modifies the entire list to have a similar card feel like you see in Google Now or Tinder style apps.
Ionic List 是一个功能强大，对用户友好的列表管理组件。使用它们是常事，我还是要提醒你不要过度滥用它。任何元素的集合都能够以列表作为理想选择。在文档中可以看到，Ionic 列表可以使用 Ionic 默认的 CSS 类设计成不同的样式。一些公共的样式包括旁边有头像或图标的列表，像封面大图那样，或者把整个列表修改成卡片样式的，就像 Google Now 和 Tinder 应用的风格一样。

### Ionic Footer Bar and Form
Ionic 底部工具栏和表单

The Ionic Footer Bar is a way to display text or simple content at the bottom of the view. It automatically positions based on the other components, was discussed earlier with `ionContent`. It does need to be outside of th  `ionContent` to position correctly, just like the  `ionNavButtons`.
Ionic 底部工具栏是在页面底部显示文本和简单内容的一种方式。它自动显示在其他控件的底部，比如我们之前讨论过的 `ionContent`。他确实需要正确地显示在 `ionContent` 外面，就像 `ionNavButtons` 一样。

The Footer Bar in this app also has a simple form, which has some Ionic styling (plus a little extra custom styling in the Sass file). Form styles are not fully designed to work in the Footer Bar, but it only took a few lines of styling to clean it up. This form is just a simple search input and button, and on submit the form will call the `add()` method to attempt to lookup and add a stock symbol to the current list.
应用中的底部工具栏有一个简单的表单，包含了一些 Ionic 样式（加上了一些 Sass 文件中定义的外部用户样式）。表单样式的设计并不是完全为了底部导航条，但是它只需要几行样式就可以清除掉。这里的表单仅用了简单的搜索输入框和一个按钮，在提交表单的时候调用 `add()` 方法去尝试查看并且添加一个股票代码到当前列表。

## Add the portfolio state
添加 portfolio state

The last major step for your app will be to add another view to keep track of your portfolio. The idea is you can specify how many stocks you purchased at a given price, and see a current rate of return or loss for that purchase. This whole state has about 60 lines of markup and 100 lines of JavaScript.
最后一个重要步骤就是添加另一个视图去记录你的投资组合。这样你就可以得到你目前在某个价格下购买了多少股票的详细信息，和目前购买股票的回报率或损失率。这整个 state 大约有 60 行 HTML 和 100 行 JavaScript 代码。

Create a new file at www/views/portfolio/portfolio.html and add the contents below.
创建一个新文件 www/views/portfolio/portfolio.html 并且添加以下内容。

    <ion-view view-title="My Portfolio">
      <!-- Add buttons to both primary and secondary sides of the navbar -->
      <ion-nav-buttons side="primary">
        <button class="button button-clear" ng-click="openModal()">Add</button>
      </ion-nav-buttons>
      <ion-nav-buttons side="secondary">
        <button class="button button-clear" ng-click="state.remove = !state.remove">Edit</button>
      </ion-nav-buttons>
      <ion-content>
        <!-- Use a list to display the list of stocks in portfolio -->
        <ion-list show-delete="state.remove">
          <!-- Repeat over each stock in the portfolio and display relevant data -->
          <ion-item ng-repeat="stock in portfolio" class="item-dark item-text-wrap">
            {{stock.symbol}} ({{stock.quantity}} @ {{stock.price | currency}})
            <div class="quote" ng-class="quoteClass(stock)" ng-if="quotes[stock.symbol]">
              <!-- These bindings calculate the current value and gain/loss of the stock -->
              <div class="quote-price">{{getCurrentValue(stock) | currency:'$'}}</div>
              <div class="quote-change">{{getChange(stock) | currency}}</div>
            </div>
            <!-- Use an ionSpinner to display while the stock price is loaded -->
            <div class="quote" ng-if="!quotes[stock.symbol]">
              <ion-spinner icon="lines"></ion-spinner>
            </div>
            <!-- Delete button allows the item to be removed -->
            <ion-delete-button class="ion-minus-circled" ng-click="remove($index)"></ion-delete-button>
          </ion-item>
        </ion-list>
      </ion-content>
    </ion-view>

Create another file at www/views/portfolio/add-modal.html and add the following markup.
创建一个新的文件 www/views/portfolio/add-modal.html，并且添加以下代码。

    <!-- Modals require a special ionModalView wrapper -->
    <ion-modal-view>
      <!-- Use Angular form to have automatic validation -->
      <form name="addQuote">
        <!-- Add an ionHeaderBar with buttons and title -->
        <ion-header-bar class="bar-balanced">
          <button class="button button-clear" ng-click="closeModal()">Cancel</button>
          <h1 class="title">Add Stock</h1>
          <button class="button button-clear" ng-click="addStock(item)" ng-disabled="addQuote.$invalid">Save</button>
        </ion-header-bar>
        <ion-content>
          <!-- Use Ionic's CSS list and form classes to format forms -->
          <div class="list">
            <label class="item item-input">
              <span class="input-label">Symbol</span>
              <input type="text" autocorrect="off" autocapitalize="off" ng-model="item.symbol" required />
            </label>
            <label class="item item-input">
              <span class="input-label">Quantity</span>
              <input type="number" autocorrect="off" autocapitalize="off" ng-model="item.quantity" required />
            </label>
            <label class="item item-input">
              <span class="input-label">Price</span>
              <input type="number" autocorrect="off" autocapitalize="off" ng-model="item.price" required />
            </label>
          </div>
        </ion-content>
      </form>
    </ion-modal-view>

Lastly, create a file at www/views/portfolio/portfolio.js and include the code below. Also be sure to create a new script tag to load this into the app in www/index.html.
最后，创建文件 www/views/portfolio/portfolio.js，然后加入以下代码。同样要确保在 app 的 www/index.html 中引用了这个文件。

    angular.module('App')
    
    .config(function($stateProvider) {
      // Declare the state for the portfolio, with the template and controller
      $stateProvider
        .state('tabs.portfolio', {
          url: '/portfolio',
          views: {
            portfolio: {
              controller: 'PortfolioController',
              templateUrl: 'views/portfolio/portfolio.html'
            }
          }
        });
    })
    
    .controller('PortfolioController', function($scope, $ionicModal, $ionicPopup, LocalStorageService, QuotesService) {
      // Create the portfolio model from localstorage, and other models
      $scope.portfolio = LocalStorageService.get('portfolio', []);
      $scope.item = {};
      $scope.state = {
        remove: false
      };
      // Private method to update the portfolio
      function updatePortfolio() {
        LocalStorageService.update('portfolio', $scope.portfolio);
      }
      // Method to get the latest quotes
      $scope.getQuotes = function() {
        var symbols = [];
        angular.forEach($scope.portfolio, function(stock) {
          if (symbols.indexOf(stock.symbol) < 0) {
            symbols.push(stock.symbol);
          }
        });
    
        if (symbols.length) {
          QuotesService.get(symbols).then(function(quotes) {
            var items = {};
            angular.forEach(quotes, function(quote) {
              items[quote.Symbol] = quote;
            });
            $scope.quotes = items;
          });
        }
      };
      // Method to calculate the current value of the stocks
      $scope.getCurrentValue = function(stock) {
        return parseFloat($scope.quotes[stock.symbol].LastTradePriceOnly) * stock.quantity;
      };
      // Method to calculate the change in value
      $scope.getChange = function(stock) {
        return $scope.getCurrentValue(stock) - stock.price * stock.quantity;
      };
      // Method to determine if the stock has positive or negative return for background color
      $scope.quoteClass = function(stock) {
        if (!stock) {
          return '';
        }
        var className = '';
        var currentValue = $scope.getCurrentValue(stock);
        if (currentValue && currentValue > stock.price) {
          className = 'positive';
        } else if (currentValue && currentValue < stock.price) {
          className = 'negative';
        }
    
        return className;
      }
      // Create an Ionic modal instance for adding a new stock
      $ionicModal.fromTemplateUrl('views/portfolio/add-modal.html', {
        scope: $scope
      }).then(function(modal) {
        $scope.modal = modal;
      });
      // Open the modal
      $scope.openModal = function() {
        $scope.modal.show();
      };
      // Close the modal and reset the model
      $scope.closeModal = function() {
        $scope.item = {};
        $scope.modal.hide();
      };
      // Ensure the modal is completely destroyed after the scope is destroyed
      $scope.$on('$destroy', function() {
        $scope.modal.remove();
      });
      // Method to add a new stock purchase
      $scope.addStock = function(item) {
        $scope.state.remove = false;
        QuotesService.get([item.symbol]).then(function(quote) {
          if (quote[0].Name) {
            item.symbol = item.symbol.toUpperCase();
            $scope.portfolio.push(item);
            updatePortfolio();
            $scope.closeModal();
            $scope.getQuotes();
          } else {
            $ionicPopup.alert({
              title: 'Could not find symbol.'
            });
          }
        });
      };
      // Method to remove an item from the portfolio
      $scope.remove = function($index) {
        $scope.portfolio.splice($index, 1);
        updatePortfolio();
      };
      // Get the quotes on load
      $scope.getQuotes();
    
    });

Once all of these changes are made, ensure `ionic serve`  is still running and go to [http://localhost:8100/#/tabs/portfolio][23] to see this new tab. You could also tap on the Portfolio icon in the tabs to navigate.
一旦这些文件修改好了，确认命令 `ionic serve` 还在运行，在浏览器输入 [http://localhost:8100/#/tabs/portfolio][23] 就可以看到这个新的标签页。你也可以点击标签上里的 Portfolio 图标导航到这个页面。

There are a few features of Ionic used here again, such as the Ionic Popup. However, in addition there are some new features such as the Ionic Modal, Ionic Header Bar, Ionic Spinner, and another feature for the Ionic List component.
这里用到了一些上面讲过的 Ionic 特性，比如 Ionic 弹出框。然而，这里还用到了一些的特性，比如 Ionic Modal、Ionic Header Bar、Ionic Spinner 以及 Ionic 列表 component 的一些其他特性。

### Ionic Modal Service
Ionic Modal Service

The Ionic Modal service is a way to overlay an entire view on the app, and can typically be thought of as a temporary state. They are used to provide related, contextual content without cluttering the original view. In traditional desktop websites, modals have gotten a bad rap from usability professionals, but in a mobile context they are often more functional and user friendly. A modal is a completely new view, so it can contain anything from a form, to a scrolling list of content, to a video.
Ionic Modal 用来弹出覆盖整个应用界面的页面，通常用来作临时的 state。他们被用来提供上下文相关的内容，而不扰乱原来的页面。在传统的桌面站点中，在专业可用性上 modals 遭人严重诟病，但是在移动应用中，它们功能更强，对用户更加友好。modal 是一个完整地页面，所以它可以包含表单中的任何东西，从可滚动的列表到一个视频。

In this example, the `$ionicModal` service creates a modal based on a loaded template, which points to the www/views/portfolio/add-modal.html file (you can also use `fromTemplate()` instead to pass a template as a string, but I don't recommend it). The modal is created and loaded when the controller first executes, but it does not immediately open. Here is the section that creates a new modal.
在这个例子中，`$ionicModal` service 基于加载的模板创建了一个 modal，它指向文件 www/views/portfolio/add-modal.html （你也可以使用 `fromTemplate()` 去加载一个 html 字符串作为模板，但是我并不建议你这么做）。当控制器第一次被执行的时候，就会创建并加载 modal，但是它并不会马上显示出来。这里是创建一个新的 modal 的代码片段。

    $ionicModal.fromTemplateUrl('views/portfolio/add-modal.html', {
      scope: $scope
    }).then(function(modal) {
      $scope.modal = modal;
    });

The `$ionicModal` service generates the modal, which is very similar to registering a new state except in this case the modal is not part of the app routing. You also pass an object with some configuration, and in this case you have `{scope: $scope}` which will use the current state's scope as the modal's scope. Creating a modal from a template returns a promise, and when it resolves the loading of the template it returns a modal instance which can be used to control the modal (such as open and close).
`$ionicModal` service 会生成 modal，这个过程和给 app 注册一个新的 state 非常像，除了 modal 并不是 app 路由的一部分。你也可以传一个包含配置信息的对象作为参数，在这个例子中，传递了`{scope: $scope}` ，它表示使用当前的状态的作用域作为 modal 的作用域。根据模板创建一个 modal，会返回一个 promise 链式调用，当它加载模板的时候，他会返回一个 modal 实例，用于控制 modal（比如打开和关闭）。

The app then has an `openModal()` and `closeModal()` which handle the opening and closing of the modal. The portfolio view contains a navbar button with `ngClick` that call  `openModal()`, and inside of the modal view there is a cancel button that calls `closeModal()`. If a user submits the form to add a stock quote, if the stock is found it will also call the `closeModal()` method to hide the modal and return to the portfolio.
在 app 中定义了方法 `openModal()` 和 `closeModal()` 来打开和关闭 modal 。portfolio 视图包括了一个导航条按钮，在 `ngClick` 事件里调用了 `openModal()`，在 modal 视图里面，有一个取消按钮，它会调用 `closeModal()`。如果一个用户提交了表单添加了股票报价，并且找到了这个股票，也会调用 `closeModal()` 这个方法去隐藏 modal 视图，返回 portfolio 页面。

Ionic Modals also require that you also add a listener for the scope `destroy` event, so you can manually remove the modal as well. Since modals are created manually and not registered with the state provider, Ionic doesn't know when they are safe to be deleted from memory. This is easy to do, as you see here.
Ionic Modals 还需要对作用域下的 `destroy` 事件添加监听，所以你也可以手动的删除 modal。由于 modals 是手动创建的且不需要在 state provider 注册，Ionic 并不知道什么时候可以安全地从内存中删除它。就像你在这里看到的，这其实很容易做到。

    $scope.$on('$destroy', function() {
      $scope.modal.remove();
    });

I find the Ionic Modal to be a very useful tool given the size of most mobile devices. Instead of trying to show lots of content on one long scrolling screen, the modals are able to provide one way to break that content up and show it only when it is relevant to the user action. If the add form was in the portfolio view instead of a modal, it would clutter the view, so the modal provides a better experience to only show it when the user is about to add a new item. They do take some design consideration since the modal will show until it is dismissed. It is also not possible to directly navigate to a modal (at least not without some additional custom logic to handle this), so anything that a user might directly navigate to is probably not a candidate for a modal.
我发现 Ionic Modal 在大多数移动设备上是一个非常有用的工具。Modal 提供了一种不在滚屏上增加更多内容的方式，只展示用用户操作相关的部分。如果增加列表项的表单没有使用 modal 而是在 portfolio 视图中，那么它将会变得杂乱无章，所以 modal 在用户只是要添加一个新项目的时候，提供了更好的用户体验。modals 从创建到销毁确实都更多地设计和考虑。因为不可能直接导航到modal（至少如果没有额外的用户逻辑是做不到的），所以任何用户可以直接导到航的任何页面都可能不适合考虑使用 modal。

### Ionic Header Bar Component
Ionic 页首工具条 Component

The Ionic Header Bar is essentially the same as the Footer Bar, except it sits in the header as you might expect. There are several different color presets that can be used as CSS classes, and in this case it uses the `bar-balanced` class, which is modified from the default by the app Sass stylings. Since the modal is a blank slate that overlays the app, the navbar does not appear and requires you to add a Header Bar to place buttons along the top.
Ionic 页首工具条和底部工具条一样，除了一点就像你知道的，它位于页面顶部。通过 CSS 类预置的几种不同的颜色可供选择，这里使用了 `bar-balanced`  class，它通过应用的 Sass 样式修改了默认的 CSS。由于 modal 是一个空白的覆盖这个 APP 界面的深蓝色页面，导航栏不会显示，需要你在页首顶部的工具条添加按钮。

### Ionic Spinner Component
Ionic Spinner Component

The Ionic Spinner is a helpful component to display an animated SVG to indicate your app is doing something that the user has to wait for to complete. With animated SVG the indicators are be more flexible than with just rotating an icon with CSS. These spinners (which not all spin, so it is a bit of a misnomer) are possible to style and Ionic comes with 10 different animations.
Ionic Spinner 是用来展示动态图形的 Component，它表明你的应用这在做某件事，用户需要等待这件事完成。使用动态图形来提示比仅仅只是用 CSS 写的旋转图标更人性化。这些 spinners（并不都是旋转效果，所以可以这个名字起得并不恰当）可以是不同的样式，Ionic 带有十种不同的动画。

In this app, the `lines` animation is used in place of the quote price while the quotes are loaded. The `ngIf` controls when to show the spinner.
在这个应用中，当报价在加载的时候，报价显示的位置上是一个“线条”动画。`ngIf` 去控制什么时候显示 spinner。

### Ionic List Component Continued
Ionic List Component 续篇

The Ionic List component also has a delete mode, which is similar to the reorder mode you saw in the quotes state but instead of moving items it will delete them. You can use both delete and reorder modes on the same list, depending on your app design and needs. The delete mode slides an icon from the left to allow users to quickly delete items.
Ionic List component 同样有删除模式，和我们之前在 quotes state 看到的重新排序模式很像，但是这里不是移动列表项而是删除它们。根据你的应用的设计和需求，可以在用一个列表中同时使用删除和排序模式。删除模式在列表左边滑出一个图标去让用户快捷地删除若干列表项。

To toggle the delete mode, the `ionList` has a `show-delete` attribute that should be `true` or `false` to toggle the delete mode. Then each of the `ionItem` components have an `ionDeleteButton` component, which have an icon declared and use an `ngClick` to call the `remove()` method in the controller.
`ionList` 根据 `show-delete` 属性 为 `true` 或 `false` 去切换删除模式。每个 `ionItem` 控件都有 `ionDeleteButton` 组件，他是一个定义好的图标，用 `ngClick` 指令调用在控制器中定义的 `remove()` 方法。

## Finishing touches
收尾

There is one last thing that our app needs, a default route. Right now if you go to [http://localhost:8100][24] it will not load the tabs and content. This is an easy remedy, but needed to be implemented after the states were added. The following snippet should be placed into your www/js/app.js file, and it uses the `$urlRouterProvider.otherwise()` method to define where the app should go when it can't find a route (in this case the defaul `/` route is not registered).
我们的应用还需要做一件事，一个默认的路由。现在如果你去 [http://localhost:8100][24]，它不会加载标签页和内容。这很容易补救，但是需要在 states 都添加后再实现。下面的代码片段应该加入你的 www/js/app.js 文件中，这里使用了 `$urlRouterProvider.otherwise()` 方法去定义当它找不到路由的时候应该跳转到的地方（在这个例子中默认的 `/` 路由没有注册）。

    angular.module('App', ['ionic'])
    
    .config(function($urlRouterProvider) {
      $urlRouterProvider.otherwise('/tabs/quotes');
    })

Now when you go to the app without any path in the URL, it will load up the quotes view by default for you. Congratulations, you now have a fairly feature rich mobile app, with around 120 lines of HTML and 200 lines of JavaScript! Who knew you could build so many features so easily?
现在，如果你在 URL 里没有加任何路径去访问这个 app，它将会默认为你加载报价页面。恭喜，你已经做好了一个功能相当丰富的移动应用，仅仅用了大约 120 行 HTML 和 200 行 JavaScript！谁能想到你如此容易的实现了这么多功能？

## Digging deeper into Ionic
深入理解 Ionic

We've flown through the example app, and learned a lot about how Ionic components work together to create a beautiful and functional mobile app using just HTML, CSS, and JavaScript. You've seen how to use many components and services such as Ionic Lists, Popups, Modals, Navigation, Content, Refresher, and others. This foundation should be great for you to build from to learn the rest of the components and dive deeper into other ways they can be leveraged.
我们已经按照步骤完成了示例的应用，学到了很多关于 Ionic 组件如何一起协同工作，仅仅使用 HTML、CSS、JavaScript  来创建一个美观且功能强大的移动应用。你已经看到过了如何使用很多 components 和 service，比如，Ionic 列表、弹出框、Modals、导航条、内容、刷新条以及其他。这个基础对于你学习其他组件并深入到其他方面来说是十分有益的。

The [Ionic documentation][25] is really good and the best place to look up detailed information about how components and services work. It also provides some primers on how to get your environment setup to build and deploy the app to an emulator or to a real device. For that, you will be using [Cordova][26] and will want to spend some time understanding how it works. You can also spend time on the [Ionic Forum][27] to find answers or ask your own questions.
[Ionic 文档][28] 是查看 components 和 services 如何工作的详细信息的最好的地方，没有之一。 它同时也提供了一些基础教程告诉你如何准备好你的开发环境，去构建并部署你的应用到虚拟机或者真实设备上。这样，你可能会使用到 [Cordova][29] ，并且需要花些时间理解它是如何工作的。你还可以在 [Ionic 论坛][30] 上花些功夫找到你的问题的答案。

If you are looking for more, I recommend you check out my book [Ionic in Action][31] which covers everything in much more detail. It also provides an Angular primer, lots of examples on how to use Ionic and Cordova plugins (with ngCordova), how to test, and how to properly build and submit to the app stores.
如果你还想学习更多，我推荐你看看 [Ionic in Action][32]，这本书介绍了更多地细节信息。它还提供了 Angular 基础教程，有大量的实例介绍如何使用 Ionic 和 Cordova 插件（通过 ngCordova ）、如何测试、还有如何正确构建应用并提交给应用商店。


  [1]: http://ionicframework.com/
  [2]: https://www.airpair.com/angularjs/posts/angularjs-tutorial
  [3]: https://ionic-starter-guide.herokuapp.com/#/tabs/quotes
  [4]: https://github.com/gnomeontherun/ionic-definitive-guide
  [5]: https://developer.chrome.com/devtools/docs/device-mode
  [6]: https://dzone.com/articles/three-types-mobile-experiences
  [7]: https://developer.apple.com/library/ios/documentation/WindowsViews/Conceptual/ViewControllerCatalog/Chapters/TabBarControllers.html
  [8]: http://developer.android.com/design/building-blocks/lists.html
  [9]: http://docs.ionic.io/tools/creator/
  [10]: http://docs.ionic.io/tools/viewapp/
  [11]: http://docs.ionic.io/push/
  [12]: http://docs.ionic.io/v1.0/docs/deploy-from-scratch
  [13]: http://docs.ionic.io/v1.0/docs/analytics-from-scratch
  [14]: http://ionicframework.com/docs/guide/
  [15]: https://nodejs.org/en/
  [16]: https://github.com/gnomeontherun/ionic-definitive-guide
  [17]: https://github.com/gnomeontherun/ionic-definitive-guide
  [18]: https://www.manning.com/books/ionic-in-action?a_aid=ionicinaction
  [19]: http://sass-lang.com/
  [20]: http://sass-lang.com/
  [21]: https://docs.angularjs.org/guide/services
  [22]: http://localhost:8100/#/tabs/quotes
  [23]: http://localhost:8100/#/tabs/portfolio
  [24]: http://localhost:8100
  [25]: http://ionicframework.com/docs/
  [26]: http://cordova.apache.org/
  [27]: http://forum.ionicframework.com/
  [28]: http://ionicframework.com/docs/
  [29]: http://cordova.apache.org/
  [30]: http://forum.ionicframework.com/
  [31]: https://www.manning.com/books/ionic-in-action?a_aid=ionicinaction
  [32]: https://www.manning.com/books/ionic-in-action?a_aid=ionicinaction