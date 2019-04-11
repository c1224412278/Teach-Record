vue 小知識
==================

1. <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js">  </script> (會自動抓取 Vue.js 最新版本，html 可使用)
2. Vue 生命週期參考網址 : https://cythilya.github.io/2017/04/11/vue-instance/
3. @import
```
import'./'      同一層目錄開始找
import'../'     上一層目錄開始找
import'@/'      src目錄下開始找
import''        直接打名稱則是node_modules
```

*   套件載入
    (1) bootStrap 套件載入。 參考網址 : https://bootstrap-vue.js.org/docs/


### 事件

參考文獻 : https://cythilya.github.io/2017/04/17/vue-methods-and-event-handling/

* .stop：等同於event.stopPropagation()，防止事件冒泡。
* .prevent：等同於event.preventDefault()，防止執行預設的行為。
* .capture：與事件冒泡的方向相反，事件捕獲 (event capturing) 是由外而內的。
* .self：只會觸發自己範圍內的事件，不包含子元素。
* .once：只會觸發一次

```
* 獲取 html Tag

<template>
  <div id="app">
      <button v-on:click="greet">Greet</button>
  </div>
</template>

<script>
import Vue from 'vue';

export default {
  data(){
    return{
      
    }
  } , 
  methods:{
    greet(event)
    {
      if(event)
      {
        alert(event.target.tagName);
      }
    }
  }
}
</script>
```
###

### js陣列 - 條件篩選
```
參考文獻 : https://wcc723.github.io/javascript/2017/06/29/es6-native-array/

    判斷陣列 number 欄位值是否大於 10，之後再返回一個新陣列
    this.arys = this.arys.filter(function(item , index , array)
    {
      return item.number > 10
    });
```
###


### CSS 模塊
```
<div>
  <p :class="$style.red">title</p>      // 當 css 有模塊時，便可直接呼叫
</div>


<style module> 
.red
{
  color:red
}
</style>
```
###

### export / import

```
* furniture.vue
    
    <template>
    </template>

    <script>
    function desk(a,b)
    {
      return a + b;
    }

    let bed = "queen size";
    export {desk,bed}

    export default {

    }
    </script>
    
    
* HelloWorld.vue

    <script>
    import Vue from 'vue'; 
    import {desk,bed} from './furniture.vue';

    export default {
      data(){
        return{

        }
      },
      mounted(){
        console.log(bed);
      }
    }
    </script>

```    
### 



<h3 id="autoescape"> v_if </h3>

```
<div id="app">
    <p v-if="seen">you look me.</p>
</div>

new Vue({
    el:"#app" ,
    data() {
        return {
            seen : true
        }
    },
})
```

<h3 id="autoescape"> v_for </h3>

```
<div id="app">
    <p v-for="(item, index) in items" :key="index">
        {{ item.id }}
    </p>
</div>

new Vue({
    el:"#app" ,
    data() {
        return {
            items : [
                {id:"pudding" , "number":1}
            ]
        }
    },
})
```
* (最好每個 for 都設 key，假如 array 更動時，資料不會更著陣列一起更新，如果設定 key 時，資料就會自動更動到該欄位)

```

<h5 id="autoescape"> Array 小知識 </h5>

	push()：新增元素。
	pop()：刪除最新加入的元素。
	shift()：刪除第一個 (即最舊的) 元素。
	unshift()：加入元素至第一個位置。
	splice()：加入或移除元素。
	sort()：由小至大排序。
	reverse()：元素反序排列。
	filter()：過濾陣列的元素，並將符合條件的元素傳回成為一個新陣列。
	concat()：連接陣列，會返回一個新的陣列。
	slice()：切割陣列，會返回一個新的陣列。
```

<h3 id="autoescape"> is vs : is </h3>

(1) is (指定一個 component 直接使用)
```
<div id="app">
    <div is="com">< /div>
</div>

Vue.component('com', {
    template:'<p> title </p>'
})

new Vue({
    el:"#app"
})
```

(2) : is (需指定一個變數，並用變數去呼叫compoent)
```
<div id="app">
    <div :is="view" >< /div>
</div>

var vm = new Vue({
    el:"#app" ,
    data() {
        return {
            view:''
        }
    },
    comments:{
        view:{
            template:'<h2> title </h2>',
        }
    }
})
```

<h3 id="autoescape"> v_model (雙向綁定) </h3>

```
<div id="app">
    <p>{{ message }}</p>
    < input v-model="message">
</div>

new Vue({
    el:"#app" ,
    data() {
        return {
            message : 'Hello'
        }
    },
})
```
* checkbox

```
<template>
  <div id="app">
    <input type="checkbox" value="Jack" v-model="checkedNames">
    <label> Jack </label>

    <input type="checkbox" value="John" v-model="checkedNames">
    <label> John </label>
  </div>
</template>

<script>
import Vue from 'vue';

export default {
  data(){
    return{
      checkedNames: []
    }
  },
  updated()
  {
    console.log(this.checkedNames);
  }
}
</script>
```


<h3 id="autoescape"> v_bind </h3>

```
* 在 Vue Data 宣告的變數，可在 html 裡使用 ": " 來進行呼叫 Vue 的變數呼叫

<template>
  <div id="app">
      <div :title="data"> test </div>
  </div>
</template>

<script>
import Vue from 'vue'
export default
{
    data(){
        return{
            data : "It's my title"
        }
    }
}
</script>

(2)Class範例


<template>
  <div id="app">
      <div :class="{active : myCheck}"> test </div>
  </div>
</template>

<script>
import Vue from 'vue'
export default
{
    data(){
        return{
            myCheck : true,
        }
    }
}
</script>

<style>
    .active
    {
        color:red;
    }
</style>
```

<h3 id="autoescape"> component </h3>

```
<template>
  <div id="app">
      <blog-post title="hello"></blog-post>
  </div>
</template>

<script>
import Vue from 'vue'

Vue.component('blog-post', {
    props:['title'],
    template:'<h3>{{ title }}</h3>'
})

export default
{
    
}
</script>
```

<h3 id="autoescape"> On </h3>

```
<button @click.prevent="">
    <a href="#"> click </a>
</button>
```

<button v-on:click.prevent="handle"></button>
* prevent 頁面轉換如果是同個頁面時，url 後會出現 #，若不想 url 出現 # ，則使用



<h3 id="autoescape"> vue 頁面轉換 </h3>

```
<router-link :to="'HelloWorld'">< /router-link>
```

```
import Vue from 'vue'
import Router from 'vue-router'
import HelloWorld from '@/components/HelloWorld'
import Parent from '@/components/Parent'
import Child from '@/components/Child'

Vue.use(Router)

export default new Router({
  routes: [
    {
       path: '/',
       name: 'HelloWorld',
       component: HelloWorld
    },
  ]
})
```

<h3 id="autoescape"> (Props) Parentand Child </h3>

	child.vue (將變數 message 藉由 props 方式傳遞給父物件)
```
    <template>
        < h5>{{ message }}< /h5>
    </template>
    <script>
      export default {
        props:['message']
      }
    </script>
``` 
    
	parent.vue

```
    <template>
      <div>
        <p>This is Parent.</p>
        <child message='Text'></child>
        <child :message='a'></child>
      </div>
    </template>

    <script>
    import Child from '../components/child.vue'

    export default {
        components:{Child} , 
        data(){
            return{
                a:10,
                b:10,
            }
        }
    }
    </script>
```
<h3 id="autoescape"> Props </h3>

```
prop=(型態) : 限制使用者只能塞特定型態
required : 一定要用此 prop
default : 當使用者沒有輸入值時，就設定默認值
validator : 條件限定，若判斷錯誤則會error
```

	child.vue 

```
<template>
    <div>
        <span>Message : {{propA}}</span>
        <span>Message : {{propB}}</span>
        <span>Message : {{propF}}</span>
    </div>
</template>

<script>
export default {
    props:{
        propA:Number,
        propB:[String , Number],
        propC:{
            type:String , 
            //required: true
        },
        propD:{
            type:Number,
            default:100
        },
        propE:{
            type:Object,
            default()
            {
                return {message: 'hello'}
            }
        },
        propF:{
            validator(value)
            {
                return value > 10
            }
        }
    }
}
</script>
```


	parent.vue 

  ```
  <template>
    <div id="app">
      <child :propA='10' propB="20" :propF="100"></child>
    </div>
  </template>

  <script>
  import Child from './Child.vue'

  export default {
      name: 'app',
      components:{Child},

  }
  </script>
```

參考網址 : https://www.jianshu.com/p/91416e11f012
(* 注意 : 只能單向傳輸。(單:父物件抓子物件，不可雙向傳輸))

(props 與 $ref的區別 : 
props 擅長傳遞變數(不傳屬系、方法)、$ref 擅長傳方法(不傳變數))


<h3 id="autoescape"> $emit </h3>

```
參考網址 :  
        (1) https://jeremysu0131.github.io/Vue-js-%E7%88%B6%E5%AD%90%E7%B5%84%E4%BB%B6%E6%BA%9D%E9%80%9A-emit-on/
        (2) https://blog.csdn.net/sllailcp/article/details/78595077
        
	parent.vue 

    <template>
        <div>
            <button v-on:click="handleClick"> Emit </button>
        </div>
    </template>

    <script>

    export default {
        methods:{
            handleClick()
            {
                this.$emit('childMethod');
            }
        }
    }
    </script>



	child.vue 

    <template>
        <div>
            <button v-on:click="handleClick"> Emit </button>
        </div>
    </template>

    <script>

    export default {
        methods:{
            handleClick()
            {
                this.$emit('childMethod');
            }
        }
    }
    </script>

```

<h3 id="autoescape"> $ref </h3>
  

	child.vue (一般的寫法。)

```
  <template>
      <h5>{{ message }}</h5>
  </template>
  <script>
    export default {
      data(){
          return{
              message : ''
          }
      },
      methods:{
          getMessage(m)
          {
              this.message = m;
          }
      }
    }
  </script>
```


	parent.vue

```
  <template>
    <div>
      <p> 我是父組件 !! </p>
      <child ref="msg"></child>
    </div>
  </template>

  <script>
  import Child from './Child.vue'

  export default {
      components:{Child},
      mounted:function()
      {
          console.log(this.$refs.msg);
          this.$refs.msg.getMessage('我是子組件 !!');
      }
  }
  </script>
```

參考網址 : https://www.jianshu.com/p/91416e11f012

* 藉由 ref = msg 指定 msg 為 child.vue
(* 注意 : 只能單向傳輸。(單:父物件抓子物件，不可雙向傳輸))

(props 與 $ref的區別 : 
props 擅長傳遞變數(不傳屬系、方法)、$ref 擅長傳方法(不傳變數))

<h3 id="autoescape"> 全局註冊 </h3>

```
*Import Vue from 'vue' 是重點，一定要寫入
import Vue from 'vue'

Vue.component('example' , {
  template:'<button> click </button>'
})

```

<h3 id="autoescape"> Computed(計算屬系) </h3>

```
<template>
  <div id="app">
    <p>{{ message }}</p>
    <p>反轉訊息：{{reversedMessage}}</p>
  </div>
</template>

<script>
export default {
  data(){
    return{
      message : 'Hello World!'
    }
  },
  computed: {
    reversedMessage() {
      return this.message.split('').reverse().join('');
    }
  },
}
</script>
```

<h3 id="autoescape"> (get , set) </h3>

```
<template>
  <div id="app">
    <button v-on:click="handle()"> click </button>

    {{ fullName }}
  </div>
</template>

<script>
export default {
  data(){
    return{
      firstName: 'Bill',
      lastName: 'Chen'
    }
  },
  computed: {
    fullName :{
      set(value){
        var name = value.split(' ');
        this.firstName = name[0];
        this.lastName = name[1];
      },
      get(){
        return this.firstName + " , " + this.lastName;
      }
    }, 
  },
  methods:{
    handle()
    {
      this.fullName = 'Gary Lu';
    }
  }
}
</script>
```

<h3 id="autoescape"> v-Html </h3>


* (可以將 msg 的資料轉為 html 輸出)
```
<template>
  <div id="app">
      <div v-html='msg'></div>
  </div>
</template>

<script>
import Vue from 'vue'

export default
{
    data(){
        return{
            msg : '<div style=color:red;> content </div>'
        }
    }
}
```
