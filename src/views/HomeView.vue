<script setup lang="ts">
import { ref, onMounted } from 'vue'

const time = ref(10)

// 重定向操作
const redirect = () => { 
  console.log("%c ⚠️ %c Redirecting... ",
  "color: #fff; margin: 1em 0; padding: 5px 0; background: #fcf4dc;",
  "margin: 1em 0; padding: 5px 0; background: #efefef;");
  // 获取浏览器链接地址
  const url = window.location.href;
  // 替换链接地址中的 ".com" 为 ".cn"
  const newUrl = url.replace(".com", ".cn");
  // 设置浏览器的链接地址
  window.location.href = newUrl;
}

onMounted(() => {
  
  console.log("%c ⚠️ %c Regional restriction! ",
          "color: #fff; margin: 1em 0; padding: 5px 0; background: #fcf4dc;",
          "margin: 1em 0; padding: 5px 0; background: #efefef;");

  console.log("%c ⚠️ %c Retrieving server... ",
  "color: #fff; margin: 1em 0; padding: 5px 0; background: #fcf4dc;",
  "margin: 1em 0; padding: 5px 0; background: #efefef;");

  // 每秒 time--
  const countdown = setInterval(
    () => {
      time.value--
      if (time.value === 0) {
        // 倒计时结束，执行其他操作 
        clearInterval(countdown) // 清除定时器
        redirect() // 重定向操作
      }
    },
    1000
  )
})
</script>

<template>
  <main>
    <h1>This website isn't currently supported in your country!</h1>
    <span>Don't worry, this is normal. 
      Detecting available sites and about to redirect 
      <span class="time">[ {{ time }}s ]</span>
      .
    </span>
  </main>
</template>

<style scoped lang="scss">
main {
  h1 {
    font-weight: bold;
  }

  span {
    font-weight: bold;
    font-size: large;

    &.time {
      color: var(--color-warning9);
    }
  }
}
</style>