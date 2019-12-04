<template>
<div>
  <p><b>{{ title }}</b></p>
<!-- ここから追加 -->
  <form>
    <div>
      <p>Hello, {{ questionnaire.nickName }}</p>
      <label>あだ名：</label>
      <input type="text" name="nickname" placeholder="呼ばれたい名前をどうぞ" v-model="questionnaire.nickName">
    </div>
    <div>
      <label>TwitterID：</label>
      <input type="text" name="belong" value="" placeholder="ないかたはスキップOK">
    </div>
    <div>
      <label>今日の勉強会との関わり：</label>
      <input type="text" name="connection" value="" placeholder="思いの丈をどうぞ！">
    </div>
    <button type="submit">submit</button>
  </form>
<!-- ここまで追加 -->
</div>
</template>

<script>
export default {
  props: {
      title : String
  },/*カンマを追加*/
  /*ここから追加*/
  data: function() {
    return {
      questionnaire: {
        nickName: null,
      }
    }
  }
  /*ここまで追加*/
}
</script>

<style scoped>
</style>
