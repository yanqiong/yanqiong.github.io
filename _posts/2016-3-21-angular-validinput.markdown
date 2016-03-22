---
layout: post
title:  "Angular 表单输入验证"
date:   2016-3-21 00:00:00 +0800
categories: angular
---

## Forms

表单是一系列输入控件的集合,客户端验证表单可以提供更好的用户体验.

    <form></from>

### Simple from

{% highlight html %}
<div ng-controller="ExampleController">
  <form novalidate class="simple-form">
    Name: <input type="text" ng-model="user.name" /><br />
    E-mail: <input type="email" ng-model="user.email" /><br />
    Gender: <input type="radio" ng-model="user.gender" value="male" />male
    <input type="radio" ng-model="user.gender" value="female" />female<br />
    <input type="button" ng-click="reset()" value="Reset" />
    <input type="submit" ng-click="update(user)" value="Save" />
  </form>
  <pre>user = {{user | json}}</pre>
  <pre>master = {{master | json}}</pre>
</div>

<script>
  angular.module('formExample', [])
    .controller('ExampleController', ['$scope', function($scope) {
      $scope.master = {};

      $scope.update = function(user) {
        $scope.master = angular.copy(user);
      };

      $scope.reset = function() {
        $scope.user = angular.copy($scope.master);
      };

      $scope.reset();
    }]);
</script>
{% endhighlight %}

**novalidate** 禁用 HTML5 浏览器原生表单验证

*******

### 添加 CSS 样式

`ngModel` 会添加以下 CSS classes:

+ `ng-valid`: the model is valid
+ `ng-invalid`: the model is invalid
+ `ng-valid-[key]`: for each valid key added by $setValidity
+ `ng-invalid-[key]`: for each invalid key added by $setValidity
+ `ng-pristine`: the control hasn't been interacted with yet
+ `ng-dirty`: the control has been interacted with
+ `ng-touched`: the control has been blurred
+ `ng-untouched`: the control hasn't been blurred
+ `ng-pending`: any $asyncValidators are unfulfilled

{% highlight html %}
<!-- 页面代码 -->
<input type="text" autocomplete="off" placeholder="用户名" name="username" 
    required ng-model="login_name"/>
    
<style type="text/css">
  input.ng-invalid.ng-touched {
    background-color: #FA787E;
  }

  input.ng-valid.ng-touched {
    background-color: #78FA89;
  }
</style>
{% endhighlight %}

{% highlight html %}
<!-- 刚加载页面/获得焦点 -->
<input class="ng-pristine ng-untouched ng-invalid ng-invalid-required" 
    type="text" autocomplete="off" placeholder="用户名" name="username" 
    required="" ng-model="login_name" aria-required="true">
{% endhighlight %}

{% highlight html %}
<!-- 单击一下输入框后,什么都不填就离开输入框,失去焦点 -->
<input class="ng-pristine ng-invalid ng-invalid-required ng-touched" 
    type="text" autocomplete="off" placeholder="用户名" name="username" 
    required="" ng-model="login_name" aria-required="true" aria-invalid="true" 
    aria-describedby="username-error">
{% endhighlight %}

{% highlight html %}
<!-- 输入内容后,焦点离开输入框 -->
<input class="ng-touched ng-dirty ng-valid-parse ng-valid ng-valid-required valid" 
    type="text" autocomplete="off" placeholder="用户名" name="username" 
    required="" ng-model="login_name" aria-required="true" aria-invalid="false" 
    aria-describedby="username-error">
{% endhighlight %}

{% highlight html %}
<!-- 删去内容,焦点离开输入框 -->
<input class="ng-touched ng-dirty ng-valid-parse valid ng-invalid ng-invalid-required" 
    type="text" autocomplete="off" placeholder="用户名" name="username" 
    required="" ng-model="login_name" aria-required="true" aria-invalid="true" 
    aria-describedby="username-error">
{% endhighlight %}

******

### binding to form and control state

一个 form 是 [`FromController`][FormController] 的实例. 这个实例可以用 `name` 属性引用.

同样地, `ng-model` 指令也会为 `input` 产生一个 [`NgModelController`][NgModelController] 实例, 也同样用 `name` 属性引用.

我们就能够在试图内部引用他们的状态, 实现一些新的特性:

+   显示用户定制化的错误信息( `$touched` 被激活后显示)
+   提交表单时显示用户定制化错误信息( `$submmit` 被激活后显示)

{% highlight html %}
<div ng-controller="ExampleController">
  <form name="form" class="css-form" novalidate>
    Name:
    <input type="text" ng-model="user.name" name="uName" required="" />
    <br />
    <div ng-show="form.$submitted || form.uName.$touched">
      <div ng-show="form.uName.$error.required">Tell us your name.</div>
    </div>

    E-mail:
    <input type="email" ng-model="user.email" name="uEmail" required="" />
    <br />
    <div ng-show="form.$submitted || form.uEmail.$touched">
      <span ng-show="form.uEmail.$error.required">Tell us your email.</span>
      <span ng-show="form.uEmail.$error.email">This is not a valid email.</span>
    </div>

    Gender:
    <input type="radio" ng-model="user.gender" value="male" />male
    <input type="radio" ng-model="user.gender" value="female" />female
    <br />
    <input type="checkbox" ng-model="user.agree" name="userAgree" required="" />

    I agree:
    <input ng-show="user.agree" type="text" ng-model="user.agreeSign" required="" />
    <br />
    <div ng-show="form.$submitted || form.userAgree.$touched">
      <div ng-show="!user.agree || !user.agreeSign">Please agree and sign.</div>
    </div>

    <input type="button" ng-click="reset(form)" value="Reset" />
    <input type="submit" ng-click="update(user)" value="Save" />
  </form>
  <pre>user = {{user | json}}</pre>
  <pre>master = {{master | json}}</pre>
</div>
{% endhighlight %}

{% highlight js %}
angular.module('formExample', [])
.controller('ExampleController', ['$scope', function($scope) {
  $scope.master = {};

  $scope.update = function(user) {
    $scope.master = angular.copy(user);
  };

  $scope.reset = function(form) {
    if (form) {
      form.$setPristine();
      form.$setUntouched();
    }
    $scope.user = angular.copy($scope.master);
  };

  $scope.reset();
}]);
{% endhighlight %}

******

### 定制模板更新的触发时机

默认表单中任何内容的改变都会触发 `model` 更新并验证表单.
可以用 `ngModelOptions` 指令去指定某些事件可以触发 `model` 更新并验证表单.

只在失去焦点时更新 `ng-model-options="{ updateOn: 'blur' }"`

按下鼠标和失去焦点时更新 `ng-model-options="{ updateOn: 'mousedown blur' }"`

在默认事件基础上添加失去焦点时 `ng-model-options="{ updateOn: 'default blur' }"`

******

### 不及时更新模板(防抖动)

延迟模板 更新/验证 ,在 `ngModelOptions` 指令中添加 `debounce` 关键字.这种延迟也适用于解析,验证,以及 model 的一些标识,比如 `$dirty` `$pristine`.

每隔 500 毫秒验证一次: `ng-model-options="{ debounce: 500 }"`

用户还可以特别指定一些事件的触发验证时间间隔,比如(失去焦点就马上验证,否则就每隔 500 毫秒验证一次):
`ng-model-options="{ updateOn: 'default blur', debounce: { default: 500, blur: 0 } }"`

*这些属性都是会被子元素继承的.*

******

### 验证数据

#### angular 已经提供的验证机制

HTML5 input types : (text, number, url, email, date, radio, checkbox)

验证指令 (required, pattern, minlength, maxlength, min, max)

ng默认提供以下状态
`$valid`: 验证通过 `$invalid`: 验证未通过
`$pristine`:还没有交互 `$dirty`: 已经有交互
`$error`: 错误状态

angular 自带的一些属性验证和相对应的验证状态有:

```
ng-required="..."       ngModel.$error.required
ng-minlength="number"   ngModel.$error.minlength
ng-maxlength="number"   ngModel.$error.maxlength
ng-min="number"         ngModel.$error.min
ng-max="number"         ngModel.$error.max
ng-pattern="pattern"	ngModel.$error.pattern
```

表单元素类型验证,angular 表单定义类型和所对应验证状态有:

```
type="email"	    ngModel.$error.email
type="url"	    ngModel.$error.url
type="number"	    ngModel.$error.number
type="date"	    ngModel.$error.date
type="time"	    ngModel.$error.time
type="datetime"	    ngModel.$error.datetimelocal
type="week"	    ngModel.$error.week
type="month"	    ngModel.$error.month
```

{% highlight html %}
<input
    name="username"
    type="text"
    placeholder="Username"
    ng-model="user.username"
    minlength="5"
    maxlength="100"
    required />
<span ng-show="loginForm.username.$error.required">Required</span>
<span ng-show="loginForm.username.$error.minlength">too little</span>
<span ng-show="loginForm.username.$error.maxlength">too much</span>
{% endhighlight %}

{% highlight html %}
<input
    type="text"
    placeholder="phone"
    name="mobile"
    ng-model="user.phone"
    ng-pattern="/1[3|5|7|8|][0-9]{9}/"
    required />
<span ng-show="loginForm.username.$error.pattern">Wrong phone number </span>
{% endhighlight %}

{% highlight html %}
<input
    name="email"
    type="email"
    placeholder="Email"
    ng-model="user.email"
    required />
<span ng-show="loginForm.email.$error.required">Need email</span>
<span ng-show="loginForm.email.$error.email">Wrong email</span>
{% endhighlight %}

表单验证未通过,禁用提交按钮

{% highlight html %}
<button type="submit" ng-disabled="loginForm.$invalid">Submit</button>
{% endhighlight %}

#### 定制化的验证

你可以把你的验证函数加在 `ngModelController` 的 `$validators` 对象上,

需要自定义指令

`$validators` 这个对象的每个函数都会接收两个参数 `modelValue` `viewValue`,
Angular 会根据函数的返回值在内部调用 `$setValidity` (true: valid, false: invalid).
验证函数会在 每次输入改变(`$setViewValue` 被调用的时候), 或者绑定的 model 改变的时候 执行.
 Validation happens after successfully running $parsers and $formatters, respectively. 
失败的验证结果会根据 key 值存储在 `ngModelController.$error`.

另外, 还有 `$asyncValidators` 对象可以处理异步验证, 比如用 `$http` 请求在后台验证. 
这种验证函数必须返回一个 `promise`, 在 验证通过时执行 `resolve()` ,验证未通过时执行 `reject()`.
一步请求验证结果根据 key 值储存在 `ngModelController.$pending`.

{% highlight html %}
<form name="form" class="css-form" novalidate>
  <div>
    Size (integer 0 - 10):
    <input type="number" ng-model="size" name="size"
           min="0" max="10" integer />{{size}}<br />
    <span ng-show="form.size.$error.integer">The value is not a valid integer!</span>
    <span ng-show="form.size.$error.min || form.size.$error.max">
      The value must be in range 0 to 10!</span>
  </div>

  <div>
    Username:
    <input type="text" ng-model="name" name="name" username />{{name}}<br />
    <span ng-show="form.name.$pending.username">Checking if this name is available...</span>
    <span ng-show="form.name.$error.username">This username is already taken!</span>
  </div>

</form>
{% endhighlight %}

{% highlight javascript %}
var app = angular.module('form-example1', []);

var INTEGER_REGEXP = /^\-?\d+$/;
app.directive('integer', function() {
  return {
    require: 'ngModel',
    link: function(scope, elm, attrs, ctrl) {
      ctrl.$validators.integer = function(modelValue, viewValue) {
        if (ctrl.$isEmpty(modelValue)) {
          // consider empty models to be valid
          return true;
        }
        // 验证 viewVlaue 而不是 modelValue
        // 因为  input[number] 在运行 $parsers 时, 会把 viewValue 转换成数字
        if (INTEGER_REGEXP.test(viewValue)) {
          // it is valid
          return true;
        }

        // it is invalid
        return false;
      };
    }
  };
});

app.directive('username', function($q, $timeout) {
  return {
    require: 'ngModel',
    link: function(scope, elm, attrs, ctrl) {
      var usernames = ['Jim', 'John', 'Jill', 'Jackie'];

      ctrl.$asyncValidators.username = function(modelValue, viewValue) {

        if (ctrl.$isEmpty(modelValue)) {
          // consider empty model valid
          return $q.when();
        }

        var def = $q.defer();

        $timeout(function() {
          // Mock a delayed response
          if (usernames.indexOf(modelValue) === -1) {
            // The username is available
            def.resolve();
          } else {
            def.reject();
          }

        }, 2000);

        return def.promise;
      };
    }
  };
});
{% endhighlight %}

#### 修改 angular 已有的验证

Angular 的验证机制是使用 control 的`$validators`, 我们可以用修改它本身的验证机制, 
下面的例子也可以使用 `ng-pattern` 来完成更严格的匹配.

{% highlight html %}
<form name="form" class="css-form" novalidate>
  <div>
    Overwritten Email:
    <input type="email" ng-model="myEmail" overwrite-email name="overwrittenEmail" />
    <span ng-show="form.overwrittenEmail.$error.email">This email format is invalid!</span><br>
    Model: {{myEmail}}
    </div>
</form>
{% endhighlight %}

{% highlight javascript %}
var app = angular.module('form-example-modify-validators', []);

app.directive('overwriteEmail', function() {
  var EMAIL_REGEXP = /^[a-z0-9!#$%&'*+/=?^_`{|}~.-]+@example\.com$/i;

  return {
    require: '?ngModel',
    link: function(scope, elm, attrs, ctrl) {
      // only apply the validator if ngModel is present and Angular has added the email validator
      if (ctrl && ctrl.$validators.email) {

        // this will overwrite the default Angular email validator
        ctrl.$validators.email = function(modelValue) {
          return ctrl.$isEmpty(modelValue) || EMAIL_REGEXP.test(modelValue);
        };
      }
    }
  };
});
{% endhighlight %}

#### 实现用户自定义表单

你可以重写你自己的表单, form control

**注意** 要使 自定义的 control 也能够根据 `ngModel` 指令实现双向数据绑定,你需要做:

+   实现 `$render` 方法, 负责渲染从 [`NgModelController.$formatters`][NgModelControllerFormatters] 来的数据
+   用户交互中,需要更新 model 时 调用 `$setViewValue`, 通常在一个 DOM 事件监听里完成

{% highlight html %}
{% raw %}
<div contentEditable="true" ng-model="content" title="Click to edit">Some</div>
<pre>model = {{content}}</pre>

<style type="text/css">
  div[contentEditable] {
    cursor: pointer;
    background-color: #D0D0D0;
  }
</style>
{% endraw %}
{% endhighlight %}

{% highlight javascript %}
angular.module('form-example2', []).directive('contenteditable', function() {
  return {
    require: 'ngModel',
    link: function(scope, elm, attrs, ctrl) {
      // view -> model
      elm.on('blur', function() {
        ctrl.$setViewValue(elm.html());
      });

      // model -> view
      ctrl.$render = function() {
        elm.html(ctrl.$viewValue);
      };

      // load init value from DOM
      ctrl.$setViewValue(elm.html());
    }
  };
});
{% endhighlight %}

******

参考:

1.  [Angular Form 文档][angularFormDoc]

2.  [http://ajiegao.com/2014/11/27/Angularjs-form-1/][blogLink]

[blogLink]: http://ajiegao.com/2014/11/27/Angularjs-form-1/

[angularFormDoc]: https://docs.angularjs.org/guide/forms

[FormController]: [https://docs.angularjs.org/api/ng/type/form.FormController]
[NgModelController]: [https://docs.angularjs.org/api/ng/type/ngModel.NgModelController]
[NgModelControllerFormatters]: [https://docs.angularjs.org/api/ng/type/ngModel.NgModelController#$formatters]
