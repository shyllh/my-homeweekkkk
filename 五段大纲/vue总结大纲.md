





# 1.框架简介

mvc概念-Model-View-Controller，MVC是单向通信。也就是View跟Model，必须

通过Controller来承上启下

 用户操作View去改变Controller，Controller改变Model, Model再直接根据业务代码显示在View上。



![1565582271119](assets/1565582271119.png)

mvvm概念，**Model-View-ViewModel**

即模型-视图-视图模型。

模型（Model）：指的是后端传递的数据。

视图    (View)    ： 指的是所看到的页面。

视图模型(ViewModel)是mvvm模式的核心，它是连接view和model的桥梁。它有两个方向：

​		一是将模型（Model）转化成视图(View)，即将后端传递的数据转化成所看到的页面。实现的方式是：数据绑定。

​		二是将视图(View) 转化成模型(Model)，即将所看到的页面转化成后端的数据。

​		实现的方式是：DOM 事件监听。这两个方向都实现的，我们称之为数据的双向绑定。

相当于MVC的升级版，因为双向绑定，真正做到了View与数据逻辑分离，用JS去实现界面的值与Model的关联。



# MVVM

如今主流的web框架基本都采用的是MVVM模式，为什么放弃了MVC模式，转而投向了MVVM模式呢。在之前的MVC中我们提到一个控制器对应一个视图，控制器用状态机进行管理，这里就存在一个问题，如果项目足够大的时候，状态机的代码量就变得非常臃肿，难以维护。还有一个就是性能问题，在MVC中我们大量的操作了DOM，而大量操作DOM会让页面渲染性能降低，加载速度变慢，影响用户体验。最后就是当Model频繁变化的时候，开发者就主动更新View，那么数据的维护就变得困难。世界是懒人创造的，为了减小工作量，节约时间，一个更适合前端开发的架构模式就显得非常重要。这时候MVVM模式在前端中的应用就应运而生。

## Model

Model 层，对应数据层的域模型，它主要做域模型的同步。通过 Ajax/fetch 等 API 完成客户端和服务端业务 Model 的同步。在层间关系里，它主要用于抽象出 ViewModel 中视图的 Model。

## View

View是作为视图模板，用于定义结构、布局。它自己不处理数据，只是将ViewModel中的数据展现出来。此外为了和ViewModel产生关联，那么还需要做的就是数据绑定的声明，指令的声明，事件绑定的声明。这在当今流行的MVVM开发框架中体现的淋淋尽致。在示例图中，我们可以看到ViewModel和View之间是双向绑定，意思就是说ViewModel的变化能够反映到View中，View的变化也能够改变ViewModel的数据值。那如何实现双向绑定呢，例如有这个input元素：

```
<input type='text' v-model='message'>
```

## ViewModel

ViewModel起着连接View和Model的作用，同时用于处理View中的逻辑。在MVC框架中，视图模型通过调用模型中的方法与模型进行交互，然而在MVVM中View和Model并没有直接的关系，在MVVM中，ViewModel从Model获取数据，然后应用到View中。相对MVC的众多的控制器，很明显这种模式更能够轻松管理数据，不至于这么混乱。还有的就是处理View中的事件，例如用户在点击某个按钮的时候，这个行动就会触发ViewModel的行为，进行相应的操作。行为就可能包括更改Model,重新渲染View

现代开发模式？     20%表现层
vue/react

传统开发模式？     80%表现层
jQuery

## mvc 和mvvm的对比：

https://www.cnblogs.com/web-record/p/11757774.html

## 1.1 vue 了解:

​		是一套用于构建用户界面的**渐进式框架**。与其它大型框架不同的是，Vue 被设计为可以自底向上逐层应用。Vue 的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与[现代化的工具链](https://cn.vuejs.org/v2/guide/single-file-components.html)以及各种[支持类库](https://github.com/vuejs/awesome-vue#libraries--plugins)结合使用时，Vue 也完全能够为复杂的单页应用提供驱动。（核心是数据）

vue-cli  router  vueX（安装）

## 1.2 vue特点：

Ø  数据驱动，数据（模型层）、视图层和模型层分离 m v c（model view controller）

Ø  双向数据绑定：MVVM  (viewmodel)  model  view  (viewmodel)

Ø  SPA（Single Page Application）单页面应用  （所有页面都是同一路径，唯一变化就是锚点，不利于seo）

Ø  组件化、模块化   - （代码封装 复用 有利于后期代码维护） export  import 

Ø  国人开发 文档通俗 学习成本低



前端渲染  （拿到数据自己组装）    vs          后台渲染（直接返回需要的数据）
降低服务器负担、带宽压力小                        SEO、兼容性好、安全性高（后台数据不可见）
用户体验好



》SPA 单页应用的优缺点？ 

 一次性请求所有的 html js css资源  跳转时候不再请求资源

优点

​		1 页面之间切换 跳转迅速

​		2 资源只请求一次 减少对于服务器的压力 （10w）   

缺点

​		1 第一次加载慢 （懒加载，压缩，elemetui  ）

​		2  url不会发生变化 不太利于seo搜索引擎的收录 seo 为了百度，谷歌，收录排名

# 2.vue语法：

## 2.1 vue实例化对象

​         let app = new Vue({})    接收一个对象作为参数，主要用来配置Vue

## 2.2 vue配置项

​		el : 挂载点 把试图html 和vue绑定在一起

​		data：vue实例中的数据

![1562577406220](assets/1562577406220.png)

## 2.3 数据渲染

​		将data里面的数据项的内容，渲染到视图层：语法：{{数据项名称}}

​		v-html(可以解析html标签)  v-text == {{}}

![1562577801233](assets/1562577801233.png)

## 2.4 指令

​		在Vue中指令（Directives）是写在html标签上的带有 v- 前缀的特殊属性。指令的职责就是当其表达式的值改变时相应地将某些行为应用到 DOM 上

#### 2.4.1 数据绑定指令

本质上是一段业务逻辑的封装（函数） 一般用来封装和dom相关的操作 

v-text，v-html （对比取值表达式）v-model(类似于onchange，主要用于输入性组件，比如input)

![1562579385601](assets/1562579385601.png)

#### 2.4.2 属性指令

​		v-bind属性指令，将数据项绑定到属性上，例：img的src属性、a标签的href属性

​        ，样式相关的属性绑定  class 属性，（v-bind：可以省略用 ：代替）

​          :class属性值（v-bind）  表达式  对象  都可

​         如下，渲染图片路径

![1562580187558](assets/1562580187558.png)

​     

​		v-bind 可以用于任何属性，有两个属性有另外的写法class、style

​        class 有做深化处理（数组，表达式  对象）为什么用数组方式的class 举例：（每个月的销售冠军，给他加个   皇冠，数组方便处理，根据各种条件给他push等等）

![1562587945778](assets/1562587945778.png)

多种处理方式







![](assets/1562580842669.png)

style：

![1562588090775](assets/1562588090775.png)





课堂练习：实现一个简单的计算器加法

![1562588672818](assets/1562588672818.png)

```
  <input type="text" v-model="n1">+
  <input type="text" v-model="n2">=
```

{{parseInt(n1)+parseInt(n2)}}



下面用methods

```
methods: {
  sum(){
    return parseInt(this.n1)+parseInt(this.n2);
  }
}
```

#### 2.4.3 条件指令

v-if （显示隐藏是将dom元素整个添加或删除） v-else-if  v-else，v-show

V-show  显示隐藏（css--display:none）

**代码演示**（随即数大于0.5 输出sorry， 小于就输出Not sorry）：  

  <div>
      <div v-if="Math.random() > 0.5">
        Sorry
      </div>
      <div v-else>
        Not sorry
  </div>

#### 2.4.4 循环指令

v-for循环指令，用来遍历数组、对象等多个数据的

语法：v-for=”(value, key) in 数组|对象”

**代码演示：**

<div id="app">
  <ul>
    <li v-for="(val,index) in arr" :key="index">
      我是：{{val}}
    </li>
     <li v-for="(val,index) in arrName" :key="index">
      <span>我是外国人：{{val.name}}</span>
    </li>
  </ul>
</div>
<script>
  new Vue({
   el: '#app',
   data:{
      arr:['张三','李四','王五'],
      arrName:[
        {'name':'Tom'},
        {'name':'Jok'},
        {'name':'lily'}
        ]
  }
});  
</script>

常用的指令：

V-text  v-html  v-show  v-if   v-bind(:)  v-on(@)  v-for  v-model 

###### 自定义指令：

**代码展示：**

<div id="app">
  <ul>
    <li v-for="(val,index) in arr" :key="index" v-color="index">
      <span>我是：{{val}}</span>
    </li>
  </ul>
</div>
<script>
Vue.directive('color',function(ele,obj){
  if(obj.value%2==0){
      ele.style.backgroundColor='red';
  }else{
      ele.style.backgroundColor='blue';
  }
})
 new Vue({
   el: '#app',
   data:{
      arr:    ['张三','李四','王五'],
      arrName:[
        {'name':'Tom'},
        {'name':'Jok'},
        {'name':'lily'}
        ]
  }
})
</script>


练习：新闻列表的添加展示（包含添加，删除，列表展示，使用自定义指令实现背景色隔行展示）

练习2：（加上隔行换色）

![image-20230329081710806](C:/Users/18613/AppData/Roaming/Typora/typora-user-images/image-20230329081710806.png)

代码展示：

<div id="abc">
  <div>
    <input type='text' v-model="news" /><button @click="add()">添加新闻</button>
    <li v-for="(item,index) in arrName" :key="index" v-colors='index'><span>{{item.name}}</span><button @click='del(index)'>删除</button></li>
  </div>
</div>

<script>
//字定义指令选出背景色
Vue.directive('colors',function(ele,obj){
  if(obj.value%2==0){
    ele.style.backgroundColor='red'
  }else{
    ele.style.backgroundColor='green'
  }
})
//实例化对象
new Vue({
    el:"#abc",
    data:{
      news:'',
      arrName:[
        {'name':'Tom'},
        {'name':'Jok'},
        {'name':'lily'},
        {'name':'luck'},
        ]
    },
    methods: {
      add(){
          //this.arrName=[{'name':this.news},...this.arrName]
        this.arrName.push({'name':this.news});
      },
      del(index){
        if(confirm('确定删除吗')){
          this.arrName.splice(index,1);
        }
      }
    },
})
</script>

计算器作业：

<body><div id="abc"><div>

​    <input type='text' v-model='n1'/>

​    <input type='text' v-model='str'/>

​    <input type='text' v-model='n2'/>=

​    {{allstr}}

​    <button @click="more()">触发</button>

  </div>

</div>

</body>

<script>

//实例化对象

new Vue({

​    el:"#abc",

​    data:{

​      n1:0,

​      n2:0,

​      str:'',

​      allstr:0

​    },

​    methods: {

​        more(){

​          let val=0;

​          switch(this.str){

​            case '+':

​            this.allstr= parseInt(this.n1) + parseInt(this.n2);

​            break;

​          case '-':

​          this.allstr= this.n1 - this.n2;

​            break;

​          case '*':

​          this.allstr= this.n1 / this.n2;

​            break;

​          default:

​          this.allstr= this.n1 * this.n2;

​            break;

​          }

​          

​        },

​        sum(){

​          let val=0;

​          switch(this.str){

​            case '+':

​            val = parseInt(this.n1) + parseInt(this.n2);

​            break;

​          case '-':

​           val = this.n1 - this.n2;

​            break;

​          case '*':

​           val = this.n1 * this.n2;

​            break;

​          default:

​            val = this.n1 / this.n2;

​            break;

​          }

​          return val

​        }

​    },

})

</script>



## 2.5  Vue实例方法

语法：

 

methods:{

​      方法名:function(){ }

​      简化写法：

  方法名(){}

}

**计算器代码示例**

<div id="app">
  a:<input type='text' v-model="a"/>+
  b:<input type='text' v-model='b'>=
  {{sum()}}
</div>
<script>
  new Vue({
   el: '#app',
   data:{
      a:10,
      b:6
  },
  methods: {
    sum(){
      return parseInt(this.a)+parseInt(this.b)
    }
  },
})
</script>

## 2.6 计算属性语法

#### 2.6.1：计算属性

​			模板内使用表达式非常便利，但是如果在模板中放入太多的逻辑会让模板过重，且难以维护，所以对于任何复杂逻辑，都应当使用计算属性

computed:{

​      方法名:function(){}

​      方法名(){}

}

**字符串反转代码演示：**

<div id="app">
    <p>原字符串: {{ msg }}</p>
    <p>反转字符串: {{ rmovemsg }}</p>
</div>
<script>
  new Vue({
   el: '#app',
   data:{
      msg:'Tom'
  },
  computed: {
    rmovemsg:function(){
      return this.msg.split("").reverse().join('');
    }
  }
      methodes:{
      a(){
      return this.msg.split("").reverse().join('');
  }
  }
})
</script>

#### 2.6.2 计算属性vs 实例方法

Ø  计算属性有缓存，而实例方法没有缓存

Ø  使用计算属性的时候，{{计算属性名}}

​     使用实例方法时，{{方法名()}} 

​    参数的传递  实例方法可以传递参数 但计算属性不能

​     共同点：数据的监听 计算属性和实例 都会监听原数据（数据改变 逻辑重新执行）

#### 2.6.3 过滤器

​	过滤器，就是将数据被渲染到视图之前进行格式化处理，而不会修改作用域中原有的数据

原则是：左值右量（变量也可以不写）

语法：  **定义过滤器（全局过滤器** **局部过滤器）**

​		filters:{

​      	过滤器1:function(参数1,参数2…){}

​		//简写方式

​		过滤器2 (参数1,参数2…){}

​		}

​		Vue.filter()

说明：定义过滤器时，必须声明参数，并且参数1是固定的，指的是要操作的数据，剩余的参数是调用过滤器时传递进来的

 **使用过滤器**-》

{{变量名 | 过滤器1（） | 过滤器2….}}

组合使用

**代码演示：**

<div id="app">
    <dl>
        <dt>{{product.name}}</dt>
        <dd>{{product.price|toprice('$')|tejia}}</dd>
      </dl>
</div>
<script>
//全局过滤器
Vue.filter('toprice',function(data,str){
      if(str=='$'){
            return (data/6.5).toFixed(2)+str;
          }else{
            return data.toFixed(2)+str;
      }
    });
    Vue.filter('tejia',function(data){
      return data+'活动价格';
    });
    new Vue({
      el:'#app',
      data:{
        name:'这是一条测试的数据',
        product:{
          name:'手机',
          price:5000,
          time:15937893922
        }
      }
      //局部过滤器
      // filters:{
      //  toprice:function(data,str){
      //    if(str=='$'){
      //      return (data/6.5).toFixed(2)+str;
      //    }else{
      //      return data.toFixed(2)+str;
      //    }
      //  }
      // }
    });
</script>






了解并熟悉vue中的内置过滤器 https://www.cnblogs.com/sweeeper/p/5945914.html

vue.2.0 已经移除内置过滤器，不能使用





计算属性练习：

用计算属性实现一个购物车的功能

![image-20230330111530200](C:/Users/18613/AppData/Roaming/Typora/typora-user-images/image-20230330111530200.png)

![1562596397205](assets/1562596397205.png)

**代码演示：**

<div id="app">
    <ul>
        <li v-for="good of goods">
            <input type="checkbox" @click="checkbox(good)" />
            <span>商品名称:{{good.goodname}}</span>
            <input type="button" value="-" @click="changeNum(0,good)" />
            <input type="number" v-bind:value="good.num || 0" />
            <input type="button" value="+" @click="changeNum(1,good)" />
            <span>单价:{{good.price}}</span>
            <span>小计:{{((good.num*good.price)?(good.num*good.price):0)|price}}</span>
        </li>
    </ul>
    <p>总金额:{{allPrice | price}}</p>
</div>
<script>
var app = new Vue({
    el: '#app',
    data: {
        goods: [{
            'id': 0,
            'goodname': '肥皂',
            'price': 4.3
        }, {
            'id': 1,
            'goodname': '洗发水',
            'price': 34
        }, {
            'id': 2,
            'goodname': '洗衣粉',
            'price': 7.3
        }],
        goodnumber: null,
    },
    methods: {
        // 改变数量
        changeNum(arg1, item) {
            if (!item.num) {
                // $set是添加值
                this.$set(item, 'num', 0);
            }
            // 判断为真的时候为增加的方法,否则为假的方法
            if (arg1) {
                item.num++;
            } else {
                item.num--;
            }
        },
        // 设置选中与不选中
        checkbox(item) {
            if (item.active) {
                this.$set(item, 'active', false);
            } else {
                this.$set(item, 'active', true);
            }
            console.log(item);
        }
    },
    filters: {
        price(arg) {
            return arg.toFixed(2) + '元';
        }
    },
    computed: {
        // 计算总价
        allPrice() {
            var result = 0;
            for (var i in this.goods) {
                if (this.goods[i].active) {
                    result += this.goods[i].price * this.goods[i].num;
                }
            }
            return result;
        }
    }
})

</script>

vue $set设置值或者对象

https://www.cnblogs.com/goloving/p/10986120.html

# 3.vue事件处理

​		事件的定义：事件指的是用户和页面的交互行为

#### 3.1 事件处理器

语法：v-on:事件类型=“事件函数（）”       《=》   v-on:click="addUser()"

可以简写为：@事件类型=”事件处理函数” 《=》   @click = “ addUser() ”

代码演示：

<div id="app">
    <button v-on:click="addUser()">添加</button>
    <button @click="addUser()">新增</button>
    <input @blur="addUser()" type="text" value="123"/>
</div>
<script>
    new Vue({
        el:'#app',
        data:{
            name:'这是一条测试的数据'
        },
        methods:{
            addUser(){
                alert('你击中我了')
            }
        }
    });
</script>

#### 3.2  事件类型总结

l  属性事件：click、dbclick、mouseover、mouseout、mouseenter、mouseleave、mousedown、mouseup、mousemove

l  键盘事件：keydown、keyup、keypress

l  ui事件：scroll、resize、load、unload

l  表单事件：focus、blur、select、change、submit

事件方法，一般都放在methods 里面写

#### 3.3 事件对象

​		事件对象是用来获取当事件发生时，事件源的一些信息（状态），例如，当鼠标移动事件发生时，想获得鼠标的坐标等，就通过事件对象来获得

在Vue中当事件发生时，会自动给事件处理函数传递一个$event事件对象，不需要手动传递，只需要接收即可

**代码演示：**

<div id="app">
    <button v-on:click="addUser($event,11111)">添加</button>
    <button @click="addUser($event,11111)">新增</button>
</div>
<script>
    new Vue({
        el:'#app',
        data:{
            name:'这是一条测试的数据'
        },
        methods:{
            addUser(e,xxx){
                console.log(e)
                alert(e.clientX)
                alert(xxx)
                alert('你击中我了')
            }
        }
    });
</script>

#### 3.4 事件修饰符

​		在原生JavaScript中，通过  event.preventDefault()    阻止默认行为，

​													  event.stopPropagation()  阻止冒泡 

在Vue中通过事件修饰符阻止，vue给我们提供了丰富的事件修饰符

- .prevent，阻止默认行为
- .stop，     阻止事件冒泡
- .capture   冒泡改为捕获
- .self           只处理自己身上的事件，不理会冒泡或捕获
- .once        一次性事件，只执行一次
- .native      触发原生的事件（有时发现用一些第三方的组件库时，例如一个封装好的button按钮，绑定点击事件却没有任何作用，这时便需要加 .native）

**代码演示：**

<div id="app">
    <button v-on:click.once="addUser()">添加</button>
    <a href="https:www.baidu.com" @click.prevent='tagHreaf()'>我要去百度</a>
</div>
<script>
    new Vue({
        el:'#app',
        data:{
            name:'这是一条测试的数据'
        },
        methods:{
            tagHreaf(){
                alert('就是不让你跳转页面')
            },
            addUser(){
                alert('你击中我了')
            }
        }
    });
</script>



课堂练习：Tab 导航切换

![1562643706425](assets/1562643706425.png)

**代码演示：**

<div id="app">
    <div>
        <button v-for="(val,index) in arrTabs" @click="indexcode=index" :class="indexcode==index?'red':''">{{val.title}}</button>
    </div>
    <div v-for="(val,index) in arrTabs" v-if="indexcode==index">
        {{val.contents}}
    </div>
</div>
<script type="text/javascript">
    new Vue({
        el:'#app',
        data:{
            indexcode:0,
            arrTabs:[
                {'title':'军事新闻','contents':'1949年，中华人民共和国今天成立了'},
                {'title':'娱乐新闻','contents':'萧敬腾，来北京了今天看来是要下雨了'},
                {'title':'科技新闻','contents':'前端是世界上最好的语言'}
            ]
        }
    });
</script>

#### 3.5 表单的处理

我们在使用Vue处理表单数据的时候，通过v-model实现双向数据绑定

v-model会同时监视表单输入、模型数据的更新，如果表单内容变化了，模型中的变量会跟着变化，同样，模型中的变量发生变化了，视图层（界面也会跟着变化）

1，输入框

v-mode会将输入框的内容赋值给变量，同样，变量内容变化了，输入框的内容也跟着变

<input type="text" v-model='testdata'/>

2，复选框

<div id="app">
    <input type="checkbox" v-model='arrTabs' value="tom"/>tom
    <input type="checkbox" v-model='arrTabs' value="jack"/>jack
    <input type="checkbox" v-model='arrTabs' value="lucy"/>lucy
    <div>{{arrTabs}}</div>
</div>
<script type="text/javascript">
    new Vue({
        el:'#app',
        data:{
            arrTabs:[]
        }
    });
</script>

3，单选框

4，select列表

<div id="app">
    <select v-model="selectData">
        <option value="">请选择</option>
        <option value="Apple">苹果</option>
        <option value="blalala">香蕉</option>
    </select>
    <div>
        选择的水果是: {{selectData}}
    </div>
</div>
<script type="text/javascript">
    new Vue({
        el:'#app',
        data:{
            selectData:''
        }
    });
</script>


#### 3.6 v-model 修饰符

语法：v-model.修饰符=”变量” 《=》v-model.lazy="aaa"

- lazy，       文本框失去焦点后再去更新数据
- number，当输入数字时，字符串类型将自动转换为number（先输数字，截取前面的数字返回）
- trim，       删除文本框中的前后空格

**代码演示：**

<div id="app">
    <input type="text" v-model.lazy="num"/>
    {{num}}
</div>
<script type="text/javascript">
    new Vue({
        el:'#app',
        data:{
            num:''
        }
    });
</script>

作业：实现用户的注册页面，并且展示在当前页面的列表中

要求：包含，用户名，密码，昵称，性别，所属城市（三级联动），兴趣爱好（复选框）

**代码演示：**

 <div id="app">
    <form>
        用户名：  <input type="text" v-model='username'/><br><br>
        密码：    <input type="text" v-model='pwd'/><br><br>
        确认密码：<input type="text" v-model='ispwd'/><br><br>
        昵称：    <input type="text" v-model='ncik'/><br><br>
        性别：    <input type="radio" value="nan" v-model='sex'/>男<input type="radio" value="nv" v-model='sex' />女<br><br>
        所属城市：<select v-model="proindex">
                    <option v-for="(item,index) in citys" :value="index">{{item.name}}</option>
                </select>
                <select v-model="citindex">
                    <option v-for="(item,index) in citys[proindex].city" :value="index">{{item.name}}</option>
                </select>
                <select v-model="no">
                    <option v-for="(item,index) in citys[proindex].city[citindex].area" :value="index">{{item}}</option>
                </select>
                <br><br>
        兴趣爱好：<input type="checkbox" v-model='arrlike' value="爬山"/>爬山
                 <input type="checkbox" v-model='arrlike' value="旅游"/>旅游
                 <input type="checkbox" v-model='arrlike' value="看书"/>看书
                 <input type="checkbox" v-model='arrlike' value="看星星"/>看星星
    </form>
    <button @click='tijiao()'>提交</button>
    </div>

```
<script type="text/javascript">
    new Vue({
        el:'#app',
        data:{
            username:'',
            pwd:'',
            ispwd:'',
            ncik:'',
            sex:[],
            arrlike:[],
            citys:citys,
            selectData:'',
            proindex:0,//省的索引
            citindex:0,//市的索引 
            no:0      
        },methods: {
            tijiao(){
                console.log('用户名：'+this.username)
                console.log('密码：'+this.pwd)
                console.log('确认密码：'+this.ispwd)
                console.log('昵称：'+this.ncik)
                console.log('性别：'+this.ncik)
                console.log('城市：'+this.citys[this.proindex].city[this.citindex].area[this.no])
                console.log('爱好：'+this.arrlike)
            }
        },
    });
</script>
```



作业2：

1  总分  平均分   (reduce )

2  筛选  button 1 及格的  不及格 全部的   (filter)

3  排序  button  2 按成绩倒叙 按成绩正序 (sort)

4  增加学生  删除学生 修改学生分数

5  搜索功能 (按名称)       ( indexOf ) 

# 4.vue组件

#### 4.1 组件介绍

​        组件（component）是vue.js最强大的功能之一。组件的作用就是封装可重用的代码，通常一个组件就是一个功能体，便于在多个地方都能够调用这个功能体

传统页面：header concents footer

#### 4.2 组件分类

我们实例化的vue对象就是一个组件，是所有组件的跟组件         new Vue({}）

《1》全局组件（可以全局进行调用）

​        .全局组件必须写在Vue实例创建之前，才在该根元素下面生效；

​        .模板里面只能有一个根标签，不能有平行标签

​         语法：    

​		     Vue.component('myDiv',{

​                 template:"<h1>我就是一个小组件</h1>"

​             })

 			调用   使用范围（全局）   命名规范 （js用驼峰命名 html 帕斯卡 小写+ -）例如：<my-div></my-div>

​			 模板必须要有一个跟元素



《2》局部组件（我们也可以在实例选项中注册局部组件，这样组件只能在这个实例中使用）

​         1.属性名为components，s千万别忘了;

​         2.套路比较深，所以建议模板定义在一个全局变量里，代码看起来容易一点，如下：（模板标签比较多的时       			候，这样子写更加简洁规整）

​		3.问题：局部组件的使用步骤

​			1 声明局部组件  2 import from 引入 3 components 注册  4调用

​         **代码示例：**

<div id="app">
    <no-more></no-more>
</div>
<script type="text/javascript">
    var mychild={
        template:"<h2>我是个局部组件</h2>"
    }
    new Vue({
        el:'#app',
        data:{          
            num:''
        },
        components:{
            'noMore':mychild
        }
    });
</script>

   组件中的其他属性，可以和实例中的一样，但是data属性必须是一个函数：

​    **代码示例：**

<div id="app">
    <no-more></no-more>
</div>
<script type="text/javascript">
    var mychild={
        template:"<h2 @click='add()'>我是个局部组件:{{num}}</h2>",
        data:()=>{
            return {
                num:1000000
            }
        },
        methods:{
            add(){
                this.num++
            }
        }
    }
    new Vue({
        el:'#app',
        components:{
            'noMore':mychild
        }
    });
</script>



个别情况：

当使用 DOM 作为模板时 (例如，将`el`选项挂载到一个已存在的元素上)，你会受到 HTML 的一些限制，因为 Vue 只有在浏览器解析和标准化 HTML 后才能获取模板内容。尤其像这些元素`<ul>`，`<ol>`，`<table>`，`<select>`限制了能被它包裹的元素，而一些像`<option>`这样的元素只能出现在某些其它元素内部。

自定义组件`<no-more>`被认为是无效的内容，因此在渲染的时候会导致错误。变通的方案是使用特殊的`is`属性：

<div id="app">
    <li is="no-more"></li>
</div>
<script type="text/javascript">
    Vue.component("noMore",{
    template:"<h1>{{message}}</h1>",
    data:function(){
        return {
            message:"hello world"
        }
    }
    });
    new Vue({
        el:'#app',
    });
</script>

作业：组件实现，一个首页，要求包含头部(不使用组件)，尾部（组件），内容（组件）

https://www.59370.com/app/ads.html





#### 4.3组件中的相互通信

1，父传子

​	prop 是父组件用来传递数据的一个自定义属性。

​    父组件的数据需要通过 props 把数据传给子组件，子组件需要展示，需要用 props 选项声明 "prop"：

动态绑定-》

**代码示例1：**

        <div id='app'>   
            <my-div :name="name" :list='list'></my-div>
        </div>
        <script type="text/javascript">
           let myDiv = {
                template:`<div>
                {{name}}
                <li v-for="val in list" >{{val}}</li>
                </div>`,
                props:['name','list']
            }           
            new Vue({
                el:"#app",
                data:{
                    name:'我是父组件的name值',
                    list:['tom','jack','rols']
                    },
                components:{
                    myDiv:myDiv
                }
            })
        </script>

**代码示例：**

        <div id='div1'>   
            <com1 :title="title" @passsc="passHandler"></com1>   
        </div>
        <script type="text/javascript">
            var com1={
                template:`<div>我是chonlid输出标题：->{{title}}</div>`,
                props:['title'],
            }
                new Vue({
                el:'#div1',
                components:{com1},
                data:{
                    name:'这是一条测试的数据',
                    title:'我是父组件的title数据'
                },
                methods:{
                    passHandler:function(mimi){
                        alert(mimi);
                    }
                }
            });
        </script>

![1562668022809](assets/1562668022809.png)

u  **父组件先定义数据**

u  **在父组件的模板中，通过属性绑定把数据绑定在子组件上**

u  **在子组件中定义props属性，用来接收父组件传递的数据。**

u  **在子组件模板中使用数据**

u  **在子组件的函数中使用数据**



一   ，props特性

2.prosp类型
		a.字符串
		如：props:['title']
		b.数组
		如：props：[ 'title','auther','time' ]
		c以对象形式列出的名称：类型
		如：props:{
			title:String
			auther:Array
			time: String
		}

3、props验证（当 prop 验证失败的时候，(开发环境构建版本的) Vue 将会产生一个控制台的警告。）
a. type
类型：String、Number、Boolean、Array、Object、Data、Function、Symbol(用来表示独一无二的值),构造函数

Ø  type，类型约束，约束父组件给子组件传递的数据类型，类型可以是：Object、Array、

Number、String、Boolean

Ø  default，指定默认值，如果父组件没有传递数据，可以指定默认值

Ø  required，指定该数据项是否必须传递

![1562676208364](assets/1562676208364.png)

**代码示例：**

 <div id='app'>   
            <my-div  :list='list'></my-div>
        </div>
        <script type="text/javascript">
           let myDiv = {
                template:`<div>
                {{name}}
                <li v-for="val in list" >{{val}}</li>
                </div>`,
                props:{
                    name:{
                        type:String,
                        default:1999
                    },
                    list:String
                }
            }        
            num=12.987   
            new Vue({
                el:"#app",
                data:{
                    list:['tom','jack','rols']
                    },
                components:{
                    myDiv:myDiv
                }
            })
        </script>

二  ，非props特性：



单项数据流是什么概念？

子组件 不能 直接修改父组件传来的数据（父组件能修改子组件的数据） 如果要修改必须先声明成自己组件的数据 才能修改

子组件中 获取父组件

This.$parent(可以对父组件的数据进行操作)

**代码演示：**

 <div id='app'>   
            <my-div></my-div>
        </div>
        <script type="text/javascript">
           //我是子组件
           let myDiv = {
                template:`<div>
                {{this.$parent.title}}
                </div>`,
                methods: {
                    add(){
                        console.log(this.$parent.title)
                    }
                },
            }
            //我是父组件          
            new Vue({
                el:"#app",
                data:{
                    name:'sdsdsd',
                    title:'标题11'
                    },
                components:{
                    myDiv:myDiv
                }
            })
        </script>
<u>4，子传父</u>

子组件中的数据不能直接在父组件中使用

解决之道：如果子组件有一些数据，需要在父组件中使用，就得通过$emit传递给父组件

父组件是使用 props 传递数据给子组件，但如果子组件要把数据传递回去，就需要使用自定义事件！！！！！！！

我们可以使用 v-on 绑定自定义事件, 每个 Vue 实例都实现了事件接口(Events interface)，即：

- 使用 `$on(eventName)` 监听事件
- 使用 `$emit(eventName)` 触发事件

具体步骤：

Ø  在子组件中添加事件监听，通过$emit从子组件向父组件发射一个事件

Ø  在父组件中接收子组件发射过来的事件

​	格式：<子组件 @子组件事件名=”父组件要执行的方法”>

​     注意：子组件上面的事件名****@addmsg****不能是驼峰法**

Ø  在父组件中定义方法接收子组件传递的事件以及数据



**代码演示：**（子组件传值给父组件）

<div id='div1'>   
        <com1  @passsc="parentMethods"></com1>   
    </div>
    <script type="text/javascript">
        var com1={
            template:`
                    <button @click="cbtn">子传父</button>              
            `,
            data:function(){
                return {
                    sc:'这是子组件的秘密'
                }
            },
            methods:{
                cbtn:function(){
                    //发送事件 相当于打电话
                    this.$emit('passsc',this.sc);
                }
            }
        }
        new Vue({
            el:'#div1',
            components:{com1},
            methods:{
                parentMethods:function(mimi){
                    console.log(mimi)
                    alert(mimi);
                }
            }
        });
    </script>

Ø  组件练习  toolist（要求列表的数组在父组件中定义，而展示是在子组件中）

![1562682613486](assets/1562682613486.png)

**代码展示：**

<div id='div1'>
    早自习迟到的人：
    <input type="text" v-model='name'/><button @click="addUser">添加</button>
    <my-data :list="list" @parentdel="pdel"></my-data>
</div>
<script>
Vue.component('myData', {
  template: `<div>
                <h4 v-for="(val,index) in list">{{val}}<button @click="del(index)">删除</button></h4>         
            </div>`,
  props:['list'],
  methods:{
        del:function(idx){
                this.$emit('parentdel',idx);
            }
        }
    })
    new Vue({
        el:"#div1",
        data:{
            name:'',
            list:['tom','jack']
        },
        methods: {
            addUser(){
                if(this.name==''){
                    return 
                }
                this.list.push(this.name)
            },
            pdel(index){
                this.list.splice(index,1);
            }
        },  
    })
</script>

<u>5，练习</u>

练习---评论功能

练习---留言板

 



由于评论的功能将来在项目的多个地方都会使用，所以我们将其设计为组件，从而提

升代码的重用性，所以我们将上面的留言板设计为2个组件：**留言列表、添加留言**



**练习--商品列表展示**：



#### 4.4  插槽

https://www.cnblogs.com/chinabin1993/p/9115396.html

​	一句话：插槽内可以是任意内容。

　　　先看一下下面的代码：声明一个child-component组件，

　　　如果现在我想在<child-component></child-component>内放置一些内容，结果会是怎样？

​           输出内容还是在组件中的内容，在 <child-component>内写的内容没起作用。

解释：没有插槽的情况下在组件标签内些一些内容是不起任何作用的，当我在组件中声明了slot元素后，在组件元素内写的内容就会跑到它这里了！

》2、默认插槽 <slot></slot>

》3、具名插槽。父类。v-slot:myslot      <slot name="zidingyi"></slot>

》4、作用域插槽（插槽可以控制html模板的显示与不显示。作用域插槽其实就是带数据的插槽。）

原来父组件可以通过绑定数据传递给子组件。作用域插槽就可以通过子组件绑定数据传递给父组件。

slot-scope就相当于是一个对象，这个对象里面的数据就是子组件插槽绑定传上来了。

https://blog.csdn.net/mobius_z/article/details/80363853（版本变化）

**代码示例：**

<div id='div1'>
    <my-data>普通插槽</my-data>
    <my-data>                
        <template slot='myslot'>
                        具名插槽
        </template>
    </my-data>
    <my-data v-slot:myheightslot>vue 2.6 以上写法具名插槽</my-data>
</div>
<script>
Vue.component('myData', {
  template: `<div>
                <h4>你好</h4>
                <slot></slot>
                <slot name='myslot'></slot> 
                <slot name='myheightslot'></slot>   
            </div>`,
    })
    new Vue({
        el:"#div1",
        data:{
        }
    })
</script>

作用域插槽代码演示：

<div id='div1'>
    <my-data :list="list">
            <template scope="slotProps">
            {{slotProps.user}}
        </template>
    </my-data>
</div>
<script>
Vue.component('myData', {
    props:['list'],
  template: `<div>
                <h4>你好</h4>
                <slot :user="list"><slot>
            </div>`,
    })
    new Vue({
        el:"#div1",
        data:{
            list:['tom','jack']
        }
    })
</script>

代码演示2：

<div id="root">
    <child>
            <template scope="qq"><!--定义一个插槽，该插槽必须放在template标签内-->
                <h1>{{qq.ad}}</h1>
            </template>
    </child>
    <child></child>
</div>
<script>
    Vue.component('child',{
        data: function(){
            return {
                list:[1,2,3,4]
            }
        },
        template: '<div><ul><slot v-for="value in list" :ad=value></slot></ul></div>',
    })
    var vm=new Vue({
        el: '#root'
    })
</script>

作业：

用插槽实现折叠效果（点击收起，在点击释放）

![1562743461596](assets/1562743461596.png)

**代码示例**

<div id="app">
    <mydiv>
            <button @click="showdiv" >修改</button>
            <ul  v-show="isshou">
                <li>apple1</li>
                <li>apple2</li>
                <li>apple3</li>
            </ul>
        </mydiv>
</div>
<script>
        var mydiv={
            template:`
            <div>
                <slot></slot>
            </div>
            `
        };
    new Vue({
      el: '#app',
      data:function(){
            return {
                isshou:true
            }
        },
      components:{mydiv},
      methods:{
        showdiv:function(){
            this.isshou=!this.isshou
        }
      }
    })
</script>

作业2：

实现一个留言板功能，要求：添加留言是一个模板，列表展示是一个模板

 1,用默认插槽实现一个面包屑 头部，可以在不同页面，显示不同的导航名字

  2，使用具名插槽实现一个选项卡的切换，比如娱乐新闻，军事新闻，政治新闻

  3，使用作用域插槽，实现在子组件中定义一个arr 数组对象，然后在父组件中，以插槽的方式，显示出列表

    <div id='div1'>
        <msgadd @passmsg="msgHandler"></msgadd>
        <msglist :pmsg="pmsg"></msglist>    
    </div>
    <script type="text/javascript">
        var msgadd={
            template:`
               <div>                
                <h3>请留言</h3>
                <textarea v-model="msg"></textarea>
                <button @click="clickHandler">提交留言</button> 
                </div>
            `,
            data:function(){
                return {
                    msg:''
                }
            },
            methods:{
                clickHandler:function(){
                    this.$emit('passmsg',this.msg);
                }
            }
        }
        var msglist={
            template:`
                <div>
                    <h3>留言列表</h3>
                    <ul>
                        <li v-for="(val,index) in list">{{val}}</li>                        
                    </ul>
                </div>
            `,
            props:['pmsg'],
            data:function(){
                return {
                    list:['这个商品不错','高端 大气上档次'],                 
                }
            },
            watch:{
                pmsg:function(pmsg){
                    this.list.push(pmsg)                    
                }
            },
        }
        new Vue({
            el:'#div1',
            components:{msgadd,msglist},
            data:function(){
                return {
                    pmsg:''
                }
            },
            methods:{
                msgHandler:function(msg){
                    this.pmsg=msg;
                }
            }
        });
    </script>

#### 4.5 深入理解Vue实例

​	每个 Vue 实例在被创建时都要经过一系列的初始化过程——例如，需要设置数据监听、编译模板、将实例挂载到 DOM 并在数据变化时更新 DOM 等。同时在这个过程中也会运行一些叫做**生命周期钩子**的函数，这给了用户在不同阶段添加自己的代码的机会。

看图说话：https://img-blog.csdnimg.cn/20190107221323124.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L21xaW5nbw==,size_16,color_FFFFFF,t_70

![https://img-blog.csdnimg.cn/20190107221323124.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L21xaW5nbw==,size_16,color_FFFFFF,t_70](https://img-blog.csdnimg.cn/20190107221323124.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L21xaW5nbw==,size_16,color_FFFFFF,t_70)

**代码展示：**

<div id="app">
    <p>{{ number }}</p>
        <input type="text" name="btnSetNumber" v-model="number">
</div>
<script>
var app = new Vue({         
    el: '#app',               
    data: {                   
    number: 1
    },
    beforeCreate: function () {
    console.log('beforeCreate 钩子执行...');
    console.log(this.number)
    },
    created: function () {
    console.log('cteated 钩子执行...');
    console.log(this.number)
    },
    beforeMount: function () {
    console.log('beforeMount 钩子执行...');
    console.log(this.number)
    },
    mounted: function () {
    console.log('mounted 钩子执行...');
    console.log(this.number)
    },
    beforeUpdate: function () {
    console.log('beforeUpdate 钩子执行...');
    console.log(this.number)
    },
    updated: function () {
    console.log('updated 钩子执行...');
    console.log(this.number)
    },
    beforeDestroy: function () {
    console.log('beforeDestroy 钩子执行...');
    console.log(this.number)
    },
    destroyed: function () {
    console.log('destroyed 钩子执行...');
    console.log(this.number)
    },
});
</script>

$refs 操作dom对象（可以操作dom和子组件，但是不建议操作组件）

代码演示：

<div id='app'>
        <input type="button" value="获取元素" @click="getElement" ref="mybtn">
        <h3 ref="myh3">哈哈哈哈哈</h3>
        <hr>
        <login ref="mylogin"></login>
</div>
<script>
var app = new Vue({         
    el: '#app',               
    data: {                   
    number: 1
    },
    methods:{
        getElement:function(){
            console.log(this.$refs.myh3)
        }
    }   
});
</script>

了解一些实例属性（vm.$data，vm.$props）$mount，成员方法，手动设置挂载点

代码演示：

<div id='div1'>
        <input type="" v-model="name" name="">
        {{name}}
    </div>
    <script type="text/javascript">
        var app=new Vue({
            // el:'#div1',
            data:{
                name:'这是一条测试的数据'
            },
            //数据的监听
            watch:{
                name:function(newname){
                    console.log(newname);
                }
            }
        });
        app.$mount('#div1');
        console.log(app.$el)
        console.log(app.$data)
    </script>

#### 4.6 动态组件

```
通过使用保留的 `<component>` 元素，动态地绑定到它的 `is` 特性，我们让多个组件可以使用同一个挂载点，并动态切换。根据 v-bind:is="组件名"
```

中的组件名去自动匹配组件，如果匹配不到则不显示。

keep-alive 包裹组件，，我们每次切换组件都会重新创建一次组件，使用keep-alive之后，会将创建过的组件保存在内存中，以后使用的时候直接使用，而不会每次重新创建

​    <keep-alive>

        <div :is="isnow"></div>
​    </keep-alive>

**代码演示：**

<div id='div1'>
    <button @click="upisnow">点击我随机切换组件</button>
    <div :is="isnow"></div>
</div>
<script type="text/javascript">
    var newdiv  = {template:"<h3>我是newdiv<h3>"}
    var newhome = {template:"<h4>我是newhome<h4>"}
    var newcom  = {template:"<h5>我是newcom<h5>"}
    var app=new Vue({
        el:'#div1',
        data:{
            isnow:'newdiv'
        },
        components:{newdiv,newhome,newcom},
        methods: {
            upisnow:function(){
                arr = ['newdiv','newhome','newcom']
                this.isnow=arr[Math.floor(Math.random()*3)]//随机取arr，0~2
            }
        },
    });
</script>

课堂练习：使用动态组件实现选项卡的功能**************

**代码演示：**

 <div id="app">
            <div class="tabBar">
                    <ul>
                        <li v-for='(item,index) in list' @mouseover='changeindex(index)'><a href="#">{{item}}</a></li>             
                    </ul>
                </div>
                <div :is='isdiv'>
                    内容
                </div>
            </div>

```
        <script>
            var mydiv={template:`<div>首页的内容</div>`};
            var myciv={template:`<div>关于的内容</div>`};
            var myniv={template:`<div>购物车的内容</div>`};
            var mysiv={template:`<div>个人中心</div>`};
            new Vue({
              el: '#app',
              data:function(){
                    return {
                        isshou:true,
                        list:['首页','关于','购物车','个人中心'],
                        isdiv:'mydiv',
                        arr:['mydiv','myciv','myniv','mysiv',]
                    }
                },
              components:{mydiv,myciv,myniv,mysiv},
              methods:{
                changeindex(index){
                    this.isdiv=this.arr[index]
                }
              }
            })
        </script>
```

#### 5.Vue.js 过渡 & 动画 

​	Vue 在插入、更新或者移除 DOM 时，提供多种不同方式的应用过渡效果。

​     Vue 提供了内置的过渡封装组件，该组件用于包裹要实现过渡效果的组件。

语法格式：

```
<transition name = "nameoftransition">
   <div></div>
</transition>
```

过渡其实就是一个淡入淡出的效果。Vue在元素显示与隐藏的过渡中，提供了 6 个 class 来切换：

- `v-enter`：定义进入过渡的开始状态。在元素被插入之前生效，在元素被插入之后的下一帧移除。
- `v-enter-active`：定义进入过渡生效时的状态。在整个进入过渡的阶段中应用，在元素被插入之前生效，在过渡/动画完成之后移除。这个类可以被用来定义进入过渡的过程时间，延迟和曲线函数。
- `v-enter-to`: **2.1.8版及以上** 定义进入过渡的结束状态。在元素被插入之后下一帧生效 (与此同时 `v-enter` 被移除)，在过渡/动画完成之后移除。
- `v-leave`:  定义离开过渡的开始状态。在离开过渡被触发时立刻生效，下一帧被移除。
- `v-leave-active`：定义离开过渡生效时的状态。在整个离开过渡的阶段中应用，在离开过渡被触发时立刻生效，在过渡/动画完成之后移除。这个类可以被用来定义离开过渡的过程时间，延迟和曲线函数。
- `v-leave-to`: **2.1.8版及以上** 定义离开过渡的结束状态。在离开过渡被触发之后下一帧生效 (与此同时 `v-leave` 被删除)，在过渡/动画完成之后移除。

![img](https://www.runoob.com/wp-content/uploads/2018/06/transition.png)

对于这些在过渡中切换的类名来说，如果你使用一个没有名字的 `<transition>`，则 `v-` 是这些类名的默认前缀。如果你使用了 `<transition name="my-transition">`，那么 `v-enter` 会替换为 `my-transition-enter`。

`v-enter-active` 和 `v-leave-active` 可以控制进入/离开过渡的不同的缓和曲线，

》》》》》》     哪些情况会执行动画《《《《

动画只在2个节点发生：

一个是进入：理解为从不显示到显示出来（v-show），从无到有。

一个是离开：理解为从显示到不显示出来（v-show），从有到无。 

条件渲染（使用v-if）根据条件控制元素添加、删除

条件展示（使用v-show）根据条件控制元素显示、隐藏



动态组件，多个组件切换（涉及到组件显示、隐藏）:is 

代码演示：实现一个显示和隐藏的动画效果

**代码演示：**

<style>
/* 可以设置不同的进入和离开动画 */
/* 设置持续时间和动画函数 */
.fade-enter-active, .fade-leave-active {
    transition: opacity 2s
}
.fade-enter, .fade-leave-to /* .fade-leave-active, 2.1.8 版本以下 */ {
    opacity: 0
}
</style>


<body>

<script src="https://cdn.staticfile.org/vue/2.2.2/vue.min.js"></script>
<div id='div1'>
    <button @click="upisnow">点击我随机切换组件</button>
    <transition name = "fade">
        <div :is="isnow"></div>
    </transition>
</div>
<script type="text/javascript">
    var newdiv  = {template:"<h3>我是newdiv<h3>"}
    var newhome = {template:"<h4>我是newhome<h4>"}
    var newcom  = {template:"<h5>我是newcom<h5>"}
    var app=new Vue({
        el:'#div1',
        data:{
            isnow:'newdiv'
        },
        created:function() {
            console.log('被创建了')
        },
        components:{newdiv,newhome,newcom},
        methods: {
            upisnow:function(){
                arr = ['newdiv','newhome','newcom']
                this.isnow=arr[Math.floor(Math.random()*3)]//随机取arr，0~2
            }
        },
    });
</script>

css动画效果：

​	CSS 动画用法类似 CSS 过渡，但是在动画中 v-enter 类名在节点插入 DOM 后不会立即删除，而是在 animationend 事件触发时删除。

**代码演示：**

<style>
    .bounce-enter-active {
      animation: bounce-in .5s;
    }
    .bounce-leave-active {
      animation: bounce-in .5s reverse;
    }
    @keyframes bounce-in {
      0% {
        transform: scale(0);
      }
      50% {
        transform: scale(1.5);
      }
      100% {
        transform: scale(1);
      }
    }
    </style>

<div id = "databinding">
<button v-on:click = "show = !show">点我</button>
<transition name="bounce">
    <p v-if="show">我是一个css动画效果！！！</p>
</transition>
</div>
<script type = "text/javascript">
new Vue({
    el: '#databinding',
    data: {
        show: true
    }
})
</script>


如果要使用animate.css

需要使用：npm 安装

npm install animate.css *--save*



import animate from 'animate.css'

Vue.use(animate)



如果在某个组件，或者页面使用可以这样

import 'animate.css'

// 或者

require('animate.css');




除了上面在transition组件上增加name属性，来实现动画效果之外，Vue还给我们提供了6个内置的类，可以直接在transition组件上使用：Vue的设计者这样设计，为了兼容animate.css这个框架

https://daneden.github.io/animate.css/

 https://www.cnblogs.com/e-cat/p/8439221.html（博客解释）

l  enter-class，相当于.v-enter效果

l  enter-active-class，相当于.v-enter-active 

l  enter-to-class(2.1.8之后)

l  leave-class

l  leave-active-class

l  leave-to-class(2.1.8之后)

 

结合vue.js和animate.css动画框架实现一些动态效果

我们不需要指定开始、结束状态时的css样式，因为在animate.css中已经指定了

**代码演示：**

<div id = "app">
  <button v-on:click = "show = !show">点我</button>
  <transition
    name="custom-classes-transition"
    enter-active-class="animate__animated animate__tada"
    leave-active-class="animate__animated animate__bounce"
  >
    <p v-if="show">hello</p>
  </transition>
</div>
<script type = "text/javascript">
new Vue({
    el: '#app',
    data: {
        show: true
    }
})
</script>


列表过渡：     transition-group

给一组元素 添加动画效果 代码测试：

**代码示例：**

<style>
    .v-enter,.v-leave-to{
        opacity: 0;
    }
    .v-enter-active,.v-leave-active{
        transition: opacity 1s;
    }
</style>

<div id="app">
        <transition-group>
        <div v-for="item  of list" :key="item.id">
            {{item.title}}-{{item.id}}
        </div>
        </transition-group>
        <button @click="handleAdd">Add</button>
    </div>
    <script>
        var count = 0;
        new Vue({
            el: '#app',
            data:{
                list:[]
            },
            methods:{
                handleAdd:function(){
                    this.list.push({
                        id: count++,
                        title: 'hello vue'
                    })
                }
            }
        })
    </script>

​      

# 5.Vue.js响应式

https://blog.csdn.net/qq_41463701/article/details/86603875





1. 通过Object.defineProperty监听数据的get,set来做一些我们想去做的事情(像是vue vdom数据更新的updateComponent)

2. 将data属性代理到了vm上

3. 模拟：代码演示

   4. <body>
          <p id='p1'></p>
      ​    <input type='text' id='input1' name='input1'>
      </body>

   <script>
       var p1 = document.getElementById('p1');
       var inpu1 = document.getElementById('input1');
       var obj = {
           name:'数据'
       }
       p1.innerHTML=obj.name
       inpu1.value=obj.name
       Object.defineProperty(obj,'name',{
           set:function(newdata){
               p1.innerHTML=newdata
               console.log('设置name')
           },
           get:function(newdata){
               console.log('获取name')
           }
       })
       input1.onchange=function(){
           obj.name=inpu1.value
       }
   </script>

# 6.vue路由

#### 6.1 基本路由

​	几个tab按钮，点击不同的tab按钮，在下面的div里面展示不同的内容，这个时候我们可以通过动态组件的方式实现此功能，但是，如果需要根据参数传递的不同，展示不同的内容的话，就需要用到我们的 路由了

路由代码示例：

    <script src="vue.js"></script>
    <script src="vue-router.js"></script>
    <div id='div1'>
        <div>
            <a href='baidu.com'>qu baidu</a>
            <!-- 使用 router-link 组件来导航. -->
            <!-- 通过传入 `to` 属性指定链接. -->
            <!-- <router-link> 默认会被渲染成一个 `<a>` 标签 -->
            <router-link to="too">gotoo</router-link>
            <router-link to="flo">goflo</router-link>
        </div>
        <!-- 路由出口 -->
        <!-- 路由匹配到的组件将渲染在这里 -->
        <router-view></router-view>
    </div>
    <script type="text/javascript">
    // 0. 如果使用模块化机制编程，導入Vue和VueRouter，要调用 Vue.use(VueRouter)
    // 1. 定义（路由）组件。
    // 可以从其他文件 import 进来
    const too={template:`<div>too do someing</div>`}
    const flo={template:`<div>flo contents</div>`}
    // 2. 定义路由
    // 每个路由应该映射一个组件。 其中"component" 可以是
    // 通过 Vue.extend() 创建的组件构造器，
    // 或者，只是一个组件配置对象。
    // 我们晚点再讨论嵌套路由。
    const routes = [
        {path:'/flo',component:flo},
        {path:'/too',component:too}
    ]
    // 3. 创建 router 实例，然后传 `routes` 配置
    // 你还可以传别的配置参数, 不过先这么简单着吧。
    const router=new VueRouter({
        routes// （缩写）相当于 routes: routes
    });
    // 4. 创建和挂载根实例。
    // 记得要通过 router 配置参数注入路由，
    // 从而让整个应用都有路由功能
    new Vue({
        el:'#div1',
        data:{
            name:'这是一条测试的数据'
        },
        router:router
    });
    </script>

这种效果动态组件也能实现

router-link的一些属性：

tag(有时候想要  `<router-link>` 渲染成某种标签，例如 `<li>`), 

active-class(设置 链接激活时使用的 CSS 类名)，

event (声明可以用来触发导航的事件)

代码示例：

        <div>
            <router-link to="/too" append>go to too</router-link>
            <router-link to="/more" active-class="qqactive">go more </router-link>
        </div>

总结：<router-view></router-view>什么时候写

有路由规则的时候写，比如在App.vue里面

如果组件中有子路由那么这个当前组件也需要写router-view

另外：router-link加事件不生效（加上修饰符.native）

1： 因为它是自定义标签，根本就没有事件和方法，所以不触发，加个native 就是告诉vue 这个标签现在有主了 它是H5标签 可以加事件了。
2：父组件要想在子组件监听自己的click事件就得加native，router-link 其实就是一个封装好的 .vue 组件，所以需要 加.native修饰符才能绑定事件。



#### 6.2 嵌套路由

通俗的讲：嵌套路由就是在父组件，或者说父模板中 写路由，路由的书写，也放在父routes里用children

代码示例：

    <div id="app">
        <div>
            <router-link to="/too" active-class="qqactive">go to too</router-link>
            <router-link to="/more" active-class="qqactive">go more </router-link>
        </div>
        <router-view></router-view>
    </div>
    <script>
        const too      = {template:`<div>this is too </div>`}
        const more     = {template:`<div>
            <p>my name is more</p>
            <router-link to="/more/childone" >go more child </router-link>
            <router-link to="/too" >go more twoooooooo </router-link>
            <router-view></router-view>
            </div>`}
        let   childone = {template:`<div>me is childs</div>`}
        let   childtwo = {template:`<div>wosshi towo</div>`}
        const routes = [
            {
                path:'/too',
                component:too
            },
            {
                path:'/more',
                component:more,
                children:[{
                    path:'/more/childone',
                    component:childone
                },
                {
                    path:'childtwo',
                    component:childtwo
                }
            ]
            }
        ]
        const router = new VueRouter({
            routes:routes
        })
        new Vue({
            el:'#app',
            router:router
        })
    </script>

#### 6.3 路由传参

同一个路由地址，根据传递的不同参数，显示不同的内容

例如，商品详情页：

[https://m.mi.com/#/](https://m.mi.com/)[product/view?product_id=](https://m.mi.com/)[**10000022**](https://m.mi.com/)

[https://m.mi.com/#/](https://m.mi.com/)[product/view?product_id=6458](https://m.mi.com/)

上面2个地址其实共用一个页面，通过传递不同的参数加以区分，这种带有动态参数的路由，称为动态路由

首先，我们在定义路由规则时，将动态参数使用 :变量 进行参数绑定

语法规则：

![1562816373156](assets/1562816373156.png)

this.$route.params.id （在模板中获取传的值）

代码演示（循环出来一个导航条，点击显示不同的内容）：

<div id="app">
        <div>
            <router-link v-for="(item,index) in list" :to="{name:'too',params:{id:index}}" active-class="qqactive">go to too 000{{item}}</router-link>
            <router-link to="/more" active-class="qqactive">go more </router-link>
        </div>
        <router-view></router-view>
    </div>
    <script>
        const too      = {template:`<div>
            this is too
            <h2>{{$route.params.id}}<h2>
             </div>`}
        const more     = {template:`<div>
            <p>my name is more</p>
            <router-link :to="{name:'childname',params:{name:'nihao'}}"  >go more child</router-link>
            <router-link to="/too/999" >go more twoooooooo </router-link>
            <router-link :to="'/page2/'+username1">page2</router-link>
            <router-view></router-view>
            </div>`}
        let   childone = {template:`<div>me is childs: {{$route.params.name}}</div>`}
        let   childtwo = {template:`<div>wosshi towo</div>`}
        const routes = [
            {
                path:'/too/:id',
                name:'too',
                component:too
            },
            {
                path:'/more',
                component:more,
                children:[{
                    path:'/more/childone/:name',
                    name:"childname",
                    component:childone
                },
                {
                    path:'childtwo',
                    component:childtwo
                }
            ]
            }
        ]
        const router = new VueRouter({
            routes:routes
        })
        new Vue({
            el:'#app',
            data:{
                num:100,
                list:[12,13]
            },
            router:router
        })
    </script>

#### 6.4 路由懒加载

懒加载：---？也叫延迟加载，即在需要的时候进行加载，随用随载。

像vue这种单页面应用，如果没有应用懒加载，运用webpack打包后的文件将会异常的大，造成进入首页时，需要加载的内容过多，时间过长，会出啊先长时间的白屏，即使做了loading也是不利于用户体验，而运用懒加载则可以将页面进行划分，需要的时候加载页面，可以有效的分担首页所承担的加载压力，减少首页加载用时

简单的说就是：进入首页不用一次加载过多资源造成用时过长！！！

写法：var  tvProgram = resolve => require(['@/page/tvProgram'],resolve);

![1562816886552](assets/1562816886552.png)

![1562816906371](assets/1562816906371.png)



#### 6.5 编程式路由

什么是编程式路由呢？就是通过写js代码来实现页面的跳转

Js  window.location.href=”url 地址”

Vue  $router.push({path: 'name'})  或者$router.push('name');

》》》》可以有多种形态方法《《《

*//* *字符串*

router.push('home')

*//* *对象*

this.$router.push({path: '/login?url=' + this.$route.path});

*//* *命名的路由*

router.push({ name: 'user', params: { userId: 123 }})

Params 必须是name属性 且是post方式传递参数

*//* *带查询参数，变成/backend/order?selected=2*

this.$router.push({path: '/backend/order', query: {selected: "2"}});

 

this.$route.query接收

代码示例：

```
<div id="app">
	<div>
		<button @click="gotomore">我要去more</button>
		<button @click="goto">我要去too</button>
	</div>
	<router-view></router-view>
</div>
<script>
	const too      = {template:`<div>
		this is too
		<h2>{{this.$route.params.id}}<h2>
		 </div>`}
	const more     = {template:`<div>
		<p>my name is more</p>
		<router-link :to="{name:'childname',params:{name:'nihao'}}"  >go more child</router-link>
		<router-link to="/too/999" >go more twoooooooo </router-link>
		<router-view></router-view>
		</div>`}
	let   childone = {template:`<div>me is childs: {{$route.params.name}}</div>`}
	let   childtwo = {template:`<div>wosshi towo</div>`}
	const routes = [
		{
			path:'/too/:id',
			name:'too',
			component:too
		},
		{
			path:'/more',
			component:more,
			name:'more',
			children:[{
				path:'/more/childone/:name',
				name:"childname",
				component:childone
			},
			{
				path:'childtwo',
				component:childtwo
			}
		]
		}
	]
	const router = new VueRouter({
		routes:routes
	})
	new Vue({
		el:'#app',
		data:{
			num:100,
			list:[12,13]
		},
		methods: {
			gotomore(){
				this.$router.push({path:'/more'})
			},
			goto(){
				this.$router.push({name:'too',params:{id:123333}});
			}
		},
		router:router
	})
</script>

```

#### 6.6 路由的重定向（redirect）

![1562826200118](assets/1562826200118.png)

#### 6.7 路由的其他配置

比如，不想要#  修改hash路由（需要后端支持）

![1562827088342](assets/1562827088342.png)

#### 6.8 路由守卫

全局守卫：如果下需要中断next(false) 即可

![1562828120148](assets/1562828120148.png)

路由独享的守卫： beforeEnter

![1562828949376](assets/1562828949376.png)

 组件内的守卫：    beforeRouterEnter、

、beforeRouteLeave后置守卫：

![1562828990655](assets/1562828990655.png)

全局的后置守卫： afterEach

![1562829187803](assets/1562829187803.png)





作业：组件管理（登录注册切换，页面做搜索功能 ，参考国美电器首页，搜索字符串，排序）



77777：

element UI 搭建使用：

https://element.eleme.cn/#/zh-CN/component/installation



echarts安装搭建：

npm install echarts -S





# 8.vueX

vuex相关原理：

https://blog.csdn.net/weixin_44667072/article/details/101164766

vuex官方介绍：  https://vuex.vuejs.org/zh/

Vuex 是一个专为 Vue.js 应用程序开发的**状态管理模式**。它采用集中式存储管理应用的所有组件的状态，并以相应的规则保证状态以一种可预测的方式发生变化

如果没有需要：npm install vuex --save

组件中取值：{{this.$store.state.num}}

》》》》》》》》vuex中《《《《《《《《《

![1562851495706](assets/1562851495706.png)



》》》》》》》》》》main.js中《《《《《《《

![1562851564279](assets/1562851564279.png)

​	》》》》》》组件中使用：《《《《《

![1562851604922](assets/1562851604922.png)

备注：

```
vuex2.X版本新增了modules模块的概念，当页面越来越多时，每个模块的getters和actions肯定会出现同名的情况，而且由于 getters 不区分模块，所以不同模块中的 getters 如果重名，Vuex 会报出 'duplicate getter key: [重复的getter名]' 错误，actions重名会导致每个actions都会去调用一遍，这个在设计上是否有缺陷？当初尤大大为何会这样设计？目前来看，如何优雅的解决重名问题？


```

![image-20230418190826755](C:/Users/18613/AppData/Roaming/Typora/typora-user-images/image-20230418190826755.png)

网上资料

https://baijiahao.baidu.com/s?id=1618794879569468435&wfr=spider&for=pc

多个moduls的使用

https://blog.csdn.net/chenzhizhuo/article/details/96872320



  computed:{

​    ...mapState({

​      sd:state=>state.sd

​    }),

​    ...mapGetters(['collapsed'])

  },

getter直接{{collapsed}} 使用即可

设计作业：

请设计下面2个组件：

l 1 子组件，AddNumber

l  2子组件，SubNumber

 

在上面2个组件中，共同维护一个数据项：counter，在AddNumber组件中可以对counter数据加1，在SubNumber组件中对counter数据项减1





# 9.axios请求

安装：

```
cnpm install --save axios
cnpm install --save vue-axios

```

#### 9.1 promise

https://blog.csdn.net/shan1991fei/article/details/78966297

Promise对象用于异步操作，它表示一个尚未完成且预计在未来完成的异步操作

Promise有各种开源实现，在ES6中被统一规范，由浏览器直接支持。

<script>
/*
 new Promise(function(resolve,reject){
        setTimeout(function(){
            resolve('success')
        },1000);
    throw 'no'
}).then(function(str){
    console.log(str)
}).catch(function(e){
    console.log(e)
});
*/
let myFirstPromise = new Promise(function(resolve, reject){
    //当异步代码执行成功时，我们才会调用resolve(...), 当异步代码失败时就会调用reject(...)
    //在本例中，我们使用setTimeout(...)来模拟异步代码，实际编码时可能是XHR请求或是HTML5的一些API方法.
    setTimeout(function(){
        resolve("成功!"); //代码正常执行！
    }, 250);
    //throw 'happen Error'; 抛出异常打印错误信息
});
myFirstPromise.then(function(successMessage){
    //successMessage的值是上面调用resolve(...)方法传入的值.
    //successMessage参数不一定非要是字符串类型，这里只是举个例子
    console.log("Yay! " + successMessage);
    alert('成功')
});
myFirstPromise.catch(function(e){
 console.log('打印错误信息');
 alert(e)
})
    console.log('他是异步操作，并没有影响我')
</script>

#### 9.2 axios 介绍

https://www.jianshu.com/p/a1c63300f729

​	axios，是基于Promise的http库，用来实现浏览器请求服务器的工具	

​    Axios特点：

- u  从浏览器中创建 XMLHttpRequests
- u 从 node.js 创建 http 请求
- u 支持 Promise API
- u 自动转换 JSON 数据
- u 客户端支持防御 XSRF

#### 9.3 axios 的语法

- get，请求的方式，如果表单请求，请使用post
- url，请求的文件地址
- then，请求成功时的回调函数
- catch，请求失败时的回调函数

#### 9.4 在vue-cli中使用axios

百度搜索引擎的接口：

[http://suggestion.baidu.com/su?wd=22](http://suggestion.baidu.com/su?wd=#content%23&cb=window.baidu.sug)

get请求：

![1562920986099](assets/1562920986099.png)

post 请求：跨域配置

https://blog.csdn.net/cateatapple/article/details/86554941

```
    '/api': {  //代理地址  
        target: 'http://10.1.0.34:8000/',  //需要代理的地址  
        changeOrigin: true,  //是否跨域  
        secure: false,    
        pathRewrite: {  
            '^/api': '/'   //本身的接口地址没有 '/api' 这种通用前缀，所以要rewrite，如果本身有则去掉  
        }
    }

```

如果是vue_cli3.0 配置方式：（根目录下面创建vue.config.js）

然后写代码：（pathRewrite不能忘记了）

 module.exports = {
  devServer: {
    proxy: {
      '/api': {
        target: 'http://suggestion.baidu.com/',
        ws: true,
        changeOrigin: true,
        pathRewrite: {'^/api' : ''}
      }
    }
  }
}



 如果打包：如果打包：需要配置 publicPath:'./',

![image-20210728150842201](assets/image-20210728150842201.png)



![img](file:///C:\Users\18613\Documents\Tencent Files\812879677\Image\C2C\TTV_I]V`Z%M2_TE_CXGFDCW.png)



作业：

百度接口实现搜索下拉框

http://www.baidu.com/s?wd=关键字  （页面）

https://sp0.baidu.com/5a1Fazu8AA54nxGko9WTAnF6hhy/su?wd=22（联想词）

post 请求需要解决跨域问题

安装 qs 模块：npm install --save qs

安装qs,在 main.js里引入

```
import axios from 'axios';
import qs from 'qs';
Vue.prototype.$qs = qs;

```

在组件中使用

```
let postData = this.$qs.stringify({
    key1:value1,
    key2:value2,
    key3:value3,
});
this.$axios({
    method: 'post',
    url:'url',
    data:postData
}).then((res)=>{
    
});

```

线文档：https://segmentfault.com/a/1190000012635783

![1562921220133](assets/1562921220133.png)

或者这样

![1562922620347](assets/1562922620347.png)

数据如果要同步：

代码展示：

<script>
  export default {
  name: 'hello',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      list:['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
      name:'张叔叔',
      pwd:80
    }
  },
  mounted(){
    this.getdata();
  },
  methods: {
      getdata(){
      //百度接口没有提供跨域访问：http://suggestion.baidu.com/su?wd=22
      //自己的接口提供了跨域访问了：http://192.168.18.111/
              this.axios.get('http://192.168.18.111/').then((response)=>{
                  console.log(response.data)
                  //throw 'happen Error'
              }).catch((response)=>{
                  console.log(response)
              })
          },
          async savedata(){
            let postData = this.$qs.stringify({
                name:this.name,
                pwd:this.pwd,
            });
            await this.axios({
                method: 'post',
                url:'http://127.0.0.1/',
                data:postData
            }).then((res)=>{
                console.log(res)
            })
             console.log(11)
          }
  }
}
</script>

# 10.web总结：

element ui 实现树型菜单控件

```
<el-tree
  :data="leide"
  show-checkbox
  node-key="id"
  :default-expanded-keys="[14]"
  :default-checked-keys="[3]"
  :props="defaultProps">
</el-tree>


vue的方法：（数据arr,leide自定义）

  menu(){
      this.axios.get('/api/index.php/index/call/getmenu',{
        params:{}
      }).then(res=>{
        this.arr = res.data.data.data
        let newarr = []
        this.arr.forEach((item,index)=>{
              let map = {}
              map['id']       = item.id
              map['label']    = item.name
              map['parentid'] = item.parentid
              newarr[index]=map            
        })
       this.leide = this.toTree(newarr)
      
      })
    },
    toTree(data) {
        let result = []
        if(!Array.isArray(data)) {
            return result
        }
        data.forEach(item => {
            delete item.children;
        });
        let map = {};
        data.forEach(item => {
            map[item.id] = item;
        });
        data.forEach(item => {
            let parent = map[item.parentid];
            if(parent) {
                (parent.children || (parent.children = [])).push(item);
            } else {
                result.push(item);
            }
        });
        return result;
    },
```



作业，修改某一项的值，让他可以点击姓名修改为别的名字，比如小红，小兰

![image-20200922142725760](assets/image-20200922142725760.png)