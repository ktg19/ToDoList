<template>
  <v-card>
    <v-card-title class="headline">Your ToDo List</v-card-title>
    <v-card-text>
      <v-row align="center" v-for="(task, key) in tasks" :key="key"> 
        <v-checkbox
          hide-details
          class="shrink"
        ></v-checkbox>
        <v-text-field label="Task" v-model="tasks[key]"></v-text-field>
        <v-btn tile small class="primary" @click="deleteElement(key)">DELETE</v-btn>
      </v-row>
    </v-card-text>
  </v-card>

</template>

<script>
import Vue from 'vue'

export default {
  data: function(){
    return {
      tasks: []
    }
  },
  props: {
    localStorageKey: String,
  },
  mounted: function(){
    this.tasks = JSON.parse(localStorage.getItem(this.localStorageKey))
    if (this.tasks == null || this.tasks.length === 0){
      this.tasks = [""]
    }
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
    tasks: function(newTaskList){
      // 必要に応じて行を追加
      this.addNewRow()
      // ローカルストレージにアイテムを保存
      localStorage.setItem(this.localStorageKey, JSON.stringify(this.tasks))
    }
  }
}
</script>
