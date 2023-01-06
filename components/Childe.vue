<template>
  <div>
    <!-- <slot>名無し</slot>とすると名無しがデフォルトになる -->
    <p>この人の名前は<slot></slot>です。</p>
    <hr>
    <ul>
      <li>名前：<slot>名無し</slot></li>
      <li>年齢：<slot name="age">記入なし</slot></li>
      <li>性別：<slot name="sex">不明</slot></li>
    </ul>
  </div>
</template>

<script>
import { defineComponent, ref } from '@nuxtjs/composition-api'

export default defineComponent({
  setup() {
    
  },
})
</script>
