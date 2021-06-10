<template>
<banner />
<!-- <banner></banner> -->

<!-- modal -->
<div class="black-bg" v-if="proView==true">
  <!-- 조건문하기 -->
  <div class="white-bg">
     <img v-bind:src="product[proNum].image">
    <div>{{product[proNum].title}}</div> 
    <div>{{product[proNum].price}}</div>
    <div>{{product[proNum].content}}</div>
    <button v-on:click="proView=false">닫기</button>
    <!-- 팝업창에 닫기버튼 만들어줘야함 -->
    <!-- proNum으로 받아주는것 -->
  </div>
</div>

<ul class="view">
  <li v-for="(item,i ) in product" :key="i">
    <img v-bind:src="product[i].image">
     <!-- .하고 title을 넣으면 이름만 나오게된다 -->
    <div>{{product[i].title}}<span v-on:click="proView=true; proNum=i">[상세보기]</span></div> 
    <!-- 상세보기를 클릭할때 팝업창이 나오게 해야함 proView라는 변수만든거임(data에도 지정해줘야한다=false값으로) -->
    <!-- proNum을 넣기위해서는 "안에 ;로 연결해주기" -->
    <div>{{product[i].price}}</div>
    </li>
    
</ul>

</template>

<script>
import vdata from './data.js'
import banner from './components/banner.vue'
// 값을 가져와야할 때 공식 import 이름 from '가져 올 위치'
//data.js 문서 첫번째에는 export default(띄어쓰기)값을 넣어줘야함 (보내다)
//이름 안에는 데이터이므로 return 안에 넣어줘야함

export default {
  name: 'App',
  data(){
    return{
      proNumt:0,
      proView:false,
      product:vdata,
      
    }
  },
  components:{
    banner:banner
    //이름이 같으면 하나만 넣어도된다
    //이름에 _ 가 들어가면 ''을 적어줘야한다
    //ex) 'm_banner':banner
  }
  
}
//name은 마음대로 작성하면됨
//data는 함수형태이므로 (){}안에 작성해야함
</script>

<style>
html,body{height: 100%};
  *{margin:0; padding: 0; box-sizing: border-box;}
  li{list-style: none;}
  img{width:100%;}
  .view li{margin-bottom:20px;}
  .black-bg{position:fixed;widht:100%;height:100%;background:rgba(0,0,0,0.4);
  z-index:1; top:0;display:flex;
  justify-content: center; align-items: center;}
  .white-bg{width:80%;background: #fff;border-radius:5px;padding: 20px;}
</style>
