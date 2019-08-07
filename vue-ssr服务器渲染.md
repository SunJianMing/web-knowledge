## VUE SSR 服务器渲染
#### 利用unxt ###
1.  新建项目并进入项目
> mkdir vue-ssr && cd vue-ssr

2. 初始化项目
> npm init -y 获取 yarn init -y

3. 安装依赖
> npm i nuxt -S 获取 yarn add nuxt

4. 新增启动命令
> 打开package.json 找到scripts增加命令

    "scripts" : {
        ...
        "dev" : "nuxt"
    }

5. 增加pages目录并新建vue页面
> mkdir pages 

> cd pages

> touch index.vue
    
    index.vue >>

    <template>
        <div>
            <h1>{{msg}}</h1>
        </div>
    </template>
    <script>
    export default {
        data (){
            return {
                msg : "hello nuxt"
            }
        }
    }
    </script>
6. 获取数据
>增加asyncData函数（没有安装axios的话安装一下 npm i axios -S 或 yarn add axios）

    import axios from 'axios'
    export default {
        async asyncData(){
            const res = await axios.get('xxxxx')

            return {data:res.data}
        }
        ...
    }
 ####  vuex
 新建store文件夹，新建xxx.js
 > mkdir store && cd mkdir && touch index.js
    
    模块方式：
    store > index.js >>
    export const state = () => ({
        counter:0
    })
    export const mutations = {
        increment(state){
            state.counter++
        }
    }
    普通方式
    store > index.js >>
    import Vue from 'vue'
    import Vuex from 'vuex'
    Vuex.use(vuex)

    const store = () => new Vuex.Store({
        state:{
            counter:0
        },
        muations:{
            increment(state){
                state.counter++
            }
        }
    })
    export default store


> 在vue中使用

    import {mapState,mapMutations} from 'vuex'

    ...
    computed:{
        ...mapState({
            counter:'counter'
        })
    },
    methods:{
        ...mapMutations({
            add:'increment'
        })
    }






