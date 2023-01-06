<template>
  <div>
    <table border="1">
      <thead>
        <tr>
          <th v-for="row_name in header" :key="row_name">{{ row_name }}</th>

        </tr>
      </thead>
      <tbody>
        <tr v-for="(item,index) in items" :key="index">
          <!-- <td v-for="(value,index) in item" :key="index">{{ value }}</td> -->

          <!-- 'FIRSTNAME', 'LASTNAME'をあ合わせてNAMEで表示する場合 -->
          <slot :item="item">
            <td v-for="(value,index) in item" :key="index">{{ value }}</td>
          </slot>
          
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import { defineComponent } from '@nuxtjs/composition-api'

export default defineComponent({
  props: {
    header: {
      type: Array,
      required: true,
    },
    items: {
      type: Array
    }
  },
  setup() {
    
  },
})
</script>
