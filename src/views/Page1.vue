<template>
    <div class="page1">
        <div class="logo"><img src="@/assets/images/logo.png" alt=""></div>
        <div class="main">
            <div class="top">
                <img src="../assets/images/t1.png" alt="">
                <img src="../assets/images/t2.png" alt="" class="time">
            </div>
            <div class="center">
                <img src="../assets/images/p.png" alt="">
            </div>
            <div class="btn1" @click="$emit('tonext',2)">
                <img src="../assets/images/btn1.png" alt="">
            </div>
        </div>
        <div class="footer">
            
        </div>
    </div>
</template>

<script>
export default {
    name:"page1",
    data(){
        return{

        }
    },
    methods:{
        
    }
}
</script>

<style scoped lang="less">
.page1{
    width: 100%;
    height: 100%;
    position: relative;
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
    border-top: 1px solid white;
    width: 90vw;
    margin-left: 5vw;
    .top{
        margin-top: 3vh;
        .time{
            width: 70vw;
            margin-left: 10vw;
            margin-top: 3vh;
        }
    }
    .center{
        margin: 3vh 0;
    }
    .btn1{
        width: 54vw;
        margin-left: 18vw;
        margin-top: 5vw;
    }
}
.footer{
    height: 12vh;
}
</style>