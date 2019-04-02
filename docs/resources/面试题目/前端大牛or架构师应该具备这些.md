# 前端大牛or架构师应该具备这些

## 熟悉html5,css3,es6

#### 1.知道其特性，能解决其对应的兼容和性能问题

#### 2.完成页面语义化的改革进程

#### 3.将页面渲染效果优化，优化产品体验，实现样式的渐进式开发

#### 4.熟悉掌握样式编程化（less,sass,stylus中至少一种）、模块化的设计思路，完成前端组件

#### 5.基本的页面布局思路，浮动、盒模型、自适应、rem、flex,viewport等

#### 6.常见的ui框架以及jq插件的二次开发

#### 7.h5页面的制作

#### 8.canvas

---

## 精通javascript

#### 1.基础考核点：this,变量提升，闭包，原型链理解，常见对象的内置方法

#### 2.熟悉es6的新特性以及语法，善于模块化编程，考核点：变量类型、模块化编程、对象新增语法、新增数据结构、异步编程

#### 3.js插件或者自定义模块的编写

#### 4.js常见的编设计模式

- 解释

> 设计模式：在面向对象软件设计过程中，针对特定问题的简洁而优雅的解决方案。

简单说，设计模式就是针对某一类问题的常规手法；对不同问题有它对应的特定解决套路，把这种套路总结起来，就是各自那套完善的解决方案，也就是设计模式了。

- 单例模式

一般用于处理在一个生命周期中仅需要存在一次即可完成任务的内容来提升性能及可用性。

常见的有每个应用中的config配置。

- 策略模式

> 定义一系列的算法，把它们一个个封装起来，并且使它们可以相互替换。

**一个基于策略模式的程序至少由 2 部分组成:**
    1. 一组策略类，策略类封装了具体的算法，并负责具体的计算过程;
    2. 环境类 Context，该 Context 接收客户端的请求，随后把请求委托给某一个策略类

```js
class Bouns {
  salary: number = null; // 原始工资
  levelObj: IPerformance = null; // 绩效等级对应的策略对象

  constructor(salary: number, performanceMethod: IPerformance) {
    this.setSalary(salary);
    this.setLevelObj(performanceMethod);
  }

  setSalary(salary) {
    this.salary = salary; // 保存员工的原始工资
  }
  setLevelObj(levelObj) {
    this.levelObj = levelObj; // 设置员工绩效等级对应的策略对象
  }
  getResult(): number {
    if (!this.levelObj || !this.salary) {
      throw new Error("Necessary parameter missing");
    }
    return this.levelObj.calculate(this.salary);
  }
}
interface IPerformance {
  calculate(salary: number): number;
}

class PerformanceA implements IPerformance {
  calculate(salary) {
    return salary * 3;
  }
}

class PerformanceB implements IPerformance {
  calculate(salary) {
    return salary * 2;
  }
}

class PerformanceC implements IPerformance {
  calculate(salary) {
    return salary * 1;
  }
}

console.log(new Bouns(4000, new PerformanceA()).getResult());
console.log(new Bouns(2500, new PerformanceB()).getResult());
```

*Ng中的依赖注入，就是使用了策略模式的设计思路*。可以把每个服务看成是一个个策略，在组件/服务的构造函数中声明需要使用哪个服务（即选择策略），Angular的注入器就会将它的实例应用在这里。

- 迭代器模式

> 提供一种方法顺序一个聚合对象中各个元素，而又不暴露该对象内部表示。

Array中已经提供了许多迭代器方法如：map,reduce,some,every,find,forEach等。

- 中介者模式

- 备忘录模式

- 发布-订阅模式

> 定义了一种一对多的依赖关系，即当一个对象的状态发生改变的时候，所有依赖他的对象都会得到通知。

```js
const event = {
  peopleList: [],
  addEventListener: function(eventName, fn) {
    if (!this.peopleList[eventName]) {
      //如果没有订阅过此类消息，创建一个缓存列表
      this.peopleList[eventName] = [];
    }
    this.peopleList[eventName].push(fn);
  },
  dispatch: function() {
    let eventName = Array.prototype.shift.call(arguments);
    let fns = this.peopleList[eventName];
    if (!fns || fns.length === 0) {
      return false;
    }
    for (let i = 0, fn; (fn = fns[i++]); ) {
      fn.apply(this, arguments);
    }
  }
};
```

DOM的节点绑定事件就是最常见的发布-订阅模式。

- 适配器模式

> 是将一个类（对象）的接口（方法或属性）转化成客户希望的另外一个接口（方法或属性），适配器模式使得原本由于接口不兼容而不能一起工作的那些类（对象）可以一些工作。

适配器模式在前端项目中一般会用于做数据接口的转换处理，比如把一个有序的数组转化成我们需要的对象格式：

```js
const arr = ["Javascript", "book", "前端编程语言", "8月1日"];
function arr2objAdapter(arr) {
  // 转化成我们需要的数据结构
  return {
    name: arr[0],
    type: arr[1],
    title: arr[2],
    time: arr[3]
  };
}

const adapterData = arr2objAdapter(arr);
```

- 参考：

[JavaScript 常见设计模式](https://juejin.im/post/5c80f57f51882532cd57b64d)

#### 5.jq,zepto的使用体验，其基本语法以及其核心思想

#### 6.手机端手势事件

---

## 持续关注业界的新话题和新技术

#### 1.研究过ng、react、vue的一种或以上，知道其原理

- 三者的区别？为什么选择angular？

[怎样在vue，angular，react快速选择一个合适的框架](https://blog.csdn.net/weixin_41879988/article/details/81638474)

beflamNext是一个用于开发tms、wms应用的平台，它是一个比较大型的项目。我们选中angular正好就是看中了它对大型项目的良好支持。react、vue是更关注view层的库，他们需要搭配其他库才可以构建一个大型项目。而angular是一整套解决方案的框架，它拥有良好的项目结构，model、view、controller天然分层，html、css、js也天然分层，结构清晰，在开发和维护上可以减少很多不必要的麻烦；同时它有一套完整的构建工具（Angular-CLI），创建、运行、编译、打包都非常快捷，不用在去配合其他构建工具；默认支持ts，它是支持ES6的，同时我们可以很好的做到类型检测。

**Angular**

1. MVVM设计模式；
2. 组件化；

    模块化和组件化的出现，都是为了提高网页开发效率、提高代码复用率、降低块与块之间的耦合性的问题。

    组件化更关注UI部分，页面的每个部件，比如头部、内容区、弹出框、按钮等都可以成为一个组件，每个组件都有独立的HTML、css、js代码。它可以放在页面的任意位置，也可以和其他组件一起形成新的组件。一个页面是各个组件的结合，可以根据需要进行组装。

    模块化侧重功能的封装，主要是争对js代码，隔离、组织js代码，将它封装成一个个具有特定功能的模块，比如验证模块、消息处理模块等等。

    [前端模块化、组件化的理解](https://www.cnblogs.com/chenzechuang/p/6559351.html)

    [浅谈前端架构的工程化、模块化、组件化、规范化](http://outofmemory.cn/html/front-end-project-component)

    - 模块化：CommonJS -> AMD -> CMD -> ES6

3. 脏值检查；

- 什么是脏值检查？

所谓脏值检查就是指存储所有变量的值，每当可能有变量发生变化时,就将所有的旧值与新值进行比较，不相等就说明检测到变化，需要更新对应的视图。

Angular把页面切分成若干个Component(组件)，组成一棵组件树。进入脏值检测后，从根组件自顶向下进行检测。Angular有两种策略：Default和OnPush。它们配置在组件上，决定脏值检测过程中不同的行为。

- 数据何时变化？
    1. 用户输入操作，比如点击，提交等；
    2. 请求服务端数据；
    3. 定时事件，比如setTimeout，setInterval。

- 如何通知变化？

Angular2是一个MVVM框架。数据模型（Model）转换成视图模型（ViewModel）后，绑定到视图（View）上渲染成肉眼可见的页面。因此，发现数据模型变化的时间点是更新页面的关键，也是调用脏值检测的关键。

经过分析，工程师们发现，数据的变化往往由macrotask和microtask等异步事件引起。因此，通过重写浏览器所有的异步API，就能从源头有效地监听数据变化。Zone.js就是这样一个猴子脚本（Monkey Patch）。Angular 4使用了一个定制化的Zone（NgZone），它会通知Angular可能有数据变化，需要更新视图中的数据（脏值检测）。

- Angular2的变更检测

Angular 中每个组件都有自己的变化检测器，这使得我们可以对每个组件分别控制如何以及何时进行变化检测。

由于每个组件都有其自己的变化检测器，即一个 Angular 应用程序由一个组件树组成，所以逻辑结果就是我们也有一个变化检测器树，这棵树也可以看作是一个有向图，数据总是从上到下流动。

数据从上到下的原因是因为变化检测也总是从上到下对每一个单独的组件进行，每一次从根组件开始，单向数据流比循环脏检查更可预测，我们总是可以知道视图中使用的数据来自哪里。

我们假设在组件树的某个地方触发一个事件，比如一个按钮被点击，zones 会进行事件的处理并通知 Angular，然后变化检测依次向下传递。

- ChangeDetectionStrategy

变更检测器用于检测变更的策略。

    1. Default：Angular默认的变化检测策略，也就是脏检查(只要有值发生变化，就全部检查)；
    2. OnPush：就是只有当输入数据的引用发生变化或者有事件触发时，组件进行变化检测。

```js
@Component({
  template: `
    <h2>{{vData.name}}</h2>
    <span>{{vData.email}}</span>
  `,
  changeDetection: ChangeDetectionStrategy.OnPush
})

class VCardCmp {
  @Input() vData;
}
```

> VCardCmp 只依赖于它的输入属性，如果它的输入没有改变，我们可以告诉 Angular 跳过这个组件的子树的变化检测;只有当输入数据的引用发生变化组件才进行变化检测。

- [ChangeDetectorRef](https://angular.cn/api/core/ChangeDetectorRef)

> Angular 各种视图的基础类，提供变更检测功能。 变更检测树会收集要检查的所有视图。 使用这些方法从树中添加或移除视图、初始化变更检测并显式地把这些视图标记为脏的，意思是它们变了、需要重新渲染。

    1. markForCheck()：当视图使用 OnPush（checkOnce）变更检测策略时，把该视图显式标记为已更改，以便它再次进行检查。*当输入已更改或视图中发生了事件时，组件通常会标记为脏的（需要重新渲染）。调用此方法会确保即使那些触发器没有被触发，也仍然检查该组件。*
    2. detach():从变更检测树中分离开视图。 已分离的视图在重新附加上去之前不会被检查。 与 detectChanges() 结合使用，可以实现局部变更检测。*即使已分离的视图已标记为脏的，它们在重新附加上去之前也不会被检查。*
    3. detectChanges()：检查该视图及其子视图。与 detach 结合使用可以实现局部变更检测。
    4. checkNoChanges():检查变更检测器及其子检测器，如果检测到任何更改，则抛出异常。*在开发模式下可用来验证正在运行的变更检测器是否引入了其它变更。*
    5. reattach()：把以前分离开的视图重新附加到变更检测树上。 视图会被默认附加到这棵树上。

[使用说明](https://angular.cn/api/core/ChangeDetectorRef#usage-notes)

- 总结

脏值检查就是存储所有变量的值，每当可能有变量发生变化时，就用新值跟旧值作比较，如果不一样就进行视图更新。

而用户输入操作、请求服务器数据、计时器等都可能引起数据变更。

数据变化往往都是由异步事件引起的，而zone.js改写了原生的异步事件api，它能从源头就有效的监听数据变化。Angular采用了定制的NgZone，它能通知angular可能有数据变化，需要进行视图变更。

- 参考文档
    - [再谈Angular4 脏值检测(性能优化)](https://www.jb51.net/article/138777.htm)
    - [Angular 2.x+ 脏检查机制理解](https://segmentfault.com/a/1190000009579737)
    - [angular2 脏检查总述--zone.js 原理](https://blog.csdn.net/u010977147/article/details/53785733)
    - [Change And Its Detection In JavaScript Frameworks](http://teropa.info/blog/2015/03/02/change-and-its-detection-in-javascript-frameworks.html)
    - [Angular2双向绑定及变化检测](https://www.jianshu.com/p/cee44e8831c9)

**补充一：ngForOf的优化**

`*ngFor`常常操作大量数据，所以性能需要被格外关注。而我们可以从变更检测上做相应的处理。下面是官方文档做出的说明：

> 变更的传导机制
> 
> 当迭代器的内容变化时，NgForOf 会对 DOM 做出相应的修改：
>
>     - 当新增条目时，就会往 DOM 中添加一个模板实例。
> 
>     - 当移除条目时，其对应的模板实例也会被从 DOM 中移除。
> 
>     - 当条目集被重新排序时，他们对应的模板实例也会在 DOM 中重新排序。
> 
> Angular 使用对象标识符（对象引用）来跟踪迭代器中的添加和删除操作，并把它们同步到 DOM 中。 这对于动画和有状态的控件（如用来接收用户输入的 <input> 元素）具有重要意义。添加的行可以带着动画效果进来，删除的行也可以带着动画效果离开。 而未变化的行则会保留那些尚未保存的状态，比如用户的输入。
> 
> 即使数据没有变化，迭代器中的元素标识符也可能会发生变化。比如，如果迭代器处理的目标是通过 RPC 从服务器取来的， 而 RPC 又重新执行了一次。那么即使数据没有变化，第二次的响应体还是会生成一些具有不同标识符的对象。Angular 将会清除整个 DOM， 并重建它（就仿佛把所有老的元素都删除，并插入所有新元素）。这是很昂贵的操作，应该尽力避免。
> 
> 要想自定义默认的跟踪算法，NgForOf 支持 trackBy 选项。 trackBy 接受一个带两个参数（index 和 item）的函数。 如果给出了 trackBy，Angular 就会使用该函数的返回值来跟踪变化。

我们可以看出，ngForOf在变更检测时，是通过一个默认函数来处理的。这个函数接收当前项并返回一些值(这个值是一个根据当前项生成的标识符对象)。然后将这个函数返回的值与该函数上次返回的值进行比较。如果值发生更改，将会执行刷新操作。所以，如果默认函数接收了一个对象引用(及时这个对象的内部值一样，它也是两个值不会恒等)的话，它将不匹配之前返回的值。

- 优化方式

```js
*ngFor = "let hero of heroes trackBy:trackByHeroes"

trackByHeroes(index : number, hero : Hero){
    return index;
}
```

[参考文档一](https://blog.csdn.net/zhao_tuo/article/details/79261083)、[参考文档二](https://stackoverflow.com/questions/44970386/how-is-angulars-ngfor-loop-implemented/44971440#44971440)

4. 服务与依赖注入；

- **简介**

- 服务

Angulkar把组件和服务区分开，以提高模块性和复用性。组件只管用户体验，它提供用于数据绑定的属性和方法，以便作为视图（由模板渲染）和应用逻辑（通常包含一些模型的概念）的中介者。

组件应该把诸如从服务器获取数据、验证用户输入或直接往控制台中写日志等工作委托给各种服务。通过把各种处理任务定义到可注入的服务类中，可以让它被任何组件使用。 通过在不同的环境中注入同一种服务的不同提供商，还可以让应用更具适应性。

通过把组件中和视图有关的功能与其他类型的处理分离开，可以让组件类更加精简、高效。

- 依赖注入（dependency injection）

DI 被融入 Angular 框架中，用于在任何地方给新建的组件提供服务或所需的其它东西。 组件是服务的消费者，也就是说，你可以把一个服务注入到组件中，让组件类得以访问该服务类。

在 Angular 中，要把一个类定义为服务，要使用 @Injectable() 装饰器来表明一个组件或其它类（比如另一个服务、管道或 NgModule）拥有一个依赖；同时用它来提供元数据，便让 Angular 可以把它作为依赖注入到组件中。

> 1. 注入器是主要的机制。Angular 会在启动过程中为你创建全应用级注入器以及所需的其它注入器。你不用自己创建注入器。
> 
> 2. 该注入器会创建依赖、维护一个容器来管理这些依赖，并尽可能复用它们。
> 
> 3. 提供商是一个对象，用来告诉注入器应该如何获取或创建依赖。

*使用的时候，在组件的构造器中建立关联*。

你的应用中所需的任何依赖，都必须使用该应用的注入器来注册一个提供商，以便注入器可以使用这个提供商来创建新实例。 对于服务，该提供商通常就是服务类本身。

当 Angular 创建组件类的新实例时，它会通过查看该组件类的构造函数，来决定该组件依赖哪些服务或其它依赖项。

当 Angular 发现某个组件依赖某个服务时，它会首先检查是否该注入器中已经有了那个服务的任何现有实例。如果所请求的服务尚不存在，注入器就会使用以前注册的服务提供商来制作一个，并把它加入注入器中，然后把该服务返回给 Angular。

当所有请求的服务已解析并返回时，Angular 可以用这些服务实例为参数，调用该组件的构造函数。

- 提供服务

对于要用到的任何服务，必须至少注册一个提供商。服务可以在自己的元数据中把自己注册为提供商，这样可以让自己随处可用。或者，你也可以为特定的模块或组件注册提供商。要注册提供商，就要在服务的 @Injectable() 装饰器中提供它的元数据，或者在@NgModule() 或 @Component() 的元数据中。

    1. 服务自身的@Injectable()的 providedIn ：通过将其与@NgModule或其他注入器类型关联，或指定其在"root"注入器中提供（默认），从而确定哪个注入器将提供注入表；而且在代码编译打包时,可以执行摇树优化，从而移除所有没在应用中使用过的服务。推荐使用此种方式注册服务；
    2. 特定的 NgModule 中的 providers 属性：该服务的同一个实例将会对该 NgModule 中的所有组件可用；
    3. 组件的@component() 的 providers 属性：会为该组件的每一个新实例提供该服务的一个新实例。

- 总结

创建可注入的服务，通过@Injectable()拥有一个依赖；Angular创建一个注入器，用来管理这些依赖，做到复用它们；提供商来告诉注入器在如何创建或获取依赖；最后在组件的构造器中创建关联，来获取这个依赖，即要求Angular在组件的构造函数中注入依赖项。

- [Angular依赖注入](https://angular.cn/guide/dependency-injection)


5. 路由工作原理、路由守卫；

  - 现在，任何用户都能在任何时候导航到任何地方。 但有时候这样是不对的：
    - 该用户可能无权导航到目标组件。
    - 可能用户得先登录（认证）。
    - 在显示目标组件前，你可能得先获取某些数据。
    - 在离开组件前，你可能要先保存修改。
    - 你可能要询问用户：你是否要放弃本次更改，而不用保存它们？

  - 你可以往路由配置中添加守卫，来处理这些场景。守卫返回一个值，以控制路由器的行为：
    - 如果它返回 true，导航过程会继续
    - 如果它返回 false，导航过程就会终止，且用户留在原地。
    - 如果它返回 UrlTree，则取消当前的导航，并且开始导航到返回的这个 UrlTree.

  - 路由器可以支持多种守卫接口：
    - 用CanActivate来处理导航到某路由的情况。
    - 用CanActivateChild来处理导航到某子路由的情况。
    - 用CanDeactivate来处理从当前路由离开的情况.
    - 用Resolve在路由激活之前获取路由数据。
    - 用CanLoad来处理异步导航到某特性模块的情况。

6. 组件生命周期；

生命周期的顺序：

|钩子                      |用途及时机|
|:---|:---|
|ngOnChanges()            | 当 Angular（重新）设置数据绑定输入属性时响应。 该方法接受当前和上一属性值的 SimpleChanges 对象。在 ngOnInit() 之前以及所绑定的一个或多个输入属性的值发生变化时都会调用。|
|ngOnInit()               | 在 Angular 第一次显示数据绑定和设置指令/组件的输入属性之后，初始化指令/组件。在第一轮 ngOnChanges() 完成之后调用，只调用一次。|
|ngDoCheck()              | 检测，并在发生 Angular 无法或不愿意自己检测的变化时作出反应。在每个变更检测周期中，紧跟在 ngOnChanges() 和 ngOnInit() 后面调用。|
|ngAfterContentInit()     | 每当 Angular 把外部内容投影进组件/指令的视图之后调用。第一次 ngDoCheck() 之后调用，只调用一次。|
|ngAfterContentChecked()  | 每当 Angular 完成被投影组件内容的变更检测之后调用。ngAfterContentInit() 和每次 ngDoCheck() 之后调用|
|ngAfterViewInit()        | 每当 Angular 初始化完组件视图及其子视图之后调用。第一次 ngAfterContentChecked() 之后调用，只调用一次。|
|ngAfterViewChecked()     | 每当 Angular 做完组件视图和子视图的变更检测之后调用。ngAfterViewInit() 和每次 ngAfterContentChecked() 之后调用。|
|ngOnDestory()            | 每当 Angular 每次销毁指令/组件之前调用并清扫。 在这儿反订阅可观察对象和分离事件处理器，以防内存泄漏。在 Angular 销毁指令/组件之前调用。|

7. 事件发射器；

    `EventEmitter`：用于指令和组件中同步或异步地发出自定义事件，并通过订阅实例为这些事件注册处理程序。
    ```js
        @Component({
      selector: 'zippy',
      template: `
      <div class="zippy">
        <div (click)="toggle()">Toggle</div>
        <div [hidden]="!visible">
          <ng-content></ng-content>
        </div>
     </div>`})
    export class Zippy {
      visible: boolean = true;
      @Output() open: EventEmitter<any> = new EventEmitter();
      @Output() close: EventEmitter<any> = new EventEmitter();
     
      toggle() {
        this.visible = !this.visible;
        if (this.visible) {
          this.open.emit(null);
        } else {
          this.close.emit(null);
        }
      }
    }
    
    <zippy (open)="onOpen($event)" (close)="onClose($event)"></zippy>
    ```

8. 延迟(懒)加载；

    ```js
    const routes: Routes = [
      {
        path: 'customers',
        loadChildren: './customers/customers.module#CustomersModule'
      },
      {
        path: 'orders',
        loadChildren: './orders/orders.module#OrdersModule'
      },
      {
        path: '',
        redirectTo: '',
        pathMatch: 'full'
      }
    ];
    
    import { NgModule } from '@angular/core';
    import { CommonModule } from '@angular/common';
    import { CustomersRoutingModule } from './customers-routing.module';
    import { CustomerListComponent } from './customer-list/customer-list.component';

    @NgModule({
      imports: [
        CommonModule,
        CustomersRoutingModule
      ],
      declarations: [CustomerListComponent]
    })
    export class CustomersModule { }
    ```

9. [编译(AOT、JIT)](https://angular.cn/guide/aot-compiler)；

  Angular应用主要由组件及其HTML模板组成，由于浏览器无法直接理解Angular所提供的组件和模板，因此Angular应用程序需要先进行编译才能在浏览器中运行。

  Angular提供了两种编译方式：

    - 即时编译（JIT）：它会在运行期间在浏览器中编译应用（ng build(仅编译)、ng serve(编译并启动本地服务器)这两个CLI命令默认为JIT编译方式）；
    - 预先编译（AOT）：它会在构建时编译应用。

- 为什么需要 AOT 编译？
  1. 渲染得更快

      使用 AOT，浏览器下载预编译版本的应用程序。 浏览器直接加载运行代码，所以它可以立即渲染该应用，而不用等应用完成首次编译。

  2. 需要的异步请求更少

      编译器把外部 HTML 模板和 CSS 样式表内联到了该应用的 JavaScript 中。 消除了用来下载那些源文件的 Ajax 请求。

  3. 需要下载的 Angular 框架体积更小

     如果应用已经编译过了，自然不需要再下载 Angular 编译器了。 该编译器差不多占了 Angular 自身体积的一半儿，所以，省略它可以显著减小应用的体积。
    
  4. 提早检测模板错误

      AOT 编译器在构建过程中检测和报告模板绑定错误，避免用户遇到这些错误。

  5. 更安全

     AOT 方式会在发给客户端之前就把 HTML 模板和组件编译成 JavaScript 文件。 不需要读取模板，也没有客户端组装 HTML 或执行 JavaScript 的危险操作，受到注入类攻击的机会也比较少。

10. 模块；
11. [动态组件](https://angular.cn/guide/dynamic-component-loader)；

  [Compiler](https://angular.cn/api/core/Compiler)


12. Observable与RxJS；

    RxJS提供了一种异步事件分发机制，在angular中主要用于实现变更检测和事件传播。

13. 构建(底层webpack)；
- dependencies：运行应用的基础；
    1. Angularr的核心和可选模块：包名以`@angular/`开头；
    2. 支持包：Angular应用运行时必须的第三方库：`rxjs`、`zone.js`；
    3. 腻子脚本：负责抹平不同浏览器的js实现之间的差异：`core-js;`
- decDependencies：只有在开发应用时才会用到;
    |包名|说明|
    |:---|:---|
    |@angular‑devkit/build‑angular |Angular 构建工具。|
    |@angular/cli 	|Angular CLI 工具。|
    |@angular/compiler‑cli 	|Angular 编译器，Angular CLI 的 ng build 和 ng serve 命令会调用它。|
    |@angular/language‑service 	|Angular 语言服务会分析组件模板并给出类型信息和错误信息，支持 TypeScript 的编辑器可以使用它来提升开发体验。具体的例子可参见 VS Code 的 Angular 语言服务扩展。|
    |@types/... 	|第三方库（如 Jasmine、Node.js）的 TypeScript 类型定义文件。|
    |codelyzer 	|Angular 应用的风格检查器（linter），它可以为满足 Angular 风格指南中的规则提供保障。|
    |jasmine/... 	|用于支持 Jasmine 测试库的包。|
    |karma/... 	|用于支持 karma 测试运行器的包。|
    |protractor 	|一个针对 Angular 应用的端到端 (e2e) 测试框架。基于 WebDriverJS 构建。|
    |ts-node 	|供 Node.js 使用的 TypeScript 运行环境和 REPL。|
    |tslint 	|一个静态分析工具，它可以检查 TypeScript 代码的可读性、可维护性和功能性方面的错误。|
    |typescript 	|TypeScript 语言的服务提供者，包括 TypeScript 编译器 tsc。|
 - 底层webpack：
    ```js
        "webpack-dev-server": "~2.7.1",
        "webpack": "~3.7.1",
        "autoprefixer": "^6.5.3",
        "css-loader": "^0.28.1",
        "cssnano": "^3.10.0",
        "exports-loader": "^0.6.3",
        "file-loader": "^1.1.5",
        "html-webpack-plugin": "^2.29.0",
        "less-loader": "^4.0.5",
        "postcss-loader": "^1.3.3",
        "postcss-url": "^5.1.2",
        "raw-loader": "^0.5.1",
        "sass-loader": "^6.0.3",
        "source-map-loader": "^0.2.0",
        "istanbul-instrumenter-loader": "^2.0.0",
        "style-loader": "^0.13.1",
        "stylus-loader": "^3.0.1",
        "url-loader": "^0.6.2",
        "circular-dependency-plugin": "^3.0.0",
        "webpack-concat-plugin": "1.4.0",
        "copy-webpack-plugin": "^4.1.1"
    ```
    
*拓展一、Webpack*

- 核心概念：
    1. Entry：入口，Webpack执行构建的第一步将从Entry开始，可抽象成输入；
    2. Module：模块，在Webpack里一切皆模块，一个模块对应着一个文件，Webpack会从配置的Entry开始递归找出所有依赖的模块；
    3. Chunk：代码块，一个Chunk由多个模块组合而成，用于代码合并与分割；
    4. Loader：模块转换器，用于把模块原内容按照需求转换成新内容；
    5. Plugin：拓展插件，在Webpack构建流程中的特定时机注入扩展逻辑来改变构建结果或做你想要的事情；
    6. Output：输出结果，在Webpack经过一系列处理并得出最终想要的代码后输出结果。
    
> Webpack 启动后会从 Entry 里配置的 Module 开始递归解析 Entry 依赖的所有 Module。 每找到一个 Module， 就会根据配置的 Loader 去找出对应的转换规则，对 Module 进行转换后，再解析出当前 Module 依赖的 Module。 这些模块会以 Entry 为单位进行分组，一个 Entry 和其所有依赖的 Module 被分到一个组也就是一个 Chunk。最后 Webpack 会把所有 Chunk 转换成文件输出。 在整个流程中 Webpack 会在恰当的时机执行 Plugin 里定义的逻辑。

14. 跨域；
15. 双向数据绑定；

[ControlValueAccessor](https://angular.cn/api/forms/ControlValueAccessor)

16. TypeScript；
17. npm；
    1. npm 模块安装机制：
        - 发出npm install命令；
        - 查询node_modules目录之中是否已经存在指定模块：
            - 若存在，不再重新安装；
            - 若不存在：
                - npm 向 registry 查询模块压缩包的网址；
                - 下载压缩包，存放在根目录下的.npm目录里；
                - 解压压缩包到当前项目的node_modules目录。
    2. npm 实现原理

        输入 npm install 命令并敲下回车后，会经历如下几个阶段（以 npm 5.5.1 为例）：
        1. 执行工程自身 preinstall

            当前 npm 工程如果定义了 preinstall 钩子此时会被执行。
        2. 确定首层依赖模块
        
            首先需要做的是确定工程中的首层依赖，也就是 dependencies 和 devDependencies 属性中直接指定的模块（假设此时没有添加 npm install 参数）。工程本身是整棵依赖树的根节点，每个首层依赖模块都是根节点下面的一棵子树，npm 会开启多进程从每个首层依赖模块开始逐步寻找更深层级的节点。
        3. 获取模块

            获取模块是一个递归的过程，分为以下几步：
            - 获取模块信息。在下载一个模块之前，首先要确定其版本，这是因为 package.json 中往往是 semantic version（semver，语义化版本）。此时如果版本描述文件（npm-shrinkwrap.json 或 package-lock.json）中有该模块信息直接拿即可，如果没有则从仓库获取。如 packaeg.json 中某个包的版本是 ^1.1.0，npm 就会去仓库中获取符合 1.x.x 形式的最新版本。
            - 获取模块实体。上一步会获取到模块的压缩包地址（resolved 字段），npm 会用此地址检查本地缓存，缓存中有就直接拿，如果没有则从仓库下载。
            - 查找该模块依赖，如果有依赖则回到第1步，如果没有则停止。
        4. 模块扁平化（dedupe）

            上一步获取到的是一棵完整的依赖树，其中可能包含大量重复模块。比如 A 模块依赖于 lodash，B 模块同样依赖于 lodash。在 npm3 以前会严格按照依赖树的结构进行安装，因此会造成模块冗余。

            从 npm3 开始默认加入了一个 dedupe 的过程。它会遍历所有节点，逐个将模块放在根节点下面，也就是 node-modules 的第一层。当发现有重复模块时，则将其丢弃。

            这里需要对重复模块进行一个定义，它指的是模块名相同且 semver 兼容。每个 semver 都对应一段版本允许范围，如果两个模块的版本允许范围存在交集，那么就可以得到一个兼容版本，而不必版本号完全一致，这可以使更多冗余模块在 dedupe 过程中被去掉。
        5. 安装模块

            这一步将会更新工程中的 node_modules，并执行模块中的生命周期函数（按照 preinstall、install、postinstall 的顺序）。

        6. 执行工程自身生命周期

            当前 npm 工程如果定义了钩子此时会被执行（按照 install、postinstall、prepublish、prepare 的顺序）。

            最后一步是生成或更新版本描述文件，npm install 过程完成。

**补充**

[Angular 2的12个经典面试问题汇总](https://www.cnblogs.com/mfmdaoyou/p/7389012.html)

#### 2.微信小程序，公众号开发

#### 3.支付宝服务窗开发

#### 4.前沿技术研究以及技术调研

#### 5.状态管理

[Angular 真的需要状态管理么？](https://www.itcodemonkey.com/article/9929.html)

[浅谈前端状态管理](http://web.jobbole.com/92397/)

---

## 具备服务端开发能力

#### 1.熟练使用一门非后端语言，如java,php；

#### 2.或者熟练掌握nodejs，熟悉express/koa等其中一种框架或以上

#### 3.了解mvc，mvvm的设计模式

[侃侃前端MVC设计模式](https://www.cnblogs.com/jinguangguo/p/3534422.html) 【1】

[浅析前端开发中的 MVC/MVP/MVVM 模式](https://www.cnblogs.com/zhouyangla/p/6936455.html) 【2】

**MVC**

- 定义

> MVC是一种设计模式，它将应用划分为3个部分：数据（模型）、展现层（视图）和用户交互（控制器）。换句话说，一个事件的发生是这样的过程：
>
> 1. 用户和应用产生交互。
> 2. 控制器的事件处理器被触发。
> 3. 控制器从模型中请求数据，并将其交给视图。
> 4. 视图将数据呈现给用户。
>
> 我们不用类库或框架就可以实现这种MVC架构模式。关键是要将MVC的每部分按照职责进行划分，将代码清晰地分割为若干部分，并保持良好的解耦。这样可以对每个部分进行独立开发、测试和维护。

- 特点：

MVC的View直接与Model打交道，Controller仅仅起一个“桥梁”作用，它负责把View的请求转发给Model，再负责把Model处理结束的消息通知View。Controller就是一个消息分发器。不传递数据（业务结果），Controller是用来解耦View和Model的，具体一点说，就是为了让UI与逻辑分离（界面与代码分离）。

- 关键点

    1.构造模型Model
    2.分离事件绑定，形成Controller
    3.维护模型Model（and 模型集合Model Collection），通过Model的改变，通知对应的View重新渲染
    4.分离View显示逻辑

- 实现

*详情见【2】*

   1. Model和View之间使用了观察者模式，View事先通过Controller调用Model提供的注册事件在Model上进行注册，进而观察Model；待将来Model上发生数据改变时，通过Controller调用Model的发射事件来通知View做出更新。
   2. View和Controller之间使用了策略模式，View在初始化时引入了Controller的实例(会调用Model提供的对数据处理的方法)来实现特定的响应策略(即对用户做出的不同操作绑定不同的响应事件)，如果要实现不同的响应策略只要用不同的Controller实例替换即可。
   3. 控制器是模型和视图之间的纽带，MVC将响应机制封装在controller对象中，当用户和你的应用产生交互时，控制器中的事件触发器就开始工作了。
   4. Model需要准备数据处理的方法、view的注册事件、数据变更的发射事件(即调用View的渲染事件)；
   5. View需要准备响应数据变更的渲染事件、响应策略的绑定事件；
   6. Controller需要准备初始化(Model、View)方法、响应策略的方法

**MVVM**

- 定义：

模型-视图-视图模型。MVVM把View和Model的同步逻辑自动化了。以前Presenter负责的View和Model同步不再手动地进行操作，而是交给框架所提供的数据绑定功能进行负责，只需要告诉它View显示的数据对应的是Model哪一部分即可。

- 特点：

    1. ViewModel是model和View的中间接口
    2. ViewMode提供View与Model数据之间的命令，即这里的data-bind的值，ViewModel中的方法
    3. UI的渲染均由ViewModel通过命令来控制
    
- 关键点：

    1. 数据绑定；
    
        目前主流框架实现数据绑定的方式大致如下：
        1. 数据劫持(Vue)；
        2. 发布-订阅模式(Knockout、Backbone)；
        3. 脏值检查(Angular)。
    2. 状态管理(angular中非必须)。
    
- 实现：

    1. Model仅关注数据本身；
    2. View使用模板语法来声明式的将数据渲染进DOM，当ViewModel对Model进行更新时，会通过数据绑定更新到View；
    3. ViewModel时整个模式的重点，业务逻辑都主要集中在此，核心是数据绑定。当Model发生变化，ViewModel就会自动更新；ViewModel变化，Model也会更新。

#### 4.nginx服务，集群服务

#### 5.linux基础

---

## 重视团队协作，沟通能力强

#### 1.善于发现工作流程、产品体验中的问题，且有较强的问题解决能力

#### 2.制定团队工作流程，协作机制

#### 3.善于与不同背景的人打交道

---

## 对前端工程化有一定的了解和实践

`前端工程化就是：代码模块化；功能组件化；打包、构建、发布自动化、流程化；以及开发规范`。[为前端工程之崛起而编程](https://juejin.im/post/5c77eecbf265da2d8532f345)

工程化就像是百叶箱一样，减少人的操作，把工作所需要的工具做到的标准化，工作的流程做到的标准化。同时把很多重复的工作交给了代码来做，保证高质，标准统一。

先从工具入手，工程化包括哪些方面：

  - 模块化与组件化: npm, es6,seajs, react/angularjs/Vue
  - 代码版本管理: git
  - 代码风格管理: jscs, editorconfig
  - 代码编译: babel, less,sass,scss, imgmin, csssprit, inline-svg
  - 代码质量管理 (QA): eslint, mocha
  - 代码构建: webpack
  - 项目脚手架: yeoman
  - 持续集成/持续交付/持续部署: jenkins
  - 本地化与国际化

进行工程化：
  - 在配置初始项目文件结构和基本文件依靠命令行（工具）自动生成。
  - 确定代码规范，缩进，换行，以及各种预编译工具less，coffee，保证输出代码的标准一致
  - 对JS文件是否规范化，进行单元测试，不用手动复制到jshint上去检测，现在配置grunt监听文件变动自动检验显示检验结果还可以通过配置构建工具自动刷新浏览器实现文件实时变动监听。
  - 以前压缩合并文件用手工复制到压缩工具然后复制到一个文件里面，现在配置一下 grunt，gulp可以做自动任务，实时编译，并且监测文件改变而做出响应。
  - 以前发布到服务器上，要手动使用 FTP 软件上传，现在也可以用工具自动打包上传。

#### 1.工程化的项目目录、开发流程、构建优化打包部署，自动化、工具化

[我们是如何做好前端工程化和静态资源管理](https://juejin.im/entry/5791e01a2e958a0065f74777)

#### 2.组件化，组件库，团队内的基础建设

#### 3.项目持续集成、优化以及一键部署，后续监测

#### 4.带领团队进行持续技改

---

## 有能力进行项目或者业务的技术选型

#### 1.根据不同业务进行准确的技术选型

#### 2.对不同的技术场景有一定的了解，

比如微信、支付宝、app，不同ua等
pc:react ,内部系统：ng,简单移动端：vue
pc:jq ，移动端zepto

---
## 制定前端的技术规范，制定文档

#### 1.持续关注前端的技术规范，整理技术文档

#### 2.监督执行团队内的代码质量

#### 3.整理记录团队内的技术解决方案

#### 4.带领团队完成技术基础建设，挺高团队开发效率

---
## 关注用户体验，与产品一起不断完善

#### 1.用户体验的三要素

#### 2.前端ued的规范化，友好化

#### 3.产品易用性研究

#### 4.公用产品组件库
