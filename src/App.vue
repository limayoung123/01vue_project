<template>
<ul class="view">
  <li v-for="(item,i ) in product" :key="i">
    {{product[i].title}} <!-- .하고 title을 넣으면 이름만 나오게된다 -->

    </li>
    
</ul>
<banner />
<banner></banner>
</template>

<script>
import vdata from './data.js'
import 명작 from './components/banner.vue'
// 값을 가져와야할 때 공식 import 이름 from '가져 올 위치'
//data.js 문서 첫번째에는 export default(띄어쓰기)값을 넣어줘야함 (보내다)
//이름 안에는 데이터이므로 return 안에 넣어줘야함

export default {
  name: 'App',
  data(){
    return{
      product:vdata,
      
    }
  },
  components:{
    banner:명작
  }
  
}
//name은 마음대로 작성하면됨
//data는 함수형태이므로 (){}안에 작성해야함
</script>

<style>
  *{margin:0; padding: 0; box-sizing: border-box;}
  li{list-style: none;}
  
</style>
