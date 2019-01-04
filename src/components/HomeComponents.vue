<template>
    <div>home组件{{age}}{{name}}
    </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component({
    components:{}
})

export default class HomeComponents extends Vue {
    //接收父组件的参数
    @Prop(Number) age!: number;
    @Prop(String) name!: string;
    //生命周期
    created(){

    }
    mounted(){
        console.log(this.age)
        this.sum()
    }
    sum():void{
        console.log(123123)
    }
}
</script>

<style scoped>

</style>
