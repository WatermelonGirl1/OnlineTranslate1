<template>
  <div class="row" id="translateForm">
      <div class="col-md-6 col-md-offset-3">
           <form class="well" v-on:submit="formSubmit" >
                <input class="form-control" type="text" v-model = 'inputTxt' placeholder="请输入要翻译的内容">
                <select class="form-control" v-model="language">
                    <option value="en">Engilish</option>
                    <option value="ru">Russian</option>
                    <option value="ko">Korean</option>
                    <option value="ja">Janpanese</option>
                </select>
                <input class="btn btn-primary" type="submit" value="翻译">
            </form>
      </div>

  </div>
</template>

<script>


export default {
  name: 'translateForm',
  data:function(){
      return{
          inputTxt:"",
          language:''
      }
  },
  methods:{
      formSubmit:function(e){
          e.preventDefault();
          this.$emit('noticeHandle',this.inputTxt,this.language);
        //   alert(this.language);
      }
  }
}
</script>

<style>

</style>
