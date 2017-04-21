# JavaScript Style

本代码规范基于 [JavaScript Standard Style](https://standardjs.com/rules-zhcn.html) 代码规范修改扩展而成。

掌握本规范的最好方法是结合 [ESLint](http://eslint.cn/) 工具在代码中使用它，验证它。

## 规则细则

### JavaScript

* **使用两个空格**进行缩进。

  eslint: [`indent`](http://eslint.cn/docs/rules/indent)

  ```js
  // ✓ ok
  function hello (name) {
    console.log('hi', name)
  }
  ```

* 除需要转义的情况外，**字符串统一使用单引号**。

  eslint: [`quotes`](http://eslint.cn/docs/rules/quotes)

  ```js
  // ✓ ok
  console.log('hello there')
  $("<div class='box'>")
  ```

* **不要定义未使用的变量**。

  eslint: [`no-unused-vars`](http://eslint.cn/docs/rules/no-unused-vars)

  ```js
  // ✗ avoid
  function myFunction () {
    var result = something()
  }
  ```

* **关键字后面加空格**。

  eslint: [`keyword-spacing`](http://eslint.cn/docs/rules/keyword-spacing)

  ```js
  // ✗ avoid
  if(condition) { ... }

  // ✓ ok
  if (condition) { ... }
  ```

* **函数声明时括号与函数名间加空格**。

  eslint: [`space-before-function-paren`](http://eslint.cn/docs/rules/space-before-function-paren)

  ```js
  // ✗ avoid
  function name(arg) { ... }
  run(function() { ... })

  // ✓ ok
  function name (arg) { ... }
  run(function () { ... })
  ```

* **始终使用** === 替代 ==。

  eslint: [`eqeqeq`](http://eslint.cn/docs/rules/eqeqeq)

  ```js
  // ✗ avoid
  if (name == 'John')
  if (name != 'John')

  // ✓ ok
  if (name === 'John')
  if (name !== 'John')
  ```

* **字符串拼接操作符 (Infix operators)** 之间要留空格。

  eslint: [`space-infix-ops`](http://eslint.cn/docs/rules/space-infix-ops)

  ```js
  // ✗ avoid
  var x=2
  var message = 'hello, '+name+'!'

  // ✓ ok
  var x = 2
  var message = 'hello, ' + name + '!'
  ```

* **else 关键字要与花括号**保持在同一行。

  eslint: [`brace-style`](http://eslint.cn/docs/rules/brace-style)

  ```js
  // ✗ avoid
  if (condition) {
    // ...
  }
  else {
    // ...
  }

  // ✓ ok
  if (condition) {
    // ...
  } else {
    // ...
  }
  ```

* **多行 if 语句的**括号不能省。

  eslint: [`curly`](http://eslint.cn/docs/rules/curly)

  ```js
  // ✗ avoid
  if (options.quiet !== true)
    console.log('done')

  // ✓ ok
  if (options.quiet !== true) console.log('done')
  if (options.quiet !== true) {
    console.log('done')
  }
  ```

* **不要丢掉**异常处理中 err 参数。

  eslint: [`handle-callback-err`](http://eslint.cn/docs/rules/handle-callback-err)

  ```js
  // ✗ avoid
  run(function (err) {
    window.alert('done')
  })

  // ✓ ok
  run(function (err) {
    if (err) throw err
    window.alert('done')
  })
  ```

* **使用浏览器全局变量时加上** `window.` 前缀。<br/>
  例外: `document`，`console`，`navigator`。

  eslint: [`no-undef`](http://eslint.cn/docs/rules/no-undef)

  ```js
  // ✓ ok
  window.alert('hi')
  ```

* **不允许有大于 2 的连续空行**。

  eslint: [`no-multiple-empty-lines`](http://eslint.cn/docs/rules/no-multiple-empty-lines)

  ```js
  // ✗ avoid
  var value = 'hello world'



  console.log(value)
  ```

  ```js
  // ✓ ok
  var value = 'hello world'
  var text = 'hello';

  console.log(value)


  console.log(text);
  ```

* **强制换行符放在操作符之前**。

  eslint: [`operator-linebreak`](http://eslint.cn/docs/rules/operator-linebreak)

  ```js
  // ✗ avoid
  var location = env.development ?
    'localhost' :
    'www.api.com'
  var foo = 1 +
            2

  if (someCondition ||
    otherCondition) {
  }

  // ✓ ok
  var location = env.development ? 'localhost' : 'www.api.com'
  var foo = 1 + 2

  if (someCondition || otherCondition) {
  }

  var location = env.development
    ? 'localhost'
    : 'www.api.com'
  var foo = 1
          + 2
  
  if (someCondition
    || otherCondition) {
  }
  ```

* **每个 `var`、`let`、`const` 关键字**单独声明一个变量。

  eslint: [`one-var`](http://eslint.cn/docs/rules/one-var)

  ```js
  // ✗ avoid
  var silent = true, verbose = true
  var silent = true,
      verbose = true

  // ✓ ok
  var silent = true
  let verbose = true
  const str = 'hello'
  ```

* **条件语句中赋值语句**必须使用括号包起来。这样使得代码更加清晰可读，而不会认为是将条件判断语句的全等号（`===`）错写成了等号（`=`）。

  eslint: [`no-cond-assign`](http://eslint.cn/docs/rules/no-cond-assign)

  ```js
  // ✗ avoid
  while (m = text.match(expr)) {
    // ...
  }

  // ✓ ok
  while ((m = text.match(expr))) {
    // ...
  }
  ```

* **单行代码块两边加空格**。

  eslint: [`block-spacing`](http://eslint.cn/docs/rules/block-spacing)

  ```js
  // ✗ avoid
  function foo () {return true}
  if (foo) { bar = 0}

  // ✓ ok
  function foo () { return true }
  if (foo) { bar = 0 }
  ```

* **对于变量和函数名统一使用驼峰命名法**。<br/>
  例外: 全大写以 `_` 连接的常量，属性名。

  eslint: [`camelcase`](http://eslint.cn/docs/rules/camelcase)

  ```js
  // ✗ avoid
  var myVar = 'hello'
  function my_function () { }

  // ✓ ok
  var my_var = 'hello'
  var obj = {
    my_pref: 1,
  }
  function myFunction () { }
  ```

* **逗号后面加空格**。

  eslint: [`comma-spacing`](http://eslint.cn/docs/rules/comma-spacing)

  ```js
  // ✗ avoid
  var list = [1,2,3,4]
  function greet (name,options) { ... }

  // ✓ ok
  var list = [1, 2, 3, 4]
  function greet (name, options) { ... }
  ```

* **始终将逗号置于行末**。

  eslint: [`comma-style`](http://eslint.cn/docs/rules/comma-style)

  ```js
  // ✗ avoid
  var obj = {
    foo: 'foo'
    ,bar: 'bar'
  }

  // ✓ ok
  var obj = {
    foo: 'foo',
    bar: 'bar',
  }
  ```

* **当最后一个元素或属性与闭括号 `]` 或 `}` 在 不同的行时，要求使用拖尾逗号；当在 同一行时，禁止使用拖尾逗号**。

  eslint: [`comma-dangle`](http://eslint.cn/docs/rules/comma-dangle)

  ```js
  // ✗ avoid
  var obj = {
    message: 'hello',
    text: 'world'
  }
  var foo = { bar: 'baz', qux: 'quux', }
  var arr = [1, 2,]
  var str = [
    'a',
    'b'
  ]

  // ✓ ok
  var obj = {
    message: 'hello',
    text: 'world',
  }
  var foo = { bar: 'baz', qux: 'quux' }
  var arr = [1, 2]
  var str = [
    'a',
    'b',
  ]
  ```

* **点号操作符须与属性需在同一行(强制在 `.` 号之前换行)**。

  eslint: [`dot-location`](http://eslint.cn/docs/rules/dot-location)

  ```js
  // ✗ avoid
  console.
    log('hello')

  // ✓ ok
  console
    .log('hello')
  ```

* **文件末尾留一空行**。

  elint: [`eol-last`](http://eslint.cn/docs/rules/eol-last)

* **函数调用时标识符与括号间不留间隔**。

  eslint: [`func-call-spacing`](http://eslint.cn/docs/rules/func-call-spacing)

  ```js
  // ✗ avoid
  console.log ('hello')

  // ✓ ok
  console.log('hello')
  ```

* **键值对当中冒号与值之间要留空白**。

  eslint: [`key-spacing`](http://eslint.cn/docs/rules/key-spacing)

  ```js
  // ✗ avoid
  var obj = { 'key' : 'value' }
  var obj = { 'key' :'value' }
  var obj = { 'key':'value' }

  // ✓ ok
  var obj = { 'key': 'value' }
  ```

* **构造函数要以大写字母开头**。

  eslint: [`new-cap`](http://eslint.cn/docs/rules/new-cap)

  ```js
  // ✗ avoid
  function animal () {}
  var dog = new animal()

  // ✓ ok
  function Animal () {}
  var dog = new Animal()
  ```

* **无参的构造函数调用时要带上括号**。

  eslint: [`new-parens`](http://eslint.cn/docs/rules/new-parens)

  ```js
  function Animal () {}

  // ✗ avoid
  var dog = new Animal

  // ✓ ok
  var dog = new Animal()
  ```

* **强制 getter 和 setter 在对象中成对出现**。

  eslint: [`accessor-pairs`](http://eslint.cn/docs/rules/accessor-pairs)

  ```js
  // ✗ avoid
  var person = {
    set name (value) {
      this.name = value
    }
  }

  // ✓ ok
  var person = {
    set name (value) {
      this.name = value
    },
    get name () {
      return this.name
    }
  }
  ```

* **子类的构造器中一定要调用 super**

  eslint: [`constructor-super`](http://eslint.cn/docs/rules/constructor-super)

  ```js
  // ✗ avoid
  class Dog {
    constructor () {
      super()
    }
  }

  // ✓ ok
  class Dog extends Mammal {
    constructor () {
      super()
    }
  }
  ```

* **使用数组字面量而不是构造器**。

  eslint: [`no-array-constructor`](http://eslint.cn/docs/rules/no-array-constructor)

  ```js
  // ✗ avoid
  var nums = new Array(1, 2, 3)

  // ✓ ok
  var nums = [1, 2, 3]
  ```

* **避免使用 `arguments.callee` 和 `arguments.caller`**。<br/>
  具体可参考: [https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/arguments/callee](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/arguments/callee)

  eslint: [`no-caller`](http://eslint.cn/docs/rules/no-caller)

  ```js
  // ✗ avoid
  function foo (n) {
    if (n <= 0) return

    arguments.callee(n - 1)
  }

  // ✓ ok
  function foo (n) {
    if (n <= 0) return

    foo(n - 1)
  }
  ```

* **避免对类名重新赋值**。

  eslint: [`no-class-assign`](http://eslint.cn/docs/rules/no-class-assign)

  ```js
  // ✗ avoid
  class Dog {}
  Dog = 'Fido'
  ```

* **避免修改使用 `const` 声明的变量**。

  eslint: [`no-const-assign`](http://eslint.cn/docs/rules/no-const-assign)

  ```js
  // ✗ avoid
  const score = 100
  score = 125
  ```

* **避免使用常量作为条件表达式的条件（循环语句除外）**。

  eslint: [`no-constant-condition`](http://eslint.cn/docs/rules/no-constant-condition)

  ```js
  // ✗ avoid
  if (false) {
    // ...
  }

  // ✓ ok
  if (x === 0) {
    // ...
  }

  while (true) {
    // ...
  }
  ```

* **正则中不要使用控制符(在 ASCII 中，0-31 范围内的控制字符是特殊的、不可见的字符)**。

  eslint: [`no-control-regex`](http://eslint.cn/docs/rules/no-control-regex)

  ```js
  // ✗ avoid
  var pattern = /\x1f/
  var pattern2 = new RegExp('\x1f')

  // ✓ ok
  var pattern = /\x20/
  var pattern2 = new RegExp('\x20')
  ```

* **禁止向 RegExp 构造器传入非法的正则表达式**。

  eslint: [`no-invalid-regexp`](http://eslint.cn/docs/rules/no-invalid-regexp)

  ```js
  // ✗ avoid
  RegExp('[a-z')

  // ✓ ok
  RegExp('[a-z]')
  ```

* **正则中不要使用空字符**。

  eslint: [`no-empty-character-class`](http://eslint.cn/docs/rules/no-empty-character-class)

  ```js
  // ✗ avoid
  const myRegex = /^abc[]/

  // ✓ ok
  const myRegex = /^abc[a-z]/
  ```

* **不要使用 `debugger`**。

  eslint: [`no-debugger`](http://eslint.cn/docs/rules/no-debugger)

  ```js
  // ✗ avoid
  function sum (a, b) {
    debugger
    return a + b
  }
  ```

* **不要对变量使用 `delete` 操作**。

  eslint: [`no-delete-var`](http://eslint.cn/docs/rules/no-delete-var)

  ```js
  // ✗ avoid
  var name
  delete name
  ```

* **禁止定义重复的函数参数**。

  eslint: [`no-dupe-args`](http://eslint.cn/docs/rules/no-dupe-args)

  ```js
  // ✗ avoid
  function sum (a, b, a) {
    // ...
  }

  // ✓ ok
  function sum (a, b, c) {
    // ...
  }
  ```

* **禁止在类中定义重复的属性**。

  eslint: [`no-dupe-class-members`](http://eslint.cn/docs/rules/no-dupe-class-members)

  ```js
  // ✗ avoid
  class Dog {
    bark () {}
    bark () {}
  }
  ```

* **禁止在象字面量中定义重复的属性名(key)**。

  eslint: [`no-dupe-keys`](http://eslint.cn/docs/rules/no-dupe-keys)

  ```js
  // ✗ avoid
  var user = {
    name: 'Jane Doe',
    name: 'John Doe'
  }
  ```

* **`switch` 语句中不要定义重复的 `case` 分支**。

  eslint: [`no-duplicate-case`](http://eslint.cn/docs/rules/no-duplicate-case)

  ```js
  // ✗ avoid
  switch (id) {
    case 1:
      // ...
    case 1:
  }
  ```

* **同一模块有多个导入时一次性写完**。

  eslint: [`no-duplicate-imports`](http://eslint.cn/docs/rules/no-duplicate-imports)

  ```js
  // ✗ avoid
  import { myFunc1 } from 'module'
  import { myFunc2 } from 'module'

  // ✓ ok
  import { myFunc1, myFunc2 } from 'module'
  ```

* **禁止解构空值**。

  eslint: [`no-empty-pattern`](http://eslint.cn/docs/rules/no-empty-pattern)

  ```js
  // ✗ avoid
  const { a: {} } = foo
  const [] = foo

  // ✓ ok
  const { a: { b } } = foo
  const [a, b] = foo
  ```

* **不要使用 `eval()`**。

  eslint: [`no-eval`](http://eslint.cn/docs/rules/no-eval)

  ```js
  // ✗ avoid
  eval( "var result = user." + propName )

  // ✓ ok
  var result = user[propName]
  ```

* **禁止在 `catch` 中对错误重新赋值**。

  eslint: [`no-ex-assign`](http://eslint.cn/docs/rules/no-ex-assign)

  ```js
  // ✗ avoid
  try {
    // ...
  } catch (e) {
    e = 'new value'
  }

  // ✓ ok
  try {
    // ...
  } catch (e) {
    const newVal = 'new value'
  }
  ```

* **禁止扩展原生对象**。

  eslint: [`no-extend-native`](http://eslint.cn/docs/rules/no-extend-native)

  ```js
  // ✗ avoid
  Object.prototype.age = 21
  ```

* **禁止不必要的 `bind`**。

  eslint: [`no-extra-bind`](http://eslint.cn/docs/rules/no-extra-bind)

  ```js
  // ✗ avoid
  const name = function () {
    getName()
  }.bind(user)

  // ✓ ok
  const name = function () {
    this.getName()
  }.bind(user)
  ```

* **禁止不必要的布尔转换**。

  eslint: [`no-extra-boolean-cast`](http://eslint.cn/docs/rules/no-extra-boolean-cast)

  ```js
  // ✗ avoid
  const result = true
  if (!!result) {
    // ...
  }

  // ✓ ok
  const result = true
  if (result) {
    // ...
  }
  ```

* **禁止使用多余的括号包裹函数**。

  eslint: [`no-extra-parens`](http://eslint.cn/docs/rules/no-extra-parens)

  ```js
  // ✗ avoid
  const myFunc = (function () { })

  // ✓ ok
  const myFunc = function () { }
  ```

* **`switch` 一定要使用 `break` 来将条件分支正常中断**。

  eslint: [`no-fallthrough`](http://eslint.cn/docs/rules/no-fallthrough)

  ```js
  // ✗ avoid
  switch (filter) {
    case 1:
      doSomething()
    case 2:
      doSomethingElse()
  }

  // ✓ ok
  switch (filter) {
    case 1:
      doSomething()
      break
    case 2:
      doSomethingElse()
  }

  switch (filter) {
    case 1:
    case 2:
      doSomething()
  }
  ```

* **禁止浮点数小数点前后必须有一个数字**。

  eslint: [`no-floating-decimal`](http://eslint.cn/docs/rules/no-floating-decimal)

  ```js
  // ✗ avoid
  const discount1 = .5
  const discount2 = 2.

  // ✓ ok
  const discount3 = 0.5
  const discount4 = 2.0
  ```

* **禁止对声明过的函数重新赋值**。

  eslint: [`no-func-assign`](http://eslint.cn/docs/rules/no-func-assign)

  ```js
  // ✗ avoid
  function myFunc () { }
  myFunc = myOtherFunc
  ```

* **禁止对全局只读对象重新赋值**。

  eslint: [`no-global-assign`](http://eslint.cn/docs/rules/no-global-assign)

  ```js
  // ✗ avoid
  window = {}
  ```

* **注意隐式的 `eval()`**。

  eslint: [`no-implied-eval`](http://eslint.cn/docs/rules/no-implied-eval)

  ```js
  // ✗ avoid
  setTimeout("alert('Hello world')")

  // ✓ ok
  setTimeout(function () { alert('Hello world') })
  ```

* **嵌套的代码块中禁止再定义函数**。

  eslint: [`no-inner-declarations`](http://eslint.cn/docs/rules/no-inner-declarations)

  ```js
  // ✗ avoid
  if (authenticated) {
    function setAuthUser () {}
  }
  function doSomethingElse() {
    if (test) {
      function doAnotherThing() { }
    }
  }

  // ✓ ok
  function doSomething() { }
  function doSomethingElse() {
    function doAnotherThing() { }
  }
  var fn
  if (test) {
    fn = function fnExpression() { }
  }
  ```

* **不要使用非法的空白符**。<br/>
  例外: 允许在字符串字面量与模板字面量中出现任何空白字符。

  eslint: [`no-irregular-whitespace`](http://eslint.cn/docs/rules/no-irregular-whitespace)

  ```js
  // ✗ avoid
  function myFunc () /*<NBSP>*/{}
  function thing() {
    return / <NBSP>regexp/
  }

  // ✓ ok
  function thing() {
    return ' <NBSP>thing';
  }
  const str = ` <NBSP>thing`
  ```

* **禁止使用 `__iterator__`**。

  eslint: [`no-iterator`](http://eslint.cn/docs/rules/no-iterator)

  ```js
  // ✗ avoid
  Foo.prototype.__iterator__ = function () {}
  foo.__iterator__ = function () {}
  foo['__iterator__'] = function () {}

  // ✓ ok
  var __iterator__ = foo
  ```

* **禁止同一作用域下与变量同名的标签**。

  eslint: [`no-label-var`](http://eslint.cn/docs/rules/no-label-var)

  ```js
  // ✗ avoid
  var score = 100
  function game () {
    score: 50
  }

  // ✓ ok
  var num = 100
  function game () {
    score: 50
  }
  ```

* **禁止使用标签语句**。

  eslint: [`no-labels`](http://eslint.cn/docs/rules/no-labels)

  ```js
  // ✗ avoid
  label:
    while (true) {
      break label
    }
  ```

* **禁止不必要的嵌套代码块**。

  eslint: [`no-lone-blocks`](http://eslint.cn/docs/rules/no-lone-blocks)

  ```js
  // ✗ avoid
  function myFunc () {
    {
      myOtherFunc()
    }
  }

  // ✓ ok
  function myFunc () {
    myOtherFunc()
  }
  ```

* **禁止混合使用空格与制表符作为缩进**。

  eslint: [`no-mixed-spaces-and-tabs`](http://eslint.cn/docs/rules/no-mixed-spaces-and-tabs)

* **除了缩进，不要使用多个空格**。

  eslint: [`no-multi-spaces`](http://eslint.cn/docs/rules/no-multi-spaces)

  ```js
  // ✗ avoid
  const id =    1234

  // ✓ ok
  const id = 1234
  ```

* **禁止使用多行字符串**。

  eslint: [`no-multi-str`](http://eslint.cn/docs/rules/no-multi-str)

  ```js
  // ✗ avoid
  const message = 'Hello \
                   world'

  // ✓ ok
  const message = 'Hello \n'
                + 'world'
  ```

* **`new` 创建对象实例后需要赋值给变量**。

  eslint: [`no-new`](http://eslint.cn/docs/rules/no-new)

  ```js
  // ✗ avoid
  new Character()

  // ✓ ok
  const character = new Character()
  ```

* **禁止使用 `Function` 构造器**。

  eslint: [`no-new-func`](http://eslint.cn/docs/rules/no-new-func)

  ```js
  // ✗ avoid
  var sum = new Function('a', 'b', 'return a + b')

  // ✓ ok
  var sum = function (a, b) {
    return a + b
  }
  ```

* **禁止使用 `Object` 构造器**。

  eslint: [`no-new-object`](http://eslint.cn/docs/rules/no-new-object)

  ```js
  // ✗ avoid
  var config = new Object()

  // ✓ ok
  var config = {}
  ```

* **禁止使用 `new require`**。

  eslint: [`no-new-require`](http://eslint.cn/docs/rules/no-new-require)

  ```js
  // ✗ avoid
  const appHeader = new require('app-header')

  // ✓ ok
  const AppHeader = require('app-header')
  const appHeader = new AppHeader()
  ```

* **禁止使用 Symbol 构造器**。

  eslint: [`no-new-symbol`](http://eslint.cn/docs/rules/no-new-symbol)

  ```js
  // ✗ avoid
  const foo = new Symbol('foo')

  // ✓ ok
  const foo = Symbol('foo')
  ```

* **禁止使用原始包装器(`String`、`Number`、`Boolean`)**。

  eslint: [`no-new-wrappers`](http://eslint.cn/docs/rules/no-new-wrappers)

  ```js
  // why
  var stringObject = new String('Hello world')
  var text = 'Hello world'
  console.log(typeof stringObject) // 'object'
  console.log(typeof text)         // 'string'

  // ✗ avoid
  const message = new String('hello')

  // ✓ ok
  const message = 'hello'
  const message = String('hello')
  ```

* **禁止将全局对象作为函数调用**。

  eslint: [`no-obj-calls`](http://eslint.cn/docs/rules/no-obj-calls)

  ```js
  // ✗ avoid
  const math = Math()
  const json = JSON()

  // ✓ ok
  const area = function (r) {
    return Math.PI * r * r
  }
  const json = JSON.parse('{}')
  ```

* **禁止使用八进制字面量**。

  eslint: [`no-octal`](http://eslint.cn/docs/rules/no-octal)

  ```js
  // ✗ avoid
  const num = 071 // 57

  // ✓ ok
  const num = '071'
  ```

* **禁止在字符串字面量中使用八进制转义字符(使用 Unicode 转义序列代替)**。

  eslint: [`no-octal-escape`](http://eslint.cn/docs/rules/no-octal-escape)

  ```js
  // ✗ avoid
  const copyright = 'Copyright \251'

  // ✓ ok
  const copyright = 'Copyright \u00A9'
  ```

* **使用 `__dirname` 和 `__filename` 时禁止使用字符串拼接**。

  eslint: [`no-path-concat`](http://eslint.cn/docs/rules/no-path-concat)

  ```js
  // ✗ avoid
  const pathToFile = __dirname + '/app.js'

  // ✓ ok
  const pathToFile = path.join(__dirname, 'app.js')
  const fullPath = path.resolve(__dirname, 'app.js')
  ```

* **禁止使用 `__proto__` 属性，使用 `getPrototypeOf` 代替**。

  eslint: [`no-proto`](http://eslint.cn/docs/rules/no-proto)

  ```js
  // ✗ avoid
  const foo = obj.__proto__

  // ✓ ok
  const foo = Object.getPrototypeOf(obj)
  ```

* **禁止重复声明变量**。

  eslint: [`no-redeclare`](http://eslint.cn/docs/rules/no-redeclare)

  ```js
  // ✗ avoid
  let name = 'John'
  let name = 'Jane'

  // ✓ ok
  let name = 'John'
  name = 'Jane'
  ```

* **禁止正则表达式字面量中出现多个空格**。

  eslint: [`no-regex-spaces`](http://eslint.cn/docs/rules/no-regex-spaces)

  ```js
  // ✗ avoid
  const regexp = /test   value/

  // ✓ ok
  const regexp = /test {3}value/
  const regexp = new RegExp('foo {3}bar')
  const regexp = /test value/
  ```

* **`return` 语句中的赋值必须有括号包裹**。

  eslint: [`no-return-assign`](http://eslint.cn/docs/rules/no-return-assign)

  ```js
  // ✗ avoid
  function sum (a, b) {
    return result = a + b
  }

  // ✓ ok
  function sum (a, b) {
    return (result = a + b)
  }
  ```

* **禁止将变量赋值给自己**。

  eslint: [`no-self-assign`](http://eslint.cn/docs/rules/no-self-assign)

  ```js
  // ✗ avoid
  name = name
  [a, b] = [a, b]

  // ✓ ok
  name = firstName
  [a, b] = [b, a]
  ```

* **禁止将变量与自己进行比较操作**。

  esint: [`no-self-compare`](http://eslint.cn/docs/rules/no-self-compare)

  ```js
  // ✗ avoid
  if (score === score) {}
  ```

* **禁止使用逗号(`,`)操作符**。

  eslint: [`no-sequences`](http://eslint.cn/docs/rules/no-sequences)

  ```js
  // ✗ avoid
  if (doSomething(), !!test) {}

  // ✓ ok
  doSomething()
  if (!!test) {}
  ```

* **禁止更改关键字的值**。

  eslint: [`no-shadow-restricted-names`](http://eslint.cn/docs/rules/no-shadow-restricted-names)

  ```js
  // ✗ avoid
  let undefined = 'value'
  ```

* **禁止使用稀疏数组（Sparse arrays）**。

  eslint: [`no-sparse-arrays`](http://eslint.cn/docs/rules/no-sparse-arrays)

  ```js
  // ✗ avoid
  const fruits = ['apple',, 'orange']

  // ✓ ok
  const fruits = ['apple', 'orange']
  ```

* **禁止使用制表符**。

  eslint: [`no-tabs`](http://eslint.cn/docs/rules/no-tabs)

* **正确使用 ES6 中的字符串模板**。

  eslint: [`no-template-curly-in-string`](http://eslint.cn/docs/rules/no-template-curly-in-string)

  ```js
  // ✗ avoid
  const message = 'Hello ${name}'

  // ✓ ok
  const message = `Hello ${name}`
  ```

* **禁止在构造函数中，在调用 `super()` 之前使用 `this` 或 `super`**。

  eslint: [`no-this-before-super`](http://eslint.cn/docs/rules/no-this-before-super)

  ```js
  // ✗ avoid
  class Dog extends Animal {
    constructor () {
      this.legs = 4
      super()
    }
  }

  // ✓ ok
  class Dog extends Animal {
    constructor () {
      super()
      this.legs = 4
    }
  }
  ```

* **用 `throw` 抛错时，抛出 `Error` 对象而不是字符串**。

  eslint: [`no-throw-literal`](http://eslint.cn/docs/rules/no-throw-literal)

  ```js
  // ✗ avoid
  throw 'error'

  // ✓ ok
  throw new Error('error')
  ```

* **行末不留空格**。

  eslint: [`no-trailing-spaces`](http://eslint.cn/docs/rules/no-trailing-spaces)

* **禁止使用 `undefined` 来初始化变量**。

  eslint: [`no-undef-init`](http://eslint.cn/docs/rules/no-undef-init)

  ```js
  // ✗ avoid
  let name = undefined

  // ✓ ok
  let name
  ```

* **循环语句中禁用一成不变的循环条件(注意更新循环变量)**。

  eslint: [`no-unmodified-loop-condition`](http://eslint.cn/docs/rules/no-unmodified-loop-condition)

  ```js
  // ✗ avoid
  for (let i = 0; i < items.length; j++) {...}

  // ✓ ok
  for (let i = 0; i < items.length; i++) {...}
  ```

* **如果有更好的实现，尽量不要使用三元表达式**。

  eslint: [`no-unneeded-ternary`](http://eslint.cn/docs/rules/no-unneeded-ternary)

  ```js
  // ✗ avoid
  let score = val ? val : 0
  let isYes = answer === 1 ? true : false
  let isNo = answer === 1 ? false : true

  // ✓ ok
  let score = val || 0
  let isYes = answer === 1
  let isNo = answer !== 1
  ```

* **`return`，`throw`，`continue` 和 `break` 后不要再跟代码**。

  eslint: [`no-unreachable`](http://eslint.cn/docs/rules/no-unreachable)

  ```js
  // ✗ avoid
  function doSomething () {
    return true
    console.log('never called')
  }
  ```

* **禁止在 `finally` 代码块中出现控制流语句**。

  eslint: [`no-unsafe-finally`](http://eslint.cn/docs/rules/no-unsafe-finally)

  ```js
  // ✗ avoid
  try {
    return 1
  } catch (e) {
    return 2
  } finally {
    return 42
  }

  // ✓ ok
  try {
    return 1
  } catch (e) {
    return 2
  } finally {
    console.log(42)
  }
  ```

* **关系运算符的左值不要做取反操作**。

  eslint: [`no-unsafe-negation`](http://eslint.cn/docs/rules/no-unsafe-negation)

  ```js
  // ✗ avoid
  if (!key in obj) {}

  // ✓ ok
  if (!(key in obj)) {}
  ```

* **避免不必要的 `.call()` 和 `.apply()`**。

  eslint: [`no-useless-call`](http://eslint.cn/docs/rules/no-useless-call)

  ```js
  // why
  // 函数的调用可以写成 Function.prototype.call() 和 Function.prototype.apply()，但是 Function.prototype.call() 和 Function.prototype.apply() 比正常的函数调用效率低。

  // ✗ avoid
  sum.call(null, 1, 2, 3)
  ```

* **避免使用不必要的计算值作对象属性**。

  eslint: [`no-useless-computed-key`](http://eslint.cn/docs/rules/no-useless-computed-key)

  ```js
  // ✗ avoid
  const user = { ['name']: 'John Doe' }

  // ✓ ok
  const user = { name: 'John Doe' }
  ```

* **禁止多余的构造器**。

  eslint: [`no-useless-constructor`](http://eslint.cn/docs/rules/no-useless-constructor)

  ```js
  // ✗ avoid
  class A extends B {
    constructor () {}
  }
  class A extends B {
    constructor () {
      super()
    }
  }
  class A extends B {
    constructor (...args) {
      super(...args)
    }
  }

  // ✓ ok
  class A extends B {
    constructor () {
      doSomething()
    }
  }
  class A extends B {
    constructor () {
      super('foo')
    }
  }
  class A extends B {
    constructor (...args) {
      super()
      doSomething()
    }
  }
  ```

* **禁止不必要的转义**。

  eslint: [`no-useless-escape`](http://eslint.cn/docs/rules/no-useless-escape)

  ```js
  // ✗ avoid
  let message = 'Hell\o'
  let message = '\" \# \e \! \@'

  // ✓ ok
  let message = 'Hello'
  let message = '\' " # e ! @ '
  ```

* **`import`, `export` 和解构操作中，禁止赋值到同名变量**。

  eslint: [`no-useless-rename`](http://eslint.cn/docs/rules/no-useless-rename)

  ```js
  // ✗ avoid
  import { config as config } from './config'
  const { name: name } = person

  // ✓ ok
  import { config } from './config'
  const { name: newName } = person
  ```

* **属性前面不要加空格**。

  eslint: [`no-whitespace-before-property`](http://eslint.cn/docs/rules/no-whitespace-before-property)

  ```js
  // ✗ avoid
  user .name

  // ✓ ok
  user.name
  ```

* **禁止使用 `with`**。

  eslint: [`no-with`](http://eslint.cn/docs/rules/no-with)

  ```js
  // ✗ avoid
  with (val) {...}
  ```

* **对象属性换行时注意统一代码风格**。

  eslint: [`object-property-newline`](http://eslint.cn/docs/rules/object-property-newline)

  ```js
  // ✗ avoid
  const user = {
    name: 'Jane Doe', age: 30,
    username: 'jdoe86',
  }

  // ✓ ok
  const user = { name: 'Jane Doe', age: 30, username: 'jdoe86' }
  const user = {
    name: 'Jane Doe', age: 30, username: 'jdoe86',
  }
  const user = {
    name: 'Jane Doe',
    age: 30,
    username: 'jdoe86',
  }
  ```

* **禁止块语句开始或末尾有空行**。

  eslint: [`padded-blocks`](http://eslint.cn/docs/rules/padded-blocks)

  ```js
  // ✗ avoid
  if (user) {

    const name = getName()

  }

  // ✓ ok
  if (user) {
    const name = getName()
  }
  ```

* **展开运算符与它的表达式间不要留空白**。

  eslint: [`rest-spread-spacing`](http://eslint.cn/docs/rules/rest-spread-spacing)

  ```js
  // ✗ avoid
  fn(... args)

  // ✓ ok
  fn(...args)
  ```

* **遇到分号时空格要后留前不留**。

  eslint: [`semi-spacing`](http://eslint.cn/docs/rules/semi-spacing)

  ```js
  // ✗ avoid
  for (let i = 0 ;i < items.length ;i++) {...}

  // ✓ ok
  for (let i = 0; i < items.length; i++) {...}
  ```

* **代码块首尾留空格**。

  eslint: [`space-before-blocks`](http://eslint.cn/docs/rules/space-before-blocks)

  ```js
  // ✗ avoid
  if (admin){...}

  // ✓ ok
  if (admin) {...}
  ```

* **圆括号间不留空格**。

  eslint: [`space-in-parens`](http://eslint.cn/docs/rules/space-in-parens)

  ```js
  // ✗ avoid
  foo( 'bar');
  foo('bar' );
  foo( 'bar' );

  // ✓ ok
  foo('bar');
  ```

* **一元运算符后面跟一个空格**。

  eslint: [`space-unary-ops`](http://eslint.cn/docs/rules/space-unary-ops)

  ```js
  // ✗ avoid
  typeof!admin
  ++ foo
  foo --
  - foo
  + '3'

  // ✓ ok
  typeof !admin
  ++foo
  foo--
  -foo
  +'3'
  ```

* **注释首尾留空格**。

  eslint: [`spaced-comment`](http://eslint.cn/docs/rules/spaced-comment)

  ```js
  // ✗ avoid
  //comment
  /*comment*/

  // ✓ ok
  // comment
  /* comment */
  /*
   * This is a comment with a whitespace at the beginning
   */
  /*
  This comment has a newline
  */
  //--------------
  // Comment block
  //--------------
  ```

* **模板字符串中变量前后不加空格**。

  eslint: [`template-curly-spacing`](http://eslint.cn/docs/rules/template-curly-spacing)

  ```js
  // ✗ avoid
  const message = `Hello, ${ name }`

  // ✓ ok
  const message = `Hello, ${name}`
  ```

* **使用 `isNaN()` 检测 `NaN`**。

  eslint: [`use-isnan`](http://eslint.cn/docs/rules/use-isnan)

  ```js
  // ✗ avoid
  if (price === NaN) { }

  // ✓ ok
  if (isNaN(price)) { }
  ```

* **用合法的字符串跟 `typeof` 进行比较操作**。

  eslint: [`valid-typeof`](http://eslint.cn/docs/rules/valid-typeof)

  ```js
  // ✗ avoid
  typeof foo === 'strnig'
  typeof foo == 'undefimed'
  typeof bar != 'nunber'
  typeof bar !== 'fucntion'

  // ✓ ok
  typeof foo === 'string'
  typeof foo === 'undefined'
  typeof bar != 'number'
  typeof bar !== 'function'
  ```

* **自调用匿名函数 (IIFEs) 使用括号包裹**。

  eslint: [`wrap-iife`](http://eslint.cn/docs/rules/wrap-iife)

  ```js
  // ✗ avoid
  const getName = function () { }()

  // ✓ ok
  const getName = (function () { }())
  const getName = (function () { })()
  ```

* **`yield *` 中的 `*` 前后都要有空格**。

  eslint: [`yield-star-spacing`](http://eslint.cn/docs/rules/yield-star-spacing)

  ```js
  // ✗ avoid
  yield* increment()
  yield *increment()

  // ✓ ok
  yield * increment()
  ```

* **请书写优雅的条件语句（avoid Yoda conditions）**。

  eslint: [`yoda`](http://eslint.cn/docs/rules/yoda)

  ```js
  // why
  // Yoda: 在条件判断表达式中，字面量在前，变量在后，这种叫 Yoda，类似星球大战中 Yoda 的讲话方式
  // if ('red' === color) { } // Yoda 条件('红色是颜色')
  // if (color === 'red') { } // 非 Yoda 条件

  // ✗ avoid
  if (42 === age) { }
  if (true === flag) { }

  // ✓ ok
  if (age === 42) { }
  if (flag === true) { }
  ```

* **不要使用分号**。<br/>
  例外: 当一行代码以 `(`、`[` 开头时请在符号前加分号。

  eslint: [`semi`](http://eslint.cn/docs/rules/semi)

  ```js
  // ✗ avoid
  window.alert('hi');

  // ✓ ok
  window.alert('hi')
  ;(function() {
    // ...
  })()
  ;[1, 2, 3].map()
  ```

* **禁止使用 `(`、`[`、```作为一行的开始**。

  eslint: [`no-unexpected-multiline`](http://eslint.cn/docs/rules/no-unexpected-multiline)

  ```js
  // ✗ avoid
  (function () {
    window.alert('ok')
  }())
  [1, 2, 3].forEach(bar)
  `hello`.indexOf('o')

  // ✓ ok
  ;(function () {
    window.alert('ok')
  }())
  ;[1, 2, 3].forEach(bar)
  ;`hello`.indexOf('o')

  // good
  var nums = [1, 2, 3]
  nums.forEach(bar)
  ```

### JSX & React

* **强制在 JSX 属性中使用双引号 `""`**。

  eslint: [`jsx-quotes`](http://eslint.cn/docs/rules/jsx-quotes)

  ```js
  // ✗ avoid
  <a b='c' />

  // ✓ ok
  <a b="c" />
  <a b='"' />
  ```


```js
/*
'react/jsx-boolean-value': 'error',
'react/jsx-curly-spacing': ['error', 'never'],
'react/jsx-equals-spacing': ['error', 'never'],
'react/jsx-indent': ['error', 2],
'react/jsx-indent-props': ['error', 2],
'react/jsx-no-duplicate-props': 'error',
'react/jsx-no-undef': 'error',
'react/jsx-space-before-closing': 'error',
'react/jsx-uses-react': 'error',
'react/jsx-uses-vars': 'error',
'react/self-closing-comp': 'error'
*/
```
