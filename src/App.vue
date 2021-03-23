<template>
<h1>Veille techno</h1>
<Form @add="saveTechno"/>
<br>
<ul>
  <li v-for="tech in technos" :key="tech.id">{{tech.techno}}</li>
</ul>

</template>


<script>

import Form from "@/components/Form";
import { ref } from '@vue/reactivity';
export default {
  name: 'App',
  components: {
    Form,
  },
  setup() {
    let technos = ref([]);

    const saveTechno = function(data) {
      console.log("app | saveTechno", data);
      technos.value = [...technos.value, { techno : data , id : Date.now()}];
            console.log("app | saveTechno", technos.value);

}
return {
    saveTechno,
    technos
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
