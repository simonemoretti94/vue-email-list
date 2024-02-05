<script>
import ApiBool from './components/ApiBool.vue';

export default {
  name: 'app',
  components: {
    ApiBool,
  },
  data() {
    return {
      mailArray: [],
    }
  },
  mounted() {
    console.log('ready to load the API\'S');

    for (let i = 0; i < 10; i++) {

      axios
        .get('https://flynn.boolean.careers/exercises/api/random/mail')
        .then((boolApiResponse) => {
          //console.log('API response: ', boolApiResponse);
          this.mailArray.push(boolApiResponse.data.response);
        });
    }

    console.log(this.mailArray);
  }
}
</script>

<template>
  <header class="d-flex flex-row justify-content-center ">
    <i class="logo fa-solid fa-paper-plane" style="color: #ffffff;"></i>
    <h2 class="text-white text-center">vue-email-list</h2>
  </header>
  <main class="d-flex flex-column  justify-content-evenly align-items-center">
    <ApiBool :mail="mailArray"></ApiBool>
  </main>
</template>

<style scoped>
header {
  border-bottom: groove 2px white;
}

.logo {
  /* height: 6em;
  padding: 1.5em; */
  will-change: filter;
  transition: filter 300ms;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}

.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
