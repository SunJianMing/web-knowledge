<template>
    <div>
        正常使用
        <h3>{{msg}}</h3>
        <hr>
        服务器获取数据
        <ul>
            <li v-for='item in data' :key='item'>{{item}}</li>
        </ul>
        <hr>   
        vuex使用 
        <h3>{{counter}}</h3>
        <button @click='add'>add</button>
    </div>
</template>

<script>
import {mapState,mapMutations} from 'vuex'
import axios from 'axios'
    export default {
        // 服务器获取数据
        async asyncData(){
            const {data}  = await axios.get('http://mrsun123.xyz/api/list')
            return {data:data.data}
        },
        data() {
            return {
                msg: 'hello nuxt'
            }
        },
        computed:{
            ...mapState({
                counter: state => state.number.counter
            })
        },
        methods: {
            ...mapMutations({
                add:'number/increment'
            })
        },
    }
</script>

<style lang="scss" scoped>

</style>