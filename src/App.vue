<script>
import axios from 'axios';

export default {
  name: 'App',
  data() {
    return {
      singleEmail: '',
      emailList: []
    }
  },
  mounted() {
    for (let i = 0; i < 10; i++) {
      axios
        .get('https://flynn.boolean.careers/exercises/api/random/mail')
        .then((email) => {
          console.log(email);
          this.singleEmail = email.data.response;
          this.emailList.push(this.singleEmail);
          console.log(this.emailList);
        })
    }
  }

}
</script>

<template>
  <ul v-if="emailList.length == 10">
    <li v-for="(email, index) in emailList">{{ index + 1 }}. {{ email }}</li>
  </ul>
</template>

<style scoped>
ul {
  list-style: none;
}
</style>
