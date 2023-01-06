<template>
  <div>
    <span>
      <!-- 親で<ScopedChild>内に何も値がなければlastNameのみ表示される -->
      <!-- <slot>{{ user.lastName }}</slot> -->

      <!-- v-bindでuserをバインドする -->
      <!-- (親側ではv-slot:default="slotProps"で受け取る) -->
      <slot :user="user" :message="message">
        {{ user.lastName }}
      </slot>
    </span>
  </div>
</template>

<script>
import { defineComponent, ref } from '@nuxtjs/composition-api'

export default defineComponent({
  setup() {
    const user = ref({
      firstName: 'John',
      lastName: 'Doe',
      age: '25',
      sex: '男性'
    })

    const message = ref()
    message.value = 'Hello Scoped Slot'

    return {
      user,
      message
    }
  },
})
</script>
