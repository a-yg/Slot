<template>
  <div>
    <h1><slot name="title">Title</slot></h1>
    <p><slot></slot></p>
    <p>Slot:{{ slotValue }}</p>
  </div>
</template>

<script>
import { computed, defineComponent, ref } from '@nuxtjs/composition-api'

export default defineComponent({
  setup() {
    const slots = ref()
    const slotvalue = computed(() => {
      return slots.value
    })
  
    return {
      slots,
      slotvalue
    }
  },
})
</script>
