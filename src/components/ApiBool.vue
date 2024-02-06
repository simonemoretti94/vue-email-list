<script>
export default {
  name: 'ApiBool',
  props: {
    mail: Array,
  },
}

</script>

<template>
  <div id="main_div" class="col-10 d-flex flex-column  justify-content-evenly  align-items-center mt-1"
    v-for="(mailAddress, index) in mail">
    <h3 class="text-center">Iteration: {{ index }} - {{ mailAddress }}</h3>
  </div>
</template>

<style scoped>
h3 {
  color: var(--fancy-blue);
  text-shadow: -1.5px -1px rgb(197, 197, 197);
}

h3:hover {
  text-decoration: underline;
  font-weight: bolder;
  color: rgba(0, 0, 255, 0.552);
  text-shadow: 0 5px 5px rgba(0, 45, 194, 0.349), 0 5px 5px rgba(0, 45, 194, 0.349);
}

#main_div h3:first-child {
  margin-top: .2rem;
  transform: skew(-5deg);
}
</style>
