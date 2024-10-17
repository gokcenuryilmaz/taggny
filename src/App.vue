<template>
  <div class="container">
    <app-tags v-model="tags" color="primary"></app-tags>
    {{ tags }}
    <hr>
    <app-tags v-model="tags2" color="danger"></app-tags>
    {{ tags2 }}
    <hr>
    <app-tags v-model="tags3" color="success"></app-tags>
    {{ tags3 }}
    <hr>
    <app-tags v-model="tags4" color="warning"></app-tags>
    {{ tags4 }}
    <hr>
    <app-tags v-model="tags5" color="info"></app-tags>
    {{ tags5 }}
  </div>
</template>

<script>
import TagsGny from './components/TagsGny.vue';

export default {
  name: 'App',
  components : {
    appTags : TagsGny
  },
  data(){
    return {
      tags : "deneme,test,gökçe",
      tags2 : "bilgisayar,defter,klavye",
      tags3 : "deneme",
      tags4 : "klavye",
      tags5 : "gökçe",
      
    }
  }
}
</script>

<style>
  body{
    font-family: sans-serif;
  }
  
</style>
