<template lang="html">
  <div >
    <input type="text" v-model="newToDoItem">
    <!-- v-on:click으로 addToDo method가 실행 된다. -->
    <button v-on:click="addToDo"></button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      //input text에 입력되는 값에 따라 ''값이 바뀐다.
      newToDoItem: ''
    }
  },
  methods: {
    addToDo() {
      // newToDoItem data를 가지고 와서 로컬 스토리지에 저장한다.
    localStorage.setItem(this.newToDoItem,this.newToDoItem);

    }
  }
}
</script>

<style lang="css" scoped>
</style>
