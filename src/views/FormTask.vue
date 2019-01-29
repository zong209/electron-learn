<template>
<div>
<h3>Task Manager</h3>
    <form class="el-padding" @submit.prevent="addTask">
        <Input v-model="task" type="text" placeholder="add task name" style="width:300px"/>
        <Button type="default" html-type="submit">submit</Button>
    </form>
    <Divider></Divider>
    <h3 class="el-padding">Task List</h3>
    <ul class="el-padding">
      <li v-for="(item,index) in tasks" :key='index'>{{ item }}</li>
    </ul>
</div>
</template>

<script>
export default {
  name:'FormTask',
  data(){
  return {
      task:null
    }
  },
  computed:{
    tasks(){
      return this.$store.state.tasks;
    }
  },
  methods:{
    addTask(){
      this.$store.commit('addTask',this.task);
      this.task=null
    }
  }
}
</script>
<style>
.el-padding{
  margin: 10px
}
</style>


