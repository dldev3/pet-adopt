<template>
  <div id="">
    <h1>{{ animal.name }} ({{ $route.params.species }})</h1>
    <p>{{animal.age}} years old</p>
    <p>Breed: {{animal.breed}}</p>
    <p>Gender: {{animal.gender}}</p>
  </div>
</template>
<script>
/* eslint-disable no-alert, no-console */
import { mapState } from 'vuex'

export default {
  data: function(){
    return {
      animal: {}
    }
  },
  computed: {
  ...mapState([
    'cats',
    'dogs'
    ])
  },
  mounted() {
      const animal = this[this.$route.params.species][this.$route.params.id]
      this.animal = animal;
    }

}
</script>
<style lang="scss" scoped>
</style>
