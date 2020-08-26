<template>
    <div class="page4">
        <div class="logo"><img src="@/assets/images/logo.png" alt=""></div>
        <div class="main">
            <img src="@/assets/images/c1.png" alt="">
            <img src="@/assets/images/c2.png" alt="">
        </div>
        <div class="footer">
        </div>
    </div>
</template>

<script>
export default {
    name:"page4"
}
</script>

<style scoped lang="less">
.page4{
    width: 100%;
    height: 100%;
    overflow: hidden;
    position: relative;
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
    border: 1px solid white;
    height: 76vh;
    width: 90vw;
    margin-left: 5vw;
    img{
        margin: 5vw 0;
    }
}
.footer{
    height: 12vh;
    background: url("../assets/images/pd.png") no-repeat center/ 100% 100%;
}
</style>
