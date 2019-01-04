<template>
    <div>home组件
        <div>{{age}}</div>
    </div>
</template>

<script lang="ts">
import { Prop, Vue } from "vue-property-decorator";
export default class HomeComponents extends Vue {
    //接收父组件的参数
    @Prop(Number) age!: number;
    mounted(){
        console.log(this.age)
    }
}
</script>

<style scoped>

</style>
