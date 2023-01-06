<template>
  <div>
    <!-- Childに挟むことでChild.vueの<slot></slot>部分に代入される -->
    <Childe>
      <!-- <template v-slot:default>で囲ってもOK -->
      John Doe
      <!-- templateタグ内でv-slotでnameを指定すると子で設定したname属性値に対応できる -->
      <template v-slot:age>25</template>
      <template #sex>男性</template>
      <!-- v-slotは#に置き換えられる -->
    </Childe>
  </div>
</template>

<script>
import { defineComponent} from '@nuxtjs/composition-api'
import Childe from '../components/Childe.vue'

export default defineComponent({
  components: {
    Childe
  },
  setup() {

  },
})
</script>
