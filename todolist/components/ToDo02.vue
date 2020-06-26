<template>
  <v-card>
    <v-card-title class="headline">Your ToDo List</v-card-title>
    <v-card-text>
      <v-row align="center" v-for="(task, key) in tasks" :key="key"> 
        <v-checkbox
          hide-details
          class="shrink"
        ></v-checkbox>
        <v-text-field label="Task" v-model="tasks[key]" @keydown="addNewRow()"></v-text-field>
        <v-btn tile small class="primary" @click="deleteElement(key)">DELETE</v-btn>
      </v-row>
    </v-card-text>
    <v-row id="example-1">
      <v-col v-for="(item, idx) in items" :key="idx">
        {{ item.message }}　{{idx}}
      </v-col>
    </v-row>
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
    /**与えられたkeyのタスクを削除する */
    deleteElement: function (key) {
      const removed = this.tasks.splice(key, 1)
    },
    /**最後の行が空文字でなければ空文字を追加する */
    addNewRow: function (){
      if(this.tasks[this.tasks.length-1]!==""){
        this.tasks.push("")
      }
    }
  },
  watch: {
    
  }
}
</script>
