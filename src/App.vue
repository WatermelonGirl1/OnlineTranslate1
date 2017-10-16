<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5>简单 / 易用 / 便捷</h5>
    <translateForm v-on:noticeHandle = 'tanslateHandle'> </translateForm>
    <transOutput v-text="tanslatedtext"></transOutput>
  </div>
</template>

<script>
import TranslateForm from './components/translateForm'
import TransOutput from './components/translateOutput'
export default {
  name: 'app',
  data:function(){
      return {
          tanslatedtext:''
      }
  },
  components: {
      TranslateForm,TransOutput
  },
  methods:{
      tanslateHandle:function(con,language){
           this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20171011T080901Z.7907cf2c20766f82.d84b362ba487712480a194cf9c1fe62d331ab756 &lang='+language+'&text='+con)
            .then((responce)=>{
               this.tanslatedtext = responce.body.text[0];
            //    alert( this.tanslatedtext);
            })
                }
            }
          }
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
