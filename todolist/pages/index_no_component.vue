<template>
  <v-layout
    column
    justify-start
    align-start
  >

  <v-card-title class="headline">Your ToDo List</v-card-title>

  <v-card-text>
      <v-row align="center" v-for="(task, key) in tasks" :key="key"> 
        <!-- v-touch:swipe.left="() => alert(11)" -->
        <v-checkbox
          v-model="includeFiles"
          hide-details
          class="shrink mr-2 mt-0"
        ></v-checkbox>
        <v-text-field label="Task" v-model="tasks[key]" @change="addNewRow"></v-text-field>
        <v-btn tile small class="primary" @click="deleteElement(key)">DELETE</v-btn>
      </v-row>
    </v-card-text>
  </v-layout>
</template>

<script>
import Vue from 'vue'
import Vue2TouchEvents from 'vue2-touch-events'
 
Vue.use(Vue2TouchEvents)

export default {
  data: function(){
    
    return {
      tasks: [],
      localStorageKey: "tasks"
    }
  },
  mounted: function(){
    // localStorage.removeItem(this.localStorageKey)
    this.tasks = JSON.parse(localStorage.getItem(this.localStorageKey))
    // alert(this.tasks)
    if (this.tasks == null || this.tasks.length === 0){
      this.tasks = [""]
    }

    // tasksを自動保存
    setInterval(function(){localStorage.setItem(this.localStorageKey, JSON.stringify(this.tasks))}.bind(this), 3000)
  },
  components: {},
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
  }
}
</script>
