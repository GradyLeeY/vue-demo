<template>
    <div id="home">
        <h1>蝶恋花 答李淑一</h1>
        
        <h1>{{site}}</h1>
        <h1>{{url}}</h1>
        <h1>{{details()}}</h1>

        <h2 v-if="ishere">问讯吴刚何所有</h2>
        <h2 v-else-if="!ishere">吴刚捧出桂花酒</h2>
        <router-link to="/">返回</router-link>
        
        <a v-on:click="doSomething()">点我</a>
    
        <div>
            <p>{{msg}}</p>
            <input v-model="msg"/>
        </div>
        <div>
            {{msg | capitalize}}
            <input type="text" v-model="kilometers"/>
            <input type="text" v-model="meters"/>
        </div>
        <div>
            <li v-for="item in dates" v-bind:key="item">
                {{item.name}}
            </li>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Home',
    data(){
        return{
            site: '我失骄杨君失柳',
            url: '杨柳轻摇直上重霄九',
            msg: '',
            kilometers: 0,
            meters: 0,
            dates: [{name: '万里长空且为忠魂舞'},
                    {name: '忽报人间曾伏虎'},
                    {name: '泪飞顿作倾盆雨'}],
            ishere: ''
        }
    },
    mounted:function(){
        let _this = this;
        _this.ishere=false;
    },
    methods:{
       details(){
           return  this.site + "哈哈哈哈哈哈";
       },
       doSomething(){
           let _this = this;
           _this.ishere=true;
           _this.msg = '寂寞嫦娥舒广绣';
       }
    },
    filters: {
        capitalize: function(value){
            if(!value){
                return '';
            }
            return value.slice(1);
        }
    },
    watch:{
        kilometers: function(val){
            this.kilometers = val;
            this.meters = this.kilometers*1000;
        },
        meters: function(val){
        
            this.kilometers = val/1000;
            this.meters = val;
        }
    }
    
}
</script>