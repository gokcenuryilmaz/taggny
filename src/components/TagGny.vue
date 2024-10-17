<template>
    <span class="tag" :class="selectedTheme" >
      <span class="content">{{ tag }}</span>
      <span class="close" @click="$emit('removeOneTagEvent', index)"> X</span>
    </span>
</template>

<script>
    export default {
      props: ["tag", "index","tagColor"],
      data (){
        return {
          selectedTheme : null
        }
      },
      created(){
        this.selectedTheme = this.tagColor;
      }// bu componenet üretildiğinde selectedTheme dışarıdan gelen tagColor'a eşit olacak
    }
</script>

<style scoped>

  .tag-container {
    border: 1px solid #ccc;
    padding: 20px;
  }
  .tag {
    padding: 10px;
    cursor: default;
    font-size: 14px;
    margin-right: 10px;
    border-radius: 5px;
  }
  .tag .close {
    font-size: 12px;
    cursor: pointer;
  }
  .tag * {
    font-size: 14px;
  }
  .primary{
    color:#004085;
    background-color: #cce5ff;
    border-color: #b6daff;
  }
  .success {
  color: #155724;
  background-color: #d4edda;
  border-color: #c3e6cb;
}

.danger {
  color: #721c24;
  background-color: #f8d7da;
  border-color: #f5c6cb;
}

.warning {
  color: #856404;
  background-color: #fff3cd;
  border-color: #ffeeba;
}

.info {
  color: #0c5460;
  background-color: #d1ecf1;
  border-color: #bee5eb;
}

.secondary {
  color: #383d41;
  background-color: #e2e3e5;
  border-color: #d6d8db;
}

</style>
