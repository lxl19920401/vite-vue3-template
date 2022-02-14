<template>
  <div class="axios">
    <span>axios</span>
    <el-button type="primary"  @click="getUserInfo">
      点击获取接口信息
    </el-button>
    <el-descriptions title="User Info" v-loading="loading">
      <el-descriptions-item  label="name:"> {{ userInfo?.name }}</el-descriptions-item>
      <el-descriptions-item label="bio:">{{ userInfo?.bio }}</el-descriptions-item>
      <el-descriptions-item label="blog:">{{ userInfo?.blog }}</el-descriptions-item>
    </el-descriptions>
  </div>
</template>
<script lang="ts">
import { defineComponent,ref } from 'vue'
import axios from '../utils/axios'

export default defineComponent({
  setup() {
    const userInfo = ref(null)
    const loading = ref(false)
    const getUserInfo = (()=>{
      loading.value = true
      axios
        .get('/users/XPoet')
        .then((res) => {
          userInfo.value = res.data
          loading.value = false
          console.log(userInfo)
        })
        .catch((err) => {
          console.log('err: ', err)
        })
    })

    return {
      loading,
      getUserInfo,
      userInfo
    }
  }
})
</script>
<style lang="less">
.axios {

}
</style>
