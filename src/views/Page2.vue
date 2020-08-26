<template>
    <div class="page2">
        <div class="logo"><img src="@/assets/images/logo.png" alt=""></div>
        <div class="main">
            <div class="test" v-for="(item,index) in questions" :key="item.id" v-show="indexnow==index">
                <question :question="item" :indexnow="indexnow" :index="index" @nextone="nextone"></question>
            </div>
            <!-- <div class="btn" @click="$emit('tonext',3)"><img src="../assets/images/btn2.png" alt=""><span>确 认</span></div> -->
        </div>
        <div class="footer">
            <img src="../assets/images/product.png" alt="">
        </div>
    </div>
    
</template>

<script>
import questions from "@/tools/questions"
import question from "./Question"
export default {
    name:"page2",
    components:{question},
    data(){
        return{
            indexnow:0
        }
    },
    computed:{
        questions(){
            return questions
        }
    },
    methods:{
        nextone(val){
            if(val===6){
                this.$emit('tonext',3)
                return
            }
            this.indexnow = val
        }
    }
}
</script>

<style scoped lang="less">
.page2{
    width: 100%;
    height: 100%;
    position: relative;
    overflow: hidden;
    background: url("../assets/images/bg.jpg") no-repeat center/ 100% 100%;
}
.logo{
    height: 12vh;
    border: 1px solid white;
    img{
        width: 20%;
        margin: 4% 0 0 4%;
    }
}
.main{
    height: 76vh;
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
    .test{
        width: 90%;
        height: 90%;
        background-color: rgba(255, 243, 247, .6);
    }
    .btn{
        position: absolute;
        left: 23%;
        bottom: -70%;
        position: relative;
        img{
            width: 50%;
            height: auto;
        }
        span{
            position: absolute;
            left: 17%;
            top: 25%;
            color: #c21948;
            font-size: 1.2rem;
            font-weight: bold;
        }
    }
}
.footer{
    height: 12vh;
    position: relative;
    img{
        width: 86%;
        position: absolute;
        left: 7%;
        top: -53%;
    }
}
</style>