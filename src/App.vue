<template>
<div id="app">

  <!-- 컴포넌트 추가 -->
  <ToDoHeader></ToDoHeader>
  <ToDoInput v-on:addTodo="addTodo"></ToDoInput>
  <ToDoList v-bind:propsdata="todoItems"></ToDoList>
  <ToDoFooter></ToDoFooter>
</div>
</template>
<script type="text/javascript">

</script>

<!-- 컴포넌트 파일의 내용을 불러오는 코드 -->
<script>
import ToDoHeader from './components/ToDoHeader.vue'
import ToDoList from './components/ToDoList.vue'
import ToDoInput from './components/ToDoInput.vue'
import ToDoFooter from './components/ToDoFooter.vue'
export default {
  data() {

    props:['propsdata'],

    return {
 //데이터 속성인 todoItems를 선언해준다.
      todoItems: []


    }
  },
   metods:{
//로컬 스토리지에 데이터를 추가한다.
     addTodo(todoItem){
       localStorage.setItem(todoItem,todoItem);
       this.todoItems.push(todoItem);




     }},


  //최상위 컴포넌트에 다른 컴포넌트 등록
  components: {
    'ToDoHeader': ToDoHeader,
    'ToDoInput': ToDoInput,
    'ToDoList': ToDoList,
    'ToDoFooter': ToDoFooter
  }

}
</script>

<style>
body {
  /* 텍스트를 중심으로 */
  text-align: center;
  background-color: #F6F6F8;
}

input {
  /* 테두리 모양 정의 */
  border-style: groove;
  width: 200px;
}

button {
  border-style: groove;
}

.shadow {
  /* 할일 입력 인풋 박스와 할 일 아이템의 그림자 정의 */
  box-shadow: 5px 10px 10px rgba(0, 0, 0.03);
}
</style>
