<template>
  <div>
    <button @click="on">Click</button>
    <slot v-if="display"></slot>
    <hr>
    <!-- ScopedSlotを利用し、親でボタンをクリックし表示・非表示を切り替える -->
    <slot name="activator" :on="on"></slot>
    <slot v-if="display"></slot>
  </div>
</template>

<script>
import { defineComponent, ref } from '@nuxtjs/composition-api'

export default defineComponent({
  setup() {
    const display = ref(true)

    // ボタンをクリックすると親で定義したのリストの表示・非表示を切り替えられる
    const on = () => {
      return display.value = !display.value
    }

    return {
      display,
      on
    }
    
  },
})
</script>
