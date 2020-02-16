<template lang="html">
  <div class="inputBox shadow" >
<!-- v-on:keyup.enter는 input박스에서 엔터를 눌렀을 때 발동 된다. -->
    <input type="text" v-model="newToDoItem" placeholder="Type what you have to do"
     v-on:keyup.enter="addToDo">
  <!-- 버튼 대신 사용되도록 속성 값을 설정해 주었다. -->
    <span class="addContainer" v-on:click="addToDo">
    <!-- + 아이콘을 사용 하도록 아이콘을 가지고온다 -->
      <i class="addBtn fas fa-plus" aria-hidden="true"></i></span>

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
      if (this.newToDoItem != "") {
        //input 박스에 입력된 텍스트의 압뒤 공백 문자열 제거
        var value = this.newToDoItem && this.newToDoItem.trim();
        //value값을 같이 전달한다.
        this.$emit('addTodo',value);
        //input 박스의 입력 값을 초기화 한다.
        this.clearInput();
      }

    },
    clearInput() {
      this.newTodoItem = '';
    }
  }
}
</script>

<style lang="css" scoped>
 input:focus{
   /* 선스타일 지정 : 아무것도 없음 */
   outline:none;}
.inputBox{
  background:white;
  height:50px;
/* 인풋 박스에 입력되는 텍스트의 중앙 정렬을 위해 설정 */
  line-height:50px;
  border-radius:5px;
}
.inputBox input{
 border-style:none;
 font-size:0.9rem;

}
.addContainer{
 /* 할 일 추가 버튼의 위치 정의 */
     float:right;
     background:linear-gradient(to right, #6478FB,#8763FB);
     display:block;
     width:3rem;
     border-radius:0 5px 5px 0;
}
 .addBtn{
   color:white;
 /* 할일 추가 버튼의 수직 정렬 정의 */
   vertical-align:middle;
 }
</style>
