<template>
  <div>
    <ScopedTable :header="header" :items="items"></ScopedTable>

    <!-- 'FIRSTNAME', 'LASTNAME'をあ合わせてNAMEで表示する場合 -->
    <ScopedTable :header="header" :items="items">
      <template #default="{item}">
        <td>{{item.id}}</td>
        <td>{{item.firstName}} {{item.lastName}}</td>
        <td>{{item.email}}</td>
      </template>
    </ScopedTable>


    <!-- Blog -->
    <ScopedBlog>
      <template #title>vue.js</template>
      I'd like to know about $vm.slots.
    </ScopedBlog>
  </div>
</template>

<script>
import { defineComponent, onMounted, ref } from '@nuxtjs/composition-api'
import ScopedTable from '../components/ScopedTable.vue'
import ScopedBlog from '../components/ScopedBlog.vue'
import axios from 'axios'

export default defineComponent({
  components: {
    ScopedTable,
    ScopedBlog
  },
  setup() {
    // 'FIRSTNAME', 'LASTNAME'をあ合わせてNAMEで表示する場合は'ID','NAME','EMAIL'にする
    const header = ref(['ID', 'FIRSTNAME', 'LASTNAME', 'EMAIL'])
    const items = ref([
      {
        id: 1,
        firstName: 'John',
        lastName: 'Doe',
        email: 'john@example.com'
      },
      {
        id: 2,
        firstName: 'John',
        lastName: 'Doe',
        email: 'john2@example.com'
      },
      {
        id: 3,
        firstName: 'John',
        lastName: 'Doe',
        email: 'john3@example.com'
      },
    ])

    // onMounted(async () => {
    //   const url = 'https://jsonplaceholder.typicode.com/users'
    //   const res = await axios.get(url)
    //   items.value = res.data
    //   console.log(items.value, "items")
    // })

    return {
      header,
      items
    }
  },
})
</script>
