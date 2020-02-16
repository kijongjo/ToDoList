<template lang="html">
  <div class="clearAllContainer">
    <!-- 버튼역할 태그 clearTodo method가 실행된다. -->
  <span class="clearAllBtn" @click="clearTodo">Clear All</span>
  </div>
</template>

<script>
export default {
  methods:{
    clearTodo(){
      //localStorage의 data가 비워진다.
     localStorage.clear();

    }
  }
}
</script>

<style lang="css" scoped>
.clearAllContainer{
     width:8.5rem;
     height:50px;
     line-height:50px;
     background-color:white;
     border-radius:5px;
     margin:0 auto;

}
.clearAllBtn{
  color:#e20303;
  display:black;
}
</style>
