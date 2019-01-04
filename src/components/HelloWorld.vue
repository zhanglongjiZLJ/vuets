<template>
  <div class="hello">
    <button @click="countAdd(number )">点我</button>
    <h1>{{ msg }}</h1>
    <h2>{{number}}{{zlj}}{{age}}</h2>
    <p>
      For a guide and recipes on how to configure / customize this project,<br>
      check out the
      <a href="https://cli.vuejs.org" target="_blank" rel="noopener">vue-cli documentation</a>.
    </p>
    <h3>Installed CLI Plugins</h3>
    <ul>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-babel" target="_blank" rel="noopener">babel</a></li>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-typescript" target="_blank" rel="noopener">typescript</a></li>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-pwa" target="_blank" rel="noopener">pwa</a></li>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-eslint" target="_blank" rel="noopener">eslint</a></li>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-unit-jest" target="_blank" rel="noopener">unit-jest</a></li>
    </ul>
    <h3>Essential Links</h3>
    <ul>
      <li><a href="https://vuejs.org" target="_blank" rel="noopener">Core Docs</a></li>
      <li><a href="https://forum.vuejs.org" target="_blank" rel="noopener">Forum</a></li>
      <li><a href="https://chat.vuejs.org" target="_blank" rel="noopener">Community Chat</a></li>
      <li><a href="https://twitter.com/vuejs" target="_blank" rel="noopener">Twitter</a></li>
      <li><a href="https://news.vuejs.org" target="_blank" rel="noopener">News</a></li>
    </ul>
    <h3>Ecosystem</h3>
    <ul>
      <li><a href="https://router.vuejs.org" target="_blank" rel="noopener">vue-router</a></li>
      <li><a href="https://vuex.vuejs.org" target="_blank" rel="noopener">vuex</a></li>
      <li><a href="https://github.com/vuejs/vue-devtools#vue-devtools" target="_blank" rel="noopener">vue-devtools</a></li>
      <li><a href="https://vue-loader.vuejs.org" target="_blank" rel="noopener">vue-loader</a></li>
      <li><a href="https://github.com/vuejs/awesome-vue" target="_blank" rel="noopener">awesome-vue</a></li>
    </ul>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Watch, Emit, Vue } from "vue-property-decorator";

interface objValidate{
    name:String; //string
    count: String | Number; //string或者number
    age?:Number;//age 被定义为可选属性，那么在传对象的时候age就可有可无。
    readonly sex:Boolean;//只读属性，一旦被赋值，不能修改
}

interface ItemObj {
    name: number;
    state: boolean;
    output: string;
}

@Component({
    components:{}
})
export default class HelloWorld extends Vue {
    //接收父组件的参数
  @Prop(String) msg!: string;
  @Prop(String) zlj!: string;
  @Prop(Number) age!: number;


  info: String = 'hello'
  number: number  = 3
  count: string = '纳尼+'
  arr: number[] = [2,7,3,8,5,9,2,6,3]

  //属性监听
  @Watch ('number')
  onNumberChanged(val: string, oldVal: string) {
      console.log(`number:${val}`)

  }
  //属性监听
  @Watch ('count')
  onCountChanged(val: string, oldVal: string):void {
        console.log(`count:${val}`)

    }
  // methods
  //3.0向父组件传值
  @Emit('countAdd')
  countAdd(number: number):void {
      this.number++
      this.count+=this.count
      let obj = {
          name:'孙章',
          count:1,
          age:3.04,
          sex:true
      }
      this.changeObj(obj);
      // this.number++
      //2.0向父组件传值
      // this.$emit('onHelloClick',this.number);
  }
  //生命周期
  created() {
      console.log(`created`)
  }
  mounted() {
      // console.log(`mounted`)
      // console.log(Number.isFinite(this.age))//判断是不是数字
      // console.log(Number.isNaN(this.age))//判断是不是NaN
      // console.log(Number.isInteger(this.age))//判断是不是整数
      // console.log(Number.parseInt(this.count))//整数转化
      // console.log(Number.parseFloat(this.count))//浮点类型转化
      // console.log(Number.isSafeInteger(this.age))//判断是不是数字


      //数组排序去重
      // this.arr = [...new Set(this.arr)]
      // console.log(Array.from(this.arr.sort()))




      let config:ItemObj[] = [{
          name: 2,
          state: true,
          output: 'Y',
      }, {
          name: 3,
          state: false,
          output: 'A',
      }, {
          name: 5,
          state: true,
          output: 'S',
      }, {
          name: 7,
          state: true,
          output: 'B',
      }, {
          name: 9,
          state: true,
          output: 'K',
      }];

      config = [...config, {
          name: 3,
          state: true,
          output: 'D',
      }]
      const newArr = config.reduce((item:any, next) => {
          let hash = {};
          next.state ? item.push(next): '';
          return item
      }, []);
      console.log(newArr);
  }
  //私有方法
  private changeObj(obj:objValidate):void{
      // console.log(this.number)
      // console.log(obj.name);
      // console.log(obj.count);
      obj.name = 'zhanglongji';
      console.log(obj)
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
