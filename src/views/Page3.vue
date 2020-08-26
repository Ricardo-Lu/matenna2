<template>
    <div class="page3">
        <div class="logo"><img src="@/assets/images/logo.png" alt=""></div>
        <div class="main">
            <div class="test">
                <div class="text">
                    <h1>您真棒！</h1>
                    <p>请前往惠氏展台工作人员处，凭此页面换取奖品。（数量有限，送完为止）</p>
                </div>
                <div class="psw">
                    <p>工作人员</p>
                    <div class="psd">密码输入<input type="password"></div>
                </div>
                <div class="btn" @click="$emit('tonext',4)"><img src="../assets/images/btn2.png" alt=""><span>提 交</span></div>
            </div>
        </div>
        <div class="footer">
            <img src="../assets/images/product.png" alt="">
        </div>
    </div>
</template>

<script>
export default {
    name:"page3"
}
</script>

<style scoped lang="less">
.page3{
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
        position: relative;
        .text{
            width: 90%;
            margin-top: 30%;
            margin-left: 6%;
            color: #c31948;
            h1{
                text-align: center;
                font-size: 3rem;
                margin: 3vw 0;
            }
            p{
                font-size: 1.2rem;
                text-indent: 1em;
                font-weight: bold;
            }
        }
        .psw{
            position: absolute;
            left: 5vw;
            bottom: 5vh;
            color: #c31948;
            font-size: 1.2rem;
            font-weight: bold;
            input[type=password]{
                border: none;
                outline: none;
                background-color: rgba(255, 243, 247, .6);
                text-align: center;
                border-bottom: 1px solid #c31948;
                width: 40%;
            }
        }
    }
    .btn{
        position: absolute;
        left: 60%;
        bottom: -32%;
        position: relative;
        img{
            width: 35%;
            height: auto;
        }
        span{
            position: absolute;
            left: 11%;
            top: 7%;
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