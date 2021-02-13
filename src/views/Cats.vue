<template>
  <div class="">
    <PetTable
      species="cats"
      :pets="cats"
    />
  </div>
</template>
<script>
import { mapState } from 'vuex'
import PetTable from '@/components/PetTable.vue'

export default {
  name: 'Cats',
  components: {
    PetTable
  },
  data: function(){
    return {
    }
  },
  computed: {
    ...mapState([
      'cats'
    ])
  }
}
</script>
<style lang="scss" scoped>
</style>
