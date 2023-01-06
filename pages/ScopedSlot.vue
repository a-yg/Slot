<template>
  <div>
    <!-- v-slot:defaultを利用してデータを受け取る -->
    <!-- slotPropsは任意なのでなんでもOK -->
    <ScopedChilde v-slot:default="slotProps">
      {{ slotProps.user.firstName }}
      <!-- 子で定義したuserのfirstNameが表示される -->
    </ScopedChilde>

    <ScopedChilde #default='dataFromChild'>
      {{ dataFromChild }}
      <!-- { "user": { "firstName": "John", "lastName": "Doe", "age": "25", "sex": "男性" } }と表示される -->

      <p>{{ dataFromChild.user.firstName }}{{ dataFromChild.user.lastName }}</p>
      <p>{{ dataFromChild.user.age }}/{{ dataFromChild.user.sex }}</p>
    </ScopedChilde>

    <!-- 渡される変数名がわかっているのであれば{}内に変数名で受け取れる -->
    <ScopedChilde v-slot:default="{ user }">
      <p>{{user.firstName}} {{user.lastName}}</p>
      <p>{{user.age}} / {{user.sex}}</p>
    </ScopedChilde>

    <!-- 子でデータが複数ある場合{}内に複数指定すればOK -->
    <ScopedChilde v-slot:default="{ user,message }">
      <p>{{user.firstName}} {{user.lastName}}</p>
      <p>{{ message }}</p>
    </ScopedChilde>


    <hr>
    <!-- 子のボタンをクリックすると↓のリストの表示・非表示を切り替えられる -->
    <ScopedMethods>
      <ul>
        <li>List1</li>
        <li>List2</li>
        <li>List3</li>
      </ul>
    </ScopedMethods>

    <!-- 親でボタンをクリックしリストの表示・非表示を切り替える -->
    <ScopedMethods>
      <template v-slot:activator="{on}">
        <button @click="on">
          Click it
        </button>
      </template>
      <ul>
        <li>List1</li>
        <li>List2</li>
        <li>List3</li>
      </ul>
    </ScopedMethods>
  </div>
</template>

<script>
import { defineComponent } from '@nuxtjs/composition-api'
import ScopedChilde from '../components/ScopedChilde.vue'
import ScopedMethods from '../components/ScopedMethods.vue'

export default defineComponent({
  components: {
    ScopedChilde,
    ScopedMethods
  },
  setup() {
    
  },
})
</script>
