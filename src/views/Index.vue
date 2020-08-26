<template>
    <div class="index">
        <page1 v-show="currentPage==1" @tonext='tonext'></page1>
        <page2 v-show="currentPage==2" @tonext='tonext'></page2>
        <page3 v-show="currentPage==3" @tonext='tonext'></page3>
        <page4 v-show="currentPage==4" @tonext='tonext'></page4>
        <div class="info">仅供医务人员参考</div>
    </div>
</template>

<script>
import page1 from './Page1'
import page2 from './Page2'
import page3 from './Page3'
import page4 from './Page4'
export default {
    name:"index",
    components:{
        page1,page2,page3,page4
    },
    data(){
        return{
            currentPage:1
        }
    },
    methods:{
        tonext(val){
            this.currentPage = val
        }
    }
}
</script>

<style>
.index{
    width: 100%;
    height: 100%;
    position: relative;
}
.info{
    position: absolute;
    bottom: 3%;
    right: 3%;
    color: white;
    font-size: 0.625rem;
}
</style>