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
    <i id="logo" class="fa-solid fa-paper-plane" style="color: #ffffff;"></i>
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

#logo {
  will-change: filter;
  transition: filter 300ms;
}

#logo:hover {
  filter: drop-shadow(1px 1px 1rem rgb(70, 78, 237));
}

h2 {
  background-color: rgba(255, 255, 255, 0);
  border-radius: 10px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.12), 0 1px 2px rgba(0, 0, 0, 0.24);
  transition: all 0.3s cubic-bezier(.25, .8, .25, 1);
}

h2:hover {
  box-shadow: 0 14px 28px rgba(0, 0, 0, 0.25), 0 10px 10px rgba(0, 0, 0, 0.22);
}
</style>
