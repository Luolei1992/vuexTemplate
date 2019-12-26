<template>
  <div class="home">
    <h1>{{ msg }}</h1>
    <p>计算属性：</p>
    <p>是否大于10？<span class="red">{{result}}</span></p>
    <p>是否小于2？<span class="red">{{resultR}}</span></p>
    <Plus/>
    <Reduce/>
    <p class="next" @click="next">Next</p>
  </div>
</template>

<script>
import Plus from './Plus';
import Reduce from './Reduce';
import {mapGetters} from 'vuex';
export default {
  name: 'Home',
  data(){
    return {
      msg:'DemoVuex',
      result:false,
      resultR:false
    }
  },
  computed:{
    ...mapGetters([
      'filterNum',
      'filterRNum'
    ])
  },
  watch:{
    filterNum:function(value){
        this.result = this.filterNum;
    },
    filterRNum:function(value){
        this.resultR = this.filterRNum;
    },
  },
  methods:{
    next(){
      this.$router.push({
        path:'/page'
      })
    }
  },
  components:{
    Plus,
    Reduce
  }
}
</script>

<style lang="less" scoped>
h1 {
  font-size: 28px;
  text-align: center;
  margin: 20px;
}
.home {
  padding: 15px;
}
.red {
  color: red;
}
.next {
  background-color: blue;
  color: #fff;
  text-align: center;
  border-radius: 10px;
  height: 50px;
  line-height: 50px;
}
</style>
