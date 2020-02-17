<template lang="html">

   <section>
<transition-group name="list" tag="ul">
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
</transition-group>
   </section>

</template>

<script>
export default {
  props: ['propsdata'],


  methods: {
    //아이콘(쓰레기통) 클릭시 삭제하는 기능이 실행되도록 하는 method
    // 할 일과 인덱스를 매개변수로 받아와 출력한다.
    removeTodo(todoItem, index) {
      this.$emit('removeTodo', todoItem, index);
    }
  }
}
</script>
<style lang="css" scoped>
    .list-enter-active,.list-leave-active{
     transition:all 1s;
    }
    .list-enter,.list-leave-to{
    opacity:0;
    transform:translateY(30px);

    }
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
