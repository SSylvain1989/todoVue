<template>
<h1>Veille techno</h1>
<Form @add="saveTechno"/>
<br>

<!-- sans les deux points devant technos , on aurait passer au composant une string , là on passe bien la valeur -->
<TechnoList :technos="technos"/>
</template>


<script>

import Form from "@/components/Form";
import TechnoList from "@/components/TechnoList";

import { ref } from '@vue/reactivity';
export default {
  name: 'App',
  components: {
    Form,
    TechnoList
  },
  setup() {
    let technos = ref([]);

    const saveTechno = function(data) {

      technos.value = [...technos.value, { techno : data , id : Date.now()}];

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
