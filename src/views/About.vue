<template>
  <div class="about">
    <h1>This is an about page</h1>
    <Questionnaire title="アンケート"></Questionnaire>
  </div>
</template>

<script>
import Questionnaire from '@/components/Questionnaire.vue'

export default {
  name: 'about',
  components: {
    Questionnaire
  }
}
</script>
