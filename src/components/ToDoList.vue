<template lang="html">

   <section>
     <ul>
      <!-- 데이터를 받아와 v-for를 이용해 출력하기 -->
       <li v-for="todoItem in todoItems" class="shadow">
       <i class="checkBtn fas fa-check" aria-hidden="true"></i>
         {{todoItem}}
       <span class="removeBtn" type="button" @click="removeTodo"(todoItem,index)>
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
   min-height:50px}

</style>
