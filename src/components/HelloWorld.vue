<template>
  <h1>{{ msg }}</h1>

  <div class="card">
    <el-button type="primary" @click="addCount">
      <el-icon>
        <Plus />
      </el-icon>
      <span>count is {{ store.state.count }}</span>
    </el-button>
    <el-button type="primary" @click="toggleDark()">切换主题</el-button>
    <p>
      Edit
      <code>components/HelloWorld.vue</code> to test HMR
    </p>
  </div>

  <p>
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank">create-vue</a>, the official Vue + Vite
    starter
  </p>
  <p>
    Install
    <a href="https://github.com/johnsoncodehk/volar" target="_blank">Volar</a>
    in your IDE for a better DX
  </p>
  <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
</template>

<script setup lang="ts">
import { useDark, useToggle } from '@vueuse/core'
import { useStore } from 'vuex';

const isDark = useDark()
const store = useStore<{
  count: number
}>()
const toggleDark = useToggle(isDark)
defineProps<{ msg: string }>()

const addCount = () => {
  store.commit('increment')
}

</script>
  
<style scoped>
.read-the-docs {
  color: #888;
}
</style>
