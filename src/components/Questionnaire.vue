<template>
<div>
  <p><b>{{ title }}</b></p>
<!-- ここから追加 -->
  <form v-on:submit.prevent="onSubmit">
    <div>
      <p>Hello, {{ questionnaire.nickName }}</p>
      <label>あだ名：</label>
      <input type="text" name="nickname" placeholder="呼ばれたい名前をどうぞ" v-model="questionnaire.nickName">
    </div>
    <div>
      <label>TwitterID：</label>
      <input type="text" name="belong" value="" placeholder="ないかたはスキップOK" v-model="questionnaire.twitterID">
    </div>
    <div>
      <label>今日の勉強会との関わり：</label>
      <input type="text" name="connection" value="" placeholder="思いの丈をどうぞ！">
    </div>
    <p class="error"> {{ validation.result }}</p>
    <button v-on:click="checkForm">submit</button>
  </form>
<!-- ここまで追加 -->
</div>
</template>

<script>
export default {
  props: {
      title : String
  },
  data: function() {
    return {
      questionnaire: {
        nickName: null,
        twitterID: null,//追加
      },/*ここにカンマを追加*/
      /*ここから追加*/
      validation:{
        result: "",
      }
      /*ここまで追加*/
    }
  },/*ここにカンマを追加*/
  /*ここから追加*/
  methods: {
    checkForm: function(event){
      var booleanTwitterID = false
      var inputTwitterID = this.questionnaire.twitterID

      if(!this.checkString(inputTwitterID)){
        this.validation.result = "半角英数字および_のみで入力ください"
      }
      else if(!this.checkMaxLength(inputTwitterID)){
        this.validation.result = "50文字以内で入力ください"        
      }
      else {
        booleanTwitterID = true
      }

      console.log(booleanTwitterID);

      if(booleanTwitterID === true){
        this.validation.result=""
        if(!inputTwitterID){
          this.$router.push('/done')
        }
        else{
          alert('Hello,' + inputTwitterID + '!')
        }
      } 
      event.preventDefault()
    },
    checkString: function(inputdata){
      var regExp = /^[a-zA-Z0-9_]*$/
      return regExp.test(inputdata);
    },
    checkMaxLength: function(inputdata){
      var booleanLength = false
      inputdata.length < 50 ? booleanLength = true : booleanLength = false;
      return booleanLength
    }
  }
  /*ここまで追加*/
}
</script>

<style scoped>
/* ここから追加 */
.error { color: red; }
/* ここまでを追加 */
</style>
