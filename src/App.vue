<script>
  import { defineComponent } from 'vue'
  import { NButton, NInput } from 'naive-ui'
  import mainBlocks from './components/mainBlocks.vue'

  export default defineComponent({
    components: {
      NButton,
      NInput,
      mainBlocks,
    },
    data(){
      return {
        forMsg: "正方",
        againstMsg: "反方",
        topic: "",
        currentStage: "",
      }
    },
  })

</script>
<template>

  <div style="font-size: 50px; display:inline-block; margin-left: 150px;" >辩题：{{topic}} <br> 现在阶段：{{currentStage}}</div>
  <mainBlocks :msg="forMsg" style="margin-top:0px"></mainBlocks>
  <mainBlocks :msg="againstMsg" style="position:absolute; margin-left: 700px; margin-top: -560px;"></mainBlocks>
  <div id="enterboxes">
    辩题：<input type="text" placeholder="输入辩题..." id="inputs" v-model="topic"/>
    <br>
    现在阶段：<input type="text" placeholder="输入现在阶段..." id="inputs" v-model="currentStage"/>
  </div>

</template>
<style scoped>
  #inputs{
    width: 600px;
    height: 30px;
    margin-left: 20px;
    margin-top: 50px;
  }
  #enterboxes{
    font-size: 20px;
    font-family: SourceHanSansCN-Regular-2;
    margin-left: 30px;
  }
</style>