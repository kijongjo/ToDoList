<template lang="html">
   <section>
     <ul>
      <!-- 데이터를 받아와 v-for를 이용해 출력하기 -->
      <!-- key로써 todoItem이 지정되고 index가 같이 출력되도록 설정한다. index는 뷰 내에서 알아서 관리된다. -->
       <li v-for="(todoItem,index) in propsdata" :key="todoItem" class="shadow">
         <!-- check 아이콘 -->
       <i class="checkBtn fas fa-check" aria-hidden="true"></i>
         {{todoItem}}
         <!-- 쓰래기통 아이콘 클릭시 removeTodo 이벤트가 실행되며 할 일과 index값이 매개변수로써 작용한다.  -->
       <span class="removeBtn" type="button" @click="removeTodo(todoItem,index)">
       <i class="far fa-trash-alt" aria-hidden="true"></i>
       </span>
       </li>
     </ul>
   </section>
</template>

<script>
export default {
  data() {
    return {
      //배열로 선언
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
    //아이콘(쓰레기통) 클릭시 삭제하는 기능이 실행되도록 하는 method
    // 할 일과 인덱스를 매개변수로 받아와 출력한다.
    removeTodo(todoItem, index) {
    // localStorage에서 todoItem을 삭제하라
    localStorage.removeItem(todoItem);
    // todoItems라는 배열의 index에서 1만큼 삭제하라.
    this.todoItems.splice(index,1);
    }
  }
}
</script>
<style lang="css" scoped>
   ul{
   list-style-type:none;
   padding-left:0px;
   margin-top:0;
   text-align:left;
   }

  li{
     display:flex;
     min-height:50px;
     height:50px;
     line-height:50px;
     margin:0.5rem 0;
     padding:0 0.9rem;
     background:white;
     border-radius:5px;
    }

  .checkBtn{
    line-height:45px;
    color:#62acde;
    margin-right:5px;
    }

  .removeBtn{
    margin-left:auto;
    color:#de4343;
}
</style>
