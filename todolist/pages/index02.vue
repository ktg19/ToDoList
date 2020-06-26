<template>
<v-layout
    column
    justify-start
    align-start
  >

  <ToDo />
</v-layout>
</template>

<script>
import ToDo from '../components/ToDo.vue'

export default {
  data: function(){
    return {
      test_message: "",
    }
  },
  components: {
    ToDo
  },
  mounted: function(){
  },
}
</script>
