<template>
<v-layout
    column
    justify-center
    align-center
  >
  <ToDo :local-storage-key="localStorageKey" />
</v-layout>
</template>

<script>
import Vue from 'vue'
import ToDo from '../components/ToDo.vue'

export default {
  data: function(){
    return {
      test_message: "",
      localStorageKey: "tasks"
    }
  },
  components: {
    ToDo
  },
  mounted: function(){


  },
}
</script>
