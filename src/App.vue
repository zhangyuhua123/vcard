<template>
  <div class="app"> 
      <step></step>
  </div>
</template>

<script>
import step from './components/step5.vue';
export default {
  name: 'app',
  components:{
    step
  }
}
</script>
<style>
 html,body{
     height: 100%;
     width: 100%;
 }   

.app{
  height: 100%;
  width: 100%;

}


</style>
