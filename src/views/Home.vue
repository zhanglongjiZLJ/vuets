<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HomeComponents :age="age" :name="name" />
    <HelloWorld @countAdd="countAdd($event)" :age="age" zlj="zlj" msg="Welcome to Your Vue.js + TypeScript App"/>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import HelloWorld from "@/components/HelloWorld.vue"; // @ is an alias to /src
import HomeComponents from "@/components/HomeComponents.vue";

@Component({
  components: {
    HelloWorld,
    HomeComponents
  }
})
export default class Home extends Vue {
    age: number = 20
    name: string = '张隆基'
    countAdd(val:void):void{
        console.log(val)
    }
}
</script>
