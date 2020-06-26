<template>
  <v-card>
    <v-card-title class="headline">Your ToDo List</v-card-title>
    <v-card-text>
      <v-row align="center"> 
        <v-checkbox
          hide-details
          class="shrink"
        ></v-checkbox>
        <v-text-field label="Task"></v-text-field>
        <v-btn tile small class="primary">DELETE</v-btn>
      </v-row>
    </v-card-text>
  </v-card>

</template>

<script>
import Vue from 'vue'

export default {
  data: function(){
    return {
      tasks: ['掃除', '選択', '買い物', '昼食準備']
    }
  },
  props: {
    // localStorageKey: String,
  },
  mounted: function(){
    
  },
  methods: {
    
  },
  watch: {
    
  }
}
</script>
