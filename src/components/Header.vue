<template>
  <div class="header">
    <div class="left">
      <span style="font-size: 20px">{{ state.name }}</span>
    </div>
    <div class="right">右</div>
  </div>
</template>

<script setup>
import { reactive, toRefs } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()
// 声明路由 和 title 对应的键值对
const state = reactive({
  name: 'dashboard'
})

// 监听路由变化方法 afterEach
router.afterEach((to) => {
  // console.log('to', to)
  // to 能获取到路由相关信息
  const { id } = to.query
  state.name = pathMap[to.name]
})
</script>

<style scoped>
.header {
  height: 50px;
  border-bottom: 1px solid #e9e9e9;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;
}
</style>