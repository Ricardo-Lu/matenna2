<template>
  <div class="quest">
      <div class="q" v-if="!result">
        <div class="n">{{question.id}}/6</div>
        <div class="topic">{{question.topic}}</div>
        <div class="ans" v-for="(item,index2) in question.ans_content" :key="index2" @click="licli(item)" :class="question.ans_my.indexOf(item.key)>-1?'active':''">
            <span class="key">{{item.key}}</span>
            <span class="text">{{item.text}}</span>
        </div>
        <div class="btn" @click="submit"><img src="../assets/images/btn2.png" alt=""><span>确 认</span></div>
      </div>
      <div class="r" v-if="result">
          <div class="rightt" v-if="right">
              <img src="../assets/images/right.png" alt="">
              <h1>回答正确</h1>
          </div>
          <div class="errorr" v-else>
              <img src="../assets/images/error.png" alt="">
              <h1>回答错误</h1>
          </div>
          <div class="ranswer" v-if="!isMultiple">
              <h2>正确选项：</h2>
              <p>{{arr[0].key}}、{{arr[0].text}}</p>
          </div>
          <div class="ranswers" v-else>
              <h2>正确选项：</h2>
              <p>{{arr[0].key}}、{{arr[0].text}}</p>
              <p>{{arr[1].key}}、{{arr[1].text}}</p>
              <p>{{arr[2].key}}、{{arr[2].text}}</p>
          </div>
          <div class="btn2" @click="$emit('nextone',this.question.id)">
              <img src="../assets/images/next.png" alt="">
          </div>
      </div>
  </div>
</template>

<script>
export default {
  name: 'question',
  props:['question','indexnow','index'],
  data() {
    return {
        ind: '',         //选中样式
        flag:false,     //是否选中答案了
        result:false,   //回答结果
        right: false,   //回答正确
        selectAns: [],   //选中的答案
        arr:[]          //正确答案
    };
  },
  computed:{
      isMultiple(){
          if(this.question.isMultiple){
              return true
          }
          return false
      }
  },
  watch:{},
  methods: {
      //选择答案
      licli(item){  
          this.flag = true
          if(this.question.isMultiple){
              let index = this.question.ans_my.indexOf(item.key)
              if(index==-1){
                  this.question.ans_my.push(item.key)
                  this.selectAns.push(item.key)
              }else{
                  this.question.ans_my.splice(index,1)
                  this.selectAns.splice(index,1)
              }
          }else{
              this.question.ans_my.splice(0,1,item.key)
              this.selectAns.splice(0,1,item.key)
          }
          this.question.ans_my.sort();
          this.$forceUpdate();
      },
      submit(){
          //未选中
          if(!this.flag){
              console.log('请选择一个答案!')
              return
          }
          //跳到结果页面
          this.result = true
          this.question.ans_my = this.selectAns     //放到ans_my数组中
          if(this.question.ans_my.join("") == this.question.ans_right){
              //跳回答正确
              this.right = true                         
          }else{
              //跳回答错误
              this.right = false
          }
      },
      
  },
  mounted(){
      //正确答案
      this.arr = this.question.ans_content.filter(item => {
             return this.question.ans_right.indexOf(item.key) > -1
          })
  }
};
</script>

<style scoped lang="less">
.quest{
    position: relative;
    width: 100%;
    height: 100%;
    border-top: 1px solid white ;
    .n{
        margin: 5% 0 5% 5%;
        font-size: 1.3rem;
    }
    .topic{
        width: 86%;
        font-size: 1.2rem;
        margin-left: 7%;
    }
    .ans{
        width: 80%;
        font-size: 0.875rem;
        margin: 4% 0 4% 10%;
        display: flex;
        span{
            display: inline-block;
        }
        .key{
            font-weight: bold;
            padding: 1% 3%;
            height: 3%;
            background-color: #c21948;
            border-radius: 50%;
            color: white;
        }
        .text{
            color: #c21948;
            margin: 1% 0 0 3%;
            font-weight: bold;
        }
    }
    .btn{
        position: absolute;
        left: 23%;
        bottom: -3%;
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
.r{
    width: 100%;
    height: 100%;
    position: relative;
    .rightt{
        position: absolute;
        left: 25%;
        top: 17%;
        img{
            width: 60%;
        }
        h1{
            color: #c21948;
            font-size: 2.5rem;
            margin-top: 5%;
        }
    }
    .errorr{
        position: absolute;
        left: 26%;
        top: 14%;
        img{
            width: 55%;
            margin-left: 5%;
        }
        h1{
            color: #c21948;
            font-size: 2.5rem;
            margin-top: 5%;
        }
    }
    .ranswer{
        width: 100%;
        position: absolute;
        left: 0;
        top: 56%;
        color: #c21948;
        h2{
            text-align: center;
            font-size: 1rem;
            margin: 3% 0;
        }
        p{
            width: 80%;
            margin-left: 10%;
            text-align: center;
            font-size: 1.2rem;
        }
    }
    .ranswers{
        width: 100%;
        position: absolute;
        left: 0;
        top: 56%;
        color: #c21948;
        h2{
            text-align: center;
            font-size: 1rem;
            margin: 0% 0;
        }
        p{
            width: 100%;
            font-size: 1rem;
        }
    }
    .btn2{
        position: absolute;
        left: 20%;
        bottom: 7%;
        img{
            width: 70%;
        }
    }
}
.active{
        box-shadow: 0 0 2px #c21948;
        border-radius: 3%;
    }
</style>
