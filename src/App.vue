<template>
<!--  <img alt="Vue logo" src="./assets/logo.png" />-->
<!--  <HelloWorld msg="Hello Vue 3 + TypeScript + Vite23test" />-->
  <el-container class="main-container">
    <el-header>Vite2.x + Vue3.x + TypeScript Starter</el-header>
    <el-container>
      <el-aside width="200px">
        <el-menu default-active="0">
          <el-menu-item :index="index+''" @click="navClick(item)" v-for="(item,index) in menuList">
            {{item.name}}
          </el-menu-item>
        </el-menu>
      </el-aside>
      <el-main>
        <router-view />
      </el-main>
    </el-container>
  </el-container>

</template>
<script lang="ts">
  import { defineComponent, reactive, toRefs, onMounted, watch } from 'vue'
  import { useRouter } from 'vue-router'
  export interface NavItem {
    path: string
    name: string
    isActive?: boolean
  }
  export default defineComponent({
    setup() {
      const router = useRouter()
      const reactiveData = reactive({
        menuList:[
          {name:'home',path:'/'},
          {name:'vuex',path:'/vuex'},
          {name:'axios',path:'/axios'},
        ],
        navClick:(e:NavItem)=>{
          router.push(e.path)
        }
      })
      return{
        ...toRefs(reactiveData)
      }
    }
  })
</script>
<style>
  *{
    margin: 0;
    padding: 0;
  }
  html,body,#app,.main-container{
    width: 100%;
    height: 100%;
  }
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
.el-menu{
  height: 100%;
}
.el-header{
  display: flex;
  align-items: center;
  font-weight: bold;
  border-bottom: 1px solid #e6e6e6;
}

</style>
