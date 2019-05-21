<template>
    <div>
        <van-nav-bar title="标题" left-text="返回" @click-left="$router.go(-1)" left-arrow>
            <van-icon name="search" slot="right" />
        </van-nav-bar>
        <div v-for="(item,index) in goods" :key="index" class="row row-good">
            <div class="col-10 col-center tac"><van-checkbox v-model="checked"></van-checkbox></div>
            <div class="col-30">
                <img :src="item.image_url" width="100%" alt="" >
            </div>
            <div class="col-50">
                <h3>{{item.name}}</h3>
                <h3>价格:{{item.price}}</h3>
                <div>
                    <van-stepper
                        v-model="value"
                        integer
                        :min="1"
                        :max="item.buy_limit"
                        :step="1"/>                      
                </div>
            </div>
            <div class="col-10 col-end">
                <van-icon name="delete" />
            </div>
            {{item.name}}--{{item.num}}
        </div>
    </div>
</template>
<script>
// 导入mapstate方法
import {mapState} from 'vuex';
// el 插件第一步 导入插件
import {NavBar,Icon,Checkbox, CheckboxGroup,Stepper} from 'vant';

export default {
    data(){
        return {checked:true}
    },
    computed:{
        ...mapState(["goods"])
    },
    components:{
        // 02 插件02 注册组件
        [NavBar.name]:NavBar,
        // vant-nav-bar:NavBar
        // es 属性动态设置写法
        [Icon.name]:Icon,
        [Checkbox.name]:Checkbox,
        [CheckboxGroup.name]:CheckboxGroup,
        [Stepper.name]:Stepper
    }
}
</script>
<style>
.row-good{
    max-height: 2rem;
    overflow: hidden
}
    .van-nav-bar .van-icon{
        color: #777;
    }
    .van-nav-bar__txt{
        color: #777;
    }
</style>

