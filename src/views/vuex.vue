<template>
  vuex
  <p>store doubleCount is: {{ count }}</p>
  <el-button type="primary" @click="double">double</el-button>
</template>

<script lang="ts">
  import { defineComponent, reactive, computed, toRefs } from 'vue'
  import { useStore } from 'vuex'
  export default defineComponent({
    name: 'Vuex',
    setup() {
      const store = useStore()
      const reactiveData = reactive({
        count: computed(() => store.state.count)
      })
      const double = () => {
        store.commit('increment')
      }
      return {
        ...toRefs(reactiveData),
        double
      }
    }
  })
</script>


<style scoped></style>
