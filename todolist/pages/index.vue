<template>
<v-layout
    column
    justify-start
    align-start
  >
  <input v-model="test_message" placeholder="edit me">
  <p>Message is: {{ test_message }}</p>

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
