<template>
<div id="app">

  <!-- 컴포넌트 추가 -->
  <ToDoHeader></ToDoHeader>
  <ToDoInput v-on:addToDo="addToDo"></ToDoInput>
  <ToDoList v-bind:propsdata="todoItems" @removeTodo="removeTodo"></ToDoList>
  <ToDoFooter v-on:removeAll="clearAll"></ToDoFooter>
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
  props: ['propsdata'],
  data() {



    return {
      //데이터 속성인 todoItems를 선언해준다.
      todoItems: []


    }
  },
  //뷰의 인스턴스가 생성되자마자 뷰 데이터에 접근 할 수 있도록 created() 라이프 사이클 훅에서 데이터를 뷰 데이터로 옮긴다.
  created() {
    //저장된 데이터 값이 0이상일 경우 반복문 실행
    if (localStorage.length > 0) {
      for (var i = 0; i < localStorage.length; i++) {
        //todoItems 배열에 값을 집어 넣는다.
        // push는 배열의 끝 요소에 배열 아이템을 하나씩 추가하는 자바스크립트 내장 API이다.
        this.todoItems.push(localStorage.key(i));
      }
    }
  },
  methods: {
    //로컬 스토리지에 데이터를 추가한다. 매개변수는 ToDoInput에서 올라온 값(=할 일)
    addToDo(todoItem) {
      localStorage.setItem(todoItem, todoItem);
      this.todoItems.push(todoItem);

    },
    //삭제기능
    clearAll() {
      localStorage.clear();
      this.todoItems = [];

    },
    removeTodo(todoItem, index) {
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
    }
  },


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
  @media(min-width:35em) {
  body{margin:0 auto;
      width:40%;
  }


  }
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
