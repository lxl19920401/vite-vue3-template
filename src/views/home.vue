<template>
<!--  <div>-->
<!--    ref-->
<!--    {{count}}-->
<!--    <el-button type="primary" @click="add">++</el-button>-->
<!--  </div>-->

  <div>
    reactive
    {{count2}}
    <el-button type="primary" @click="add2">++</el-button>
  </div>
</template>

<script  lang="ts">
  import { defineComponent,ref,reactive,toRefs } from 'vue'
  interface dataProps{
    count2 : number;
    add2:() => void;

  }
  export default defineComponent({
    setup() {
      // const count = ref(0)
      // const add = (()=>{
      //   count.value++
      // })
      const fun:dataProps=reactive({
        count2:0,
        add2:()=>{
          fun.count2++
        }
      })
      return {
        ...toRefs(fun)
        // count,
        // add
      }
    }
  })
</script>

<style scoped></style>
